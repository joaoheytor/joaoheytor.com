---
title: 'Pwn Plug: O pesadelo dos administradores de rede'
author: blogadminjoaoheytor
type: post
date: 2012-04-14T20:48:57+00:00
url: /2012/04/14/pwn-plug-o-pesadelo-dos-administradores-de-rede/
dsq_thread_id:
  - 2202459673
categories:
  - Diversos

---
Salve, salve galera&#8230; Como vão? Espero que bem&#8230; por aqui estou correndo (como sempre) e começando a separar alguns materiais de estudos para mais uma prova de certificação, dessa vez será a vez de encara a 70-646 (Pro: Windows Server 2008, Server Administrator) que conta como créditos para a certificação MCITP Windows Server 2008 Server Administrator. Vamos que vamos&#8230; assim que tiver coisas mais concretos, venho contar pra vocês aqui&#8230;

Por ora, fiquem com essa notícia que acabou de me deixar preocupado. Lembrem-se, algumas empresas levam a confidencialidade de seus dados muitos à sério, por isso mesmo a existência de um aparelho desse nível pode ser algo bem preocupante para nós que trabalhamos com redes.

_Para alguém desavisado poderia parecer tratar-se de um perfumador de ambientes ou algo do gênero, mas o cabo ethernet dá a dica de que trata-se de um dispositivo bem mais perigoso do que aparenta. Baseado no SheevaPlug, um kit de desenvolvimento compacto, baseado em um SoC ARM de 1.2 GHz que é capaz de rodar múltiplas distribuições Linux, o [Pwn Plug][1] oferece uma forma simples de obter acesso a redes corporativas: basta plugá-lo em qualquer tomada e conseguir um cabo de rede e ele passará a operar como um backdoor; não apenas oferecendo acesso remoto, mas oferecendo inúmeras ferramentas de detecção de vulnerabilidades e scripts pré-carregados para executar ataques furtivos. Em outras palavras, ele é a última coisa que você gostaria de encontrar na sua rede._

_De uma forma geral, redes corporativas são bastante seguras quando atacadas a partir do perímetro externo. A menos que o firewall esteja encaminhando portas para máquinas vulneráveis dentro da rede interna ou você consiga acesso através de vulnerabilidades em um servidor web ou outro recurso externo com conexão com a rede interna, suas chances de obter acesso deste modo são relativamente pequenas. Por outro lado, caso você tenha acesso a um sistema diretamente conectado à rede interna, as coisas se tornam muito simples, já que dentro do perímetro interno a segurança é muito mais relaxada, especialmente a partir da rede cabeada._

_Ao mesmo tempo, o pessoal da empresa é geralmente treinado em relação a ataques externos (não revelar credenciais de acesso à rede wireless, não executar programas recebidos via e-mail, etc.) mas podem ser muito ingênuos em relação a ataques de engenharia social. Alguém vestido como um técnico da empresa de luz ou de telefone, dizendo estar realizando algum tipo de checagem na instalação, ou mesmo alguém se fazendo passar por cliente que tivesse a chance de ficar alguns momentos sozinho teria boas chances de conseguir plugar um Pwn plug na rede, abrindo completamente as portas para acesso remoto._

_No modelo básico, o Pwn Plug pode ser acessado via web ou wireless (o que torna necessário instalá-lo próximo a uma janela e estacionar em algum local próximo para captar o sinal) mas na versão Elite ele oferece também um adaptador 3G, que permite acesso diretamente a partir da rede celular. O kit inclui até mesmo outros cabos e adesivos, que permitem disfarçá-lo de outras formas, como por exemplo uma fonte de impressora:_

_<img loading="lazy" class="aligncenter size-medium wp-image-499" title="pwnplug1" src="/img/sites/4/2012/04/pwnplug1-300x179.png" alt="" width="300" height="179" />_

_Entre os scripts disponíveis remotamente está até mesmo um script de limpeza, que remove todos os logs e históricos de comandos, para que, quando eventualmente descoberto, o Pwn Plug não revele nada sobre como foi usado. Por enquanto a única real segurança contra eles é mesmo o preço, já que o modelo básico custa US$ 480 e o Elite US$ 730._

Fonte: **<a href="http://www.hardware.com.br/noticias/2012-03/pwnplug.html?goback=%2Egde_2642415_member_100672437" target="_blank">Clube do Hardware</a>**

 [1]: http://www.pwnieexpress.com/