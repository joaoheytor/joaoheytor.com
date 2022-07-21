---
title: Instalando VIM no pfSense
author: João Heytor
type: post
date: 2017-10-19T00:04:45+00:00
url: /2017/10/18/instalando-vim-no-pfsense/
featured_image: /img/2017/10/logo-665x435.png
dsq_thread_id:
  - 6225015063
categories:
  - Redes

---
Olá pessoal,

Não sei quanto a vocês, mas eu me sinto muito desconfortável ao utilizar o **_VI_** nas máquinas _Linux_. Isso não é diferente quando preciso editar algum arquivo junto ao _pfSense_! Várias e várias vezes, acabo fazendo alguma modificação ou checagem direto nos arquivos do sistema. Acredito que seja costume de ver a telinha preta&#8230; Enfim&#8230;  
Por isso, em todas as oportunidades possíveis, tento sempre instalar o **VIM**. Ele é um software que faz parte do meu kit de sobrevivência junto a esse ambiente de _sysadmin_!

Bom, vamos a parte prática&#8230;

Caso seu _SO_ seja _Windows_, você poderá utilizar o **Putty** (Disponível em <a href="http://www.putty.org" target="_blank" rel="noopener">http://www.putty.org</a>) para efetuar uma conexão _SSH_ ao _pfSense_ (Lembre-se de verificar se a conexão _SSH_ está habilitada em **System >> Advanced >> Admin Access >> Enable Secure Shell**).

No menu inicial do _pfSense_, vamos de opção “**8**” para abrir o _shell_!

{{< figure src="/img/2017/10/001-1.png" title="pfSense - Menu Inicial" width="671" height="423" >}}

Como de costume, vamos atualizar a lista de pacotes usando o comando
```shell
pkg update
```

{{< figure src="/img/2017/10/002-1.png" title="pfSense - Atualizando pacotes" width="623" height="97" >}}

Em seguida, vamos instalar o VIM usando o comando:
```shell
pkg install vim-lite
```

{{< figure src="/img/2017/10/003.png" title="pfSense - Instalando VIM-LITE" width="577" height="336" >}}

Aguardemos o download e instalação e pronto!! Nosso VIM já está instalado e disponível para uso!

Podemos testar digitando:
```shell
vim ARQUIVO
```

{{< figure src="/img/2017/10/004-1.png" title="pfSense - VIM" width="640" height="387" >}}


É isso pessoal, espero que gostem de mais essa dica!
