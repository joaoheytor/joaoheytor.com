---
title: Active Directory – Alterar local padrão de computadores e usuários
author: blogadminjoaoheytor
type: post
date: 2016-09-20T22:07:45+00:00
url: /2016/09/20/active-directory-alterar-local-padrao-de-computadores-e-usuarios/
dsq_thread_id:
  - 5159934548
php_everywhere_code:
  - 'Just put [php_everywhere] where you want the code to be executed.'
categories:
  - Servidores

---
Por padrão, ao adicionarmos um computador ao Active Directory, ele é colocado no contêiner _**Computers**_ (**CN=Computers,DC=domain**). Até aí tudo bem, não há problemas os computadores estarem todos em um único lugar! O problema ocorre quando temos um ambiente um pouco maior, onde temos GPOs (Group Policy Object) de segurança vinculadas as máquinas! A principal diferença de um contêiner para uma _Unidade Organizacional_ (_**OU**_) é a possibilidade de aplicarmos _GPO_ nela!

**NÃO** é possível aplicarmos _GPO_ em um contêiner! Ou seja, toda máquina que adicionarmos ao domínio, será necessário abrir o _Active Directory Users and Computers_ e mover tal objeto! Quando nosso ambiente é pequeno, não temos problemas! Fazemos essa mudança manualmente, até porque colocamos apenas pontualmente as máquinas em domínio. Porém, quando o ambiente começa a crescer, fica desgastante fazer tal ação! Sem contar que as vezes um computador pode ficar perdido no contêiner _Computers_ durante um bom tempo!

Bom, com essa pequena explicação, podemos supor que seria muito fácil se assim que eu adicionar uma máquina ao domínio, ela fosse automaticamente acrescentada em uma _OU_ onde tivesse algumas _GPOs_ básicas de segurança e/ou instalação de software.

<!--more-->

## OBJETIVO

Nossa meta é aprender como é possível alterar o local padrão dos computadores e usuários assim que eles são ingressão/criados no domínio.

## CENÁRIO

Para atingirmos nosso objetivo, estarei efetuando todos os testes em uma máquina com _Windows Server 2012 R2 Standard_ com a role _Active Directory Domain Services_ instalada!

## PRÁTICA

Para conseguirmos atingir nosso objetivo, devemos abrir o _**prompt de comando**_! Os comandos responsáveis por fazer a &#8220;mágica&#8221; são:

  * **redircmp:** Usado para alterar o local padrão dos computadores;
  * **redirusr:** Similar ao _redircmp_ porém, é voltado para os usuários.

Se digitarmos &#8220;_**redircmp /?**_&#8221; podemos ver o seguinte conteúdo da ajuda:<figure id="attachment_1131" aria-describedby="caption-attachment-1131" style="width: 618px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1131 size-full" src="/img/2016/09/002.png" alt="Active Directory - Usando o comando redircmp" width="618" height="188" />][1]<figcaption id="caption-attachment-1131" class="wp-caption-text">Active Directory &#8211; Usando o comando redircmp</figcaption></figure> 

Como também observamos na imagem acima, a sintaxe deste comando é bem simples: **redircmp ENDEREÇO\_LDAP\_DA\_NOVA\_OU**.** **No exemplo, **redircmp OU=Computadores,DC=GrupoEmpresas,DC=local** (Meu domínio é **GrupoEmpresas.local**), ou seja, estou fazendo o redirecionamento de todas as máquinas que ingressarem no domínio para a OU _Computadores._ Atenção que a _OU_ já precisa estar criada.

Em relação a mudança de usuários, a sintaxe é a mesma:<figure id="attachment_1132" aria-describedby="caption-attachment-1132" style="width: 598px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1132 size-full" src="/img/2016/09/003.png" alt="Active Directory - Usando o comando redirusr" width="598" height="188" />][2]<figcaption id="caption-attachment-1132" class="wp-caption-text">Active Directory &#8211; Usando o comando redirusr</figcaption></figure> 

Observando a sintaxe, temos: **redirusr OU=Usuários,DC=GrupoEmpresas,DC=Local**.

**Lembrem-se que para estes comandos funcionarem, é preciso que o domínio esteja com nível funcional de pelo menos Windows Server 2003.**

Legal né? Espero que tenham gostado de mais essa dica!

 [1]: /img/2016/09/002.png
 [2]: /img/2016/09/003.png