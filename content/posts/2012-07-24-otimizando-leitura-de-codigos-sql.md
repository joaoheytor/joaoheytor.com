---
title: Otimizando Leitura de Códigos SQL
author: João Heytor
type: post
date: 2012-07-24T22:05:04+00:00
url: /2012/07/24/otimizando-leitura-de-codigos-sql/
dsq_thread_id:
  - 2236245338
categories:
  - Banco de Dados

---
Salve, salve galera&#8230; Hoje vou para uma dica que achei fantástica e bem rápida!!!!

**Imaginem o cenário:**

Entramos numa empresa, na vaga de um antigo desenvolvedor, DBA que seja. Como de costume, os softwares desenvolvidos internamente quase não possuem documentação.  Temos que aprender o que o código faz o quanto antes para efetuarmos qualquer otimização e/ou implementação de novas funcionalidades.

Para nossa sorte, abrimos o código-fonte do software X e nos deparamos com vários arquivos. Ao abrir estes arquivos, encontramos um emaranhado de códigos e, para nossa sorte, cada linha possuí um milhão de caracteres.

Fale se isso nunca aconteceu com você também?

Pois é, temos várias escolhas aqui, uma delas é ir por nossa conta e risco alterando o código visualmente e colocando de uma forma mais amigável para que possamos facilmente ler e interpretar todo o código.

Mas o problema está quando temos vários arquivos e/ou várias e várias linhas de código!!

Para facilitar nossa vida, existe um site chamado **SQL Formatte**r, que mesmo tendo como foco a linguagem SQL, também podemos utilizar na interpretação de vários códigos fontes.

Para utiliza-lo, basta acessar: **<a href="http://www.dpriver.com/pp/sqlformat.htm" target="_blank">http://www.dpriver.com/pp/sqlformat.htm</a>** e logo no primeiro campo, colarmos nosso código-fonte.

Neste caso, estou fazendo uma simples consulta SQL para demonstração:

<img loading="lazy" class="aligncenter size-medium wp-image-647" title="001" src="/img/sites/4/2012/07/0011-300x231.png" alt="" width="300" height="231" /> 

E note que temos várias opções de saída (Output). Ao clicarmos no botão &#8220;Format SQL&#8221;, nos é mostrado uma versão mais amigável do código.

<img loading="lazy" class="aligncenter size-medium wp-image-646" title="002" src="/img/sites/4/2012/07/0021-300x216.png" alt="" width="300" height="216" /> 

Ah, também a possibilidade de lermos pelo código HTML, bastando apenas criar um arquivo HTML com o código informado.

Bem legal, não? Imagem se ao invés de ser uma consulta simples, fosse uma linha com vários e vários comandos!!

Espero que tenham gostado dessa dica!! Um forte abraço à todos!