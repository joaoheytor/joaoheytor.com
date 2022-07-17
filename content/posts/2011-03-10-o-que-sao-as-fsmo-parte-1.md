---
title: O que são as FSMO ??? – Parte 1
author: João Heytor
type: post
date: 2011-03-11T01:59:41+00:00
url: /2011/03/10/o-que-sao-as-fsmo-parte-1/
gwo4wp:
  - 'a:4:{s:7:"enabled";s:0:"";s:14:"control_script";s:0:"";s:15:"tracking_script";s:0:"";s:17:"conversion_script";s:0:"";}'
  - 'a:4:{s:7:"enabled";s:0:"";s:14:"control_script";s:0:"";s:15:"tracking_script";s:0:"";s:17:"conversion_script";s:0:"";}'
dsq_thread_id:
  - 2184354214
categories:
  - Servidores

---
_Flexible Single-Master Operation_ ou simplesmente FSMO, nada mais são do que Controladores de Domínio (em inglês, _Domain Controller_, ou apenas DC) dotados de certas capacidades especiais, que só eles podem fazer dentro da sua rede, independente do número de Controladores de Domínio que você possui em sua rede. Nota: Apenas os Controladores de Domínio podem hospedar essas funções pois são apenas eles que possuem uma cópia do tipo “Escrita” do Active Directory.

Resolvi fazer esse post, pois há alguns dias tive um problema relacionado aos Operadores Mestres (FSMO), onde numa determinada rede que administro, coisas estranhas estavam acontecendo. Começando com o fato de não ser mais possível à criação de novos usuários na rede. Em seguida, e para piorar as coisas, os usuários não estavam mais conseguindo efetuar logon na rede. Fui chamado nessa hora, já com o pensamento de sempre:

<del><em>“F*@&!, certeza&#8230; Será que algum dia vou em um cliente que o problema seja fácil de solucionar ?”</em></del>

Hahahaha&#8230; Será que só eu tenho essa sensação? Que o pessoal só lembra de nós quando o negócio tá feio? E que para ajudar, é sempre urgente&#8230;

Mas enfim&#8230; Deixemos de lado esse pensamento bobo e voltemos ao tópico&#8230;

Gosto muito de usar algumas ferramentas que acompanham o _Support Tools_ (Para quem não sabe, esse conjunto de ferramentas se encontra no CD do Windows Server 2003, na pasta SupportTools).

Então a primeira coisa que fiz, foi rodar o seguinte comando:

> **_netdom query fsmo_**

**_[<img loading="lazy" class="aligncenter size-full wp-image-282" title="netdom_query_fsmo" src="/img/sites/4/2011/03/netdom_query_fsmo.png" alt="" width="664" height="327" />][1]  
_** 

Também podemos ver os FSMO em modo gráfico, em vários snap-ins temos a opção de exibir os “Mestres de Operações”, como podemos observar na imagem abaixo, onde escolhi o snap-in Usuários e Computadores do Active Directory para ilustrar.

[][2]{.broken_link}[<img loading="lazy" class="aligncenter size-full wp-image-283" title="fsmo_user_computers" src="/img/sites/4/2011/03/fsmo_user_computers.png" alt="" width="401" height="444" />][3]

_De qualquer forma, os Mestres de Operações se dividem em 2 grupos:_

**_&#8211; Floresta:_** _são regras que afetam toda uma floresta Windows 2000 ou 2003 e podem ser hospedadas por qualquer DC dentro da floresta._

**_&#8211; Domínio:_** _são regras que afetam apenas um domínio Windows 2000 ou 2003, e podem ser hospedadas por DCs dentro do domínio._

_Ao todo, temos cinco FSMO, duas que afetam a floresta como um todo e outras três que afetam um domínio, conforme explicação abaixo:_

# **_Floresta_**

**_&#8211; Schema Master:_** _O Schema é o coração do Active Directory. Ele é composto de objetos e atributos, que modelam o Active Directory. É através do Schema que dizemos, por exemplo, que o objeto do tipo &#8220;USUÁRIO&#8221; terá os atributos &#8220;NOME&#8221;, &#8220;ENDEREÇO&#8221;, &#8220;TELEFONE&#8221;, etc. Como o esquema pode ser customizado e deve ser o mesmo em toda a floresta Windows, a regra &#8220;Schema Master&#8221; se encarrega de evitar conflitos entre os DCs._

