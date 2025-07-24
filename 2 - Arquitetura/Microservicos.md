# Arquitetura de Microserviços (Microservices)

A **arquitetura de microserviços** é um padrão que organiza uma aplicação como um conjunto de **serviços pequenos, independentes e focados em negócios**, cada um executando em seu próprio processo e se comunicando via APIs leves (REST, gRPC, mensagens…) :contentReference[oaicite:1]{index=1}.

---

## 🧩 Características Principais

- **Desacoplamento fraco**: cada serviço é independente, implantado e escalado separadamente :contentReference[oaicite:2]{index=2}.  
- **Delegação de dados**: cada microserviço possui seu **próprio banco de dados** (modelos de dados isolados) :contentReference[oaicite:3]{index=3}.  
- **Tecnologias diversas**: por serviço, é possível escolher diferentes linguagens, frameworks e bancos :contentReference[oaicite:4]{index=4}.  
- **Equipes autônomas**: cada equipe é responsável por um subconjunto do sistema :contentReference[oaicite:5]{index=5}.

---

## ✅ Vantagens

1. **Escalabilidade independente** das partes que mais exigem recursos :contentReference[oaicite:6]{index=6}.  
2. **Tolerância a falhas**: erro em um serviço não afeta o sistema inteiro :contentReference[oaicite:7]{index=7}.  
3. **Velocidade de implantação**: equipes podem implantar seus serviços sem afetar outros :contentReference[oaicite:8]{index=8}.  
4. **Flexibilidade técnica**: permite experimentar tecnologias por serviço :contentReference[oaicite:9]{index=9}.  
5. **Modularidade e clareza**: código mais simples, de fácil entendimento e manutenção :contentReference[oaicite:10]{index=10}.

---

## ❌ Desafios

- **Complexidade operacional**: orquestração, deployment, monitoramento e observabilidade são mais complicados :contentReference[oaicite:11]{index=11}.  
- **Latência de rede**: comunicação entre serviços muitos ocorre via rede, mais lenta que chamada local :contentReference[oaicite:12]{index=12}.  
- **Consistência eventual de dados**: cada serviço tem seu banco; manter sincronia exige padrões como sagas :contentReference[oaicite:13]{index=13}.  
- **Testes distribuídos**: testes de integração se tornam mais complexos :contentReference[oaicite:14]{index=14}.  
- **Gestão de transações**: sem ACID global, exige soluções mais sofisticadas :contentReference[oaicite:15]{index=15}.

---

## 🛠 Exemplo prático em C#/.NET

Suponha um sistema de e‑commerce:

ProductService ← gerencia produtos (CRUD)
OrderService ← processa pedidos
UserService ← autenticação e usuários
PaymentService ← processa pagamentos


Cada serviço é um **ASP.NET Core Web API**, com seu próprio banco (ex: SQL Server, MongoDB). Eles podem ser empacotados em **Docker containers**, comunicando-se via HTTP/gRPC ou mensagens. O .NET oferece guia oficial como *eShopOnContainers* :contentReference[oaicite:16]{index=16}.

### Exemplo simplificado – ProductsController

```csharp
[ApiController]
[Route("api/products")]
public class ProductsController : ControllerBase
{
  private readonly IProductService _svc;

  public ProductsController(IProductService svc) => _svc = svc;

  [HttpGet] public IActionResult GetAll() => Ok(_svc.GetAllProducts());
  [HttpPost] public IActionResult Create(Product p) => Created(..., _svc.AddProduct(p));
}
Cada serviço expõe endpoints isoladamente, permitindo deploy independente.

📋 Boas práticas
API Gateway: mecanismo único de entrada para os microserviços.

Service Discovery: localiza automaticamente serviços registrados.

Circuit Breaker / retries: garante resiliência em chamadas remotas.

Monitoramento e logs centralizados: uso de APMs e tracing distribuído.

Domain‑Driven Design (DDD): organiza serviços por contextos de negócio.

CQRS/Saga: para separar leitura/escrita e gerenciar transações distribuídas.

🔄 Quando adotar?
Ideal para sistemas grandes, com escala crescente, equipes autônomas e necessidade de alta disponibilidade.

Em casos menores ou menos complexos, um monolito modular pode ser mais eficiente 
Wikipédia.

Migração gradual é recomendada: comece com monolito e evolua para microserviços conforme necessário.