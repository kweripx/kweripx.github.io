---
title: "Aprendendo Aws"
date: 2023-11-07T18:33:02-03:00
draft: false
---

* O que é cloud: 
	Cloud é entrega de serviços sobre demanda. 
* Amazon EC2 (Elastic Compute Cloud): 
	* É efetivamente a maquina virtual na nuvem, entrega a capacidade computacional. Busca-se pagar apenas pelo que se utiliza.
	* Tipos de Instâncias EC2: 
		* Uso Geral: Equilibra recursos de computação, memória e redes. Adequado para uma ampla gama de workloads.
		* Otimizada para computação: Oferece processadores de alta performance. Ideal para aplicações com uso intensivo de computação e workloads de processamento em lote.
		* Otimizada para memória: Oferece a performance rápida para workloads com uso intensivo de memória. Adequada para bancos de alta performance.
		* Computação acelerada: Usa aceleradores de hardware para agilizar o processamento de dados. Ideal para fazer streaming de aplicações e workloads gráficos.
		* Otimizada para armazenamento: Oferece baixa latência e alta taxa de operações de entrada/saída por segundo (IOPS). Adequada para workloads como sistema de arquivos distribuídos e aplicações de data warehousing.  
* Computação Serverless:
	* AWS Lambda: 
		* Executa código sem provisionar ou gerenciar servidores.
		* Pague apenas pelo tempo de computação enquanto o código estiver em execução.
		* Use outros serviços AWS para acionar automaticamente o código.
		1. **Criação de Função**: Você começa criando uma função Lambda, que é basicamente o código que você deseja executar. As funções Lambda podem ser escritas em várias linguagens de programação, como Python, Node.js, Java, C#, entre outras.
		2. **Definição de Gatilhos**: Depois de criar sua função Lambda, você precisa definir os gatilhos que acionarão a execução da função. Um gatilho é um evento que desencadeia a execução da função. Os gatilhos podem ser eventos de outros serviços da AWS, como S3, SNS, API Gateway, CloudWatch, entre outros, ou eventos personalizados.
		3. **Implantação de Código**: Você carrega seu código da função Lambda para a AWS. Isso pode ser feito diretamente na AWS Management Console, usando a AWS Command Line Interface (CLI) ou ferramentas de automação.
		4. **Escala Automática**: O AWS Lambda gerencia automaticamente a escala para você. Quando um gatilho é acionado, o AWS Lambda provisiona automaticamente a capacidade necessária para atender a demanda. Isso significa que você não precisa se preocupar com a alocação de recursos ou a capacidade de servidores.
		5. **Execução de Função**: Quando o gatilho é acionado, o AWS Lambda executa sua função. O código da função é executado em um ambiente altamente disponível e gerenciado pela AWS. Você é cobrado apenas pelo tempo de execução real da função, medido em milissegundos.
		6. **Resultados e Logs**: A função Lambda pode retornar resultados e gerar logs que podem ser armazenados em serviços como CloudWatch Logs. Isso ajuda na depuração e no monitoramento do desempenho da função.
		7. **Escalabilidade e Concorrência**: O AWS Lambda lida automaticamente com a escalabilidade e a concorrência. Ele pode executar várias instâncias da sua função simultaneamente para lidar com cargas de trabalho pesadas, se necessário.
		8. **Fim da Execução**: Após a conclusão da execução da função, o ambiente é desativado. Isso permite que você economize recursos quando a função não está em execução.
		9. **Custo Baseado no Uso**: Você é cobrado apenas pelo tempo de execução da função e pelos recursos de computação consumidos durante a execução. Isso torna o AWS Lambda uma opção econômica para cargas de trabalho intermitentes ou de baixo tráfego.
		10. **Integração com Outros Serviços**: O AWS Lambda pode ser facilmente integrado com outros serviços da AWS e também pode ser usado para criar pipelines de processamento de dados, automações, aplicativos de microserviços e muito mais.
		11. ![[LAMBDA DIAGRAM.png]]
* Tipos de armazenamento da AWS:
	* Armazenamento em bloco (Amazon EBS): 
		* No armazenamento em bloco, os arquivos são separados em partes iguais (blocos) de dados.
		* O armazenamento em bloco é usado para aplicações executadas em instâncias do Amazon EC2.
		* Amazon EBS fornece volumes de armazenamento de blocos para instâncias EC2 (Elastic Compute Cloud).
		* É apropriado para armazenamento de dados que requerem acesso de baixa latência, como sistemas de arquivos, bancos de dados e aplicativos que exigem armazenamento persistente.
		* ![[EBS DIAGRAM.png]]
	* Armazenamento de objetos (Amazon S3):
		* No armazenamento de objetos, cada objeto consiste em dados, metadados e uma chave.
		* Amazon S3 é um serviço de armazenamento de objetos altamente escalável e durável.
		* É adequado para armazenar dados não estruturados, como arquivos, imagens, vídeos, backups e muito mais.
		* ![[Amazon S3 Diagram.png]]
		* Classes de armazenamento do Amazon S3:
			* Oferece opções de armazenamento de classes, como S3 Standard, S3 Intelligent-Tiering, S3 Glacier, entre outras, para atender a diferentes requisitos de desempenho e custo.
			* ![[Amazon S3 Class Diagram.png]]
	* Armazenamento de arquivos:
		* No Armazenamento de arquivos, vários clientes podem acessar dados armazenados em pastas de arquivos compartilhados
		* Amazon Elastic File System:
			* Amazon EFS é um sistema de arquivos NFS (Network File System) totalmente gerenciado que pode ser montado em várias instâncias EC2.
			* É ideal para aplicativos que exigem compartilhamento de dados entre instâncias EC2.
			* ![[Amazon Elastic File System Diagram.png]]
* Bancos de dados AWS: 
	* Amazon Relational Database Service:
		* ![[Amazon RDS (Relational Database Service.png]]
		* Amazon RDS é um serviço de banco de dados gerenciado que oferece suporte a várias engines de banco de dados relacionais, como MySQL, PostgreSQL, Oracle e SQL Server.
		* É projetado para hospedar bancos de dados relacionais de alto desempenho e oferece recursos como escalabilidade automática, backup e recuperação.
	* Amazon DynamoDB: 
		* ![[Amazon DynamoDB.png]]
		* Amazon DynamoDB é um banco de dados NoSQL totalmente gerenciado que fornece escalabilidade e desempenho de baixa latência para aplicativos que requerem acesso a dados de alta velocidade e flexibilidade no modelo de dados.
* Redes:
	* 