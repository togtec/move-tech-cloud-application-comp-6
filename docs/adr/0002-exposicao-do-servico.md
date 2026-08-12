# ADR 002: Estratégia de exposição e roteamento de tráfego (Ingress / Load Balancer) 

- **Status:** Aprovado 
- **Data:** 2026-08-12 

## Contexto
A aplicação precisa ser acessível externamente e o tráfego recebido deve ser encaminhado para os Pods disponíveis, permitindo a distribuição das requisições entre as instâncias da aplicação.

Nesse cenário, foi necessário decidir entre:

- Utilizar um Service do tipo LoadBalancer.

- Utilizar uma camada de Ingress para realizar o roteamento HTTP/HTTPS entre os serviços.

## Decisão 
Utilizar Load Balancer.

Para o cenário atual, em que a aplicação é composta por um único serviço que precisa ser exposto externamente, optou-se pelo Service do tipo LoadBalancer por sua simplicidade e por exigir menos componentes de configuração e gerenciamento.

No ambiente atual, o cluster K3s é executado em uma VM. Dessa forma, a exposição externa da aplicação ocorre por meio do endereço IP público da VM, utilizando a porta 80, que é encaminhada pelo Service para a porta 8000 dos Pods da aplicação.

O uso de Ingress foi considerado, mas adicionaria uma camada de roteamento que não é necessária no momento, em razão da aplicação possuir apenas um serviço a ser exposto.

## Consequências 
- **Positivas:** 
    - Fácil de configurar.
    - Menos componentes para administrar.
    - Adequado ao cenário atual: aplicação composta por um único serviço.
    - Permite que o Service distribua o tráfego entre as instâncias da aplicação.
 
- **Negativas:** 
    - Caso a aplicação cresça e passe a possuir vários serviços, a utilização de Load Balancers individuais pode aumentar a quantidade de pontos de exposição e a complexidade de gerenciamento.

    - Não oferece os recursos de roteamento HTTP/HTTPS baseados em hosts e caminhos que uma solução com Ingress pode fornecer.

