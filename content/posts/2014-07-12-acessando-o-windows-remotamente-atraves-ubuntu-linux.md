---
title: Acessando o Windows remotamente através do Ubuntu (Linux)
author: blogadminjoaoheytor
type: post
date: 2014-07-12T16:55:21+00:00
url: /2014/07/12/acessando-o-windows-remotamente-atraves-ubuntu-linux/
dsq_thread_id:
  - 2916089374
categories:
  - Clientes

---
A dica de hoje é simples: Acessar uma máquina com Windows através de qualquer distribuição Linux.

Nesse exemplo, estou usando o Ubuntu porém acredito que se aplique as outras distribuições sem problemas.

Para que o acesso seja feito iremos utilizar o rdesktop, que nada mais é do que um cliente  RDP (Remote Desktop Protocol) &#8211; protocolo utilizado nas tecnologias Microsoft para acesso remoto.

Mãos a massa! Precisamos abrir o terminal como root;

Em seguida, iremos instalar o rdesktop usando o comando:

> \# apt-get install rdesktop

# [<img loading="lazy" class="alignnone wp-image-751 size-full" src="/img/sites/4/2014/07/Img001.jpg" alt="Img001" width="723" height="132" />][1]

Pronto! Já podemos testar usando o próprio terminal:

> $ rdesktop terminal.minhaempresa.com.br

[<img loading="lazy" class="alignnone size-full wp-image-752" src="/img/sites/4/2014/07/Img02.jpg" alt="Img02" width="723" height="123" />][2]

ou

> $ rdesktop 192.168.0.1

Legal né?!

Apenas lembrando que o acesso remoto já deve estar configurado e funcionando no Windows.

 [1]: /img/sites/4/2014/07/Img001.jpg
 [2]: /img/sites/4/2014/07/Img02.jpg