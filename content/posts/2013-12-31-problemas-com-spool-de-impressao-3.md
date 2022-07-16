---
title: Problemas com Spool de Impressão 3
author: blogadminjoaoheytor
type: post
date: 2013-12-31T13:54:32+00:00
url: /2013/12/31/problemas-com-spool-de-impressao-3/
dsq_thread_id:
  - 2191307816
categories:
  - Clientes

---
Dando continuidade ao último post, onde falamos um método rápido para consertar o spooler de impressão, aqui vamos ver uma solução bem prática e funcional que podemos aplicar quando estamos com tempo livre na máquina do usuário (Lembro que peguei essa dica no site do <a href="http://www.microsoft.com/brasil/technet/default.mspx" target="_blank" class="broken_link">Technet Brasil</a>, porém não lembro o autor).

Primeira coisa que devemos fazer é remover todos os softwares de impressoras instalados no Painel de Controle / Programas e Recursos.

Em seguida, devemos parar o spooler de impressão através do Prompt de Comando em modo Administrador (Iniciar / Todos os Programas / Acessórios / Com o botão direito do mouse clique em Prompt de comando ( Executar como Administrador)).

Execute o comando abaixo e pressione ENTER:

> <p align="center">
>   <b>NET STOP SPOOLSV</b>
> </p>

Acessar a pasta Spool (Computador, aponte para **C:WindowsSystem32spool**).

Agora devemos excluir a pasta “**Printers**”.

Exclua também o conteúdo da pasta &#8220;**W32x86**&#8220;, que está localizada em **C:WindowsSystem32spooldrivers.**

Nesse momento, devemos acessar o **Editor de Registro do Windows** (Iniciar e na pesquisa digite **regedit** e pressione ENTER).

Acesse esse caminho:

> <p style="text-align: center">
>   <strong>HKEY_LOCAL_MACHINESYSTEMCurrentControlSetServicesSpooler</strong>
> </p>

Do lado direito localize a chave “**DependOnService**”.

Clique com o botão direito do mouse e em seguida **Modificar**, digite o valor abaixo.

> <p style="text-align: center">
>   <strong>RPCSS</strong>
> </p>

Ainda no Editor de Registro , acesse a pasta:

> <p style="text-align: center">
>   <strong>HKEY_LOCAL_MACHINESystemCurrentControlSetControlPrintProviders</strong>
> </p>

Deixe somente as subpastas abaixo, excluindo todas as outras:

  * Internet Print Provider;
  * LanMan Print Services.

Devemos navegar até a pasta:

> <p style="text-align: center">
>   <strong>HKEY_LOCAL_MACHINESystemCurrentControlSetControlPrintMonitors</strong>
> </p>

E excluir as subpastas, deixando somente as listadas abaixo (E qualquer outra com o nome de Microsoft ).

  * Local Port;
  * Statndard TCP;
  * USB Monitor.

Mais uma vez, ainda dentro do Editor de Registro, vamos navegar até:

> <p style="text-align: center">
>   <strong>HKEY_LOCAL_MACHINESystemCurrentControlSetControlPrintPrinters</strong>
> </p>

Exclua as pastas que fazem referencia a impressoras como HP, Lexmark, Epson etc.

Também é necessário excluir a pasta abaixo ( Algumas vezes não é possível ou a pasta não existe):

> <p style="text-align: center">
>   <strong>HKEY_LOCAL_MACHINESYSTEMCurrentControlSetEnumLPTENUM</strong>
> </p>

Por fim, feche o Editor de Registro, reinicie o computador e acesse o site do fabricante da impressora para baixar e instalar o driver mais recente do dispositivo.

Essa solução resolve problemas de spooler de impressão parando, impressoras sumindo entre outros&#8230;

Espero que tenham gostado&#8230;