---
title: AWS – Criação de Máquinas Windows Server
author: blogadminjoaoheytor
type: post
date: 2016-04-26T02:24:22+00:00
url: /2016/04/25/aws-criacao-de-maquinas-windows-server/
php_everywhere_code:
  - 'Just put [php_everywhere] where you want the code to be executed.'
dsq_thread_id:
  - 4776981878
categories:
  - Cloud Computing

---
O foco de hoje é descobrirmos como criar uma máquina virtual baseada em Windows Server no player AWS (Amazon).

Atualmente, para os profissionais de TI é quase que obrigatório entender de máquinas virtuais e computação em nuvem (cloud computing). Isso virou uma tendência de mercado devido as inúmeras vantagens que estas tecnologias nos trazem, sejam elas com corte de custos de licença, agilidade para criação de novos ambientes, entre outros!

Neste artigo, pretendo ensinar a como iremos instalar uma máquina com Windows Server 2012 R2 em **APENAS 5 MINUTOS**.

<!--more-->

Mãos a massa! Primeira coisa que devemos fazer, é entrar no site _**<a href="http://aws.amazon.com" target="_blank">http://aws.amazon.com</a>** _e efetuar login (ou criarmos uma conta seguindo o passo-a-passo).

Em seguida, iremos selecionar o serviço de _**EC2**_, que é o serviço da Amazon voltado para a criação das máquinas virtuais em nuvem!

&nbsp;<figure id="attachment_1086" aria-describedby="caption-attachment-1086" style="width: 264px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1086 size-full" title="AWS - EC2" src="/img/2016/04/001-1.png" alt="AWS - EC2" width="264" height="226" />][1]<figcaption id="caption-attachment-1086" class="wp-caption-text">AWS &#8211; EC2</figcaption></figure> 

Após está seleção, nos é mostrado um resumo do que temos naquela região (Instâncias, grupos de segurança, etc).

**ATENÇÃO: No canto superior direito, temos a região onde desejamos criar nossas máquinas e/ou quaisquer outros serviços. Vale ressaltar que POR PADRÃO, as regiões não conversam entre si! Isso quer dizer que, se eu quiser ter uma rede de máquinas virtuais que se comuniquem entre si, irei precisar criar todas as minhas máquinas na mesma região!**

Na imagem abaixo, podemos ver que para este lab, estarei criando minha máquina virtual na região de **São Paulo**.

Para começarmos a criação, devemos clicar no botão _**LAUNCH INSTANCE**_.<figure id="attachment_1087" aria-describedby="caption-attachment-1087" style="width: 665px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1087 size-large" title="AWS - Resumo" src="/img/2016/04/002-1-1024x264.png" alt="AWS - Resumo" width="665" height="171" />][2]<figcaption id="caption-attachment-1087" class="wp-caption-text">AWS &#8211; Resumo</figcaption></figure> 

P**asso 1, selecionarmos o Sistema Operacional**. Aqui, iremos escolher o Microsoft Windows Server 2012 R2 Base e iremos clicar no botão _**Select**_.<figure id="attachment_1088" aria-describedby="caption-attachment-1088" style="width: 665px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1088 size-large" title="AWS - Passo 1 - Selecionar Sistema Operacional" src="/img/2016/04/003-1-1024x337.png" alt="AWS - Passo 1 - Selecionar Sistema Operacional" width="665" height="219" />][3]<figcaption id="caption-attachment-1088" class="wp-caption-text">AWS &#8211; Passo 1 &#8211; Selecionar Sistema Operacional</figcaption></figure> 

**Passo 2, escolher o tipo de instância**. Isso varia muito de acordo com o que será executado na máquina virtual! Normalmente, as máquinas da família **_General Purpose_** (Propósitos Gerais) conseguem rodar tranquilamente os principais softwares e sistemas de mercado! Vale lembrar que cada tamanho tem um preço específico! Para saber mais sobre os valores cobrados pela AWS, basta entrar no link: _<a href="https://aws.amazon.com/pt/ec2/pricing/" target="_blank"><strong>https://aws.amazon.com/pt/ec2/pricing/</strong></a>_. Como este é apenas um lab, estarei criando uma instância do tipo **t2.micro** que, caso ainda não tenha usado, posso utiliza-la durante o período de **12 meses SEM CUSTO**! Está é uma possibilidade bem interessante para quem quer estudar o **_EC2_** da AWS.