**_&#8211; Domain Naming Master:_** _Se você adiciona um novo domínio em uma floresta (por exemplo, se você adiciona um domínio filho), o nome deste domínio deve ser único na floresta. É esta regra responsável por assegurar isto e evitar conflitos entre outros domínios._

# **_Domínio_**

**_&#8211; PDC Emulator:_** _Como o nome já diz, uma das funções desta regra é &#8220;emular&#8221; um PDC NT 4.0 para manter a compatibilidade com servidores legados (por exemplo, BDCs NT 4.0) e clientes mais antigos. Mesmo que você migre todo seu ambiente para Windows 2000 ou 2003, esta regra ainda é importante, pois é responsável por tratar alterações de contas de usuários, &#8220;lockouts&#8221; de contas, relações de confianças com outros domínios e pelo sincronismo do relógio no domínio._

**_&#8211; RID Master:_** _Qualquer DC pode criar novos objetos (usuários, grupos, contas de computadores). Cada objeto deve possuir um identificador único, conhecido como SID. O SID do objeto é construído usando o SID do domínio, mais um ID relativo (RID). Porém, após criar 512 objetos, um DC precisa contatar o RID Master para conseguir mais 512 RIDs (atualmente, um DC contata o RID Master quando ele possui menos de 100 RIDs disponíveis). Isto evita que dois objetos diferentes tenham o mesmo RID em todo o domínio._

**_&#8211; Infrastructure Master:_** _Esta regra é muitas vezes conhecida apenas como &#8220;cosmética&#8221;, já que sua função é se assegurar que o &#8220;Display Name&#8221; de usuários pertencentes a um grupo sejam atualizados caso este atributo seja alterado. Ele é mais importante em ambientes que possuem vários domínios, pois vai assegurar que todos os grupos que um determinado usuário pertença irá refletir o &#8220;Display Name&#8221; correto._

**Problemas com FSMO**

Se uma das FSMO falhar, com certeza você terá problemas em seu ambiente. A tabela abaixo ajuda a identificar possíveis problemas que possam ocorrer:

<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td style="text-align: center" valign="top">
      <strong>Sintoma</strong>
    </td>
    
    <td valign="top">
      <p style="text-align: center">
        <strong>Possível regra envolvida</strong>
      </p>
    </td>
    
    <td valign="top">
      <p style="text-align: center">
        <strong>Explicação</strong>
      </p>
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <strong>Usuários não conseguem fazer logon.</strong>
    </td>
    
    <td valign="top">
      <p style="text-align: center">
        PDC Emulator
      </p>
    </td>
    
    <td valign="top">
      O relógio do sistema pode não estar sincronizado, o que faz a autenticação Kerberos falhar.
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <strong>Não é possível alterar senhas.</strong>
    </td>
    
    <td valign="top">
      <p style="text-align: center">
        PDC Emulator
      </p>
    </td>
    
    <td valign="top">
      Alterações de senhas necessitam desta regra ativa.
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <strong><em>&#8220;Lockout&#8221;</em></strong><strong> de contas não funciona.</strong>
    </td>
    
    <td valign="top">
      <p style="text-align: center">
        PDC Emulator
      </p>
    </td>
    
    <td valign="top">
      Esta operação necessita do PDC Emulator ativo.
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <strong>Não é possível &#8220;elevar&#8221; o nível funcional de um domínio.</strong>
    </td>
    
    <td valign="top">
      <p style="text-align: center">
        PDC Emulator
      </p>
    </td>
    
    <td valign="top">
      Esta regra precisa estar ativa para o processamento desta operação.
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <strong>Não é possível criar novos usuários ou grupos.</strong>
    </td>
    
    <td valign="top">
      <p style="text-align: center">
        RID Master
      </p>
    </td>
    
    <td valign="top">
      RID pool precisa ser renovado, e para isto, é necessário contatar o RID Master.
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <strong>Problemas com membros de grupos universais.</strong>
    </td>
    
    <td valign="top">
      <p style="text-align: center">
        Infrastructure Master
      </p>
    </td>
    
    <td valign="top">
      Esta regra é responsável por atualizar o <em>&#8220;Display Name&#8221;</em> dos membros de grupos.
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <strong>Não é possível adicionar um remover um domínio.</strong>
    </td>
    
    <td valign="top">
      <p style="text-align: center">
        Domain Naming Master
      </p>
    </td>
    
    <td valign="top">
      Alterações deste porte necessitam desta regra.
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <strong>Não é possível promover ou despromover um DC</strong>
    </td>
    
    <td valign="top">
      <p style="text-align: center">
        Domain Naming Master
      </p>
    </td>
    
    <td valign="top">
      Alterações deste porte necessitam desta regra.
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <strong>Não é possível modificar o schema.</strong>
    </td>
    
    <td valign="top">
      <p style="text-align: center">
        Schema Master
      </p>
    </td>
    
    <td valign="top">
      Modificações no Schema devem ser controladas por esta regra.
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <strong>Não é possível &#8220;elevar&#8221; o nível funcional de uma floresta.</strong>
    </td>
    
    <td valign="top">
      <p style="text-align: center">
        Schema Master
      </p>
    </td>
    
    <td valign="top">
      Esta regra precisa estar ativa para o processamento desta operação.
    </td>
  </tr>
