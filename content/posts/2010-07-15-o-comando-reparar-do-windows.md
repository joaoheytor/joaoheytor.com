---
title: O Comando Reparar do Windows
author: João Heytor
type: post
date: 2010-07-15T14:10:57+00:00
url: /2010/07/15/o-comando-reparar-do-windows/
aktt_notify_twitter:
  - yes
  - yes
gwo4wp:
  - 'a:4:{s:7:"enabled";s:1:"1";s:14:"control_script";s:0:"";s:15:"tracking_script";s:0:"";s:17:"conversion_script";s:0:"";}'
  - 'a:4:{s:7:"enabled";s:1:"1";s:14:"control_script";s:0:"";s:15:"tracking_script";s:0:"";s:17:"conversion_script";s:0:"";}'
aktt_tweeted:
  - 1
dsq_thread_id:
  - 2247094776
categories:
  - Clientes

---
Todas as vezes que executamos o comando de Reparar uma conexõa de rede, são lançados comandos básicos, que também podem ser executados dentro de um Prompt de Comando, como por exemplo:
- **ipconfig /release** - Limpa as configurações do TCP/IP;  
- **ipconfig /flushdns** - Limpa o chace do DNS Resolver;  
- **ipconfig /registerdns** - Atualiza as concessões DHCP e registra novamente nomes DNS;  
- **ipconfig /renew** - Obtem novamente as configurações TCP/IP.  
- **arp -d *** - Limpa o Cache do Address Resolution Protocol (ARP);  
- **nbtstat -r** - Carrega o cache de nomes NetBIOS;  
- **nbtstat -rr** - Atualiza os nomes NetBIOS;

Vale lembrar, que esses são apenas alguns dos principais comandos básicos que o comando Reparar Conexão efetua. Para saber todos as funlões de um comando, basta digitar: **COMANDO /?**