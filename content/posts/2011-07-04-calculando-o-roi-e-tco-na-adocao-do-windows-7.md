---
title: Calculando o ROI e TCO na adoção do Windows 7
author: blogadminjoaoheytor
type: post
date: 2011-07-04T13:39:33+00:00
url: /2011/07/04/calculando-o-roi-e-tco-na-adocao-do-windows-7/
dsq_thread_id:
  - 2214650469
categories:
  - Planejamento e Gerenciamento

---
Pessoal, achei esse fantástico artigo no blog do <a href="http://marcelomatias.wordpress.com" target="_blank">Marcelo Martias</a>, que acho que seria extremamente útil para vários de nós, que também precisamos trabalhar com a parte de planejamento e custos:

<img loading="lazy" class="size-full wp-image-384 alignright" title="image" src="/img/sites/4/2011/07/image.png" alt="" width="250" height="214" /> 

_Ao planejar a implementação do Windows 7 em seu ambiente vários assuntos precisam ser discutidos: infraestrutura, comp__atibilidade de aplicações, compatibilidade de hardware, processo de instalação, migração dos dados, etc… Essas são etapas “técnicas” do projeto (<a href="http://technet.microsoft.com/pt-br/windows/dd361745" target="_blank">portal TechCenter do Windows 7</a>)._

_No entanto, provavelmente você vai precisar de investimentos para realizá-lo. E quando você levar esse assunto ao gestor financeiro, ele pode te questionar:_

  * _Quanto custa?_
  * _Como essa solução pode aumentar o faturamento da nossa empresa?_
  * _Em quantos anos (ou meses) teremos o Retorno desse Investimento (ROI)?_
  * _Qual a proposta de redução do Custo Total de Propriedade (TCO)?_

_Responder essas questões não é tarefa fácil, mas pode ser uma tarefa menos árdua se tivermos uma ferramenta com esse propósito._

_A boa notícia é que essa ferramenta existe, e ainda por cima é gratuita!_

_Ela foi desenvolvida pela [Alinean][1], com base em muita análise de mercado e avaliação profunda em grandes clientes que já adotaram o Windows 7 desde o seu lançamento._

_**Importante**: a Alinean foi fundada por especialistas do Gartner, e trabalha para várias empresas como: Dell, Citrix, HP, VMware, Cisco, Oracle, EMC, IBM…_

_Saiba nesse artigo como acessar e usar essa ferramenta, gerando sua própria análise de ROI e TCO, com base na proposta de migração dos seu parque de PCs para Windows 7._

