---
title: Modelo de Política de Backup
author: blogadminjoaoheytor
type: post
date: 2012-05-22T19:23:58+00:00
url: /2012/05/22/modelo-de-politica-de-backup-2/
dsq_thread_id:
  - 2180287721
categories:
  - Infraestrutura

---
Uma coisa que muitos de nossos amigos não costumam fazer, é o famoso backup. Infelizmente, por vezes já vi alguns administradores que lembram do backup somente quando precisam dele, no bom e velho português, quando ferrou tudo!!!

Como boa prática da boa funcionalidade de nossos ambientes, devemos sempre fazer backup dos dados importantes. Tentem sempre pensar na famosa Lei de Murphy: _Se algo pode dar errado, vai dar errado_. E, pode ser justamente da pior maneira possível e da maneira que não seja possível recuperar os arquivos e justamente no meio de algo extramente importante, onde aquele diretor precisava acessar tal recurso.

Como outra boa prática, é sempre interessante documentarmos todos os procedimentos internos que devemos seguir. E é nesse ponto que chegamos ao tópico em si.

Achei um exemplo bem legal e que nos dá uma ótima base para construir uma política de backup em nossa empresa. Espero que gostem&#8230;

## _Política de Backup e Restauração de Arquivos_

### _Versão x.x_

#### _1. Introdução_

_O presente documento estabelece uma política de cópias de segurança (backup) e restauração de arquivos digitais armazenados no parque tecnológico desta empresa._

_Os donos dos dados deverão ter ciência dos tempos de retenção aqui estabelecidos para cada tipo de informação e os administradores / operadores de backup deverão zelar pelo cumprimento das diretrizes aqui estabelecidas._

#### _2. Considerações iniciais_

_O serviço de backup deve ser orientado para a restauração das informações no menor tempo possível, principalmente havendo indisponibilidade de serviços que dependam da operação de restore._

_Este documento deverá ter conhecimento e anuência da Diretoria._

#### _3. Orientações Gerais:_

  1. _Cabem aos administradores prever a realização de testes periódicos de restauração, no intuito de averiguar os processos de backup e estabelecer melhorias._
  2. _A administração dos backups também deve ser orientada para que seus trabalhos respeitem as janelas para execução, inclusive realizando previsão para a ampliação da capacidade dos dispositivos envolvidos no armazenamento._
  3. _As mídias (ou dispositivos de armazenamento) deverão ser armazenados em cofre corta-fogo, ou em localidade diversa da origem dos dados (backup off-site)._
  4. _As mídias defeituosas ou inservíveis serão encaminhadas para picotamento, incineração, procedimentos de sobrescrita de dados remanescentes (disco rígido) ou outro procedimento que impossibilite a recuperação dos dados por terceiros._
  5. _As solicitações de restauração de arquivos deverão ser abertas formalmente através de ferramentas de abertura de chamados e / ou formulário que deverá conter os nomes dos arquivos e pastas que deverão ser recuperados e, principalmente, a data do aquivo que se pretende ter acesso._

#### _4. Estratégia Geral Backup:_

_De acordo com a natureza dos dados trazemos a seguinte classificação:_

  * _Arquivos dos Sistemas Operacionais;_
  * _Servidores de Arquivos;_
  * _Bancos de Dados;_
  * _Máquinas Virtuais (imagem);_
  * _Servidores de E-mail;_

_Por padrão será adotada o seguinte esquema de realização de backups, baseado no esquema GFS (exceto se especificada necessidade especial no item 5):_

  * _Backups diferenciais (denominados diários) de **segunda à quinta-feira**, realizados a partir das 20:00h., **com uma semana de retenção;**_
  * _Backups completos (full – denominados semanais) nas **segundas, terças e quartas sexta-feiras do mês**, realizados a partir das 20:00h., **com um mês de retenção;**_
  * _Backups completos (full – denominados mensais) na **primeira sexta-feira do mês**, realizados a partir das 20:00h., **com um ano de retenção;**_

#### _5. Necessidades especiais de backup (exceções):_

##### _5.1 Máquinas Virtuais (imagem);_

_O backup das máquinas virtuais como imagem (adequado para fins de disaster recovery – ou seja: restauração da máquina como um todo), será feito apenas na seguinte periodicidade:_

  * _Backups completos (full – denominados mensais) na **primeira sexta-feira do mês**, realizados a partir das 20:00h., **com um ano de retenção;**_

_No mais, as Máquinas Virtuais serão tratadas como outras máquinas físicas, devendo o cliente de backup ser instalado em cada uma delas._

Fonte: <a href="http://www.bacula.com.br/?p=792" target="_blank" class="broken_link">Bacula Backup Brazil</a>