Após selecionarmos nossa instância, é necessário clicar em _**Next: Configure Instance Details**_:<figure id="attachment_1089" aria-describedby="caption-attachment-1089" style="width: 665px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1089 size-large" title="AWS - Passo 2 - Selecionar o tipo de instância" src="/img/2016/04/004-1-1024x501.png" alt="AWS - Passo 2 - Selecionar o tipo de instância" width="665" height="325" />][4]<figcaption id="caption-attachment-1089" class="wp-caption-text">AWS &#8211; Passo 2 &#8211; Selecionar o tipo de instância</figcaption></figure> 

**Passo 3, configurar os detalhes da instância.** As principais configurações que devemos efetuar são: **Network** (Que indica em qual rede nossa máquina ficará), **Subnet** (Subnet da nossa rede) e **Shutdown behavior** (O que acontecerá com o volume caso está máquina seja desligada. **ATENÇÃO:** Se deixarmos marcado **Terminate**, caso nossa máquina seja desligada, o volume da máquina será apagado). Feito essas configurações, iremos clicar em _**Next: Add Storage**_.<figure id="attachment_1090" aria-describedby="caption-attachment-1090" style="width: 665px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1090 size-large" title="AWS - Passo 3 - Detalhes de Configuração da Instância" src="/img/2016/04/005-1-1024x507.png" alt="AWS - Passo 3 - Detalhes de Configuração da Instância" width="665" height="329" />][5]<figcaption id="caption-attachment-1090" class="wp-caption-text">AWS &#8211; Passo 3 &#8211; Detalhes de Configuração da Instância</figcaption></figure> 

**Passo 4, adicionar armazenamento!** É neste item que iremos definir o tamanho de nosso HD! Também é possível adicionar mais volumes a nossa máquina virtual. **ATENÇÃO: Para termos direito aos 12 meses gratuitos, nosso volume pode ter no máximo 30 GB.** Aqui também é possível alterarmos o tipo de volume e também os IOPS que desejamos reservar.

Em seguida, devemos clicar em **Next: Tag Instance**.<figure id="attachment_1091" aria-describedby="caption-attachment-1091" style="width: 665px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1091 size-large" title="AWS - Passo 4 - Adicionar Armazenamento" src="/img/2016/04/006-1-1024x446.png" alt="AWS - Passo 4 - Adicionar Armazenamento" width="665" height="290" />][6]<figcaption id="caption-attachment-1091" class="wp-caption-text">AWS &#8211; Passo 4 &#8211; Adicionar Armazenamento</figcaption></figure> 

**Passo 5, tags da instância**. Aqui podemos adicionar _**tags**_, que são marcações para melhor identificarmos nossa máquina virtual. Essa função se torna bastante útil quando nosso parque de máquinas virtuais começa a crescer!

Assim que criarmos as _**tags**_ que desejamos, iremos clicar em _**Next: Configure Security Group**_.<figure id="attachment_1092" aria-describedby="caption-attachment-1092" style="width: 665px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1092 size-large" title="AWS - Passo 5 - Tags da Instância" src="/img/2016/04/007-1-1024x448.png" alt="AWS - Passo 5 - Tags da Instância" width="665" height="291" />][7]<figcaption id="caption-attachment-1092" class="wp-caption-text">AWS &#8211; Passo 5 &#8211; Tags da Instância</figcaption></figure> 

**Passo 6, configurar grupos de segurança**. Na AWS, grupos de segurança são grupos de portas de serviços liberadas! Por exemplo, no grupo abaixo, tenho apenas a porta **3389** (MS RDP) liberada para qualquer IP conectar. Podemos facilmente adicionar novas portas clicando em _**Add Rul****e**_. Lembrando que este item está diretamente ligado aos tipos de serviços que estarão sendo executadas na máquina virtual! **ATENÇÃO: No item SOURCE, por questões de segurança, tente sempre colocar algum IP!** Quando é setado **_Anywhere_**, isso quer dizer que nossa máquina estará acessível por qualquer IP do mundo! Portanto, muito cuidado com as portas que serão liberadas.

