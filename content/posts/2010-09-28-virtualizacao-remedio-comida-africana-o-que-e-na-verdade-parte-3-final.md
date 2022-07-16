---
title: Virtualização, remédio? Comida africana? O que é na verdade? – Parte 3 – FINAL
author: blogadminjoaoheytor
type: post
date: 2010-09-28T03:41:46+00:00
url: /2010/09/28/virtualizacao-remedio-comida-africana-o-que-e-na-verdade-parte-3-final/
aktt_notify_twitter:
  - yes
gwo4wp:
  - 'a:4:{s:7:"enabled";s:1:"1";s:14:"control_script";s:0:"";s:15:"tracking_script";s:0:"";s:17:"conversion_script";s:0:"";}'
Thumbnail:
  - http://blog.joaoheytor.com/wp-content/uploads/2010/09/virtu2.jpg
aktt_tweeted:
  - 1
dsq_thread_id:
  - 2296519212
categories:
  - Diversos

---
Mais uma vez, estamos aqui devolta. Vou aproveitar que estou postando mesmo hoje, e finalizar o artigo que fala sobre virtualização. Então chega de enrolação e vamos ao tema.

Comecemos, falando das principais arquiteturas que estão por trás da Virtualização:

<img loading="lazy" class="size-full wp-image-138 alignleft" title="001" src="/img/sites/4/2010/09/001.png" alt="" width="121" height="131" /> 

**&#8211; Virtualização Tipo-2 VMM ou Hypervisor Hospedado:**

Na arquitetura de virtualização Tipo-2 VMM (Virtual Machine Management, Gerenciamento da Máquina Virtual) os Guests (Sistemas Operacionais virtualizados) trabalham “em conjunto” com o SO Host. Na verdade, o Hypervisor depende de um SO Host para hospedá-lo e manter muito dos serviços necessários para o funcionamento do host.

Nesse tipo de arquitetura, o hypervisor faz a tradução dos comandos enviados pelas VMs e repassa a solicitação para o SO Host executar.

<div id="_mcePaste">
  <span style="color: #000000">Como exemplo, podemos citar o JVM (Java Virtual Machine).</span>
</div>

<div>
  <strong>&#8211; VMM Híbrida ou Emulação</strong>
</div>

<img loading="lazy" class="size-full wp-image-139 alignright" title="002" src="/img/sites/4/2010/09/002.png" alt="" width="252" height="94" /> 

É a reprodução das caracteriscas de um ambiente desejado. Um exemplo seriam os emuladores de vídeo games que “criam” o ambiente necessário para que os  jogos desenvolvidos para uma arquitetura de hardware específica possam rodar.

A desvantagem desse tipo de virtualização é que geralmente a performance é ruim, e pelo fato de ser uma simulação nem sempre os resultados obtidos serão os mesmos que o ambiente real poderia gerar.

<img loading="lazy" class="size-full wp-image-140 alignleft" title="003" src="/img/sites/4/2010/09/003.png" alt="" width="120" height="96" /> 

<div>
  <span style="color: #0000ee"><span style="color: #000000"><strong>&#8211; Tipo-1 VMM (Hypervisor):<br /> </strong></span></span>
</div>

<div>
  <span style="color: #0000ee"><span style="color: #000000">O Hypervisor não necessita de um SO Host e pode ser instalado diretamente no Host. Ele controla a abstração do hardware e executa todas as tarefas para que as VMs tenham máximo desempenho. Pelo fato de não haver um SO Host, que também consome recursos do Host,  existem mais recursos físicos disponíveis.</span></span>
</div>

