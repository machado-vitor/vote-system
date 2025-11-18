RDS, DynamoDB e como escolher

RDS

É o "Relational data base service", foi feito para operar bancos de dados no ambiente AWS. Possui features de segurança, integração com outros serviços da AWS e mais importante, pode escalar o banco de dados prevendo múltiplas instâncias, levantando uma quando outra cai. Possui features de mult-AZ, então consegue sincronizar instâncias baseadas na disponibilidade de zonas.

Pros / Cons

Mult AZ
	CARO - Custo feito por instancia / tamanho do banco

Escalabilidade
	Configuração complexa

Sincronia e Segurança



DynamoDB

É o "MongoDB da amazon" em outras palavras é um banco de documentos feito para ser rápido, serverless, feito para trabalhar com dados que não constantes, me refiro a dados flexíveis, como json's variados. Dynamodb é feito pra alto volume, alta escalabilidade e alta performance, li um artigo que esta nas fontes, isso daí torna ele  MUITO CARO

Segue aqui um Diagrama resumindo como que ele funciona:
Indo um tanto além, comentando coisas que eu não sabia, ele usa um esquema de líder e toma decisões baseadas nos metadados das requests, em outras palavras existe uma engenharia para garantir que tudo seja rápido, então ele usa LAMBDA (funções de cloud que são instanciadas somente no momento da execução) pra fazer ações, consegue se replicar automaticamente

Pros / Cons

Mult AZ
	MUITO CARO / MUITO CARO DE NOVO
Custo feito por operação

Escalabilidade Garantida
	Tem limite de 400kb por objeto instanciado, guardado no banco

Sincronia e Segurança
	Casos de uso muito específicos

Velocidade muito



Como escolher

São propostas de armazenamento de dados diferentes, usamos dynamo quando precisamos de baixa latencia, acesso aos dados tanto de leitura quanto escrita em larga escala, os modelos guardados não podem ser maiores que 400k, e normalmente pode-se usar o dynamo para lidar com segmentos de dados específicos, exemplo, aplicações serveless usando lambda, coisas que precisam de baixa latência em tempo real, tipo placa de jogos, ou eventos de propaganda (marketing advertisement), processamentos de algo tráfico com picos, como carrinhos de ecommerce ou metadados de websites muito acessados.
Já o RDS é mais comum de ser usado, primeiro porquê ele é mais "barato" e usa bancos de dados relacional baseados em SQL, logo, quase tudo. O RDS permite a gente usar consultas SQL, ou seja, joins, transactions,  escala verticalmente (aumentando o tamanho do banco). O RDS tem um desempenho menor, mas se a gente tem um gap uma previsibilidade do volume de E/S, no RDS precisamos gerenciar o CPU, RAM Etc.

Conclusão
DynamoDB é muito específico na minha humilde opinião, e nos casos que observei na minha pesquisa de agora e antes, eu acredito que o melhor uso dele é para integrações serverless lambda e usar o dynamo em conjunto com o RDS para armazenar dados dados que vão ser usados o tempo todo, tipo dados de sessão, coisas que precisam ser respondidas em uma velocidade que o RDS não provê, tipo escalar rapidamente de 0 a milhões. Podemos ter um caso de uso em cima disso, minha opinião, é, deveríamos consultar o nogueira kkkkk, da pra implementra no momento da votação por ex para ser usado em um serviço de dedução de dados duplicados, mas não para ser o volume final de armazenamento.


Fontes:

RDS

https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html

Dynamodb

https://en.wikipedia.org/wiki/Amazon_DynamoDB
https://aws.amazon.com/pt/dynamodb/
https://medium.com/@joudwawad/dynamodb-architecture-5a38761501a7
https://medium.com/@christopheradamson253/deep-dive-into-aws-dynamodb-a-nosql-database-for-high-performance-applications-4c80d1410533
