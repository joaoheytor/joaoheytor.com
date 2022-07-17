---
title: Planejando o Gerenciamento dos Objetos de Política de Grupo
author: João Heytor
type: post
date: 2011-07-12T00:37:02+00:00
url: /2011/07/11/planejando-o-gerenciamento-dos-objetos-de-politica-de-grupo/
dsq_thread_id:
  - 2214650456
categories:
  - Planejamento e Gerenciamento

---
Bom, como estou separando o conteúdo para as provas do Windows 2008 que devo fazer entre os meses de julho/agosto, achei um assunto que aposto que muitos ainda precisam de alguma ajudinha (inclusive eu).

Comecemos com esse pensamento:

> Melhor gastar mais tempo planejando suas atividades, do que perder tempo com a técnica tentativa e erro.

Acredite, eu sei como é difícil nos doutrinarmos sobre isso, mas é algo imprescindível para nós, que resolvemos trabalha com tecnologia da informação. Temos que criar o hábito de estudar mais e para de tentar fazer as coisas por “força bruta”.

Pois bem, para quem não sabe, existe uma parte do site da Microsoft voltada totalmente para as Políticas de Grupo [<a href="http://technet.microsoft.com/en-us/windowsserver/bb310732" target="_blank">http://technet.microsoft.com/en-us/windowsserver/bb310732</a> ]. O seu é legal, pois aborda desde o ba-bá, até o total controle e gerenciamento das políticas.

De qualquer forma, reparei que no MOC do curso 6430B, são destacados os seguintes itens:

**&#8211; GPOs Iniciais:** Extremamente importante para a saúde de qualquer domínio do Active Directory.  Lembrando que há um artigo aqui no blog explicando o que são e como restaura-las ([https://www.joaoheytor.com/group-policy-management-comando-dcgpofix/][1].

**&#8211; Reuso ou Copia de GPOs:** Muito cuidado com isso! É extremamente importante que seja feita uma análise de qualquer GPO (principalmente as de terceiro) que é incorporada ao seu domínio.  Uma GPO que parece inocente, pode por ventura bloquear (ou desbloquear) alguma função vital da sua infraestrutura. Portanto, cuidado!!

**&#8211; Considerar como será o Backup e o possível Restore  das GPOs:** Você faz backup das GPOs do seu domínio? Acredite, poucos administradores se lembram de fazer backup das GPOs, lembrando das mesmas, apenas quando deu algum problema. Não se esqueça, as GPOs não estão inclusas no backup do System State, elas devem ser salvas separadamente!

**&#8211; Questões ligadas à delegação do Gerenciamento das GPOs:** Delegar, ou não delegar, eis a questão. Talvez, em algumas estruturas grandes, é interessante delegar a questão do gerenciamento de GPO para mais de um administrador. Mas cuidado, é de extrema importância que seja analisado e planejado o que os demais administradores poderão fazer com as GPOs.

Além do site da Microsoft, também recomendo:

Planning Guide for Microsoft Advanced Group Policy [<http://www.microsoft.com/download/en/details.aspx?id=5448> ]

Enfim, essas foram algumas dicas básicas que li e observei durante meu dia-a-dia.

 [1]: https://www.joaoheytor.com/2011/04/23/group-policy-management-comando-dcgpofix/