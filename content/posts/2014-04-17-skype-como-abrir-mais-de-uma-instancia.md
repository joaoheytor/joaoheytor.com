---
title: 'Skype: Como abrir mais de uma instância'
author: João Heytor
type: post
date: 2014-04-17T08:38:04+00:00
url: /2014/04/17/skype-como-abrir-mais-de-uma-instancia/
dsq_thread_id:
  - 2621458686
categories:
  - Diversos

---
Salve galera!

Hoje a dica é bem prática! Por N razões, as vezes precisamos abrir mais de uma instância do software de comunicação da Microsoft, o _**Skype**_. Porém, ao clicarmos novamente no ícone do software, é mostrado o Skype com o usuário já logado.

Para resolvermos esse &#8220;problema&#8221;, temos que adicionar a tag: _**/secondary**_ ao executável **skype.exe**.

Podemos fazer isso, simplesmente clicando com o Botão Direito do mouse em cima do ícone do Skype, em seguida clicar em propriedades. Na aba **ATALHO**, devemos olhar para o item **DESTINO**. Provavelmente, teremos algo assim:

> &#8220;C:Program FilesSkypePhoneSkype.exe&#8221;

O que precisamos fazer é simples, adicionar a tag **/secondary**, antes da última aspa. Dessa maneira, teremos o seguinte resultado:

> &#8220;C:Program FilesSkypePhoneSkype.exe /secondary&#8221;

Só clicarmos em **OK** e pronto! Assim que clicarmos novamente no ícone do Skype, será aberta quantas instâncias desejarmos.

Simples não? Espero que gostem!