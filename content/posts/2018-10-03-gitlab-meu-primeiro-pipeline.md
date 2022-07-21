---
title: 'Gitlab: Meu primeiro pipeline'
author: João Heytor
type: post
date: 2018-10-04T02:41:31+00:00
url: /2018/10/03/gitlab-meu-primeiro-pipeline/
featured_image: /img/2018/10/jenkins-pipeline-1-1-1.png
categories:
  - DevOps

---
Salve pessoal! Hoje vamos começar a trabalhar com os conceitos de CI/CD criando uma pipeline no GitLab.

# Por que GitLab?
Existem inúmeras razões pra eu gostar do GitLab. Entre elas, posso destacar:

  * Possibilidade de criar repositórios privados gratuitamente;
  * Possibilidade de usar o GitLab na &#8220;nuvem&#8221; ou baixa-lo e instala-lo em um servidor privado;
  * GitLab Runner, este é um motivo matador para a minha escolha em alguns projetos. O GitLab permite que você use o Runner, que é um projeto open source que é usado para executar os jobs e enviar os resultados de volta para o GitLab. Ou seja, ele nos permite buildar sem a necessidade de nenhuma instalação externa.

# Definições Importantes
Antes de prosseguirmos, é importante estar claro os seguintes conceitos:

## **Pipeline**
_A pipeline is a group of jobs that get executed in stages. All of the jobs in a stage are executed in parallel (if there are enough concurrent Runners), and if they all succeed, the pipeline moves on to the next stage. If one of the jobs fails, the next stage is not (usually) executed. You can access the pipelines page in your project&#8217;s Pipelines tab._

_In the following image you can see that the pipeline consists of four stages (build, test, staging, production) each one having one or more jobs._

Tradução livre:

_Uma pipeline é um grupo de jobs que são executados em estágios. Todos os jobs em um estágio são executados em paralelo (se houver Runners suficientes), e se todos eles tiverem sucesso, a pipeline move para o próximo estágio. Se um dos jobs falharem, o próximo estágio não será executado (geralmente). Você pode acessar a página de pipelines na aba Pipelines do seu projeto._

