---
title: Como Gerenciar GPOs de um Domínio com Windows 2003 no Windows 7
author: João Heytor
type: post
date: 2011-04-25T18:16:40+00:00
url: /2011/04/25/como-gerenciar-gpos-de-um-dominio-com-windows-2003-no-windows-7/
dsq_thread_id:
  - 2181425080
categories:
  - Servidores

---
Hoje vou trazer para vocês algo que acredito que pouca gente saiba. Com a vinda das versões do Windows Vista/7, perdemos muitas opções de  
configuração de GPO se ainda optarmos por utilizar Controladores de Domínio com o Windows Server 2003 instalados, tendo em vista que diversas das novas GPOs, apenas estão disponíveis nas versões do Windows Server 2008).

Pois bem, para podermos administrar as novas configurações de GPO, podemos instalar o R.S.A.T. (Remote Server Administration Tools)  for Windows 7 (Observação: Apenas é possível rodá-lo nas versões Enterprise, Profissional ou Ultimate do Windows 7), que contém o GPMC (Group Policy Management Console), que no Windows 2008 agora é nativo do sistema.

O RSAT está disponível para download **em <a href="http://go.microsoft.com/fwlink/?LinkId=130862.Não" target="_blank">http://go.microsoft.com/fwlink/?LinkId=130862.Não</a>**[.][1]

Não podemos esquecer que mesmo instalando o RSAT, ele não instala automaticamente o GPMC. Para instalá-lo, temos que ir ao Painel de Controle e abrir o ícone Programas e Recursos. Na tela que se abre, devemos clicar em Ativa ou Desativar Recursos do Windows, expandir Ferramentas de Administração de Recursos e por fim, marcar a caixa de seleção Ferramentas de Administração de Recursos e Ferramentas de Gerenciamento de Diretiva de Grupo.

Lembrando que após a instalação, o GPMC ficará disponível dentro da pasta Ferramentas Administrativas (Tanto no Menu Iniciar como dentro  
do Painel de Controle), sob o nome de Gerenciamento de Diretiva de Grupo.

O mais interessante, é que também podemos administrar várias roles e features do Windows 2008 e algumas do Windows 2003.

É isso ai pessoal, espero que tenham gostado de mais dica!! E não deixem de comentar!!

Baseado no Artigo: **<a href="http://windows.microsoft.com/pt-BR/windows7/Group-Policy-management-for-IT-pros" target="_blank">http://windows.microsoft.com/pt-BR/windows7/Group-Policy-management-for-IT-pros</a>**

 [1]: http://go.microsoft.com/fwlink/?LinkId=130862