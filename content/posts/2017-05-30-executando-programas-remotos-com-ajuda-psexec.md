---
title: Executando programas remotos com a ajuda do PsExec
author: João Heytor
type: post
date: 2017-05-30T03:12:41+00:00
url: /2017/05/30/executando-programas-remotos-com-ajuda-psexec/
dsq_thread_id:
  - 5862238686
categories:
  - Otimização

---
Fala galera!

Dando continuidade as aplicabilidades do utilitário _**PsExec**_, hoje a ideia é demonstrarmos como podemos rodar um script copiando-o para várias máquinas cujo nomes estão em um arquivo de texto!

Essa dica funciona muito bem quando estamos trabalhando em um ambiente de domínio com o _Active Directory_.

<!--more-->

Antes de continuarmos, lembro que já explorarmos este utilitário em outras postagens:

  * <a href="https://www.joaoheytor.com/2015/03/13/forcar-atualizacao-de-politica-de-grupo-remotamente-usando-psexec/" target="_blank" rel="noopener noreferrer">Forçar atualização de Política de Grupo remotamente usando PsExec</a>
  * <a href="https://www.joaoheytor.com/2017/05/11/script-para-remover-internet-explorer-11-10-e-9/" target="_blank" rel="noopener noreferrer">Script para remover Internet Explorer 11, 10 e 9</a>

A primeira coisa que devemos fazer para atingirmos nosso objeto é criar um arquivo de texto com o nome de todas as máquinas que necessitamos rodar nosso script. Lembro que é necessário um nome de máquina por linha!

Neste exemplo, vou criar um arquivo de texto com o nome &#8220;**Computadores.txt**&#8221; cujo conteúdo se resume a:

> COODMTZ453  
> COODMTZ418  
> COODMTZ16  
> COODMTZ13  
> COODMTZ416  
> COODMTZ505

Estarei salvando este arquivo direto na unidade &#8220;_C:_&#8221; junto com o **PsExec.exe** (Caso ainda não tenha feito download, <a href="https://technet.microsoft.com/en-us/sysinternals/bb897553.aspx" target="_blank" rel="noopener noreferrer"><strong>clique aqui</strong></a> para baixa-lo).

Nosso próximo passo é criar o script que desejamos copiar e executar nas máquinas remotas! Para este exemplo, usarei o script disponibilizado no post que discutimos como remover o Internet Explorer (Versões 9, 10 e 11).

O conteúdo do nosso arquivo, que chamarei script.bat, também deve ser salvo na unidade &#8220;C:&#8221; e se resumo as seguintes linhas

> @echo off  
> echo Removendo IE11  
> FORFILES /P %WINDIR%\servicing\Packages /M Microsoft-Windows-InternetExplorer-\*11.\*.mum /c “cmd /c echo Removendo pacote @fname && start /w pkgmgr /up:@fname /quiet /norestart”

Agora que temos tudo pronto, é hora de iniciar nossos testes!! Devemos abrir o _prompt de comando_ (vulgo **cmd.exe**), navegarmos até o local onde está salvo nossos arquivos (**psexec.exe, script.bat e computadores.txt**). Antes de executarmos o utilitário, vamos digitar:

> PsExec .exe -h

O sufixo &#8220;**-h**&#8221; funciona em quase todos os utilitários do _Windows_. Ele nos retorna o &#8220;**ajuda**&#8221; do programa, com parâmetros necessários, exemplos e outras informações de uso. Os parâmetros que precisamos prestar atenção e que utilizaremos hoje são:

> **@file:** PsExec executará o comando em cada um dos computadores listados em um arquivo;
> 
> **-u:** Específica o usuário que poderá executar a ação que queremos;
> 
> **-h:** Se o computador estiver rodando Windows Vista ou superior, ele executará o processo em &#8220;modo elevado&#8221;;
> 
> **-c:** Copia o programa especificado para a máquina remota para execução.

Temos inúmeras outras funções porém, para este caso estaremos usando apenas estes parâmetros. Portanto, nossa linha de comando deverá ser:

> **PsExec.exe @C:\Computadores.txt -u meudominio\usuario_admin -h -c C:\Script.bat**

Ao apetamos o ENTER, a primeira coisa que será solicitado é a senha do usuário que passamos através do parâmetro &#8220;**-u&#8221;**.

Pronto! O _PsExec_ tentará efetuar conexão junto a todas as máquinas presentes no arquivo de texto, em seguida copiara o arquivo _bat_ e o executará usando o usuário que informamos.