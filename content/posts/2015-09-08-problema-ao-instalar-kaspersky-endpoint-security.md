---
title: Problema ao instalar Kaspersky Endpoint Security
author: João Heytor
type: post
date: 2015-09-08T20:59:30+00:00
url: /2015/09/08/problema-ao-instalar-kaspersky-endpoint-security/
php_everywhere_code:
  - 'Just put [php_everywhere] where you want the code to be executed.'
dsq_thread_id:
  - 4145554605
categories:
  - Diversos

---
[<img loading="lazy" class="size-full wp-image-58 alignleft" src="/img2015/09/Erro-KAV.png" alt="Erro KAV" width="538" height="357" />][1]

A dica é para que está fazendo deploy do Kaspersky Endpoint Security (Aqui o problema ocorreu na versão 10) e recebe o erro 27302 Installing Network Components (Maximum Number of filters supported by the operationg system has been reached.<!--more-->

A resolução é fácil, basta abrir o registro do Windows, navegar até a chave HKEY\_LOCAL\_MACHINESYSTEMCurrentControlSetControlNetworkMaxNumFilters e alterar o valor de 8 (Padrão para Windows 7) para 16.

Em seguida, basta reiniciar a máquina e instalar novamente.

Fonte: <a href="http://forum.kaspersky.com/index.php?showtopic=315163" target="_blank" rel="noopener noreferrer" class="broken_link">Kaspersky Fórum</a>

 [1]: /img2015/09/Erro-KAV.png