---
title: Powershell – Habilitando conexão remota
author: blogadminjoaoheytor
type: post
date: 2016-07-09T02:54:04+00:00
url: /2016/07/08/powershell-habilitando-conexao-remota/
dsq_thread_id:
  - 4971596389
php_everywhere_code:
  - 'Just put [php_everywhere] where you want the code to be executed.'
categories:
  - Otimização

---
Uma das tendências que veio para ficar é o Powershell da Microsoft! A cada versão do Windows a Microsoft aprimora mais e mais está ferramenta, fazendo com que seja possível fazermos as mesmas coisas tanto em linha de comando quanto via interface gráfica! Para alguns, talvez isso não faça muito sentido porém, quando você começa a gerenciar muitos servidores, é extremamente necessário otimizarmos nosso tempo e esforço a fim de não perdermos muito tempo com tarefas repetitivas!

Como forma de aprimorar minhas habilidades com o PowerShell, estou me desafiando a fazer a maior quantidade possível de tarefas através dele!! Tarefas básicas como: criar usuários/grupos, resetar senha de usuários, alterar grupo, checar logs, dentre outras coisas que um administrador de sistemas precisa fazer!

E a dica que pretendo dar hoje é justamente para as pessoas que estão querendo iniciar suas tarefas junto ao PowerShell.

<!--more-->

## OBJETIVO:

Gerenciar remotamente qualquer servidor, independente da minha máquina cliente estar em um ambiente de domínio ou não.

## CENÁRIO:

Para atingirmos este objetivo, contaremos com o seguinte cenário:

  * Ambiente com Active Directory instalado, com várias versões do Windows Server (2008, 2008 R2 e 2012 R2);
  * Notebook com **Windows 10 HOME**, que não faz parte do Active Directory!

## PRÁTICA:

  * Para iniciar nossos testes, iremos abrir o Windows Powershell.<figure id="attachment_1115" aria-describedby="caption-attachment-1115" style="width: 300px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1115 size-full" src="/img/2016/07/001.png" alt="Abrindo Powershell" width="300" height="108" />][1]<figcaption id="caption-attachment-1115" class="wp-caption-text">Abrindo Powershell</figcaption></figure> 

  * Agora tentaremos efetuar uma conexão remota usando o cmdlet Enter-PSSession:<figure id="attachment_1116" aria-describedby="caption-attachment-1116" style="width: 635px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1116 size-full" src="/img/2016/07/002.png" alt="Ingressando em uma máquina remota" width="635" height="91" />][2]<figcaption id="caption-attachment-1116" class="wp-caption-text">Ingressando em uma máquina remota</figcaption></figure> 

**Explicação:**

  1. **Enter-PSSession:** Cmdlet para iniciar uma conexão interativa com um computador remoto;
  2. **-ComputerName IP/NOME:** Especifica o nome ou endereço IP da máquina que estamos efetuando conexão;
  3. **-Credential USUÁRIO:** Usuário que será utilizado para efetuar está conexão

  * Será retornando o seguinte erro:<figure id="attachment_1117" aria-describedby="caption-attachment-1117" style="width: 859px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1117 size-full" src="/img/2016/07/003.png" alt="Erro ao tentar conectar remotamente em uma máquina" width="859" height="197" />][3]<figcaption id="caption-attachment-1117" class="wp-caption-text">Erro ao tentar conectar remotamente em uma máquina</figcaption></figure> 

O erro mostrado é:

> _“Enter-PSSession : Falha ao conectar ao servidor remoto 192.168.88.1 com a seguinte mensagem de erro: O cliente WinRM não pode processar a solicitação. Se o esquema de autenticação for diferente de Kerberos ou se o computador cliente não tiver ingressado em um domínio, o transporte HTTPS deverá ser usado ou o computador de destino deverá ser adicionado à opção de configuração TrustedHosts. Use winrm.cmd para configurar TrustedHosts. Observe que os computadores na lista TrustedHosts podem não ser autenticados. Você pode obter mais informações sobre isso executando o seguinte comando: winrm help config. Para obter mais informações, consulte o tópico da Ajuda about\_Remote\_Troubleshooting.”_

