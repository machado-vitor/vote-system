API Gateway vs ALB vs ELB, CloudflareAPI gateway
É um serviço da AWS para criação, publicação, manutenção, monitoramento e proteção de APIs REST e WebSocket. É uma camada de software que apresenta um único ponto de entrada para os clientes acessarem vários serviços de back-end, ao mesmo tempo em que gerencia as interações cliente/servidor.
Algumas funções:
- gerenciamento de tráfego
- controle de autorização e acesso
- monitoramento
- gerenciamento de versão de APIs


ALB
O Application Load Balancer é um serviço de balanceamento de carga projetado especificamente para distribuir o tráfego de aplicativos baseados em HTTP e HTTPS em nível de aplicativo. Ele distribuir o tráfego de aplicativos entre várias instâncias de servidores com o objetivo de melhorar a escalabilidade, a disponibilidade e o desempenho do aplicativo. O ALB opera no nível da camada 7 do modelo OSI, o que significa que ele é capaz de tomar decisões de roteamento com base em informações do aplicativo, como o conteúdo do cabeçalho HTTP, o caminho da URL ou as informações do cookie. Isso permite que o ALB distribua o tráfego de forma inteligente, direcionando solicitações específicas para servidores apropriados.


ELB
O Elastic Load Balancing é um serviço que distribui automaticamente o tráfego de entrada para várias instâncias EC2 (Elastic Compute Cloud) ou contêineres, ajudando a melhorar a escalabilidade, a disponibilidade e a resiliência de aplicações. Ele é usado para aumentar a escalabilidade e a disponibilidade dos aplicativos, roteando requisições apenas para destinos saudáveis e gerenciando picos de demanda de forma eficiente.


API gateway vs ALB vs ELB
Embora as 3 lidem com o request do client, elas são usadas em diferentes etapas desse request.
Ao realizar uma requisição para uma aplicação, a primeira etapa é o ELB, é ele quem vai dizer para qual maquina (EC2) deve seguir o request. Definido a maquina, a próxima etapa é o ALB, que vai pegar as informações contidas no HTTP/HTTPS do request e com base nisso dizer qual o melhor caminho para o request continuar seguindo. Chegando assim a ultima etapa, que é o API gateway, que vai guiar para qual serviço especifico deve bater a requisição.


CloudFlare
É um proxy reverso com funções CDN. Ele atua entre o client request e o servidor, criando versões em cache do conteúdo estático de aplicações e espalhando-as por uma rede de servidores, agilizando o seu desempenho da aplicação, pois o retorno cache sera do servidor que estiver mais proximo da localização da origem do request.
