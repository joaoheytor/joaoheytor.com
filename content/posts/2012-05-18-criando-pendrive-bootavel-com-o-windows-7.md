---
title: Criando pendrive bootável com o Windows 7
author: João Heytor
type: post
date: 2012-05-18T17:08:15+00:00
url: /2012/05/18/criando-pendrive-bootavel-com-o-windows-7/
dsq_thread_id:
  - 2181210034
categories:
  - Clientes

---
Olá povo, como vão?

Com a crescente popularização dos netbooks, muitos de nossos amigos estão encontrando um novo problema. Como instalar o Sistema Operacional se não temos um drive de CD/DVD ?? Como já comentei há algum tempo atrás (Ver tópico: **<a href="https://joaoheytor.com/ubuntu-grave-seu-cd-ou-crie-seu-drive-usb/" target="_blank">Ubuntu, Grave seu CD ou crie seu drive USB</a>**), existe há possibilidade de criarmos um pen drive totalmente inicializável a partir de uma imagem do Microsoft Windows 7.

Para facilitar nossa vida, a própria Microsoft desenvolveu uma ferramenta chamada “Windows 7 USB/DVD Download Tool” (Download em: [http://www.microsoftstore.com/store/msstore/html/pbPage.Help\_Win7\_usbdvd_dwnTool][1]).

Após efetuar o download, basta insta-lo. Basicamente é um passo a passo como outro qualquer, sem nenhuma configuração adicional.

Ao abri-lo, temos a seguinte tela:

<p style="text-align: center">
  <img loading="lazy" class="aligncenter  wp-image-554" title="Img001" src="/img/sites/4/2012/05/Img001.png" alt="" width="501" height="260" />
</p>

É nessa tela onde devemos selecionar onde está a imagem do nosso Windows 7. Após escolhermos onde está a imagem do SO, basta clicar-los em NEXT.

<p style="text-align: center">
  <img loading="lazy" class="aligncenter  wp-image-555" title="Img002" src="/img/sites/4/2012/05/Img002.png" alt="" width="504" height="264" />
</p>

Nesse segundo, o software nos dá duas possibilidades: USB Device e DVD. Ou seja, você deseja criar um pen drive (por exemplo) ou um DVD inicializável. No nosso caso, obviamente, iremos escolher USB Device.

<p style="text-align: center">
  <img loading="lazy" class="aligncenter  wp-image-553" title="Img003" src="/img/sites/4/2012/05/Img003.png" alt="" width="501" height="262" />
</p>

Por fim, selecionamos qual a unidade de nosso pen drive. Como podem notar, aqui na minha máquina não tenho nenhum pen drive, então ele me informa que não há dispositivos USB  detectados. No caso de vocês que estão criando um pen drive bootável, basta seleciona-lo nesta lista, clicar em BEGIN COPYING e aguardar.

Pronto, seu pen drive está totalmente inicializável e pronta para ser instalado em qualquer dispositivo que tenha entrada USB.

Ah, não se esqueçam que é necessários entrar no **SETUP** (Configuração da BIOS) da máquina e colocar o primeiro boot (_First Boot_) para _USB Device_.

 [1]: http://www.microsoftstore.com/store/msstore/html/pbPage.Help_Win7_usbdvd_dwnTool