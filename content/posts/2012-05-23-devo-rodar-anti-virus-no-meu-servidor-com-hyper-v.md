---
title: Devo rodar anti-vírus no meu servidor com Hyper-V ?
author: blogadminjoaoheytor
type: post
date: 2012-05-23T03:30:42+00:00
url: /2012/05/23/devo-rodar-anti-virus-no-meu-servidor-com-hyper-v/
dsq_thread_id:
  - 2188139754
categories:
  - Servidores

---
Olá pessoas, como vão? Vamos hoje falar de mais uma dica bem legal que vi no Technet. Abaixo transcrevo o post total:

<p align="justify">
  <em>Recebi algums emails com essa pergunta, e todo mundo responderia essa pergunta com um sim bem sonoro certo ? Bom, a verdade é que a Microsoft recomenda que a role de Hyper-V seja habilitada no Windows Server 2008 R2 CORE e que <strong>nenhuma aplicação seja instalada</strong> nesse servidor, <strong>inclusive o software de anti-vírus</strong> ! O software do anti-virus deve ser instalado apenas nos guests.</em>
</p>

<p align="justify">
  <em>Mas Robson, e se eu estiver rodando Windows Server 2008 R2 Full e não a versão CORE ? </em>
</p>

_Bom, eu recomendo que você repense essa estratégia, pois o CORE foi concebido para rodar aplicações específicas e certamente vai ter melhor performance e um downtime muito menor._  
_Enquanto isso você deve instalar o software de anti-vírus e excluir os seguintes arquivos / diretórios:_  
_Arquivos: Vmms.exe, Vmswp.exe, VMSWP.exe e CLUSSVC.exe_  
_Diretórios: todos os diretórios que contem arquivos VHDs e arquivos de configuração das virtual machines._

<p align="justify">
  <em>Algums links importantes sobre o assunto:</em>
</p>

<p align="justify">
  <em>Problemas Causados por Anti-virus no Hyper-V: <a href="http://support.microsoft.com/kb/961804">http://support.microsoft.com/kb/961804</a></em>
</p>

<p align="justify">
  <em>Planejando a Segurança do Hyper-V: <a href="http://technet.microsoft.com/en-us/library/cc974516.aspx">http://technet.microsoft.com/en-us/library/cc974516.aspx</a></em>
</p>

Fonte: <a href="http://blogs.technet.com/b/robsonsilva/archive/2009/10/29/devo-rodar-anti-v-rus-no-meu-servidor-com-hyper-v.aspx" target="_blank">Technet</a>

Pois é, bem interessante isso né&#8230; gostei porque faz referência a um post um tanto quanto antigo aqui do blog (**Lista de exclusão para os anti-vírus, <https://joaoheytor.com/lista-de-exclusao-para-os-anti-virus/>**), onde postei alguns arquivos que devemos sempre excluir da verificação dos antivírus dos nossos servidores.

Fica aqui a dica para quem está com essa dúvida e possui o Hyper-V instalado!