</table>

**Regras para configurações das FSMO**

DCs irão hospedá-las. Por padrão, quando você instala o primeiro DC da sua floresta (que neste caso é também o domínio raiz ou root), este DC irá hospedar as cinco FSMO. Quando você instala o primeiro DC de qualquer outro domínio dentro de sua floresta, ele irá hospedar as três FSMO do domínio. Porém, dependendo da complexidade do seu ambiente, este comportamento padrão pode não ser o mais apropriado e você deve transferir algumas regras para máquinas diferentes para um melhor desempenho. Os artigos <a href="http://support.microsoft.com/default.aspx?scid=kb;en-us;223787" target="_blank">KB 223787</a> e <a href="http://support.microsoft.com/default.aspx?scid=kb;en-us;255504" target="_blank">KB 255504</a> descrevem como este procedimento deve ser efetuado.

As regras a seguir podem ser usadas na definição das FSMO:

**1 &#8211; PDC Emulator e RID Master devem estar na mesma máquina porque o PDC Emulator é um grande consumidor de RID´s**

Dica: Como o PDC Emulator é a regra mais utilizada num ambiente Windows, se a máquina que hospeda estas duas regras está com um alto nível de utilização, é necessário mover estas regras para um outro DC (de preferência que não seja um Global Catalog (GC), já que este também possui alta utilização) ou realizar um upgrade de hardware.

**2 &#8211; Infrastructure Master não deve estar em um DC que também é GC (Global Catalog)**

**Dica:** Certifique-se que o Infrastructure Master e o GC estejam em um mesmo site físico e que estes dois DCs sejam configurados como &#8220;Replication Partner&#8221;, usando o &#8220;Active Directory Sites and Services&#8221;.

**Exceção 1:** se você possui apenas um domínio (Single Domain), você pode ter na mesma máquina o Infrastructure Master e o GC  
**Exceção 2:** se todos os DCs em sua floresta são também GC, você pode ter o Infrastructure Master junto com o GC.

**3 &#8211; Para um gerenciamento facilitado, Schema Master e Domain Naming Master podem estar na mesma máquina, que deve ser também um Global Catalog (GC).**

**4 &#8211; De tempos em tempos, verifique se todas as FSMO estão disponíveis e funcionando corretamente.**

Bom&#8230; por enquanto é só pessoal. Nesse primeiro artigo, dei um enfoque no que são e para que servem as FSMO. Espero que tenham gostado&#8230; em seguida, volto com a segunda parte, postando possíveis soluções para problemas relacionados aos Operadores Mestres.**  
** 

**Fonte: <a href="http://technet.microsoft.com/pt-br/library/cc716426.aspx" target="_blank">Technet</a>**

 [1]: /img/sites/4/2011/03/netdom_query_fsmo.png
 [2]: ../wp-content/uploads/2011/03/fsmo_user_computers.png
 [3]: /img/sites/4/2011/03/fsmo_user_computers.png