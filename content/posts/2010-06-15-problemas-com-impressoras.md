---
title: Problema com Spool de Impressão
author: João Heytor
type: post
date: 2010-06-15T19:00:44+00:00
excerpt: Algumas vezes, temos dificuldades para usar a impressora. As vezes até achamos que o problema é da própria impressora, mas não, muitas vezes é apenas o serviço de spool do Windows que deu algum problema...
url: /2010/06/15/problemas-com-impressoras/
Thumbnail:
  - http://blog.joaoheytor.com/img/2010/06/windowslogobk8.jpg
Tab:
  - IMPRESSORAS NO WINDOWS
dsq_thread_id:
  - 2180694387
categories:
  - Clientes

---
Para começarmos, iremos ver um problema que muitos de nós ainda encontramos no nosso dia-a-dia&#8230;

Quantas vezes, já mandamos imprimir alguma coisa e a impressora simplesmente não responde?? O pior de tudo, nós conseguimos ver os arquivos na fila de impressão, mas mesmo assim a impressora não dá nem sinal de vida. Então tentamos remover os arquivos da fila para que possamos enviá-los novamente. É onde entra outro problema, os arquivos não são exluidos. O Windows nos retorna que está excluindo tais documentos, mas não passa disso.

Algumas vezes, a resolução do problema é extremamente fácil e rápida. Abaixo, veremos como criar um simples script que para o spool de impressão do Windows e depois o reinicia.

```shell
@echo off  
net stop spooler  
pause  
del %windir%system32spoolprinters\*.\* /q /s  
net start spooler
```

Já tive muitas dores de cabeça com tal problema&#8230; Para usá-lo, basta abrir o Bloco de Notas do Windows (Iniciar, Programas, Acessórios, Bloco de Notas). Em seguida, copiar o código acima e colar dentro do mesmo. Na hora de salvar, digite um nome qualquer, porém adicione a extensão “.bat” ao fim do nome escolhido. Pronto, faça o teste!

Ao executar o arquivo, o serviço de impressão do Windows será parado. Em seguida, todos os documentos que estão na fila de impressão, serão apagados. E por fim, O serviço de impressão do Windows será re-iniciado.

Como opção, sempre tenho um atalho que aponta para o código acima na minha área de trabalho.

Dúvidas ou sugestões, não deixe de comentar&#8230;