---
title: Problema com Spool de Impressão 2
author: blogadminjoaoheytor
type: post
date: 2013-12-29T03:00:44+00:00
url: /2013/12/29/problema-com-spool-de-impressao-2/
dsq_thread_id:
  - 2186381169
categories:
  - Clientes

---
_Spooler de Impressão_, famoso por suas dores de cabeça. Quem nunca teve problemas com ele que atire a primeira pedra&#8230;

Pela internet, há vários relatos das dores de cabeça que esse serviço pode nos causar (Na verdade, eu mesmo já tive inúmeros problemas com esse serviços), tais como ao enviar um documento para impressão todas as impressoras simplesmente somem e, o _spooler de impressão_ simplesmente é **PARADO**. Também existem relatos de travamentos e vários outros problemas relacionados à esse serviços.

Há algum tempo atrás, fiz um post ensinando como podemos criar um pequeno script para automatizar a limpeza e a iniciação do spooler no caso de erros (<https://joaoheytor.com/problemas-com-impressoras/>).

Porém, faltou mostrar uma forma de automatizar a utilização desse script&#8230;

Para isso, podemos acessar o item _Serviços_ (Painel de Controle, Ferramentas Administrativas, Serviços, no caso das versões mais recentes do Windows ou, Iniciar, Executar e em seguida digitar “services.msc”).

[<img loading="lazy" class="aligncenter size-medium wp-image-666" alt="services" src="/img/sites/4/2013/12/services-300x155.png" width="300" height="155" />][1]

Esse item _Serviços_ mostra para nós TODOS os serviços ativos ou inativos que o Windows possui. Por ora, não iremos entrar em detalhes deste item.

Para o exemplo deste post, iremos procurar o serviços _**Spooler de Impressão**_. Ao abrir esse item, ele irá mostrar o estado do serviços e, sua função (Assim como é mostrados caso queiramos abrir qualquer outro serviço).

Devemos clicar na aba **RECUPERAÇÃO**. Por costume, prefiro sempre deixar as duas primeiras opções (Primeira Falha e Segunda Falha) como “Reiniciar o Serviços”, ou seja, caso ocorra algum problema, o próprio Windows tentará reiniciar o serviços para restaura-lo. Já o terceiro item (Falhas Posteriores) marco sempre “Executar um Programa”.

[<img loading="lazy" class="aligncenter size-medium wp-image-665" alt="spooler" src="/img/sites/4/2013/12/spooler-263x300.png" width="263" height="300" />][2]

Em seguida, devemos clicar no botão “**PROCURAR**” que é habilitado e, escolher onde salvamos o script do post anterior.

Simples não?

Em outras, o Windows tentará por duas vezes reiniciar o serviços. Caso o erro aconteça novamente, ele irá executar o script para restaurar o serviços.

Bom&#8230; essa é a forma &#8220;gambiarra&#8221; para resolver problemas com o spooler. Na verdade, sempre adoto essa opção quando tenho que resolver o problema rapidamente, ou seja, estou apagando incêndio.

Em breve, postarei o que devemos fazer assim que possível para evitar problemas com esse serviço.

Um forte abraço à todos e, qualquer dúvida só deixar nos comentários.

 [1]: /img/sites/4/2013/12/services.png
 [2]: /img/sites/4/2013/12/spooler.png