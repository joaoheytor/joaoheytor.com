---
title: 'Active Directory: Diferença de LastLogon e LastLogonTimeStamp'
author: João Heytor
type: post
date: 2014-09-23T01:11:46+00:00
url: /2014/09/22/active-directory-diferenca-de-lastlogon-e-lastlogontimestamp/
dsq_thread_id:
  - 3044370492
categories:
  - Servidores

---
Salve galera!

No artigo de hoje, tentarei explicar a diferença entre dois campos importantes que o Active Directory possui: **LastLogon** e **LastLogonTimeStamp**.

Resumindo, é o campo onde é armazenado a data do último login com sucesso feito pelo usuário.

Vamos às definições:

&#8211; **LastLogon** é um atributo não-replicável. Isso significa que é um valor único para cada controlador de domínio;

&#8211; **LastLogonTimeStamp** é um atributo replicável porém, ele não é atualizado todas as vezes que usuário faz login. Ele apenas é atualizado quando seu valor atual é mais antigo que o valor atualmente armazenado menos o valor do atributo **mSDS-LogonTimeSyncInterval** (Seu valor padrão é de 14 dias).

Vale lembrar que, como o atributo _LastLogon_ não é replicável, para sabermos exatamente a hora do último login do usuário, é necessário verificar este item em todos os Controladores de Domínio.

É isso pessoal&#8230; espero ter sido bastante claro!

Dúvidas, não deixem de comentar!!!

**Fontes:**

  * <a href="http://msdn.microsoft.com/en-us/library/ms676824(VS.85).aspx" target="_blank">http://msdn.microsoft.com/en-us/library/ms676824(VS.85).aspx</a>
  * <a href="http://msdn.microsoft.com/en-us/library/ms676823(VS.85).aspx" target="_blank">http://msdn.microsoft.com/en-us/library/ms676823(VS.85).aspx</a>