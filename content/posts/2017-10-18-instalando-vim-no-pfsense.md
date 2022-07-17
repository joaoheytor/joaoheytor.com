---
title: Instalando VIM no pfSense
author: João Heytor
type: post
date: 2017-10-19T00:04:45+00:00
url: /2017/10/18/instalando-vim-no-pfsense/
featured_image: /wp-content/uploads/2017/10/logo-665x435.png
dsq_thread_id:
  - 6225015063
categories:
  - Redes

---
Olá pessoal,

Não sei quanto a vocês, mas eu me sinto muito desconfortável ao utilizar o **_VI_** nas máquinas _Linux_. Isso não é diferente quando preciso editar algum arquivo junto ao _pfSense_! Várias e várias vezes, acabo fazendo alguma modificação ou checagem direto nos arquivos do sistema. Acredito que seja costume de ver a telinha preta&#8230; Enfim&#8230;  
Por isso, em todas as oportunidades possíveis, tento sempre instalar o **VIM**. Ele é um software que faz parte do meu kit de sobrevivência junto a esse ambiente de _sysadmin_!

<!--more-->Bom, vamos a parte prática&#8230;

Caso seu _SO_ seja _Windows_, você poderá utilizar o **Putty** (Disponível em <a href="http://www.putty.org" target="_blank" rel="noopener">http://www.putty.org</a>) para efetuar uma conexão _SSH_ ao _pfSense_ (Lembre-se de verificar se a conexão _SSH_ está habilitada em **System >> Advanced >> Admin Access >> Enable Secure Shell**).

No menu inicial do _pfSense_, vamos de opção “**8**” para abrir o _shell_!<figure id="attachment_1208" aria-describedby="caption-attachment-1208" style="width: 671px" class="wp-caption aligncenter">

<img loading="lazy" class="size-full wp-image-1208" src="https://www.joaoheytor.com/wp-content/uploads/2017/10/001-1.png" alt="pfSense - Menu Inicial" width="671" height="423" srcset="https://www.joaoheytor.com/wp-content/uploads/2017/10/001-1.png 671w, https://www.joaoheytor.com/wp-content/uploads/2017/10/001-1-300x189.png 300w" sizes="(max-width: 671px) 100vw, 671px" /> <figcaption id="caption-attachment-1208" class="wp-caption-text">pfSense &#8211; Menu Inicial</figcaption></figure> 

Como de costume, vamos atualizar a lista de pacotes usando o comando

> **pkg update**<figure id="attachment_1209" aria-describedby="caption-attachment-1209" style="width: 623px" class="wp-caption aligncenter">

<img loading="lazy" class="size-full wp-image-1209" src="https://www.joaoheytor.com/wp-content/uploads/2017/10/002-1.png" alt="pfSense - Atualizando pacotes" width="623" height="97" srcset="https://www.joaoheytor.com/wp-content/uploads/2017/10/002-1.png 623w, https://www.joaoheytor.com/wp-content/uploads/2017/10/002-1-300x47.png 300w" sizes="(max-width: 623px) 100vw, 623px" /> <figcaption id="caption-attachment-1209" class="wp-caption-text">pfSense &#8211; Atualizando pacotes</figcaption></figure> 

Em seguida, vamos instalar o VIM usando o comando:

> **pkg install vim-lite**<figure id="attachment_1210" aria-describedby="caption-attachment-1210" style="width: 577px" class="wp-caption aligncenter">

<img loading="lazy" class="size-full wp-image-1210" src="https://www.joaoheytor.com/wp-content/uploads/2017/10/003.png" alt="pfSense - Instalando VIM-LITE" width="577" height="336" srcset="https://www.joaoheytor.com/wp-content/uploads/2017/10/003.png 577w, https://www.joaoheytor.com/wp-content/uploads/2017/10/003-300x175.png 300w" sizes="(max-width: 577px) 100vw, 577px" /> <figcaption id="caption-attachment-1210" class="wp-caption-text">pfSense &#8211; Instalando VIM-LITE</figcaption></figure> 

Aguardemos o download e instalação e pronto!! Nosso VIM já está instalado e disponível para uso!

Podemos testar digitando:

> **vim ARQUIVO**<figure id="attachment_1211" aria-describedby="caption-attachment-1211" style="width: 640px" class="wp-caption aligncenter">

<img loading="lazy" class="size-full wp-image-1211" src="https://www.joaoheytor.com/wp-content/uploads/2017/10/004-1.png" alt="pfSense - VIM" width="640" height="387" srcset="https://www.joaoheytor.com/wp-content/uploads/2017/10/004-1.png 640w, https://www.joaoheytor.com/wp-content/uploads/2017/10/004-1-300x181.png 300w" sizes="(max-width: 640px) 100vw, 640px" /> <figcaption id="caption-attachment-1211" class="wp-caption-text">pfSense &#8211; VIM</figcaption></figure> 

É isso pessoal, espero que gostem de mais essa dica!

&nbsp;