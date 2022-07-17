---
title: Script para remover Internet Explorer 11, 10 e 9
author: João Heytor
type: post
date: 2017-05-12T01:18:53+00:00
url: /2017/05/11/script-para-remover-internet-explorer-11-10-e-9/
featured_image: /wp-content/uploads/2017/05/ie11-logo.png
dsq_thread_id:
  - 5809028559
categories:
  - Otimização

---
Olá pessoal,

Há alguns dias, em um de nossos clientes, pegamos um sério problema que envolve a utilização do Internet Explorer 11. Após algum tempo procurando a solução, recorrendo aos canais de comunicação oficial, comunidade, fóruns e especialistas, resolvemos temporariamente voltar para o IE 10. Isso se fez necessário devido a incompatibilidade que o IE11 apresentou em relação aos nossos demais sistemas.

Após efetuar algumas pesquisas e testes, tal necessidade foi atendida utilizando o seguinte script:

> @echo off  
> echo Removendo IE11  
> FORFILES /P %WINDIR%\servicing\Packages /M Microsoft-Windows-InternetExplorer-\*11.\*.mum /c “cmd /c echo Removendo pacote @fname && start /w pkgmgr /up:@fname /quiet /norestart”

Salve como **RemoveIE11.bat** e execute como Administrador! Pronto! O Internet Explorer 11 será removido sem problemas! **ATENÇÃO** a tag **/norestart** que impede a reinicialização do sistema! Para a correta remoção, o ideal seria reiniciarmos o equipamento assim que a remoção for concluída.

É interessante observar que o script pode ser facilmente adaptador para também remover o IE 10 ou IE 9! Para isso, altere a parte do código que se refere a versão do navegador:

**Exemplo do IE 10:**

> FORFILES /P %WINDIR%\servicing\Packages /M Microsoft-Windows-InternetExplorer-\*10.\*.mum /c “cmd /c echo Removendo pacote @fname && start /w pkgmgr /up:@fname /quiet /norestart”

**Exemplo do IE 9:**

> FORFILES /P %WINDIR%\servicing\Packages /M Microsoft-Windows-InternetExplorer-\*9.\*.mum /c “cmd /c echo Removendo pacote @fname && start /w pkgmgr /up:@fname /quiet /norestart”

Aqui utilizamos este script em conjunto com o utilitário **PsExec**, que serve para executar comandos em máquinas remotas! Mas isso é assunto para um próximo post! 😀