---
title: Instalando Speedtest no pfSense
author: blogadminjoaoheytor
type: post
date: 2017-10-15T23:11:42+00:00
url: /2017/10/15/instalando-speedtest-no-pfsense/
featured_image: /wp-content/uploads/2017/10/001-665x415.png
dsq_thread_id:
  - 6217634809
categories:
  - Redes

---
Olá pessoal,

Gostaria de compartilhar com vocês um item que tenho implementado nos nossos clientes que possuem _pfSense_.

#### Cenário Inicial

A maioria dos clientes que temos aqui possuem o _pfSense_ atuando como _gateway/proxy_, fazendo todo o direcionamento e filtro do trafego de dados _LAN/WAN_. Um detalhe importante é que, boa parte desses clientes, também possuem mais de um link de dados ativo (O principal e seu backup).

As pessoas que possuem alguma familiaridade com o _pfSense_ devem sabem que ele monitora os links estão online através de um item chamado “**monitor IP**”! É através deste monitoramento que o _pfSense_ sabe se precisa trocar de link ou não, tudo isso de acordo com a regra especificada.

<!--more-->

O ponto é que esse monitoramento é bem simples, fazendo com que não tenhamos muitas informações disponíveis sobre nossos links! Para sanar este _gap_, ou quem sabe melhorar o teste de performance e obter mais algumas informações, e porque não se aproximar um pouco mais dos testes que fazemos em nosso dia-a-dia, descobri uma aplicação chamada **speedtest-cli** (site oficial: <a href="https://pypi.python.org/pypi/speedtest-cli/" target="_blank" rel="noopener">https://pypi.python.org/pypi/speedtest-cli/</a>). Talvez algumas pessoas já tenham usado o **Speedtest** (<a href="http://www.speedtest.net/" target="_blank" rel="noopener">http://www.speedtest.net/</a>) para testar o desempenho de sua internet. Pois bem, o **speedtest-cli** é uma aplicação feita em _Python_ que usa a _API_ do **Speedtest** para testar nosso link.

Além de facilitar nossa vida, é possível também automatizarmos este processo, seja ele enviando o resultado via e-mail, salvando em algum banco de dados&#8230; aqui a imaginação é o limite!

### Vamos por a mão na massa agora!!!!!

Existem inúmeras formas de instalarmos está aplicação, a que achei mais fácil e rápida, foi fazer uma conexão _SSH_ ao _pfSense_ usando o _Putty_ (Lembre-se de checar se o _SSH_ está habilitado em **System >> Advanced >> Admin Access >> Enable Secure Shell**).<figure id="attachment_1197" aria-describedby="caption-attachment-1197" style="width: 666px" class="wp-caption aligncenter">

<img loading="lazy" class="size-full wp-image-1197" src="https://www.joaoheytor.com/wp-content/uploads/2017/10/001.png" alt="pfsense - Tela Inicial" width="666" height="415" srcset="https://www.joaoheytor.com/wp-content/uploads/2017/10/001.png 666w, https://www.joaoheytor.com/wp-content/uploads/2017/10/001-300x187.png 300w, https://www.joaoheytor.com/wp-content/uploads/2017/10/001-665x415.png 665w" sizes="(max-width: 666px) 100vw, 666px" /> <figcaption id="caption-attachment-1197" class="wp-caption-text">pfsense &#8211; Tela Inicial</figcaption></figure> 

Iremos na **opção 8** para abrir o **shell**. Em seguida, gosto de atualizar a lista de pacotes do _FreeBSD_ usando o comando (Este passo não é obrigatório, mas gosto de atualizar a lista caso precise fazer alguma correção ou instalar alguma outra coisa):

> pkg update<figure id="attachment_1198" aria-describedby="caption-attachment-1198" style="width: 666px" class="wp-caption aligncenter">

<img loading="lazy" class="size-full wp-image-1198" src="https://www.joaoheytor.com/wp-content/uploads/2017/10/002.png" alt="pfSense - Atualizando pacotes" width="666" height="415" srcset="https://www.joaoheytor.com/wp-content/uploads/2017/10/002.png 666w, https://www.joaoheytor.com/wp-content/uploads/2017/10/002-300x187.png 300w, https://www.joaoheytor.com/wp-content/uploads/2017/10/002-665x415.png 665w" sizes="(max-width: 666px) 100vw, 666px" /> <figcaption id="caption-attachment-1198" class="wp-caption-text">pfSense &#8211; Atualizando pacotes</figcaption></figure> 

Outro detalhe importante, o **speedtest-cli** foi feito em _Python_, por isso é necessário verificar se realmente já temos o _Python_ instalado (Utilizando o comando **pkg version | grep python**). Caso não tenha, use o comando:

> pkg add http://pkg.freebsd.org/freebsd:10:x86:64/latest/All/python36-3.6.3.txz

Agora entra o **Speedtest-cli** propriamente dito! A sequência de comandos que vamos usar é:

> cd /tmp/  
> fetch https://github.com/sivel/speedtest-cli/archive/master.zip  
> unzip master.zip  
> cd speedtest-cli-master/  
> chmod 755 speedtest_cli.py  
> mv speedtest_cli.py /usr/bin<figure id="attachment_1199" aria-describedby="caption-attachment-1199" style="width: 666px" class="wp-caption aligncenter">

<img loading="lazy" class="size-full wp-image-1199" src="https://www.joaoheytor.com/wp-content/uploads/2017/10/004.png" alt="pfSense - Baixando speedtest-cli" width="666" height="445" srcset="https://www.joaoheytor.com/wp-content/uploads/2017/10/004.png 666w, https://www.joaoheytor.com/wp-content/uploads/2017/10/004-300x200.png 300w" sizes="(max-width: 666px) 100vw, 666px" /> <figcaption id="caption-attachment-1199" class="wp-caption-text">pfSense &#8211; Baixando speedtest-cli</figcaption></figure> 

Pronto! Agora é só testar usando a sintaxe:

> /usr/bin/speedtest-cli &#8211;source **IP_INTERFACE**<figure id="attachment_1200" aria-describedby="caption-attachment-1200" style="width: 666px" class="wp-caption aligncenter">

<img loading="lazy" class="size-full wp-image-1200" src="https://www.joaoheytor.com/wp-content/uploads/2017/10/005.png" alt="pfSense - Testando speedtest-cli" width="666" height="418" srcset="https://www.joaoheytor.com/wp-content/uploads/2017/10/005.png 666w, https://www.joaoheytor.com/wp-content/uploads/2017/10/005-300x188.png 300w, https://www.joaoheytor.com/wp-content/uploads/2017/10/005-665x418.png 665w" sizes="(max-width: 666px) 100vw, 666px" /> <figcaption id="caption-attachment-1200" class="wp-caption-text">pfSense &#8211; Testando speedtest-cli</figcaption></figure> 

A saída que ele é essa aí de cima!! Podemos observar os itens:

  * Provedor: NET Virtua;
  * Download: 99,29 Mbit/s;
  * Upload: 6,53 Mbits/s;
  * Entre outras informações&#8230;

Para não precisar executar esse processo na mão todas as vezes que queremos testar nossos links, uso o pacote **mailreport** do _pfSense_ e coloco para receber via e-mail algumas vezes por dia o teste dos links!

Bom é isso pessoal, espero que tenham gostado!

Inspirado em um post do fórum oficial que pode ser acessado por aqui <a href="https://forum.pfsense.org/index.php?topic=106185.0" target="_blank" rel="noopener">https://forum.pfsense.org/index.php?topic=106185.0</a>.