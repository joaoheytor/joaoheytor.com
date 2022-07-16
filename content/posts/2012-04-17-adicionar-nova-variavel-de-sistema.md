---
title: Adicionar Nova Variável de Sistema
author: blogadminjoaoheytor
type: post
date: 2012-04-17T12:39:53+00:00
url: /2012/04/17/adicionar-nova-variavel-de-sistema/
dsq_thread_id:
  - 2944824273
categories:
  - Clientes

---
Salve pessoas, como vão?

Hoje irei postar um script em VBS bem simples que adiciona uma nova variável de sistema ao Windows. Isso é extremamente útil para quando desejamos otimizar a instalação de algum software que por algum motivo, não criou na hora de sua instalação.

Para funcionar, basta abrir o Bloco de Notas do Windows e copiar o seguinte código:

> Set WshShell = WScript.CreateObject(&#8220;WScript.Shell&#8221;)  
> Set WshEnv = WshShell.Environment(&#8220;SYSTEM&#8221;)  
> WshEnv(&#8220;NOME\_VARIÁVEL&#8221;) = WshEnv(&#8220;NOME\_VARIÁVEL&#8221;) & &#8220;VALOR_VARIÁVEL&#8221;  
> msgbox &#8220;Variável de Sistema Adicionada com sucesso!&#8221;, 0 + 64, &#8220;Sucesso!&#8221;

Salve com o nome de NOME\_DO\_ARQUIVO.vbs, levando em conta que o que vale é a extensão &#8220;**.vbs**&#8220;.

Pronto, nosso script já está pronto para uso! Espero que tenham gostado!