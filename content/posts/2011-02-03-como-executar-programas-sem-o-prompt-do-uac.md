---
title: Como executar programas sem o Prompt do UAC
author: blogadminjoaoheytor
type: post
date: 2011-02-03T18:07:10+00:00
url: /2011/02/03/como-executar-programas-sem-o-prompt-do-uac/
gwo4wp:
  - 'a:4:{s:7:"enabled";s:1:"1";s:14:"control_script";s:0:"";s:15:"tracking_script";s:0:"";s:17:"conversion_script";s:0:"";}'
aktt_notify_twitter:
  - yes
aktt_tweeted:
  - 1
dsq_thread_id:
  - 2192165362
categories:
  - Clientes

---
Muitos usuários desativam o **UAC** (_User Account Control_) por acharem extremamente irritante quando executamos um software que exige a elevação de privilégios.

O UAC é um recurso extremamente útil que está presente nas versões do Windows Vista e 7, que faz com que nosso sistema se torne mais seguro e robusto, pois determinados programas não são executados diretamente como administrador, onde precisamos explicitamente dizer que autorizamos a elevação de privilégios. Isso faz com que determinados malwares não sejam executados.

Mas e quando temos que rodar toda hora um software que exige tal elevação, e toda hora aparece aquela “telinha” perguntando se autorizamos sua execução com privilégios administrativos ou não, isso acaba tomando um certo tempo e paciência de nossa parte.

Para solucionarmos tal problema, podemos fazer uma pequena “trapaça”.

Devemos utilizar o Agendador de Tarefas (Iniciar, Todos os Programas, Acessórios e Ferramentas de Sistemas, ou simplesmente **taskschd.msc** no prompt de executar).

Gosto de usar um programa chamado FileHippo, que verifica se existe uma versão mais nova de alguns softwares instalados. Para ser executado, o FileHippo precisa ter privilégios administrativos, e como deixo o UAC sempre na opção padrão, sou vítima da “telinha” de autorização.

Após abrirmos o Agendador de Tarefas, devemos clicar em Biblioteca do Agendador de Tarefas (Lado Esquerda).

Em seguida, clicar em “Criar Tarefa&#8230;”

Dê um nome para sua tarefa, no meu caso ela se chama FileHippo.

Agora vem o famoso pulo do gato. Nessa mesma tela, não podemos esquecer de ticar o item: **“Executar com privilégios mais altos”**.

Nesse instante, devemos clicar em Ações, e em seguida no botão Novo.

Na parte de Ação, devemos deixar “Iniciar Um Programa” e clicar no botão Procurar, para agora indicar onde está o programa em questão.

Para que não seja necessário executarmos o Agendador de Tarefas toda hora que desejemos executar o aplicativo, devemos criar um atalho para essa tarefa (Nota: Para criar atalho, é o botão direito, Novo e Atalho).

No local solicitando o local do item, devemos digitar:

**schtasks /run /tn &#8220;FileHippo&#8221;**

Onde obviamente está &#8220;FileHippo&#8221; deve ser o nome da tarefa previamente criada.

E pronto, tarefa criada com sucesso! Agora toda vez que você executar o atalho, não será mais incomodado pelo UAC.

Espero que tenham gostado de mais essa dica. Não lembro de onde peguei isso, só lembro que vi há alguns meses, então se alguém souber me avise que dou os devidos créditos.