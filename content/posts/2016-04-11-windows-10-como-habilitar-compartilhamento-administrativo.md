---
title: Windows 10 Como habilitar Compartilhamento Administrativo
author: João Heytor
type: post
date: 2016-04-11T20:51:30+00:00
url: /2016/04/11/windows-10-como-habilitar-compartilhamento-administrativo/
dsq_thread_id:
  - 4740585160
php_everywhere_code:
  - 'Just put [php_everywhere] where you want the code to be executed.'
categories:
  - Clientes

---
O Compartilhamento Administrativo (Vulgo Compartilhamento Oculto, ou C$ ou D$, etc) por padrão não está disponível no Windows 10 (E Windows 8.x) quando a máquina **NÃO** estiver em um ambiente de domínio.

Esse tipo de acesso é bem útil para os sysadmins efetuarem alguma checagem, seja copia de arquivo, verificação, auditoria, etc&#8230;

<!--more-->

**A solução:**

Caso queiramos habilita-lo, é necessário efetuarmos uma alteração junto ao registro do Windows.

Para isso, é necessário seguir os seguintes passos:

  1. Devemos efetuar login na máquina com uma conta que tenha poderes administrativos (**Adm Local**);
  2. Clicar no logo do Windows e procurar por &#8220;**regedit**&#8220;. Dar um botão direito e escolher &#8220;**Executar como Administrador**&#8220;;
  3. Em seguida, será necessário navegar até a chave: HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\policies\system ;
  4. Agora é necessário criarmos uma nova chave ( Botão Direito -> Novo -> Valor DWORD (32bit);
  5. Nome da chave: &#8220;LocalAccountTokenFilterPolicy&#8221; e colocar como valor &#8220;1&#8221;.
  6. Clicar em OK e reiniciar a máquina.

Pronto! Os compartilhamentos administrativos já estão habilitados! Lembrando que para acessa-los, é necessário digitar **_\NOME\_DA\_MÁQUINAc$_**. Será necessário informar usuário/senha do usuário local!