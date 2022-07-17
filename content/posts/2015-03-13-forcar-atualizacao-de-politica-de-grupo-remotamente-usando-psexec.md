---
title: Forçar atualização de Política de Grupo remotamente usando PsExec
author: João Heytor
type: post
date: 2015-03-13T21:42:03+00:00
url: /2015/03/13/forcar-atualizacao-de-politica-de-grupo-remotamente-usando-psexec/
dsq_thread_id:
  - 3593263611
php_everywhere_code:
  - 'Just put [php_everywhere] where you want the code to be executed.'
categories:
  - Clientes

---
Hoje deixo à vocês uma dica bem legal em como podemos atualizar as políticas de grupo usando o software **_<a href="https://technet.microsoft.com/en-us/sysinternals/bb897553.aspx" target="_blank">PsExec</a>_** e o comando _gpupdate_.

Para quem não conhece, o _**PsExec**_ faz parte do <a href="https://technet.microsoft.com/en-us/sysinternals/bb545021.aspx" target="_blank"><em><strong>Windows Sysinternals</strong></em></a>, que é um conjunto de poderosas ferramentas disponibilizadas pela Microsoft para gerenciarmos nosso ambiente Windows.

Dentre essas várias ferramentas, existe uma chamada **PsExec** que nos permite executar comandos em máquinas remotas.

<!--more-->

Bom, vamos por a mão a passa:

Antes de mais nada, precisamos efetuar o download do **PsExec** e, descompacta-lo em uma pasta do computador. No exemplo abaixo, deixarei o executável do **PsExec** direto na unidade C.

<img loading="lazy" class="aligncenter size-full wp-image-781" src="/img/sites/4/2015/03/001.jpg" alt="001" width="664" height="1039" /> 

Como podemos observar, a sintaxe do software é simples:

> PsExec.exe computador -u USUARIO -p SENHA ARGUMENTOS

Nesse caso específico das GPOs, utilizarei este comando:

<img loading="lazy" class="aligncenter size-full wp-image-783" src="/img/sites/4/2015/03/002.jpg" alt="002" width="366" height="59" /> 

Ou seja, estarei executando um comando presente na máquina destino. Neste caso, estou efetuando o gpupdate com os argumentos:

> /force = Faz com que o Windows reaplique todas as políticas de grupo. Lembrando que sem este comando, o Windows apenas aplicará as politicas de grupo que foram alteradas;

&nbsp;

> /boot = Faz com que o Windows seja reiniciado após a execução deste comando.

A saída final pode apresentar o seguinte:

<img loading="lazy" class="aligncenter size-full wp-image-786" src="/img/sites/4/2015/03/003.jpg" alt="003" width="515" height="222" /> 

Como não tive erros, me foi retornado o error code = 0.

Algumas considerações:

  * Não foi necessário especificar o usuário/senha pois estava executando o prompt com privilégios elevados (Administrador);
  * PsExec usa o protocolo SMB, portando é necessário ter a porta TCP 445 aberta (Isso é possível através de GPO);
  * Falando em segurança, não é viável abrirmos a porta 445 em ambientes de produção, já que essa porta pode ser usada para diversos ataques;
  * PsExec é um comando relativamente lento&#8230; para contar isso, também temos o comando Invoke-GPUpdate (PowerShell).

Bom, é isso&#8230; obrigado pessoal!