Liberando as portas necessárias, iremos clicar em _**Review and Launch**_.<figure id="attachment_1093" aria-describedby="caption-attachment-1093" style="width: 665px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1093 size-large" title="AWS - Passo 6 - Configurar Grupos de Segurança" src="/img/2016/04/008-1024x447.png" alt="AWS - Passo 6 - Configurar Grupos de Segurança" width="665" height="290" />][8]<figcaption id="caption-attachment-1093" class="wp-caption-text">AWS &#8211; Passo 6 &#8211; Configurar Grupos de Segurança</figcaption></figure> 

**Passo 7, revisar a criação da instância.** Aqui temos apenas um resumo dos itens que selecionamos durante todo este passo-a-passo.

O importante aqui é verificar se selecionamos as opções corretas e em seguida clicar em _**Launch**_.<figure id="attachment_1094" aria-describedby="caption-attachment-1094" style="width: 665px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1094 size-large" title="AWS - Passo 7 - Revisar Criação da Instância" src="/img/2016/04/009-1-1024x477.png" alt="AWS - Passo 7 - Revisar Criação da Instância" width="665" height="310" />][9]<figcaption id="caption-attachment-1094" class="wp-caption-text">AWS &#8211; Passo 7 &#8211; Revisar Criação da Instância</figcaption></figure> 

Ao clicarmos em _**Launch**_, será necessário criarmos (ou atribuirmos, caso já tenhamos criado) uma chave de acesso a está máquina. Para isto, será necessário selecionarmos _**Create a new key pair**_, e no campo abaixo, digitarmos uma frase secreta. **ATENÇÃO: Guarde em um local seguro este arquivo!** Nos ambientes Windows, ele é necessário para geramos uma senha de administrador! Isso quer dizer que, qualquer pessoa com este arquivo, consegue, eventualmente, gerar uma nova senha de admin!.

Preenchendo estes campos, iremos clicar no botão _**Download Key Pair**_. Salve este arquivo em um local seguro pois iremos usa-lo no próximo passo!<figure id="attachment_1095" aria-describedby="caption-attachment-1095" style="width: 705px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1095 size-full" title="AWS - Criando uma key pair" src="/img/2016/04/010-1.png" alt="AWS - Criando uma key pair" width="705" height="506" />][10]<figcaption id="caption-attachment-1095" class="wp-caption-text">AWS &#8211; Criando uma key pair</figcaption></figure> 

Nossa máquina virtual está sendo criada! Basta clicarmos em _**View Instances**_.<figure id="attachment_1096" aria-describedby="caption-attachment-1096" style="width: 665px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1096 size-large" title="AWS - Máquina criada com sucesso!" src="/img/2016/04/011-1-1024x361.png" alt="AWS - Máquina criada com sucesso!" width="665" height="234" />][11]<figcaption id="caption-attachment-1096" class="wp-caption-text">AWS &#8211; Máquina criada com sucesso!</figcaption></figure> 

Voltando ao painel principal, no item _**Instances**_, agora temos nossa máquina virtual sendo executada! Ao selecionarmos este item, na parte debaixo aparece um resumo da máquina como IP, volume anexado, etc.<figure id="attachment_1097" aria-describedby="caption-attachment-1097" style="width: 665px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1097 size-large" title="AWS - Resumo da Instância" src="/img/2016/04/012-1024x449.png" alt="AWS - Resumo da Instância" width="665" height="292" />][12]<figcaption id="caption-attachment-1097" class="wp-caption-text">AWS &#8211; Resumo da Instância</figcaption></figure> 

Nossa máquina virtual já está criada e funcionando perfeitamente!

Como passo final, precisamos criar uma senha de administrador! Para isso, clique com o botão direito em cima da instância e selecione _**Get Windows Password**_.<figure id="attachment_1098" aria-describedby="caption-attachment-1098" style="width: 481px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1098 size-full" title="AWS - Get Windows Password" src="/img/2016/04/013.png" alt="AWS - Get Windows Password" width="481" height="340" />][13]<figcaption id="caption-attachment-1098" class="wp-caption-text">AWS &#8211; Get Windows Password</figcaption></figure> 

