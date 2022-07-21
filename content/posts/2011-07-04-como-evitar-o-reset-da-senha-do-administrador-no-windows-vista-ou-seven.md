---
title: Como evitar o reset da senha do Administrador no Windows Vista ou Seven
author: João Heytor
type: post
date: 2011-07-04T15:45:03+00:00
url: /2011/07/04/como-evitar-o-reset-da-senha-do-administrador-no-windows-vista-ou-seven/
gwo4wp:
  - 'a:4:{s:7:"enabled";s:0:"";s:14:"control_script";s:0:"";s:15:"tracking_script";s:0:"";s:17:"conversion_script";s:0:"";}'
  - 'a:4:{s:7:"enabled";s:0:"";s:14:"control_script";s:0:"";s:15:"tracking_script";s:0:"";s:17:"conversion_script";s:0:"";}'
dsq_thread_id:
  - 2183325691
categories:
  - Clientes

---
Galera, como vão? Notei que há um grande número de pessoas que acessaram a página onde explico como resetar a senha de administrador tanto do Windows Vista ou do Windows 7 [ <a href="https://joaoheytor.com/como-resetar-a-senha-do-administrador-no-windows-vista-ou-seven/" target="_blank">ESSE LINK</a> ].

Pois bem, já faz algum tempo que planejo esse tópico, onde pretendo dar algumas dicas de como eu, como Administrador de Redes, faço para que os usuários não tenham acesso ao Administrador Local da Máquina (Fato este muito importante, principalmente quando as máquinas estão em um domínio). Também é necessário ter em mente, que sempre que é possível o contato físico com a máquina, sempre corrermos o risco de algum usuário descobrir uma nova maneira para driblar nossa segurança, por isso mesmo, que o recomendo é que os servidores em geral fiquem em uma sala reservada, de preferência trancada.

**1ª Dica: Mudar o nome do Administrador Local:**
Para evitar o acesso não autorizado ao usuário Administrador (Local), porque não adotarmos como prática alterarmos seu nome??? Ao invés de Administrador, podemos colocar _Zequinha_, _Banana_, _Amendoim_, enfim qualquer outro nome (de preferência não sugestivo) para que as pessoas não autorizadas não consigam nem ao menos saber qual é o nome do Administrador Local.

**2ª Dica: Alterar a senha do Administrador Local:**
Agora que alterarmos seu nome, o interessante também é alterar sua senha.

Uma dica bem legal, é utilizar o **<a href="http://technet.microsoft.com/en-us/bb897543.aspx" target="_blank">PsPasswd</a>**, que é uma ferramente da própria Microsoft que permite que você altere as senhas dos usuários locais remotamente.

**3ª Dica: Desativar à conta:**
Se você não trabalha com usuários locais, porque não desabilitar essa nova conta??? Sua infraestrutura certamente ficará mais segura ainda, tendo o fato de além de você já ter alterado o nome do administrador local, sua senha, também estará desabilitando-o.

**4ª Dica: Criar um Novo usuário com o nome Administrador:**
Já pensando como Administrador Paranoico, porque não criar um novo usuário padrão (Usuário comum, sem qualquer privilégio), com o nome Administrador e uma senha para monitorar quem fica tentando descobrir a senha desse usuário??? Muito bom para pegar os famosos espertões, que sempre há em todas as empresas!

**5ª Dica: Ativar os Logos de Segurança**
E por fim, se você adotou a dica 4, não pode esquecer de ativar os logs de segurança para que as tentativas de login sejam gravadas para futuras auditorias.

Dependendo das circunstâncias, também podemos colocar senha na BIOS e talvez até colocar cadeado na CPU para que não seja possível abrir a parte lateral para ter acesso ao hardware.

Enfim, essas foram algumas dicas que costumo adotar em certos ambientes!! Como costumo dizer, não existe certo ou errado, o que existe é o que vai atender suas necessidades (ou seu ambiente) da melhor forma. Talvez em alguns ambientes, e dependendo dos valores das informações armazenadas, é necessário pensarmos como Administradores Paranoicos, focando sempre sempre em máxima segurança. Em outros casos, apenas queremos pegar os espertões do nosso ambiente.

E vocês, o que mais podem nos recomendar??? Deixem nos comentários!! ;D
