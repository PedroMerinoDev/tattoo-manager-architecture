# Arquitetura Tattoo Manager SaaS 🏛️

> **Overview de Engenharia de um Sistema ERP em Produção**

Este repositório serve como um **Showcase de Arquitetura e Documentação** para o **Tattoo Manager**, uma plataforma SaaS madura que atende milhares de estúdios.

> **Nota:** O código-fonte é proprietário. Este repositório demonstra os princípios de engenharia, decisões arquiteturais e padrões de qualidade aplicados no projeto.

## Visão Geral do Sistema

Tattoo Manager é um ERP Multi-Tenant que gerencia:
- Agendamento Avançado & Calendário
- Transações Financeiras (Split de Pagamentos)
- Anamnese & Jurídico
- Controle de Estoque
- Push Notifications & CRM

## Arquitetura: O Core

Seguimos estritamente princípios de **Clean Architecture** para garantir desacoplamento e testabilidade.

### Camadas

1.  **Domain Layer (Puro Dart/Java):**
    *   Entidades (Regras de Negócio Corporativas)
    *   Casos de Uso (Regras de Negócio da Aplicação)
    *   *Zero dependência de frameworks (Flutter/Spring).*

2.  **Infrastructure Layer:**
    *   Implementação de Repositórios
    *   APIs Externas (Stripe, Firebase, Brevo)
    *   Adaptadores de Banco de Dados (PostgreSQL / Hive)

3.  **Presentation Layer:**
    *   Controllers / BLoCs
    *   Componentes de UI (Design System)

## Design Patterns Utilizados

- **Repository Pattern:** Para abstrair fontes de dados.
- **Adapter Pattern:** Para isolar serviços externos (Gateways de Pagamento).
- **Factory Pattern:** Para criação de objetos complexos (Políticas de Usuário).
- **Decorator Pattern:** Para estender funcionalidades core sem "herança infernal".

## Estratégia de Testes (A Pirâmide)

Enforcamos uma cultura de testes rígida:
- **Testes Unitários:** 100% de cobertura em Entidades e Casos de Uso. (Lógica sem mocks).
- **Testes de Integração:** Verificando contratos Infra <-> Banco de Dados.
- **Testes de Widget/UI:** Garantindo que fluxos críticos (Checkout, Login) nunca quebrem.

## Pipeline CI/CD

- **Commit:** Dispara linting & testes unitários.
- **Merge Request:** Dispara testes de integração & verificação de build.
- **Release:** Deploy automatizado para as Lojas (App Center / Play Store).

---
*Arquitetado por [Pedro Merino](https://github.com/PedroMerinoDev)*
