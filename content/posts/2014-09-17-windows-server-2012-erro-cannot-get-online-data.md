---
title: Windows Server 2012 – Erro Cannot get online data
author: João Heytor
type: post
date: 2014-09-17T10:15:59+00:00
url: /2014/09/17/windows-server-2012-erro-cannot-get-online-data/
dsq_thread_id:
  - 3048124112
categories:
  - Servidores

---
Salve galera!

Ontem efetuando uma checagem preventiva em um dos servidores que gerencio, me deparei com algo demasiadamente estranho: Ao abrir o Server Manager do Windows Server 2012, todos os meus serviços ( _AD DS / AD LDS / Hyper-V / DHCP / DNS, etc, etc _) estavam com aquela &#8220;**tarja  vermelha**&#8221; no item &#8220;**Manageability**&#8220;, informando o erro &#8220;**Online &#8211; Cannot get online data**&#8220;.

O que mais me causou espanto, na verdade foi que em todos os serviços estavam com este erro.

No log do servidor, encontrei o evento: &#8220;**Events from &#8216;ADAM.Events.xml&#8217; could not be enumerated**.&#8221; O que também não me deu nenhuma luz&#8230;

Como este era um servidor que já estava funcionando há algum tempo, pensei que estava tudo configurado. Porém, ao pesquisar no site da Microsoft, vi que esse erro é referente à algum serviço Pós-Instalação que não havia sido configurado.

Checando os serviços, resolvi executar o wizard do **AD LDS** (_Active Directory Lightweight Directory Services Setup Wizard, dentro do menu tools_). Para minha surpresa, ao termina-lo, todos os meus serviços ficaram normais.

Espero que essa dica ajuda também meus amigos administradores.

Caso seu problema seja outro, um ótimo ponto de partida são sempre os materiais oficiais, como por exemplo:

  * <a href="http://social.technet.microsoft.com/wiki/contents/articles/13443.windows-server-2012-server-manager-troubleshooting-guide-part-i-overview.aspx" target="_blank">Windows Server 2012 &#8211; Server Manager Troubleshooting Guide, Part I: Overview</a>
  * <a href="http://social.technet.microsoft.com/wiki/contents/articles/13444.windows-server-2012-server-manager-troubleshooting-guide-part-ii-troubleshoot-manageability-status-errors-in-server-manager.aspx" target="_blank">Windows Server 2012 &#8211; Server Manager Troubleshooting Guide, Part II: Troubleshoot Manageability Status Errors in Server Manager</a>

&nbsp;