---
title: Rodando jogos antigos no Windows 7
author: João Heytor
type: post
date: 2011-11-08T14:21:45+00:00
url: /2011/11/08/rodando-jogos-antigos-no-windows-7/
dsq_thread_id:
  - 2188662448
categories:
  - Clientes

---
Se você assim como eu, passou pela fase de alguns clássicos dos jogos para PC, como Constructor, Constructor Street Wars, Prince of Persia (Não esse com 1 bilhão de cores que parece mais real do que a realidade&#8230; aquele de 8 bits da época do Windows 95), Doom, Duke Nukem, entre outros, e já teve a frustação de tentar roda-los no Windows 7, mesmo com aquela opção de Compatibilidade Ativada e nada, saiba que agora seus problemas acabaram!!!!

Existe um programa chamado DosBox [<a href="http://www.dosbox.com/" target="_blank">http://www.dosbox.com/</a> ] que nada mais é do que um emulador de DOS, ou melhor dizendo, um santo software para todo nerd das antigas&#8230; hehehe

Atualmente, o DosBox está na versão 0.74 e para roda-lo é bem simples. Vamos aos passos:

**1º Passo:** Criar uma pasta onde os jogos serão salvos. No meu caso, preferi C:DosProgs;

**2º Passo:** Após abrir o DosBox, devemos montar a unidade que usaremos para instala-lo. Para isso, devemos digitar:

> <p style="text-align: center">
>   <strong>mount c C:DosProgs </strong>
> </p>

****Onde DosProgs é a pasta que queremos usar como base para salvar nossos jogos;

[<img loading="lazy" class="aligncenter" title="dosbox001" src="/img/sites/4/2011/11/dosbox001-300x31.png" alt="" width="300" height="31" />][1]****

**3º Passo:** Precisamos do CD do jogo que queremos instalar. Pode ser o CD físico mesmo, ou pode ser um arquivo iso com a imagem do jogo. Apenas lembro, que se você tiver a imagem do jogo em iso, você irá precisar de um programa para emular um drive de CD-ROM, como por exemplo Daemon Tools ou o Virtual CloneDrive, entre outros;

**4º Passo:** Após estar com o CD já emulado com dentro do seu drive de CD, basta digitar:

> <p style="text-align: center">
>   <strong>mount d D: -t cdrom -usecd 0 –ioctl</strong>
> </p>

Onde D: é a letra da unidade em que está o nosso jogo, como no meu caso, a minha unidade onde está a instalação do jogo é a G:;

[<img loading="lazy" class="aligncenter size-medium wp-image-458" title="dosbox002" src="/img/sites/4/2011/11/dosbox002-300x49.png" alt="" width="300" height="49" />][2]

**5º Passo:** Agora basta digitarmos D: e rodar o setup do jogo, onde normalmente basta digitarmos install.exe ou setup.exe, que são nomes clássicos para rodar a instalação de programas dessa época.

Bom é isso pessoal!! Esse é um software bem legal para relembrar os velhos tempos&#8230; hehehe&#8230;

 [1]: /img/sites/4/2011/11/dosbox001.png
 [2]: /img/sites/4/2011/11/dosbox002.png