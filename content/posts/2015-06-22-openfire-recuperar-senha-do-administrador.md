---
title: 'Openfire: Recuperar senha do administrador'
author: João Heytor
type: post
date: 2015-06-23T02:53:46+00:00
url: /2015/06/22/openfire-recuperar-senha-do-administrador/
dsq_thread_id:
  - 3870835312
php_everywhere_code:
  - 'Just put [php_everywhere] where you want the code to be executed.'
categories:
  - Infraestrutura

---
A dica de hoje é voltada para as pessoas que trabalham com o **OpenFire** integrado ao Active Directory. Por algum motivo, algumas vezes o usuário administrador desaparece, fazendo com que perquemos o acesso ao _webadmin_ (Notei esse problema em algumas vezes que alterei as opções relacionadas as configurações de _LDAP_).

<!--more-->

Depois de vascular alguns sites, achei um tópico no fórum da _Ignite Realtime_ com uma dica fantástica para resolver o problema.

Temos duas possíveis soluções:

**1 &#8211; Para o banco de dados e executar a query:**

> <span class="keyword">DELETE</span> <span class="keyword">FROM</span> OFPROPERTY <span class="keyword">WHERE</span> <span class="keyword">NAME</span>=<span class="string">&#8216;admin.authorizedJIDs&#8217;</span>;
> 
> <span class="keyword">INSERT</span> <span class="keyword">INTO</span> OFPROPERTY <span class="keyword">VALUES</span>(<span class="string">&#8216;admin.authorizedJIDs&#8217;,&#8217;admin@example-com,new@example.com&#8217;</span>);
> 
> <span class="keyword">COMMIT</span>;

**2 &#8211; Editar o arquivo &#8220;_openfire.xm_l&#8221; que fica na pasta _&#8220;conf&#8221;_ do Openfire e adicionar as linhas:**

> <admin>  
> <authorizedUsernames>usuario\_active\_directory</authorizedUsernames>  
> </admin>

Obs.: Colocar logo após a tag **<span class="tag"><</span><span class="tag-name">jive</span>**<span class="tag"><strong>></strong>.</span>

Importante, independente da solução escolhida, será necessário reiniciar o serviço do OpenFire.

Em meus testes, ambas as soluções resolveram o problema, sendo que em minha estrutura utilizo o SQL Server 2008

Fonte: <a href="https://community.igniterealtime.org/docs/DOC-2062" target="_blank">https://community.igniterealtime.org/docs/DOC-2062</a>