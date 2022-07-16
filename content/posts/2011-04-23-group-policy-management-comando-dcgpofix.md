---
title: Group Policy Management – Comando DCGPOFIX
author: blogadminjoaoheytor
type: post
date: 2011-04-23T18:02:14+00:00
excerpt: Nesse rápido post, aprendemos como restaurar as duas políticas de grupo padrão que estão inclusas no Active Directory
url: /2011/04/23/group-policy-management-comando-dcgpofix/
dsq_thread_id:
  - 2179539695
categories:
  - Servidores

---
Por padrão, assim que criamos um novo domínio, são criadas duas políticas de grupo que são extremamente importantes para o seu correto funcionamento. São elas: a **Default Domain** **Policy**, que é aplicada a todos os computadores e usuários do domínio e, a **Default Domain** **Controllers Policy**, que é aplicada a todos os Controladores de Domínio (Lembrando que isso só é válido se, os Controladores de Domínio ainda estiverem dentro do contêiner Domain Controllers).

As Melhores Práticas de administração de servidores nos recomendam a NUNCA alterar nada dessas duas políticas. O ideal é sempre criarmos uma nova política antes de fazermos qualquer nelas.

Porém, se por algum motivo, ambas se corromperem, é possível usarmos uma ferramenta para que ambas as políticas retornem ao seu estado original, isto é, o estado logo após o Active Directory ter sido instalado.

Essa ferramenta, ou melhor, comando, é conhecido como **DCGPOFIX** e, apenas membros dos grupos **Administradores do Domínio** e/ou **Administradores da Empresa** podem usar.

**&#8211; Utilizando o DCGPOFIX:**

Como a maioria dos comandos, para utiliza-lo devemos abrir o &#8220;CMD&#8221; do Windows (Clicar em Iniciar, apontar para Executar. Na tela que se abre, devemos digitar &#8220;cmd&#8221; [Sem as Aspas] e cliar no botão OK.)

Na tela que se abre, devemos digitar o comando DCGPOFIX e teclar ENTER.

<img loading="lazy" class="aligncenter size-full wp-image-324" title="dcgpofix000" src="/img/sites/4/2011/04/dcgpofix000.png" alt="" width="642" height="373" /> 

Após LERMOS atentamente o que estamos prestes a fazer, devemos apertar a tecla S e, em seguir ENTER.

<img loading="lazy" class="aligncenter size-full wp-image-325" title="dcgpofix001" src="/img/sites/4/2011/04/dcgpofix001.png" alt="" width="641" height="407" /> 

Outro aviso, após LERMOS e termos a completar certeza do que estamos fazendo, mais uma vez, iremos pressionar a tecla S e após ENTER.

<img loading="lazy" class="aligncenter size-full wp-image-326" title="dcgpofix002" src="/img/sites/4/2011/04/dcgpofix002.png" alt="" width="643" height="544" /> 

Pronto!!! Nossas políticas foram restauradas!!!

O comando DCGPOFIX, é composto pela seguinte sintaxe:

<img loading="lazy" class="aligncenter size-full wp-image-327" title="dcgpofix003" src="/img/sites/4/2011/04/dcgpofix003.png" alt="" width="640" height="303" /> 

**dcgpofix \[/ignoreschema\]\[/target: {domain | dc | both}\]**

Onde:

**/target: {Domain | DC | BOTH}:** Especifica qual a GPO você deseja fazer a restauração [ Domain: A Default Domain Policy; DC: A Default Domain Controller Policy e BOTH: Ambas ];

**/ignoreschema:** É um comando opcional que ignora a versão do Schema do Active Directory;

Ah, o comando DCGPOFIX está disponível em DC&#8217;s com Windows 2000, Windows 2003 (Inclusive o R2) e o Windows 2008 (Inclusive o R2).

É isso ai pessoal, espero que tenham gostado de mais essa rápida dica que consegui escrever entre a correria que anda minha vida&#8230; e torçendo para tudo se normalizar nos próximos dias&#8230; 😀**  
**