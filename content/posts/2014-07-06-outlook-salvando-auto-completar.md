---
title: Outlook Salvando Auto-Completar
author: blogadminjoaoheytor
type: post
date: 2014-07-06T19:32:30+00:00
url: /2014/07/06/outlook-salvando-auto-completar/
dsq_thread_id:
  - 2846366597
categories:
  - Diversos

---
Olá galera!

Aposto que muitos de vocês, assim como eu já tiveram problemas com os seus Outlook&#8217;s.

Pois bem, a dica de hoje é simples, vamos aprender como salvar os itens que ficam no Auto-Completar do campo **PARA** (Acho que já perceberam que quando enviamos um e-mail para fulano@beltrano.com.br o e-mail fica gravado no Outlook, fazendo com que quando formos enviar um novo e-mail ao Fulano, o próprio Outlook mostrará o último e-mail digitando assim que começarmos a escrever o e-mail do Sr. Fulano).

O arquivo Nk2 do Outlook fica armazenado na pasta do perfil do usuário. A localização dessa pasta muda de acordo com a versão do SO:

<ul style="color: #333333">
  <li>
    Para Windows XP:<br /> <var>Unidade</var>:Documents and SettingsUsernameApplication DataMicrosoftOutlook
  </li>
  <li>
    Para Windows Vista e versões posteriores<br /> <var>Unidade</var>:UsersUsernameAppDataRoamingMicrosoftOutlook
  </li>
</ul>

Pronto! Só fazer backup deste arquivo e, teremos nossa lista de AutoCompletar salva.

Uma boa dica, é que as vezes apenas queremos juntar o arquivo de um computador com o outro. Para isso, basta colocar o arquivo Nk2 na pasta <span style="color: #333333"><strong>%appdata%MicrosoftOutlook</strong> e, iniciar o Outlook com o comando:</span>

> outlook.exe /importnk2

Fonte: <a href="http://support.microsoft.com/kb/980542/pt-br" target="_blank">Microsoft</a>

Dúvidas, só deixar nos comentários!