_Na imagem abaixo você pode ver que uma pipeline consiste de quatro estágios (build, test, staging, production (cada um tendo um ou mais jobs).

![Estágios de uma pipeline](/img/2018/10/pipelines.png)
Estágios de uma pipeline

Mais detalhes sobre pipeline em _<https://docs.gitlab.com/ee/development/pipelines.html#pipelines-for-the-gitlab-project>.

## Job
São um conjunto de instruções que executarão uma determinada ação. Exemplo: job para criar um pacote para uma determinada distribuição Linux.

## **Continuous Integration (CI)**
_Continuous Integration_ ou _Integração contínua_, é a prática de integração e testes de um novo código comitado. A ideia é que no processo de merge de um novo código exista uma forma automatizada de testa-lo e com isso identificar possíveis problemas o mais cedo possível.

## Continuous Deployment (CD)
Em resumo, _Continuous Deployment_ ou _Implantação Contínua_, é a prática de continuamente (e automaticamente) tratarmos o envio de código para os ambientes, que normalmente são **DEV** (Desenvolvimento), **STAGE** (Homologação) e **PROD** (Produção). Ou seja, caso o meu novo código passe em todos os testes do ambiente DEV, ele será automaticamente promovido para o ambiente de STAGE. Se passar em todos os testes deste stage, será promovido para PROD. E assim por diante&#8230;

É com a união destes conceitos e boas práticas, que algumas empresas conseguem fazer vários e vários commits por dia em ambiente de produção, sem impactar o dia-a-dia de seus clientes.

# O Problema
Bom, vamos ao problema que devemos resolver hoje:

Ao efetuar um commit na branch master, o GitLab deverá atualizar um determinado site via FTP.

Para este exemplo, vamos utilizar o _<a href="https://www.joaoheytor.com/curriculo/" target="_blank" rel="noopener">https://www.joaoheytor.com/curriculo/</a>_, que é onde hospedo o meu currículo.

# Desenvolvendo a Solução
Para iniciarmos a resolução deste problema, precisamos criar um arquivo com o nome de **.gitlab-ci.yml** cujo conteúdo segue o padrão **YML** (A propósito, no link _<https://docs.gitlab.com/ee/ci/yaml/README.html#jobs>_ você pode ver o conteúdo que este arquivo aceita).

_GitLab offers a continuous integration service. If you add a .gitlab-ci.yml file to the root directory of your repository, and configure your GitLab project to use a Runner, then each commit or push triggers your CI pipeline._

_The .gitlab-ci.yml file tells the GitLab runner what to do. By default it runs a pipeline with three stages: build, test, and deploy. You don&#8217;t need to use all three stages; stages with no jobs are simply ignored._

Em tradução direta:

_GitLab oferece um serviço de integração continuo. Se você adicionar um arquivo .gitlab-ci.yml no diretório raiz do seu repositório, e configurar seu projeto no GitLab para usar um Runner, então qualquer commit ou push dispara sua pipeline de CI._

_O arquivo .gitlab-ci.yml diz ao GitLab runner o que fazer. Por padrão ele roda uma pipeline com três estágios: build, test e deploy. Vocâ não precisa usar os três estágios; estágios com nenhum job são simplesmente ignorados. _

O arquivo que estaremos usando é bem simples e se resume a:

<div>
  <div>
    <strong>deploy:</strong>
  </div>
  <div>
    <strong>script:</strong>
  </div>

  <div>
    &#8211; apt-get update -qq && apt-get install -y -qq lftp
  </div>

  <div>
    &#8211; lftp -c &#8220;set ftp:ssl-allow no; open -u $BLOGUSERNAME,$BLOGPASSWORD $BLOGHOST; mirror -Rnev ./ ./public_html/curriculo &#8211;ignore-time &#8211;parallel=10 &#8211;exclude-glob .git* &#8211;exclude .git/ &#8211;exclude README.md&#8221;
  </div>

  <div>
    <strong>only:</strong>
  </div>

  <div>
    &#8211; master
  </div>
</div>

Onde:
  * **script:** O que será executado, ou seja, a ação do nosso pipeline. No nosso exemplo, estamos usando os comandos Linux **apt-get update** para atualizar a lista de pacotes disponíveis e em seguida será instalado o pacote chamado **lftp**, que fará a mágica de fazer o upload via ftp. Após a instalação, ele chamará o lftp com alguns parâmetros: 
      * **$BLOGUSERNAME &#8211; $BLOGPASSWORD &#8211; $BLOGHOST:** São as variáveis usadas para autenticação via FTP.  Como boa prática, não é interessante deixamos dados sensíveis fixos em nosso código. Ao invés disso, passamos tais dados por variável. Mais abaixo mostro como podemos fazer essas configurações;
      * **exclude-glob** e **exclude:** Não devemos transferir os arquivos/diretórios que tenham o prefixo **.git** e **README.md**.

Para mais detalhes sobre o funcionamento do **lftp**, seu manual está disponível em: [_https://lftp.yar.ru/lftp-man.html_.][1]

  * **only:** Indica em qual branch este script estará sendo executado. Neste caso, o pipeline só será executado para commits na branch **master**.

Agora precisamos efetuar o login junto ao _<a href="https://gitlab.com/" target="_blank" rel="noopener"><strong>https://gitlab.com/ </strong></a>_(Estarei assumindo que já temos um repositório criado e funcionando normalmente) e configurar as variáveis que comentei há pouco. Para isso, vá em **Settings** >> **CI/CD** e clique no botão **Expand** do item **Variables**:

![](/img/2018/10/gitlab1.png)
É aqui que devemos criar as variáveis que utilizaremos para nos autenticar em nosso FTP. Atenção para os nomes das variáveis que devem ser os mesmos utilizados dentro do nosso arquivo **.gitlab-ci.yml**.

Nossa primeiro pipeline já está pronto! Para testar, devemos fazer um commit qualquer no nosso repositório na branch master:

![](/img/2018/10/gitlab2.png)
Assim que o commit for executado, devemos voltar para a interface do **GitLab**, acessar o menu **Repository** >> **Commits** e observar que o commit que acabamos de fazer além de estar aqui, também já disparou a execução da nossa pipeline. Observem o ícone azul ao lado do código do commit:

![](/img/2018/10/gitlab3.png)
Após alguns minutos, podemos observar que o pipeline executou com sucesso (Ícone verde ao lado do código do commit):

![](/img/2018/10/gitlab4.png)
Agora se você for no menu **CI / CD** >> **Jobs** e clicar em cima do commit que acabamos de fazer, você pode ver a tela do **GitLab Runner** com todo o processo que foi executado durante nossa pipeline:

![](/img/2018/10/gitlab5.png)
Pronto! Ao acessar nossa página podemos ver que o arquivo **index.html** (Que foi o arquivo modificado) foi atualizado com sucesso.

Gostou? Têm muito mais nos links:

  * <a href="https://docs.gitlab.com/ee/ci/pipelines.html" target="_blank" rel="noopener" class="broken_link">https://docs.gitlab.com/ee/ci/pipelines.html</a>
  * <a href="https://docs.gitlab.com/ee/ci/README.html" target="_blank" rel="noopener">https://docs.gitlab.com/ee/ci/README.html</a>
  * <a href="https://docs.gitlab.com/ee/ci/quick_start/" target="_blank" rel="noopener">https://docs.gitlab.com/ee/ci/quick_start/</a>
  * <a href="https://blog.ippon.tech/continuous-delivery-with-jenkins-pipeline/" target="_blank" rel="noopener">https://blog.ippon.tech/continuous-delivery-with-jenkins-pipeline/</a> 