_**Importante:** Antes de prosseguir com o uso dessa ferramenta, eu recomendo que você faça uma avaliação do modelo de maturidade da sua infraestrutura básica (<a href="http://www.microsoft.com/brasil/servidores/otimizacao/tools/overview.mspx" target="_blank" class="broken_link">Microsoft Core IO</a> &#8211; “Auto-Avaliação de Otimização” – “Infraestrutura Básica”). O resultado do nível de maturidade é um dos parâmetros dessa análise de ROI/TCO para Windows 7. Se você não conhece esse conceito entre em contato com seu parceiro Microsoft para esclarecimentos._

_Com o resultado da análise do nível de maturidade em mãos, vamos agora para a análise da adoção do Windows 7!_

_Acessa a ferramenta através do site [https://roianalyst.alinean.com/msft/AutoLogin.do?d=202102636954012893][2]{.broken_link}_

_Você precisa preencher/confirmar todos os campos, de todas as abas. Veja abaixo uma visão geral de cada uma delas:_

_**Dica:** se um campo está com fundo amarelo é porque você ainda não mudou seu o valor padrão. Quando o valor é alterado o campo passa para a cor verde. Quanto mais precisão houver no preenchimento dessas informações, melhor será o resultado._

_**Aba “Perfil da Organização”**_

_Escreva o nome da empresa a ser avaliada, setor e e país. Selecione o método “Avançado” e comece o preenchimento de todos os campos do formulário._

_**Dica:** Passe o mouse sobre o ícone redondo azul para saber informações sobre cada campo, como no exemplo abaixo (clique em cada uma das imagens desse artigo para vê-las em tamanho real):_

_[<img loading="lazy" class="aligncenter size-thumbnail wp-image-385" title="image1" src="/img/sites/4/2011/07/image1-150x150.png" alt="" width="150" height="150" />][3]_

_**Aba “Perfil Atual de PCs”**_

_Aqui você indica os detalhes da situação atual da empresa em relação aos PCs: quantos PCs com Windows XP, Windows Vista, Windows 7…_

_Ao final dessa página há um link chamado “Analisar / Editar Suposições Atuais Adicionais”. É muito importante que você clique nesse link e confira os valores de cada campo (ex.: custo com energia elétrica)._

_[[<img loading="lazy" class="size-thumbnail wp-image-387 alignleft" title="image3" src="/img/sites/4/2011/07/image3-150x150.png" alt="" width="150" height="150" />][4]<img loading="lazy" class="aligncenter size-thumbnail wp-image-386" title="image2" src="/img/sites/4/2011/07/image2-150x150.png" alt="" width="150" height="150" />][5]  
_ 

_**Aba “Estratégia do Windows 7”**_

_Chegou a hora de detalhar qual é a solução proposta, incluindo os custos com aquisição de software. É muito importante que nessa etapa você conte com o apoio do parceiro Microsoft responsável por licenciamento. Isso te ajudará a descobrir a melhor forma de licenciamento e custos envolvidos._

_Ao final dessa página também há um formulário “escondido”. Clique em “Exibir / editar detalhes da agenda de implantação do Windows 7” e atualize todos os campos de acordo com a sua realidade._

<p style="text-align: center">
  <em><a href="/img/sites/4/2011/07/image4.png"><a href="/img/sites/4/2011/07/image5.png"><img loading="lazy" class="size-thumbnail wp-image-389 alignleft" title="image5" src="/img/sites/4/2011/07/image5-150x150.png" alt="" width="150" height="150" /></a><img loading="lazy" class="aligncenter size-thumbnail wp-image-388" title="image4" src="/img/sites/4/2011/07/image4-150x150.png" alt="" width="150" height="150" /></a><br /> </em>
</p>

_**Aba “Implantação do Windows 7”**_

_Aqui você detalha as ferramentas e métodos usados na implementação do Windows 7._

  * _Vai usar System Center Configuration Manager (Intervenção Zero) ou apenas o Microsoft Deployment Toolkit (Intervenção Leve) no processo de migração?_
  * _Quantos minutos serão gastos em cada etapa? – esses valores já estão pré-populados, como a grande maioria._
  * _Como que a questão de compatibilidade de aplicações será trabalhada?_
  * _Qual o custo de treinamento para o usuário final?_
  * _etc…_

_[<img loading="lazy" class="aligncenter size-thumbnail wp-image-390" title="image6" src="/img/sites/4/2011/07/image6-150x150.png" alt="" width="150" height="150" />][6]  
_ 

_**Aba “Comparação de TCO”**_

_Chegou a hora de colher os resultados? Calma, ainda não…_

_Note que nessa página você pode marcar/desmarcar quais itens serão considerados no resultado final (há um “checkbox” à esquerda de cada item). Marque cada um de acordo com a sua necessidade._

_Além disso cada item sublinhado em azul esconde outro formulário (e nessa página existem vários). Revise cada um e faça as alterações necessárias._

_[<img loading="lazy" class="aligncenter size-thumbnail wp-image-394" title="image7" src="/img/sites/4/2011/07/image7-150x150.png" alt="" width="150" height="150" />][7]  
_ 

_**Aba “Análise de ROI”**_

_Aqui você também escolhe quais itens devem, ou não, ser considerados na avaliação. Note a grande liberdade que você tem para incluir custos extras, que também podem fazer parte desse projeto._

_[<img loading="lazy" class="aligncenter size-thumbnail wp-image-391" title="image8" src="/img/sites/4/2011/07/image8-150x150.png" alt="" width="150" height="150" />][8]  
_ 

_**Gerando os relatórios**_

_Agora sim chegou a hora de colher os frutos!_

_Clique no botão “Criar um relatório” na parte superior do site. Ao ser questionado sobre a necessidade de fazer o seu registro clique em OK._

_Preencha seu endereço de e-mail, clique em “Registro”, preencha os dados solicitados e clique em “Registro” novamente._

_Você receberá uma confirmação por e-mail contendo uma senha. Isso permite retornar à ferramenta mantendo o registro das suas análises._

_Pronto, agora basta selecionar o relatório desejado e clicar no botão “Criar relatório”. Veja abaixo o exemplo de dois slides do relatório em formato PPT (todos os relatórios são em Português):_

_[<img loading="lazy" class="alignleft size-thumbnail wp-image-392" title="image9" src="/img/sites/4/2011/07/image9-150x150.png" alt="" width="150" height="150" />][9]_

<img loading="lazy" class="alignright size-thumbnail wp-image-393" title="image10" src="/img/sites/4/2011/07/image10-150x150.png" alt="" width="150" height="150" /> 

&nbsp;

_Os tipos de relatório são:_

  * _Relatório Completo em formato .DOC (~179 páginas)_
  * _Relatório Resumido em formato .DOC (~28 páginas)_
  * _Apresentação em formato .PPT (~50 slides)_

&nbsp;

_**Outros recursos interessantes**_

_Navegue no menu superior esquerdo (Arquivar, Exibir, Opções, Ajuda) para personalizar a ferramenta._

_Você pode convidar outras pessoas para colaborar com a sua análise. Para isso use o botão “Colaborar”, no menu superior direito, e siga com os convites!_

_Lembre-se de consultar um parceiro Microsoft para te ajudar com essa análise._

_Esse tipo de avaliação faz muita diferença ao gestor financeiro da sua organização._

Para quem quiser dar uma olhada melhor, o artigo original se encontra em: **<a href="http://marcelomatias.wordpress.com/2011/07/04/calculando-o-roi-e-tco-windows-7" target="_blank">http://marcelomatias.wordpress.com/2011/07/04/calculando-o-roi-e-tco-windows-7</a>**

 [1]: http://www.alinean.com/aboutalinean.aspx
 [2]: https://roianalyst.alinean.com/msft/AutoLogin.do?d=202102636954012893 "https://roianalyst.alinean.com/msft/AutoLogin.do?d=202102636954012893"
 [3]: /img/sites/4/2011/07/image1.png
 [4]: /img/sites/4/2011/07/image3.png
 [5]: /img/sites/4/2011/07/image2.png
 [6]: /img/sites/4/2011/07/image6.png
 [7]: /img/sites/4/2011/07/image7.png
 [8]: /img/sites/4/2011/07/image8.png
 [9]: /img/sites/4/2011/07/image9.png