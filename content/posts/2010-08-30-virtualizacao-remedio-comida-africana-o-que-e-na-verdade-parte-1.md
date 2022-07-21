---
title: Virtualização, remédio? Comida africana? O que é na verdade? – Parte 1
author: João Heytor
type: post
date: 2010-08-31T00:32:00+00:00
url: /2010/08/30/virtualizacao-remedio-comida-africana-o-que-e-na-verdade-parte-1/
aktt_notify_twitter:
  - yes
gwo4wp:
  - 'a:4:{s:7:"enabled";s:1:"1";s:14:"control_script";s:0:"";s:15:"tracking_script";s:0:"";s:17:"conversion_script";s:0:"";}'
aktt_tweeted:
  - 1
dsq_thread_id:
  - 2296519853
categories:
  - Diversos

---
Dando uma pequena pausa nos artigos de ITIL&#8230; e uma grande pausa na vida pessoal (Como pode, faculdade e trabalho consumirem tanto tempo de uma pessoa???!! :O), resolvi criar um tópico relacionado ao tema virtualização, que por coincidência, foi o tema de um seminário que tive que apresentar há alguns dias atrás!

Então chege de enrolação, vamos ao tema!!!!

Graças ao advento da tecnologia e ao baixo custo para a aquisição de memórias e Hard Disks, a virtualização tem ganhado cada vez mais destaque no dia-a-dia de um profissional de tecnologia da informação.

Porém, para alguns esse termo ainda é bastante desconhecido. Virtualização é uma técnica utilizada para podermos mascarar as características físicas dos recursos de qualquer computador de forma que outros sistemas, aplicações ou usuários finais possam interagir com tais recursos, em outras palavras, virtualização poderia ser definido como a abstração do hardware para os sistemas.

## Terminologias Importantes

Para podermos compreender como funciona a virtualização, temos que ter em mente as seguintes definições:
  - **Hypervisor:** Além de ser o componente mais básico da virtualização, é o componente principal que gerencia as maquinas virtual, ele é responsável por separar o sistema operacional e os aplicativos de seus recursos físicos. O Hypervisor possui um kernel próprio, e é instalado diretamente no hardware;
  - **Máquina Virtual:** Nada mais é do que um ambiente auto-suficiente, isto é, um aplicativo que funciona com, mas é independente de, um sistema operacional host;
  - **Virtualização Completa (Full Virtualization):** Nesse modo, o Hypervisor mascara completamente a virtualização para o Sistema Operacional;
  - **Para-virtualização (Para-virtualization / Enlightenment)**: Tanto o Hypervisor quanto o Sistema Operacional virtualizado colaboram para obter o máximo em desempenho, isto é, o sistema operacional como um todo roda sobre o hypervisor, que se comunica com ele diretamente, por isso que há o aumento de desempenho;
  - **Virtualização de Aplicação:** Um método para mascarar e executar aplicações em um SO ou vindo de um SO, tanto local quanto via rede através de streaming;
  - **Virtualização de Apresentação**: Neste modelo de virtualização apenas a camada de apresentação de um aplicativo é executada na maquina cliente. O processamento e uso de memória ficam no servidor que estiver provendo esta modalidade de virtualização;
  - **Hosted Virtualization**: Uma virtualização de aplicação , que executa um SO não-modificado, executando no topo de um sistema operacional padrão;
  - **Hardware Virtualization Assistance**: Uma Full Virtualization melhorada, que conta com processadores que já suportam a virtualização. Os processadores que suportam tal modo, possuem as marcações Intel-VT (Para processadores Intel) e AMD-V (Para processadores AMD).

<h5 style="text-align: right">
  Seminário apresentado no dia 26/08/2010, durante aula de Aplicação de Sistemas Distribuidos.
</h5>

<p style="text-align: left">
  Mais tarde volto pra explicar os tipos de virtualização e como funcionam suas respectivas arquiteturas.
</p>