No item _**Key Name**_, é informado o nome da chave de segurança desta máquina (Ver passo que fizemos logo após o item 7). Devemos clicar em _**Escolher Arquivo**_, selecionarmos o arquivo _***.pem**_ que fizemos download e clicar em **_Decrypt Password_**.<figure id="attachment_1099" aria-describedby="caption-attachment-1099" style="width: 766px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1099 size-full" title="AWS - Gerando senha de Administrador" src="/img/2016/04/014.png" alt="AWS - Gerando senha de Administrador" width="766" height="467" />][14]<figcaption id="caption-attachment-1099" class="wp-caption-text">AWS &#8211; Gerando senha de Administrador</figcaption></figure> 

Pronto! Já temos o usuário e senha para efetuarmos uma conexão remota ao nosso servidor!<figure id="attachment_1100" aria-describedby="caption-attachment-1100" style="width: 766px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1100 size-full" title="AWS - Senha de Administrador Criada" src="/img/2016/04/015.png" alt="AWS - Senha de Administrador Criada" width="766" height="490" />][15]<figcaption id="caption-attachment-1100" class="wp-caption-text">AWS &#8211; Senha de Administrador Criada</figcaption></figure> 

O passo seguinte, é abrimos o programa **Conexão de Área de Trabalho Remota (mstsc.exe)** do Windows e em computador, podemos utilizar o _**Public DNS**_ que nos foi fornecido no passo acima.<figure id="attachment_1101" aria-describedby="caption-attachment-1101" style="width: 407px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1101 size-full" title="Conectando ao servidor" src="/img/2016/04/016.png" alt="Conectando ao servidor" width="407" height="253" />][16]<figcaption id="caption-attachment-1101" class="wp-caption-text">Conectando ao servidor</figcaption></figure> 

Será necessário informar o usuário e senha, que também obtemos no passo acima:<figure id="attachment_1102" aria-describedby="caption-attachment-1102" style="width: 425px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1102 size-full" title="Credenciais para efetuar login" src="/img/2016/04/017.png" alt="Credenciais para efetuar login" width="425" height="419" />][17]<figcaption id="caption-attachment-1102" class="wp-caption-text">Credenciais para efetuar login</figcaption></figure> 

O Windows nos avisa que não é possível autenticar o certificado de segurança desta máquina. Devemos apenas clicar em Sim para que nossa conexão continue normalmente.<figure id="attachment_1103" aria-describedby="caption-attachment-1103" style="width: 392px" class="wp-caption aligncenter">

[<img loading="lazy" class="wp-image-1103 size-full" title="Conexão Remota - Aviso de Certificado" src="/img/2016/04/018.png" alt="Conexão Remota - Aviso de Certificado" width="392" height="401" />][18]<figcaption id="caption-attachment-1103" class="wp-caption-text">Conexão Remota &#8211; Aviso de Certificado</figcaption></figure> 

E é isso pessoal! Abaixo podemos ver a máquina que criamos em menos de 5 minutos sendo executada normalmente.

Agora podemos instalar qualquer software, criar uma VPN para nossa rede local e etc! É um Windows Server 2012 R2 sendo executado em nuvem e completamente licenciado.

[<img loading="lazy" class="aligncenter size-large wp-image-1104" src="/img/2016/04/019-1024x576.png" alt="019" width="665" height="374" />][19]

Espero que tenham gostado de mais essa dica! Qualquer dúvida e ou sugestão, deixem nos comentários!

 [1]: /img/2016/04/001-1.png
 [2]: /img/2016/04/002-1.png
 [3]: /img/2016/04/003-1.png
 [4]: /img/2016/04/004-1.png
 [5]: /img/2016/04/005-1.png
 [6]: /img/2016/04/006-1.png
 [7]: /img/2016/04/007-1.png
 [8]: /img/2016/04/008.png
 [9]: /img/2016/04/009-1.png
 [10]: /img/2016/04/010-1.png
 [11]: /img/2016/04/011-1.png
 [12]: /img/2016/04/012.png
 [13]: /img/2016/04/013.png
 [14]: /img/2016/04/014.png
 [15]: /img/2016/04/015.png
 [16]: /img/2016/04/016.png
 [17]: /img/2016/04/017.png
 [18]: /img/2016/04/018.png
 [19]: /img/2016/04/019.png