Vejam como é importante prestarmos atenção a todos os erros que nos é informado! Sempre! Neste caso, o erro é porque a nossa máquina destino não confia em nossa máquina cliente **(Não está na lista de _TrustedHosts_)**.

Para corrigir tal problema, precisarmos executar o _cmdlet **Enable-PSRemoting**_ junto ao servidor:<figure id="attachment_1118" aria-describedby="caption-attachment-1118" style="width: 574px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1118 size-full" src="/img/2016/07/004.png" alt="Enable-PSRemoting -Force" width="574" height="129" />][4]<figcaption id="caption-attachment-1118" class="wp-caption-text">Enable-PSRemoting -Force</figcaption></figure> 

**Explicação:** O comando _**Enable-PSRemoting -Force**_ além de habilita o _**WinRM**_ também criar regras de exceção junto ao firewall para permitir o acesso remoto.

<p style="text-align: center">
  <strong>Atenção: É necessário executar esse comando usando o Powershell elevado (Como administrador).</strong>
</p>

Lembram no início do post onde disse que estarei usando uma máquina em _standalone_ (Que não faz parte do domínio)? Caso está também seja sua a situação, ainda teremos alguns comandos pela frente! Caso contrário, nossa configuração está terminada e já podemos efetuar a conexão remota para o servidor!

## CONFIGURANDO O TRUSTEDHOSTS:

Como ambas as máquinas não se _conhecem_, precisamos fazer com que nosso servidor confie em nossa máquina cliente!

Para isso, teremos que adicionar o IP do nosso equipamento na lista de hosts confiáveis:<figure id="attachment_1119" aria-describedby="caption-attachment-1119" style="width: 872px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1119 size-full" src="/img/2016/07/005.png" alt="Setando Trustedhosts" width="872" height="134" />][5]<figcaption id="caption-attachment-1119" class="wp-caption-text">Setando Trustedhosts</figcaption></figure> 

**Explicação:**

  1. O _cmdlet_ **Set-Item WSMan:\localhost\client\TrustedHosts *** faz com que o servidor aceite a conexão de qualquer origem! Não restrição alguma do cliente que estará efetuando a conexão! Nossa única segurança, é a credencial exigida para conexão! Por questões de segurança, seria **recomendável** substituir o asterisco pelo **IP da(s) máquina(s) cliente**.

Também é necessário executarmos o mesmo comando em nossa máquina cliente! Lembrem-se que está configuração não é bidirecional! É necessário fazer com que ambas as máquinas se conheçam e confiem em si mesmas.

## REINICIANDO O SERVIÇO:

Devido a alteração das configurações dos _hosts_ confiáveis que fizemos, temos que reiniciar o serviço do _WinRM_:<figure id="attachment_1120" aria-describedby="caption-attachment-1120" style="width: 576px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1120 size-full" src="/img/2016/07/006.png" alt="Reiniciando o WinRM" width="576" height="68" />][6]<figcaption id="caption-attachment-1120" class="wp-caption-text">Reiniciando o WinRM</figcaption></figure> 

## EFETUANDO UMA CONEXÃO REMOTA:

Como resultando das nossas configurações, podemos finalmente efetuar uma conexão remota junto ao nosso servidor usando:<figure id="attachment_1122" aria-describedby="caption-attachment-1122" style="width: 671px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1122 size-full" src="/img/2016/07/008.png" alt="Utilizando o Enter-PSSession" width="671" height="48" />][7]<figcaption id="caption-attachment-1122" class="wp-caption-text">Utilizando o Enter-PSSession</figcaption></figure> 

Pronto! Nossa configuração está completa!

Além do **Enter-PSSession**, também podemos utilizar outros _cmdlets_ para efetuar comandos remotos, como o **Invoke-Command**!

Espero que tenham gostado de mais essa dica!!! Qualquer dúvida, não deixem de entrar em contato!

 [1]: /img/2016/07/001.png
 [2]: /img/2016/07/002.png
 [3]: /img/2016/07/003.png
 [4]: /img/2016/07/004.png
 [5]: /img/2016/07/005.png
 [6]: /img/2016/07/006.png
 [7]: /img/2016/07/008.png