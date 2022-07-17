---
title: Windows Server – Como deletar Unidades Organizacionais bloqueadas
author: João Heytor
type: post
date: 2014-03-04T22:34:41+00:00
url: /2014/03/04/windows-server-como-deletar-unidades-organizacionais-bloqueadas/
dsq_thread_id:
  - 2360557255
categories:
  - Servidores

---
<p style="text-align: justify">
  Olá Administradores de plantão. Hoje vamos ver uma dica bem útil que as vezes nos fazem perder um certo tempo, principalmente para quem está acostumando com as &#8220;novas&#8221; versões do Windows Server.
</p>

Quando estamos desenvolvendo a estrutura do nosso Active Directory ou, simplesmente quando estamos efetuando uma remodelação de nossa estrutura, pode ser que encontremos um problema ao tentar remover uma Unidade Organizacional, como este:

<p style="text-align: center">
  <a href="/img/sites/4/2014/03/image.jpg"><img loading="lazy" class="size-medium wp-image-720 aligncenter" alt="image" src="/img/sites/4/2014/03/image-300x118.jpg" width="300" height="118" /></a>
</p>

<p style="text-align: justify">
  Isso da pelo fato de na hora da criação da OU, por padrão vem marcado o item de &#8220;proteger contra exclusão acidental&#8221;.
</p>

<p style="text-align: justify">
  Para conseguirmos prosseguir, precisamos clicar com o botão direito na OU que desejamos excluir e, escolher propriedades.
</p>

<p style="text-align: justify">
  Em seguida, devemos ir na aba &#8220;objeto&#8221; e desmarcar o item &#8220;Proteger objeto contra exclusão acidental.
</p>

[<img loading="lazy" class="size-medium wp-image-723 aligncenter" alt="image" src="/img/sites/4/2014/03/image1-270x300.jpg" width="270" height="300" />][1]

&nbsp;

Agora é só excluirmos a OU normalmente.

Legal né&#8230; Esperemos que gostem.

Um forte abraço!

 [1]: /img/sites/4/2014/03/image1.jpg