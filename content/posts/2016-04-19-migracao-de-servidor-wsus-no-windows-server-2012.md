---
title: Migração de Servidor WSUS no Windows Server 2012
author: blogadminjoaoheytor
type: post
date: 2016-04-19T22:07:57+00:00
url: /2016/04/19/migracao-de-servidor-wsus-no-windows-server-2012/
php_everywhere_code:
  - 'Just put [php_everywhere] where you want the code to be executed.'
dsq_thread_id:
  - 4760745745
categories:
  - Servidores

---
O case da semana é referente a migração de servidores WSUS! Para quem não sabe, WSUS é uma _role_ do Windows Server para controle dos _updates_ dos programas da Microsoft.

Essa dica é bem útil para implantarmos um servidor de contingência ou até mesmo a migração do serviço para um outro equipamento (Em alguns casos, também há a segmentação do serviço WSUS, que também pode ser implementada seguindo praticamente os mesmos passos que descreverei).

<!--more-->

Essa necessidade ocorreu está semana em um cliente, onde estamos migrando alguns serviços para nuvem e um desses serviços é justamente o WSUS!

Abaixo teremos a configuração completa, do momento da instalação do WSUS até sua configuração!

Vamos lá, mãos a massa!

Primeira coisa, dentro do _Server Manager_ do Windows Server 2012, devemos ir no ícone _Manage_ e escolher _Add Roles and Features_:<figure id="attachment_1001" aria-describedby="caption-attachment-1001" style="width: 300px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1001 size-medium" title="Serve Manager - Tela inicial" src="/img/2016/04/001-300x111.png" alt="Serve Manager - Tela inicial" width="300" height="111" />][1]<figcaption id="caption-attachment-1001" class="wp-caption-text">Serve Manager &#8211; Tela inicial</figcaption></figure> <figure id="attachment_1002" aria-describedby="caption-attachment-1002" style="width: 300px" class="wp-caption aligncenter">[<img loading="lazy" class="wp-image-1002 size-medium" title="Serve Manager - Instalação de Role e Features" src="/img/2016/04/002-300x213.png" alt="Serve Manager - Instalação de Role e Features" width="300" height="213" />][2]<figcaption id="caption-attachment-1002" class="wp-caption-text">Serve Manager &#8211; Instalação de Role e Features</figcaption></figure> 

<p style="text-align: left">
  Devemos avançar até o ponto que devemos escolher as <em>Server Roles</em>. Nesse ponto, iremos selecionar a role <em>Windows Server Update Services</em>.
</p><figure id="attachment_1003" aria-describedby="caption-attachment-1003" style="width: 300px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1003 size-medium" title="Serve Manager - Instalação de Role e Features" src="/img/2016/04/003-300x211.png" alt="Serve Manager - Instalação de Role e Features" width="300" height="211" />][3]<figcaption id="caption-attachment-1003" class="wp-caption-text">Serve Manager &#8211; Instalação de Role e Features</figcaption></figure> 

Assim que clicamos em _Next_, nos é solicitado para instalarmos algumas _features_ que são necessárias para o correto funcionamento do WSUS. Podemos aceitar as configurações padrões e clicar em _Add Features_.<figure id="attachment_1004" aria-describedby="caption-attachment-1004" style="width: 300px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1004 size-medium" title="Serve Manager - Instalação de Role e Features" src="/img/2016/04/004-300x211.png" alt="Serve Manager - Instalação de Role e Features" width="300" height="211" />][4]<figcaption id="caption-attachment-1004" class="wp-caption-text">Serve Manager &#8211; Instalação de Role e Features</figcaption></figure> 

O próximo passo da instalação do WSUS é referente a qual pasta usaremos para armazenamento dos _updates_ baixados (Lembrando que existem duas configurações para os updates: Baixar e Armazenar junto ao servidor WSUS ou fazer com que os clientes façam download diretamente do site da Microsoft):<figure id="attachment_1005" aria-describedby="caption-attachment-1005" style="width: 300px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1005 size-medium" title="WSUS - Local para Armazenar os Updates" src="/img/2016/04/005-300x209.png" alt="WSUS - Local para Armazenar os Updates" width="300" height="209" />][5]<figcaption id="caption-attachment-1005" class="wp-caption-text">WSUS &#8211; Local para Armazenar os Updates</figcaption></figure> 

Como este servidor tem apenas uma unidade, deixei no diretório _**C:\WSUS**_.

Ao clica em _Next_, teremos que efetuar algumas configurações iniciais do WSUS:<figure id="attachment_1006" aria-describedby="caption-attachment-1006" style="width: 300px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1006 size-medium" title="WSUS - Configurações Iniciais" src="/img/2016/04/006-300x217.png" alt="WSUS - Configurações Iniciais" width="300" height="217" />][6]<figcaption id="caption-attachment-1006" class="wp-caption-text">WSUS &#8211; Configurações Iniciais</figcaption></figure> <figure id="attachment_1007" aria-describedby="caption-attachment-1007" style="width: 300px" class="wp-caption aligncenter">[<img loading="lazy" class="wp-image-1007 size-medium" title="WSUS - Configurações Iniciais" src="/img/2016/04/007-300x219.png" alt="WSUS - Configurações Iniciais" width="300" height="219" />][7]<figcaption id="caption-attachment-1007" class="wp-caption-text">WSUS &#8211; Configurações Iniciais</figcaption></figure> 

