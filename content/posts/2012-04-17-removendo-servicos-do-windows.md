---
title: Removendo Serviços do Windows
author: blogadminjoaoheytor
type: post
date: 2012-04-17T18:50:41+00:00
url: /2012/04/17/removendo-servicos-do-windows/
dsq_thread_id:
  - 2478711094
categories:
  - Clientes

---
Hoje vou mostrar para vocês outra dica ótima que aprendi quebrando a cabeça em um antigo cliente.

Inúmeras vezes temos problemas com os serviços do Windows. Problemas esses que podem ser desde serviços que não eram para estar rodando até de aplicativos que já removemos, mas o dito cujo do serviço insiste em continuar por lá.

Antes de tudo, vamos ao comando **_Executar_** e digitar **services.msc**:

<p style="text-align: center">
  <a href="/img/sites/4/2012/04/img01.png"><img loading="lazy" class="alignnone size-full wp-image-520" title="img01" src="/img/sites/4/2012/04/img01.png" alt="" width="345" height="177" /></a>
</p>

Na tela de Serviços que se abre, devemos nos atentar ao nome completo do serviço que queremos remover:

<p style="text-align: center">
  <a href="/img/sites/4/2012/04/img02.png"><img loading="lazy" class="alignnone size-full wp-image-521" title="img02" src="/img/sites/4/2012/04/img02.png" alt="" width="406" height="456" /></a>
</p>

Em seguida, dentro do **_Prompt de Comando_** iremos trabalhar com o comando **_SC DELETE_**, como abaixo mostrado:

<p style="text-align: center">
  <a href="/img/sites/4/2012/04/img03.png"><img loading="lazy" class="alignnone size-full wp-image-522" title="img03" src="/img/sites/4/2012/04/img03.png" alt="" width="438" height="86" /></a>
</p>

Notem que no meu caso, o nome do meu serviço era **_JOAOHEYTOR_**, portanto utilizei o seguinte comando:

> **SC delete JOAOHEYTOR** 

Pronto! Viram como é fácil nos livrar de qualquer serviço do Windows! Pois é, espero que tenham gostado!

Um forte abraço a todos!!!!