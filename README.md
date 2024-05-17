# Netflix Architecture
 - A escolha da Netflix como tema deste trabalho foi motivada pela sua infraestrutura tecnológica complexa e robusta, que serve como um excelente estudo de caso. A Netflix, líder global no mercado de streaming de vídeo, exemplifica como arquiteturas de software avançadas podem suportar escalabilidade massiva, alta disponibilidade e entrega eficiente de conteúdo a milhões de usuários simultâneos em todo o mundo. Além disso, a Netflix utiliza uma variedade de tecnologias e padrões arquiteturais inovadores, como microserviços, computação em nuvem e práticas de DevOps, tornando-a um modelo exemplar para a aplicação de princípios modernos de arquitetura de software em sistemas de larga escala. Estudar a Netflix proporciona uma oportunidade valiosa para entender como esses conceitos foram implementados para atender às exigências rigorosas de desempenho e confiabilidade.

## Caracterização do sistema
 - A caracterização do sistema da Netflix revela diversos dados importantes que influenciam nas decisões arquiteturais. Atuando no nicho de mercado de streaming de vídeo, a Netflix atende a uma base global de mais de 230 milhões de assinantes, com picos de acessos simultâneos que podem alcançar dezenas de milhões de usuários. Esta escala massiva exige uma arquitetura altamente escalável e resiliente. A segurança é um requisito crucial, considerando a necessidade de proteger vastos volumes de dados pessoais e transações financeiras dos usuários, bem como garantir a integridade e a privacidade do conteúdo distribuído. Além disso, a infraestrutura deve suportar uma entrega eficiente e de baixa latência de conteúdo de alta definição, o que implica no uso de tecnologias avançadas de cache, redes de entrega de conteúdo (CDNs) e otimização de tráfego. Estes fatores, juntamente com a necessidade de uma disponibilidade contínua e a capacidade de atualização frequente dos serviços sem interrupções, guiam as decisões arquiteturais da plataforma.

## Modelo arquitetural do sistema
- Para atender seus mais de 230 milhões de assinantes em mais de 200 países, a Netflix trabalha com dois sistemas clouds, AWS e Open Connect, que trabalham juntas para prover uma boa responsabilidade e streaming de alta qualidade a seus usuários

![Modelo de Arquitetura](imagens/Netflix-High-Level-System-Architecture.png "Modelo de Arquitetura em Alto Nível")
**Figura 1 - Modelo de Arquitetura em Alto Nível da Netflix (tirado de: https://www.geeksforgeeks.org/system-design-netflix-a-complete-architecture/)**

- A aplicação possui 3 componentes principais:
- Cliente:
    Dispositivo (Interface do Usuário) que é usado para navegar e reproduzir vídeos da Netflix. TV, XBOX, laptop ou celular, etc.
- OC (Open Connect) ou Netflix CDN:
    CDN é a rede de servidores distribuídos em diferentes localizações geográficas, e Open Connect é a própria CDN global personalizada da Netflix.
    Ele lida com tudo o que envolve streaming de vídeo.
    É distribuído em diferentes locais e uma vez que você clica no botão de reprodução, o fluxo de vídeo deste componente é exibido em seu dispositivo.
    Então, se você está tentando reproduzir o vídeo sentado na América do Norte, o vídeo será servido do open connect (ou servidor) mais próximo em vez do servidor original (resposta mais rápida do servidor mais próximo).
- Backend (Database):
     Esta parte lida com tudo o que não envolve streaming de vídeo, como fazer upload de novos conteúdos, processar vídeos, distribuí-los para servidores localizados em diferentes partes do mundo e gerenciar o tráfego de rede.
    A maioria dos processos é cuidada pela Amazon Web Services.

## Arquitetura de microsserviços da Netflix
- A arquitetura da Netflix é construída por uma coleção de serviços, conhecida como arquitetura de microserviços e ela alimenta todas as APIs necessárias para suas aplicações e serviços Web. Quando a solicitação chega ao endpoint, ela chama outros microsserviços para obter os dados necessários e esses microsserviços também podem solicitar dados de diferentes microsserviços. Depois disso, uma resposta é enviada para a solicitação da API de volta ao endpoint.

![Arquitetura de Microsserviços](imagens/microservice-architecture.jpg "Modelo de Arquitetura em Alto Nível")
**Figura 2 - Arquitetura de Microsserviços da Netflix (tirado de: https://www.geeksforgeeks.org/system-design-netflix-a-complete-architecture/)**

