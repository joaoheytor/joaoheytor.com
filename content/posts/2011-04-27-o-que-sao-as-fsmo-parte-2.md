---
title: O que são as FSMO ??? – Parte 2
author: João Heytor
type: post
date: 2011-04-28T00:41:24+00:00
url: /2011/04/27/o-que-sao-as-fsmo-parte-2/
dsq_thread_id:
  - 2254127371
categories:
  - Servidores

---
Aproveitando uma pequena brechá na minha rotina, resolvi trazer a continuidade do post: [O que são as FSMO??? &#8211; Parte 1][1].

Após explicar o que são as FSMOS e mostrar alguns dos principais sintomas de problemas com elas, vamos ver o que podemos fazer para solucionarmos tais problemas.

Quando algum Domain Controller &#8220;morre&#8221; e este tinha alguma das FSMO&#8217;s, temos que &#8220;sequestrar&#8221; tal função, para só assim conseguirmos normalizar nosso ambiente.

_Vale lembrar que os passos que descreverei nesse post, são apenas para os casos que o seu DC &#8220;morrer&#8221; ou que  você realmente não for mais colocar o DC devolta ao domínio. Se você quiser distribuir as FSMOs para outros DCs mantendo-os todos operantes, os comandos abaixo não se aplicam._

Para fazermos tal &#8220;sequestro&#8221;, podemos utilizar a ferramenta NTDSutil.exe, com o auxilio do comando seize.

**NOTA: Muito cuidado ao utilizar a ferramenta NTDSutil.exe pois a mesma pode fazer com que você perca totalmente as funções do seu AD.**

Mãos a massa:

Primeira coisa a se fazer, devemos abrir o CMD do Windows em qualquer DC disponível;

No CMD, digite o comando NTDSutil e tecle ENTER;

<img loading="lazy" class="aligncenter size-full wp-image-343" title="FSMO000" src="/img/sites/4/2011/04/FSMO000.png" alt="" width="665" height="328" /> 

Digite: _roles_, e tecle ENTER;

<img loading="lazy" class="aligncenter size-full wp-image-344" title="FSMO001" src="/img/sites/4/2011/04/FSMO001.png" alt="" width="664" height="324" /> 

Agora digite: _connections_, e tecle ENTER;

Então digite: _connect to server <NOME\_DO\_SERVIDOR>,_ onde obviamente <NOME\_DO\_SERVIDOR> é o nome do servidor que você quer usar, e tecle ENTER;

<img loading="lazy" class="aligncenter size-full wp-image-345" title="FSMO002" src="/img/sites/4/2011/04/FSMO002.png" alt="" width="666" height="329" /> 

Após efetuar a conexão, digite a letra _q_, e aperte ENTER.

<img loading="lazy" class="aligncenter size-full wp-image-346" title="FSMO003" src="/img/sites/4/2011/04/FSMO003.png" alt="" width="664" height="325" /> 

Essa é a hora que utilizamos do comando _seize_. Devemos digitar _seize <NOME\_DA\_ROLE>,_ onde <NOME\_DA\_ROLE> é o nome da role que você desejar &#8220;sequestrar&#8221;. Por exemplo, podemos alterar todas as roles utilizando dos comandos:

_Seize domain naming master_  
_Seize infrastructure master_  
_Seize PDC_  
_Seize RID master_  
_Seize schema master_

Vale lembra, que a cada seize utilizado, irá aparecer uma tela de confirmação, onde nos é perguntado se realmente desejamos fazer a função.

Se gostou, não se esqueça de comentar!!

Um forte abraço e até a próxima!!!

 [1]: http://www.joaoheytor.com/o-que-sao-as-fsmo-parte-1/