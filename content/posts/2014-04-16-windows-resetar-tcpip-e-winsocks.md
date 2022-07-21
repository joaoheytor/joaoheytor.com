---
title: 'Windows: Resetar TCP/IP e Winsocks'
author: João Heytor
type: post
date: 2014-04-16T17:56:48+00:00
url: /2014/04/16/windows-resetar-tcpip-e-winsocks/
dsq_thread_id:
  - 2640644580
categories:
  - Clientes

---
Por vários fatores, as vezes precisamos _(ou queremos, já que talvez possamos estar trabalhando na causa de algum problema específico)_ resetar o protocolo TCP/IP e o Winsocks de nosso Sistema Operacional.

**DEFINIÇÕES:**

Para os novos, vamos primeiramente as definições básicas:

  * Protocolo TCP/IP: Bem resumido, é o protocolo para envio e recebimento de dados pela/para internet;
  * Winsocks: Conjunto de bibliotecas que possibilitam a comunicação TCP/IP.

**RESOLUÇÃO DO PROBLEMA:**

Para que seja feito o reset do TCP/IP e do Winsock, usaremos o comando _**netsh**_ (Já abordado em outro tópico deste blog: [_**Dicas para o comando netsh https://joaoheytor.com/dicas-para-o-comando-netsh**_][1]/).

Antes de mais nada, deveremos abrir o prompt de comando como Administrador. Em seguida, usamos estes comandos:
```powershell
netsh int ip reset c:resetlog.txt  
netsh winsock show catalog  
netsh winsock reset
```

Agora é só reiniciar o computador!

Simples não?! Espero que gostem!

Dúvidas, por gentileza deixar nos comentários&#8230;

&nbsp;

 [1]: https://joaoheytor.com/dicas-para-o-comando-netsh/