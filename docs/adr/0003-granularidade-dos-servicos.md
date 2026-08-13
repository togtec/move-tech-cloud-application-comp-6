# ADR 003: Justificativa sobre a granularidade da aplicação (Monolito Modular vs. Microsserviços)

- **Status:** Aprovado
- **Data:** 2026-08-13

## Contexto
Durante o projeto foi necessário decidir entre:

- Utilizar arquitetura Monolito Modular.

- Utilizar arquitetura de Microsserviços.


## Decisão 
Utilizar arquitetura Monolito Modular.

A aplicação possui atualmente um único serviço e um único domínio (orders), responsável pelo cadastro e exibição de pedidos. Sendo assim, deve manter uma arquitetura simples, de forma a agilizar o desenvolvimento, simplificar os processos de operação e atender às demandas atuais.

Caso a aplicação evolua em funcionalidades e complexidade, novas abordagens podem ser aplicadas, incluindo a separação de determinados módulos em microsserviços independentes.

## Consequências 
- **Positivas:** 
    - Redução da complexidade de operação (menor quantidade de componentes de infraestrutura para administrar).
    - Aceleração do desenvolvimento.
    - Realização dos trabalhos com equipes menores.
 
- **Negativas:**
    - Escalabilidade independente limitada entre os módulos, pois o crescimento de um módulo pode exigir escalar a aplicação como um todo.

    - Uma futura migração de módulos para microsserviços exigirá esforço de refatoração e definição de novas fronteiras entre os serviços.