Podemos ir clicando em _Next_ até o item &#8220;**_Choose Upstream Serve_**&#8220;:

&nbsp;<figure id="attachment_1013" aria-describedby="caption-attachment-1013" style="width: 300px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1013 size-medium" title="WSUS - Choose Upstream Server" src="/img/2016/04/008a-300x220.png" alt="WSUS - Choose Upstream Server" width="300" height="220" />][8]<figcaption id="caption-attachment-1013" class="wp-caption-text">WSUS &#8211; Choose Upstream Server</figcaption></figure> 

Aqui é onde toda a mágica ocorre! É necessários selecionarmos a segunda opção &#8220;**_Synchronize from another Windows Server Update Services server_**&#8220;. Ao fazermos isso, é habilitado a opção **_Server Name_** e **_Port number_**, onde devemos informar o endereço e a porta, respectivamente, do nosso servidor WSUS atual. Antes de clicarmos em continuar, é necessário também marcarmos a opção &#8220;_**This is a replica of the upstream server**_&#8220;.

Na próxima tela, é apresentado para escolhermos se já queremos iniciar o sincronismo entre os servidores WSUS ou não.

Para o sincronismo iniciar, devemos clicar em _**Start Connecting**_.<figure id="attachment_1009" aria-describedby="caption-attachment-1009" style="width: 300px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1009 size-medium" title="WSUS - Iniciando sincronismo" src="/img/2016/04/009-300x220.png" alt="WSUS - Iniciando sincronismo" width="300" height="220" />][9]<figcaption id="caption-attachment-1009" class="wp-caption-text">WSUS &#8211; Iniciando sincronismo</figcaption></figure> <figure id="attachment_1010" aria-describedby="caption-attachment-1010" style="width: 300px" class="wp-caption aligncenter">[<img loading="lazy" class="wp-image-1010 size-medium" title="WSUS - Iniciando sincronismo" src="/img/2016/04/010-300x220.png" alt="WSUS - Iniciando sincronismo" width="300" height="220" />][10]<figcaption id="caption-attachment-1010" class="wp-caption-text">WSUS &#8211; Iniciando sincronismo</figcaption></figure> 

Após alguns minutos, já é possível clicarmos em _**Next**_ e acompanharmos a sincronização através do item **_Syncronizations,_** que fica ao lado esquerdo do painel do WSUS:<figure id="attachment_1011" aria-describedby="caption-attachment-1011" style="width: 300px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1011 size-medium" title="WSUS - Syncronizations" src="/img/2016/04/011-300x171.png" alt="WSUS - Syncronizations" width="300" height="171" />][11]<figcaption id="caption-attachment-1011" class="wp-caption-text">WSUS &#8211; Syncronizations</figcaption></figure> 

<p style="text-align: left">
  Pronto! Agora é aguardar a sincronização estar concluída que ele migrará as atualizações aprovadas/negadas e os grupos de equipamentos.
</p>

<p style="text-align: left">
  Em seguida, podemos ir em <strong><em>Options</em></strong>, <strong><em>Update Source and Proxy Server</em></strong> e marcar a opção <strong><em>Synchronize from Microsoft Update</em></strong> para fazer com que nosso servidor volte a pesquisar as atualizações diretamente no serviço da Microsoft, e não mais fique subordinado ao nosso outro servidor WSUS.
</p>

<p style="text-align: left">
  Uma ressalva que preciso lembrar, é que ele não migra as máquinas, é necessário alterar o endereço do servidor WSUS nos clientes (Seja via GPO ou manualmente).
</p>

<p style="text-align: left">
  Como mencionei no começou do post, fiz essa migração para uma máquina na nuvem porém, já tinha um endereço DNS externo para onde meus clientes estavam apontados (Por padrão, adotamos aqui a nomenclatura https://wsus.empresa.com.br), o que facilitou a alteração do domínio dos clientes, já que precisei apenas alterar o endereço do DNS.
</p>

<p style="text-align: left">
  Espero que tenham gostado e qualquer coisa, deixe seu comentário.
</p>

 [1]: /img/2016/04/001.png
 [2]: /img/2016/04/002.png
 [3]: /img/2016/04/003.png
 [4]: /img/2016/04/004.png
 [5]: /img/2016/04/005.png
 [6]: /img/2016/04/006.png
 [7]: /img/2016/04/007.png
 [8]: /img/2016/04/008a.png
 [9]: /img/2016/04/009.png
 [10]: /img/2016/04/010.png
 [11]: /img/2016/04/011.png