<div style="text-align: center">
  <span style="color: #0000ee"><span style="color: #000000">// </p> 
  
  <p>
    </span></span></div> 
    
    <div>
      <span style="color: #0000ee"><span style="color: #000000"><br /> </span></span>
    </div>
    
    <div>
      <span style="color: #0000ee"><span style="color: #000000">Como principais vantagens que obtemos com a utilização da virtualização, podemos destacar:</span></span>
    </div>
    
    <div>
      <p>
        <span style="color: #0000ee"><span style="color: #000000"> </span></span>
      </p>
      
      <div>
        •<span> </span>Gerenciamento centralizado;
      </div>
      
      <div>
        •<span> </span>Instalações simplificadas;
      </div>
      
      <div>
        •<span> </span>Facilidade para a execução de backups;
      </div>
      
      <div>
        •<span> </span>Suporte e manutenção simplificados;
      </div>
      
      <div>
        •<span> </span>Independência de Hardware;
      </div>
      
      <div>
        •<span> </span>Disponibilização de novos servidores fica reduzida para alguns minutos;
      </div>
      
      <div>
        •<span> </span>Migração de servidores para novo hardware de forma transparente;
      </div>
      
      <div>
        •<span> </span>Maior disponibilidade e mais fácil recuperação em caso de desastres;
      </div>
      
      <div>
        •<span> </span>Compatibilidade total com as aplicações;
      </div>
      
      <div>
        •<span> </span>Economia de espaço físico;
      </div>
      
      <div>
        •<span> </span>Economia de energia elétrica utilizada em refrigeração e na alimentação dos servidores.;
      </div>
      
      <div>
        •<span> </span>Segurança: Usando máquinas virtuais, pode-se definido qual é o melhor ambiente para executar cada serviço, com diferentes requerimentos de segurança, ferramentas diferentes e o sistema operacional mais adequado para cada serviço. Além disso, cada máquina virtual é isolada das demais. Usando uma máquina virtual para cada serviço, a vulnerabilidade de um serviço não prejudica os demais;
      </div>
      
      <div>
        •<span> </span>Confiança e disponibilidade: A falha de um software não prejudica os demais serviços;
      </div>
      
      <div>
        •<span> </span>Custo: A redução de custos é possível utilizando pequenos servidores virtuais em um único servidor mais poderosos;
      </div>
      
      <div>
        •<span> </span>Adaptação às diferentes cargas de trabalho: A carga de trabalho pode ser tratada de forma simples. Normalmente os softwares de virtualização realocam os recursos de hardware dinamicamente entre uma máquina virtual para a outra;
      </div>
      
      <div>
        •<span> </span>Balanceamento de carga: Toda a máquina virtual está encapsulada, assim é fácil trocar a máquina virtual de plataforma e aumentar o seu desempenho;
      </div>
      
      <div>
        •<span> </span>Suporte a aplicações legadas: Quando uma empresa decide migrar para um novo Sistema Operacional, é possível manter o sistema operacional antigo sendo executado em uma máquina virtual, o que reduz os custos com a migração. Vale ainda lembrar que a virtualização pode ser útil para aplicações que são executadas em hardware legado, que está sujeito a falhas e tem altos custos de manutenção. Com a virtualização desse hardware, é possível executar essas aplicações em hardwares mais novos, com custo de manutenção mais baixo e maior confiabilidade;
      </div>
      
      <div>
        •<span> </span>Segurança: as máquinas virtuais podem ficar isoladas e independentes umas das outras, inclusive independente da máquina hospedeira;
      </div>
      
      <div>
        •<span> </span>Redução de custos: com menos equipamentos físicos para se gerenciar o custo com pessoal, energia e refrigeração fica mais reduzido;
      </div>
      
      <div>
        •<span> </span>Melhor aproveitamento do espaço físico: menos dispositivos físicos instalados maior o espaço  disponível em racks;
      </div>
      
      <div>
        •<span> </span>Melhor aproveitamento do hardware: com o compartilhamento do  hardware entre as máquinas virtuais reduz-se a ociosidade do equipamento;
      </div>
      
      <div>
        •<span> </span>Simulações: Com as máquinas virtuais é possível simular redes inteiras, inclusive redes heterogenias;
      </div>
      
      <div>
        •<span> </span>Pode-se utilizar sistemas operacionais que não possuam compatibilidade com o hardware, utilizando os recursos de virtualização de hardware. Possibilitando assim testes ou até mesmo economia com a compra de hardware de menor custos;
      </div>
      
      <div>
        •<span> </span>Redução do downtime;
      </div>
      
      <div>
        •<span> </span>Facilidade ao migrar ambientes: evita reinstalação e reconfiguração dos sistemas a serem migrados.
      </div>
      
      <div>
        E claro, como não poderiamos deixar de citar, também temos as desvantagens:
      </div>
    </div>
    
    <p>
      •<span> </span>Grande uso de espaço em disco, já que é preciso de todos os arquivos para cada sistema operacional instalado em cada máquina virtual;
    </p>
    
    <p>
      •<span> </span>Dificuldade no acesso direto a hardware, como por exemplo placas específicas ou dispositivos USB;
    </p>
    
    <p>
      •<span> </span>Grande consumo de memória RAM dado que cada máquina virtual vai ocupar uma área separada da mesma;
    </p>
    
    <p>
      •<span> </span>Segurança: As máquinas virtuais podem ser menos seguras que as máquinas físicas justamente por causa do seu host. Este ponto é interessante, pois se o sistema operacional hospedeiro tiver alguma vulnerabilidade, todas as máquinas virtuais que estão hospedadas nessa máquina física estão vulneráveis;
    </p>
    
    <p>
      •<span> </span>Gerenciamento: Os ambientes virtuais necessitam ser instanciados, monitorados, configurados e salvos. Existem produtos que fornecem essas soluções, mas esse é o campo no qual estão os maiores investimentos na área de virtualização, justamente por se tratar de um dos maiores contra-tempos na implementação da virtualização;
    </p>
    
    <p>
      •<span> </span>Desempenho: Atualmente, não existem métodos consolidados para medir o desempenho de ambientes virtualizados. No entanto, a introdução de uma camada extra de software entre o sistema operacional e o hardware, o VMM ou hypervisor, gera um custo de processamento superior ao que se teria sem a virtualização. Outro ponto importante de ressaltar é que não se sabe exatamente quantas máquinas virtuais podem ser executadas por processador, sem que haja o prejuízo da qualidade de serviço.
    </p>
    
    <p>
      E é isso pessoal&#8230; fico por aqui, qualquer dúvida, só deixar nos comentários!
    </p>