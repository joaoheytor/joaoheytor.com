---
title: Como resetar a senha do Administrador no Windows Vista ou Seven
author: João Heytor
type: post
date: 2010-07-01T00:18:54+00:00
excerpt: Uma pequena gambiarra para podermos resetar a senha do Windows Vista ou 7
url: /2010/06/30/como-resetar-a-senha-do-administrador-no-windows-vista-ou-seven/
aktt_notify_twitter:
  - yes
  - yes
gwo4wp:
  - 
  - 
aktt_tweeted:
  - 1
dsq_thread_id:
  - 2181086363
categories:
  - Clientes

---
> **UPDATE:** Para os administradores de rede preocupados com essa dica, criei outro artigo onde dou algumas dicas para evitar que pessoas má intencionadas consigam resetar a senha do administrador [ Basta acessar em: <https://joaoheytor.com/como-evitar-o-reset-da-senha-do-administrador-no-windows-vista-ou-seven/> ]

Nesse artigo, vamos aprender a como remover a senha do Administrador para pessoas que estão rodando tanto o Windows Vista quanto o Windows Seven.

**Cenário 1:** Você pega férias da empresa onde trabalha, viaja, descança e por fim, volta ao trabalho&#8230; nesse momento, você se dá conta que esqueceu a sua própria senha de Administrador do computador&#8230;

**Cenário 2:** Seu amigo / irmão resolve mudar a senha do Administrador apenas para te sacanear&#8230;

Depois de digitar várias e várias senhas&#8230; numeros de cartões de crédito&#8230; CPF&#8230; RG&#8230; data de nascimento da mãe&#8230; data de nascimento do pai&#8230; do cachorro&#8230; senha do banco&#8230; nome da primeira namorada&#8230; você começa a suar frio&#8230; arrancar os cabelos&#8230; e o pior de tudo, você começa a ver serviço acumulado&#8230; seu chefe pede um relatório URGENTE&#8230; e você ainda não lembrou sua senha!!!

Pode parecer piada, mas não é&#8230; isso é algo extremamente comum nos dias de hoje&#8230; principalmente, quando temos que guardar várias senhas, de vários lugares diferentes.

Se você está passando por isso, esse é o seu lugar&#8230; então mãos à obra:

**1º Passo:** Antes de mais nada, é necessário baixar algum **live CD Linux** (Aquelas distribuições que tem a possibilidade de serem executadas diretamente do CD, sem que seja necessária a instalação do mesmo). No site_ <a href="http://www.livecdlist.com/" target="_blank"><strong>The LiveCD List</strong></a>_, há uma lista com praticamente todas as distribuições Linux que aceitam tal opção. Particularmento, recomendo o _**<a href="http://www.ubuntu.com/" target="_blank">Ubuntu</a>**_, que é uma distribuição leve, intuitiva e com uma ótima interface;

**2º Passo:** Após gravar a iso baixada em um CD ou DVD, certifique-se que o boot inicial do seu computador seja pela unidade de CD/DVD;

**3º Passo:** Ao carregar a tela de boot inicial do Ubuntu, escolha a opção &#8220;Testar Ubuntu sem qualquer mudança no seu computador&#8221;. Lembro que essa opção é válida apenas para quem estiver usando o Ubuntu. Quem estiver com outra distribuição do Linux, escolha a opção que dê boot diretamente da unidade de CD/DVD;

**4º Passo:** Assim que o sistema carregar, localize a partição onde o sistema Windows esteja instalado. Vá na pasta &#8220;windows/system32&#8221; e localize o arquivo com o nome &#8220;sethc.exe&#8221;. Renomeio para qualquer outro nome (Por exemplo, &#8220;original_sethc.exe&#8221;, ou qualquer outro que achar melhor. Apenas lembre-se do nome para depois poder desfazer tal alteração.

**5º Passo:** Depois de renomear o arquivo anterior, na mesma pasta encontre o arquivo &#8220;cmd.exe&#8221;. Você deve copia-lo e cola-lo (No Ubuntu, quando você seleciona um arquivo e pressiona Ctrl + C [Atalho para Copiar] e em seguida Ctrl + V [Atalho para Colar], o próprio sistema cria uma cópia do arquivo;

**6º Passo:** Altere o nome da cópia do &#8220;cmd.exe&#8221; para &#8220;sethc.exe&#8221;;

**7º Passo:** Reinicie o computador, mas antes remova o CD do Ubuntu para que o computador possa carregar o Windows normalmente;

**8º Passo:** Ao aparecer a tela de login, aperte 5 (isso mesmo, cinco) vezes a tecla &#8220;SHIFT&#8221; da esquerda;

**9º Passo:** Na tela de comando que se abre, digite o comando &#8220;control userpasswords2&#8221; (Sem aspas) e aperte &#8220;ENTER&#8221;;

**10º Passo:** Escolha o usuário desejado e clique no botão &#8220;Redefinir Senha&#8221;. Digite sua nova senha e seja feliz!!!!

É isso pessoal, se gostaram, peço que comentem!!! 😀

_**Obs.: Não se esqueça de desfazer as alterações nos arquivos renomeados, assim que conseguir efetuar o login com sua nova senha!!!**_