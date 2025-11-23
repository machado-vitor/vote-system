Difference Between EC2 & ECS
* O que são
* EC2: máquinas virtuais (instâncias), VMs gerenciadas por mim.
* ECS: serviço de orquestração de containers (executa tasks/serviços Docker). Não é VM, roda containers em cima de instâncias (EC2) ou no modo serverless (Fargate).
** AWS Fargate é um motor de execução "serverless" para containers que permite rodar containers sem gerenciar instâncias EC2
* Nível de abstração
* EC2 = infraestrutura (instância, SO, rede, storage).
* ECS = plataforma para executar e orquestrar containers (tasks, serviços, auto-restart, balanceamento).
* Modos de execução do ECS
* Launch type EC2: você provisiona instâncias EC2 no cluster e o ECS agenda containers nelas.
* Fargate: serverless, não gerencia instâncias; paga por CPU/memória por task.
* Operação e responsabilidade
* EC2: mais controle (kernel, security, agentes).
* ECS+Fargate: menos operação, foco na aplicação; ECS+EC2: ainda delega orquestração, mas você gerencia instâncias.
* Escalabilidade e custo
* EC2: custo por instância; pode ser mais barato em cargas estáveis (reservations/spot).
* Fargate: custo por recurso usado por task; bom para variabilidade e menor overhead operacional.
* Casos típicos
* Use EC2 direto quando precisa de VMs para rodar aplicações não conteinerizadas ou controle total.
* Use ECS+EC2 quando quer orquestração de containers mas precisa controlar instâncias (custom AMIs, drivers, GPUs).
* Use ECS+Fargate quando quer minimizar operação e pagar por uso por container.

