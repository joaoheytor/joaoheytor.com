---
title: Instalando Speedtest no pfSense
author: João Heytor
type: post
date: 2017-10-15T23:11:42+00:00
url: /2017/10/15/instalando-speedtest-no-pfsense/
featured_image: /img/2017/10/001-665x415.png
dsq_thread_id:
  - 6217634809
categories:
  - Redes

---
Olá pessoal,

Gostaria de compartilhar com vocês um item que tenho implementado nos nossos clientes que possuem _pfSense_.

## Cenário Inicial

A maioria dos clientes que temos aqui possuem o _pfSense_ atuando como _gateway/proxy_, fazendo todo o direcionamento e filtro do trafego de dados _LAN/WAN_. Um detalhe importante é que, boa parte desses clientes, também possuem mais de um link de dados ativo (O principal e seu backup).

As pessoas que possuem alguma familiaridade com o _pfSense_ devem sabem que ele monitora os links estão online através de um item chamado “**monitor IP**”! É através deste monitoramento que o _pfSense_ sabe se precisa trocar de link ou não, tudo isso de acordo com a regra especificada.

O ponto é que esse monitoramento é bem simples, fazendo com que não tenhamos muitas informações disponíveis sobre nossos links! Para sanar este _gap_, ou quem sabe melhorar o teste de performance e obter mais algumas informações, e porque não se aproximar um pouco mais dos testes que fazemos em nosso dia-a-dia, descobri uma aplicação chamada **speedtest-cli** (site oficial: <a href="https://pypi.python.org/pypi/speedtest-cli/" target="_blank" rel="noopener">https://pypi.python.org/pypi/speedtest-cli/</a>). Talvez algumas pessoas já tenham usado o **Speedtest** (<a href="http://www.speedtest.net/" target="_blank" rel="noopener">http://www.speedtest.net/</a>) para testar o desempenho de sua internet. Pois bem, o **speedtest-cli** é uma aplicação feita em _Python_ que usa a _API_ do **Speedtest** para testar nosso link.

Além de facilitar nossa vida, é possível também automatizarmos este processo, seja ele enviando o resultado via e-mail, salvando em algum banco de dados&#8230; aqui a imaginação é o limite!

## Vamos por a mão na massa agora!!!!!

Existem inúmeras formas de instalarmos está aplicação, a que achei mais fácil e rápida, foi fazer uma conexão _SSH_ ao _pfSense_ usando o _Putty_ (Lembre-se de checar se o _SSH_ está habilitado em **System >> Advanced >> Admin Access >> Enable Secure Shell**).

{{< figure src="/img/2017/10/001.png" title="pfsense - Tela Inicial" width="666" height="415" >}}

Iremos na **opção 8** para abrir o **shell**. Em seguida, gosto de atualizar a lista de pacotes do _FreeBSD_ usando o comando (Este passo não é obrigatório, mas gosto de atualizar a lista caso precise fazer alguma correção ou instalar alguma outra coisa):

```shell
pkg update
```

{{< figure src="/img/2017/10/002.png" title="pfSense - Atualizando pacotes" width="666" height="415" >}}

Outro detalhe importante, o **speedtest-cli** foi feito em _Python_, por isso é necessário verificar se realmente já temos o _Python_ instalado (Utilizando o comando **pkg version | grep python**). Caso não tenha, use o comando:

```shell
pkg add http://pkg.freebsd.org/freebsd:10:x86:64/latest/All/python36-3.6.3.txz
```

Agora entra o **Speedtest-cli** propriamente dito! A sequência de comandos que vamos usar é:
```shell
cd /tmp/  
fetch https://github.com/sivel/speedtest-cli/archive/master.zip  
unzip master.zip  
cd speedtest-cli-master/  
chmod 755 speedtest_cli.py  
mv speedtest_cli.py /usr/bin
```

{{< figure src="/img/2017/10/004.png" title="pfSense - Baixando speedtest-cli" width="666" height="445" >}}

Pronto! Agora é só testar usando a sintaxe:

```shell
/usr/bin/speedtest-cli -source **_IP_INTERFACE_**
```

<figure id="attachment_1200" aria-describedby="caption-attachment-1200" style="width: 666px" class="wp-caption aligncenter">

{{< figure src="/img/2017/10/005.png" title="pfSense - Testando speedtest-cli" width="666" height="418" >}}

A saída que ele é essa aí de cima!! Podemos observar os itens:
  * Provedor: NET Virtua;
  * Download: 99,29 Mbit/s;
  * Upload: 6,53 Mbits/s;
  * Entre outras informações.

Para não precisar executar esse processo na mão todas as vezes que queremos testar nossos links, uso o pacote **mailreport** do _pfSense_ e coloco para receber via e-mail algumas vezes por dia o teste dos links!

Bom é isso pessoal, espero que tenham gostado!

Inspirado em um post do fórum oficial que pode ser acessado por aqui <a href="https://forum.pfsense.org/index.php?topic=106185.0" target="_blank" rel="noopener">https://forum.pfsense.org/index.php?topic=106185.0</a>.
