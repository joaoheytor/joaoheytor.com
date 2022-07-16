---
title: Dicas para o comando Netsh
author: blogadminjoaoheytor
type: post
date: 2010-07-01T15:00:35+00:00
url: /2010/07/01/dicas-para-o-comando-netsh/
aktt_notify_twitter:
  - yes
  - yes
gwo4wp:
  - 'a:4:{s:7:"enabled";s:1:"1";s:14:"control_script";s:0:"";s:15:"tracking_script";s:0:"";s:17:"conversion_script";s:0:"";}'
  - 'a:4:{s:7:"enabled";s:1:"1";s:14:"control_script";s:0:"";s:15:"tracking_script";s:0:"";s:17:"conversion_script";s:0:"";}'
aktt_tweeted:
  - 1
dsq_thread_id:
  - 2192592680
categories:
  - Clientes

---
Abaixo, veremos alguns comandos para serem usados com o NETSH.EXE:

**<> Visualizar as configurações do TCP/IP:**  
netsh interface ip show config

**<> Alterar as configurações de IP, máscara e gateway  
** netsh interface ip set address name=&#8221;Local Area Connection&#8221; static IP MÁSCARA GATEWAY  
Exemplo:  
netsh interface ip set address name=&#8221;Local Area Connection&#8221; static 10.0.0.2 255.0.0.0 10.0.0.1

**<> Exportar as configurações do protocolo TCP/IP para um arquivo de texto:  
** netsh -c interface dump > C:arquivo.txt

**<> Importar as configurações do protocolo TCP/IP de um arquivo de texto:  
** netsh -f c:arquivo.txt

**<> Configurar para obter IP a partir de um servidor DHCP:  
** netsh interface ip set address &#8220;Local Area Connection&#8221; dhcp

**<> Configurar o DNS  
** netsh interface ip set dns &#8220;Local Area Connection&#8221; static IP_DNS  
Exemplo:  
netsh interface ip set dns &#8220;Local Area Connection&#8221; static 10.0.0.1

**<> Configurar WINS:  
** netsh interface ip set WINS &#8220;Local Area Connection&#8221; static IP_WINS  
Exemplo:  
netsh interface ip set WINS &#8220;Local Area Connection&#8221; static 10.0.0.1

**<> Configurar para o DNS ser obtido via DHCP:  
** netsh interface ip set dns &#8220;Local Area Connection&#8221; dhcp

Esses são apenas alguns comandos disponíveis para o comando NETSH. Existem muitos outros, esses são apenas os principais.  
Os créditos não são meus, porém não lembro de onde peguei tais comandos&#8230; se alguém souber, me avise!!! 😀