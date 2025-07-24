# Arquitetura MVC (Model‑View‑Controller)

A **Arquitetura MVC** organiza a aplicação em três componentes principais — Model, View e Controller — promovendo separação de responsabilidades e facilitando manutenção e testes :contentReference[oaicite:0]{index=0}.

---

## 🧩 Camadas do MVC

1. **Model**  
   - Representa dados e lógica de negócio  
   - Responsável por persistência, validação e regras complexas :contentReference[oaicite:1]{index=1}

2. **View**  
   - Exibe os dados para o usuário  
   - Deve ser "leve", com lógica mínima; envolve HTML, Razor, CSS, JavaScript :contentReference[oaicite:2]{index=2}

3. **Controller**  
   - Interpreta requisições do usuário  
   - Executa ações no Model e seleciona a View adequada :contentReference[oaicite:3]{index=3}

---

## 🔄 Fluxo de Execução

1. O usuário faz uma requisição (ex: via URL ou formulário).
2. O **Controller** recebe a requisição e chama métodos do **Model**.
3. O **Model** processa dados e retorna ao Controller.
4. O Controller escolhe uma **View** e envia os dados.
5. A View renderiza o resultado ao usuário :contentReference[oaicite:4]{index=4}.

---

## ✅ Vantagens e Desvantagens

**Vantagens**
- Separação de responsabilidades — cada parte lida com sua função :contentReference[oaicite:5]{index=5}
- Testabilidade — Models e Controllers podem ser testados isoladamente
- Colaboração paralela — designers cuidam da View, devs da lógica :contentReference[oaicite:6]{index=6}

**Desvantagens**
- Pode gerar muitos arquivos e pastas, aumentando a complexidade :contentReference[oaicite:7]{index=7}
- Requer maior entendimento do padrão e disciplina na organização

---

## 🛠 Exemplo em C# (.NET Core MVC)

```csharp
// Model - Models/Product.cs
public class Product
{
    public int Id { get; set; }
    public string Name { get; set; }
    public decimal Price { get; set; }
}

// Controller - Controllers/ProductController.cs
public class ProductController : Controller
{
    private static readonly List<Product> _produtos = new()
    {
        new Product { Id = 1, Name = "Caneta", Price = 1.20m },
        new Product { Id = 2, Name = "Caderno", Price = 12.50m },
    };

    public IActionResult Index()
    {
        return View(_produtos);
    }

    [HttpPost]
    public IActionResult Create(Product p)
    {
        p.Id = _produtos.Max(x => x.Id) + 1;
        _produtos.Add(p);
        return RedirectToAction(nameof(Index));
    }
}
html
Copiar
Editar
<!-- View - Views/Product/Index.cshtml -->
@model List<Product>

<h1>Produtos</h1>
<table>
  <tr><th>Nome</th><th>Preço</th></tr>
  @foreach (var item in Model)
  {
    <tr><td>@item.Name</td><td>@item.Price:C</td></tr>
  }
</table>

<h2>Novo Produto</h2>
<form method="post" asp-action="Create">
  <input name="Name" placeholder="Nome" />
  <input name="Price" type="number" step="0.01" placeholder="Preço" />
  <button type="submit">Adicionar</button>
</form>
Como funciona:

ProductController.Index() chama os dados do Model e passa para a View.

Index.cshtml exibe a lista de produtos e permite criar novos.

Create() trata o formulário, adiciona o produto e redireciona para Index.

🧭 Quando usar MVC
Aplicações web de médio/grande porte

Projetos onde se deseja manter o HTML separado da lógica de negócio

Equipes com membros focados em UI (frontend) e backend, permitindo desenvolvimento paralelo.