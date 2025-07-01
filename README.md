# Design Patterns com Java

> Este repositório foi elaborado assistindo às aulas da [Digital Innovation One](https://dio.me) onde foi incentivado criar repositório explorando sobre Design Patterns (Padrões de Design).

## Projeto

O **projeto** utiliza os padrões de projeto **Singleton, Facade e Strategy** de forma clara e alinhada ao ecossistema Spring Boot:

### **Singleton**

- No Spring, classes anotadas com `@Service` (como `ClienteServiceImpl`) são tratadas como singleton por padrão. Isso significa que existe apenas uma instância dessas classes durante o ciclo de vida da aplicação.
- Os repositórios e serviços (`ClienteRepository`, `EnderecoRepository`, `ViaCepService`) são injetados via `@Autowired`, aproveitando o gerenciamento de instâncias único do container do Spring.
Strategy

### **Strategy**

- O padrão Strategy é implementado pela interface `ClienteService`. Ela define as operações do domínio de clientes (`buscarTodos`, `buscarPorId`, `inserir`, `atualizar`, `deletar`).
- A classe `ClienteServiceImpl` implementa `ClienteService` e pode ser substituída por outras implementações no futuro, se necessário, sem alterar o restante do sistema.
- Isso permite a troca de estratégias de negócio para manipulação de clientes de forma flexível.

### **Facade**

- O controller `ClienteRestController` atua como fachada para o domínio de clientes. Ele expõe uma **interface REST** simples para operações como buscar, inserir, atualizar e deletar clientes.
- Internamente, o controller **abstrai** toda a complexidade de integração com banco de dados e serviços externos (como a API ViaCEP), **centralizando as operações** em métodos simples.
- Isso **facilita o uso do sistema** por clientes externos (frontends, outros sistemas) e **desacopla a interface pública da implementação interna.**

Esses padrões estão bem documentados nos próprios comentários do código, tornando o projeto um bom exemplo prático de uso dos principais Design Patterns em aplicações Java com Spring Boot.

## Sobre Design Patterns

O que são 'Design Patterns'?

> ***Design patterns***, ou padrões de design, são **soluções** recorrentes para problemas comuns que surgem no design, representam as  **melhores práticas** desenvolvidas e empregadas por designers ao longo do tempo e oferecem **soluções testadas** e otimizadas para problemas específicos, promovendo a reutilização de ideias e técnicas em situações similares, servindo como guias confiáveis, muitas vezes incompreendidos como simples cópias. No entanto, eles são mais do que replicação; são a **arte de padronizar** para elevar a experiência do usuário.
> [MUTUNDA, Clénio](https://www.linkedin.com/pulse/design-patterns-n%C3%A3o-%C3%A9-copiar-padronizar-cl%C3%A9nio-mutunda-3y7of/)

