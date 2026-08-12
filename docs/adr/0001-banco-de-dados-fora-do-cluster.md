# ADR 001: Utilização de Banco de Dados Gerenciado Fora do Cluster K3s 

- **Status:** Aprovado 
- **Data:** 2026-08-12 

## Contexto
A aplicação exige a persistência de dados relacionais com alta confiabilidade e backups automáticos. Em decorrência, é necessário decidir entre:
- Rodar o PostgreSQL como um Pod/StatefulSet dentro do cluster Kubernetes

- Utilizar um banco de dados PostgreSQL gerenciado (DBaaS). 

## Decisão 
Utilizar um banco de dados PostgreSQL Gerenciado (DBaaS) fora do cluster Kubernetes. 

## Consequências 
- **Positivas:** Redução da complexidade de gerenciamento de volumes persistentes no K3s, backups automatizados pelo provedor, facilidade de failover e alta disponibilidade.
 
- **Negativas:** Custo direto adicional do serviço gerenciado em comparação com a execução em Pods simples com armazenamento local.