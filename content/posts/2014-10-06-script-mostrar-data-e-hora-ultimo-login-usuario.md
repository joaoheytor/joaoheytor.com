---
title: 'Script: Mostrar data e hora do último login do usuário'
author: blogadminjoaoheytor
type: post
date: 2014-10-06T23:12:26+00:00
url: /2014/10/06/script-mostrar-data-e-hora-ultimo-login-usuario/
dsq_thread_id:
  - 3090068513
php_everywhere_code:
  - 'Just put [php_everywhere] where you want the code to be executed.'
categories:
  - Servidores

---
Abaixo temos um simples script que tenho que mostra a data e hora do último login do usuário&#8230;

<!--more-->

Bom vamos lá&#8230; primeiro passo e colar o código abaixo no Bloco de Notas e salvar como _**LastLogin.vbs**_:

> Set oADSystemInfo = CreateObject(&#8220;ADSystemInfo&#8221;)  
> strDefaultDN = oADSystemInfo.username  
> strDN = InputBox(&#8220;Coloque o distinguished name&#8221; & _  
> vbCrLf & &#8220;(Exemplo &#8221; & strDefaultDN & &#8220;)&#8221;, , strDefaultDN)
> 
> Set objUser = GetObject(&#8220;LDAP://&#8221; & strDN)  
> Set objLastLogon = objUser.Get(&#8220;lastLogon&#8221;)  
> intLastLogonTime = objLastLogon.HighPart * (2^32) + objLastLogon.LowPart  
> intLastLogonTime = intLastLogonTime / (60 * 10000000)  
> intLastLogonTime = intLastLogonTime / 1440
> 
> WScript.Echo &#8220;ULTIMO LOGON : &#8221; & int(intLastLogonTime + #1/1/1601#)

Ao abrir o arquivo, temos a seguinte tela:

[<img loading="lazy" class="size-medium wp-image-773 aligncenter" src="/img/sites/4/2014/10/img001-300x127.png" alt="img001" width="300" height="127" />][1]

&nbsp;

Ou seja, temos que inserir o DC Name do usuário (CN=USER, OU=NOMEOU, DC=DOMINIO, DC=COM, etc) e clicar no botão OK.

Por fim, nos é mostrado a seguinte tela:

[<img loading="lazy" class="size-full wp-image-774 aligncenter" src="/img/sites/4/2014/10/img002.png" alt="img002" width="211" height="144" />][2]

Legal né&#8230; espero que tenham gostado!

&nbsp;

 [1]: /img/sites/4/2014/10/img001.png
 [2]: /img/sites/4/2014/10/img002.png