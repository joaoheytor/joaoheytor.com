---
title: XAMPP e WordPress problemas com admin usando multisite
author: João Heytor
type: post
date: 2015-07-05T22:06:57+00:00
url: /2015/07/05/xampp-e-wordpress-problemas-com-admin-usando-multisite/
php_everywhere_code:
  - 'Just put [php_everywhere] where you want the code to be executed.'
dsq_thread_id:
  - 4048806484
categories:
  - Diversos

---
Hoje quero dar uma dica de um problema que tive em um cliente. Lá temos um servidor com _XAMPP_ e _WordPress_ para fazermos a homologação de conteúdos internos.

Tudo funcionava perfeitamente, até termos a ideia de optarmos pelo _WordPress Multisite_, o que nos permite trabalharmos com vários sites com uma única instalação/base do WordPress.

Após efetuarmos todas as alterações no _wp-config.php_ e _.htaccess_, perdíamos o acesso ao painel administrativo do _WordPress_.

<!--more-->

Para resolvermos esse problema, achei um tópico no Fórum Oficial do WordPress, onde precisamos alterar uma linha no arquivo:

> C:\xampp\apps\wordpress\conf\httpd-app.conf

Dentro dele, devemos alterar a opção **`AllowOverride None`** para **`AllowOverride All`**.

Pronto! Agora basta reiniciar o serviço do Apache que o acesso administrativo deve voltar ao normal.

Fonte: <a href="https://wordpress.org/support/topic/multisite-localhost-xampp-subfolders-infinite-redirect-loop" target="_blank">Fórum WordPress</a>