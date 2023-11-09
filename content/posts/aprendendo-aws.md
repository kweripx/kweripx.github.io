---
title: "Aprendendo Aws"
date: 2023-11-07T18:33:02-03:00
draft: false
---

## O que é cloud
Cloud é entrega de serviços sobre demanda. 
### Amazon EC2 (Elastic Compute Cloud)
* É efetivamente a maquina virtual na nuvem, entrega a capacidade computacional. Busca-se pagar apenas pelo que se utiliza.
	* Tipos de Instâncias EC2: 
		* Uso Geral: Equilibra recursos de computação, memória e redes. Adequado para uma ampla gama de workloads.
		* Otimizada para computação: Oferece processadores de alta performance. Ideal para aplicações com uso intensivo de computação e workloads de processamento em lote.
		* Otimizada para memória: Oferece a performance rápida para workloads com uso intensivo de memória. Adequada para bancos de alta performance.
		* Computação acelerada: Usa aceleradores de hardware para agilizar o processamento de dados. Ideal para fazer streaming de aplicações e workloads gráficos.
		* Otimizada para armazenamento: Oferece baixa latência e alta taxa de operações de entrada/saída por segundo (IOPS). Adequada para workloads como sistema de arquivos distribuídos e aplicações de data warehousing.  
### Computação Serverless
#### AWS Lambda
Executa código sem provisionar ou gerenciar servidores.
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
### Tipos de armazenamento da AWS
#### Armazenamento em bloco (Amazon EBS)
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
### Bancos de dados AWS
* Amazon Relational Database Service:
	* ![[Amazon RDS (Relational Database Service.png]]
		* Amazon RDS é um serviço de banco de dados gerenciado que oferece suporte a várias engines de banco de dados relacionais, como MySQL, PostgreSQL, Oracle e SQL Server.
		* É projetado para hospedar bancos de dados relacionais de alto desempenho e oferece recursos como escalabilidade automática, backup e recuperação.
	* Amazon DynamoDB: 
		* ![[Amazon DynamoDB.png]]
		* Amazon DynamoDB é um banco de dados NoSQL totalmente gerenciado que fornece escalabilidade e desempenho de baixa latência para aplicativos que requerem acesso a dados de alta velocidade e flexibilidade no modelo de dados.
### Redes
* Amazon Virtual Private Cloud: 
	* O Amazon Virtual Private Cloud (VPC) é um serviço da Amazon Web Services (AWS) que permite que você crie uma rede virtual isolada na nuvem. Ele oferece controle total sobre a sua rede, permitindo a criação de sub-redes, configuração de tabelas de rotas, e a definição de gateways de rede. Aqui estão alguns pontos-chave sobre o Amazon VPC:
		1. **Isolamento Lógico**: O Amazon VPC permite que você crie uma rede isolada logicamente na nuvem. Isso significa que você pode lançar recursos da AWS, como instâncias EC2, em uma rede virtual dedicada.
		2. **Sub-redes**: Você pode dividir sua VPC em sub-redes para organizar e isolar recursos. Cada sub-rede é associada a uma ou mais zonas de disponibilidade para garantir alta disponibilidade.
		3.  **Gateways**: O Amazon VPC suporta diferentes tipos de gateways para conexões de rede:
			- **Internet Gateway (IGW)**: Permite que recursos dentro da VPC se comuniquem com a Internet.
			-  **Virtual Private Gateway (VGW)**: Permite conexões VPN (Virtual Private Network) seguras com sua infraestrutura local.
			-  **Peering de VPC**: Permite a comunicação direta entre VPCs.
		4. **AWS VPN e Direct Connect**: O Amazon VPC oferece opções para conectar sua VPC à sua infraestrutura local de maneira segura, seja por meio de VPN (Virtual Private Network) ou Direct Connect.
		5. **Segurança**: O Amazon VPC permite que você controle a segurança da sua rede. Você pode usar grupos de segurança para controlar o tráfego de entrada e saída das instâncias EC2, além de utilizar listas de controle de acesso de rede (ACLs) para controlar o tráfego na camada da sub-rede. ![[Pasted image 20231109142626.png]]![[Pasted image 20231109142727.png]]
		6. **Elastic Load Balancing (ELB)**: Você pode usar o Elastic Load Balancer dentro de sua VPC para distribuir o tráfego entre várias instâncias EC2 em diferentes zonas de disponibilidade.
		7. **AWS Resource Access Manager (RAM)**: O Amazon VPC é compatível com o AWS RAM, permitindo que você compartilhe recursos da VPC entre contas da AWS.
		8. **IPv6 Support**: O Amazon VPC oferece suporte para IPv6, permitindo que seus recursos tenham endereços IPv6 públicos e privados.
		9. **AWS PrivateLink**: Permite que você acesse serviços da AWS (como S3 e DynamoDB) de forma privada, sem precisar de tráfego pela Internet pública.
		10. **AWS Transit Gateway**: Facilita a escala da conectividade entre VPCs e suas redes locais.
* AWS Identity And Access Management (IAM): 
	* O AWS Identity and Access Management (IAM) é um serviço da Amazon Web Services (AWS) que permite que você controle o acesso aos recursos da AWS de forma segura. Aqui estão alguns pontos-chave sobre o IAM:
		1. **Usuários e Grupos**: Com o IAM, você pode criar usuários e grupos para conceder acesso aos serviços da AWS. Os usuários são identidades individuais com credenciais únicas, enquanto grupos são conjuntos de usuários com permissões semelhantes.
		2. **Políticas de Acesso**: O IAM utiliza políticas para definir permissões. As políticas são documentos JSON que especificam quais ações são permitidas ou negadas em recursos específicos. Você pode anexar políticas a usuários, grupos ou funções.
		3. **Funções IAM**: As funções IAM são entidades que definem uma coleção de políticas e permissões associadas. Elas são frequentemente usadas para conceder acesso temporário a recursos, como em casos de acesso a serviços por instâncias EC2.
		4. **Autenticação Multi-Fator (MFA)**: O IAM suporta autenticação multi-fator para aumentar a segurança. Isso requer que os usuários forneçam uma segunda forma de autenticação além de suas credenciais usuais.
		5. **Integração com Serviços AWS**: O IAM é integrado com muitos serviços da AWS, permitindo que você controle quem pode acessar quais recursos em serviços como S3, EC2, RDS e outros.
		6. **Policies de Managed AWS**: A AWS oferece políticas gerenciadas que você pode associar a usuários, grupos ou funções. Essas políticas são criadas e gerenciadas pela AWS e são projetadas para tarefas específicas, facilitando a atribuição de permissões comuns.
		7. **Auditoria e Registro**: O IAM fornece recursos de auditoria, permitindo que você registre e monitore as ações dos usuários. Isso ajuda na detecção de atividades suspeitas e na conformidade com requisitos de segurança.
		8. **Integração com Serviços de Identidade Externos**: O IAM pode ser integrado com serviços de identidade existentes, como Microsoft Active Directory, facilitando a integração de identidades existentes com as permissões da AWS.
		9. **Criação de Políticas Personalizadas**: Além das políticas gerenciadas, você pode criar suas próprias políticas personalizadas para atender a requisitos específicos de segurança e conformidade da sua organização.
		10. **Controle de Acesso Granular**: O IAM oferece controle granular sobre o acesso, permitindo que você especifique permissões a nível de recurso e ação. Isso significa que você pode conceder permissões específicas para ações específicas em recursos específicos.
* AWS Web Application Firewall (WAF):
	* O AWS Web Application Firewall (WAF) é um serviço de segurança da Amazon Web Services projetado para proteger suas aplicações web contra ataques maliciosos e tentativas de exploração de vulnerabilidades.
		1. **Proteção contra Ataques**: O AWS WAF ajuda a proteger suas aplicações web contra uma variedade de ataques, incluindo injeção de SQL, cross-site scripting (XSS), cross-site request forgery (CSRF), entre outros.
		2. **Regras Personalizadas**: Você pode criar regras personalizadas no AWS WAF para bloquear ou permitir tráfego com base em condições específicas. Isso permite que você adapte as regras de segurança de acordo com as necessidades específicas da sua aplicação.
		3. **Regras Prontas para Uso**: Além de regras personalizadas, o AWS WAF oferece regras prontas para uso para proteção contra ameaças comuns da web. Isso inclui regras gerenciadas pela AWS e regras da AWS Marketplace.
		4. **Integração com Outros Serviços**: O AWS WAF pode ser integrado com outros serviços da AWS, como o Amazon CloudFront (para distribuição de conteúdo), a Application Load Balancer (para balanceamento de carga) e a API Gateway (para APIs).
		5. **Logs e Métricas**: O serviço fornece logs detalhados que incluem informações sobre tráfego permitido e bloqueado. Além disso, você pode utilizar métricas do Amazon CloudWatch para monitorar o desempenho e a eficácia das suas regras.
		6. **Automação com AWS WAF Rules**: Você pode usar o AWS WAF Rules para automatizar a criação, atualização e exclusão de regras do AWS WAF. Isso permite uma abordagem mais automatizada e dinâmica para a segurança da sua aplicação.
		7. **Integração com AWS Shield**: O AWS WAF pode ser integrado ao AWS Shield, que fornece proteção contra ataques DDoS (Distributed Denial of Service). Essa integração ajuda a proteger sua aplicação contra diferentes tipos de ameaças online.
		8. **Whitelisting e Blacklisting**: O AWS WAF permite que você crie listas brancas (whitelists) e listas negras (blacklists) para controlar quais endereços IP ou ranges são permitidos ou bloqueados.
		9. **Gerenciamento Centralizado**: Se você tem várias aplicações, o AWS WAF permite o gerenciamento centralizado das regras e configurações de segurança, facilitando a aplicação de políticas consistentes em vários ambientes.
		10. **Segurança Ativa e em Tempo Real**: O AWS WAF opera em tempo real, analisando e filtrando o tráfego à medida que ele chega à sua aplicação, oferecendo uma camada de segurança eficaz contra ameaças online.