---
title: Parâmetros Inválidos ao instalar impressora
author: João Heytor
type: post
date: 2015-04-11T01:17:55+00:00
url: /2015/04/10/parametros-invalidos-ao-instalar-impressora/
dsq_thread_id:
  - 3683753920
php_everywhere_code:
  - 'Just put [php_everywhere] where you want the code to be executed.'
categories:
  - Clientes

---
Salve, salve galera!

Hoje vou deixar registrado um problema que tive junto à um servidor com _Print Server_ instalado.

Por algum motivo, ao instalar novas impressoras podemos ter problemas no momento em que o Windows copia os arquivos do driver para o repositório local.

O problema maior ocorre ao tentar remover ou atualizar esses drivers posteriormente. Os erros são os mais vários possíveis, entre eles o erro &#8220;**0x80070057**&#8221; é reportado no **_Event Viewer_**.

<!--more-->

Pois bem, para remover esses drivers, a melhor opção é utilizando a ferramenta _**pnputil**_.

Para isso, vamos abrir o _Prompt de Comando_ e digitar:

> **pnputil -e**

Dependendo da quantidade de drivers, pode ser que você tenha uma lista um pouco grande, por isso mesmo eu gosto de exportar a saída desse comando para um outro arquivo (Lembrando que o prompt deve estar aberto como administrador):

<img loading="lazy" class="alignnone size-full wp-image-791" src="/img/sites/4/2015/04/pnputil.png" alt="pnputil" width="677" height="102" /> 

Na prática, este comando lista todos os arquivos .inf que ficam na pasta **%system32%DriverStoreFileRepository**.

Dessa forma, anote o nome dos arquivos que queremos remover e utilize o seguinte comando:

> **pnputil -f -d ARQUIVO.inf**

Pronto! O driver da impressora foi removido e com isso você pode reinstalar o driver sem problemas.

Espero que tenham gostado e, caso precisem de alguma ajuda, podem deixar nos comentários..,.