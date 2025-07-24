# Arquitetura em Camadas (Layered Architecture)

A **arquitetura em camadas** organiza aplicações em níveis hierárquicos, onde cada camada tem responsabilidades bem definidas e se comunica apenas com a camada imediatamente adjacente. É amplamente usada por facilitar modularidade, manutenibilidade e escalabilidade :contentReference[oaicite:1]{index=1}.

---

## 🧩 Camadas Típicas

1. **Camada de Apresentação (UI)**  
   - Lida com a interação com o usuário: gráficos, formulários, navegação e validação básica :contentReference[oaicite:2]{index=2}.

2. **Camada de Aplicação / Lógica de Negócio**  
   - Centraliza processamento: regras de negócio, orquestração de dados e serviços externos :contentReference[oaicite:3]{index=3}.

3. **Camada de Persistência / Acesso a Dados**  
   - Responsável por operações com banco de dados, ORM, consultas e armazenamento :contentReference[oaicite:4]{index=4}.

4. **Camada de Infraestrutura (opcional)**  
   - Oferece suporte técnico: logging, autenticação, cache, integração com serviços externos :contentReference[oaicite:5]{index=5}.

---

## 🔄 Fluxo de Dados

- As requisições começam pela UI → passam pela camada de aplicação → chegam à camada de dados.
- A resposta sobe no fluxo inverso até a UI, promovendo isolamento entre camadas :contentReference[oaicite:6]{index=6}.

---

## ✅ Vantagens

- **Separação de responsabilidades**: cada camada foca em uma parte específica do sistema :contentReference[oaicite:7]{index=7}.  
- **Modularidade & Reutilização**: camadas podem ser usadas em diferentes contextos :contentReference[oaicite:8]{index=8}.  
- **Testabilidade**: facilita testes isolados por camada :contentReference[oaicite:9]{index=9}.  
- **Manutenção & Escalabilidade**: alterações isoladas têm impacto mínimo nas demais :contentReference[oaicite:10]{index=10}.

---

## ⚠️ Desvantagens

- Pode trazer **latência extra** por sobreposição de camadas :contentReference[oaicite:11]{index=11}.  
- Em sistemas simples, a complexidade da arquitetura pode ser um overhead desnecessário :contentReference[oaicite:12]{index=12}.  
- Risco de **dependências indevidas** entre camadas, anulando o benefício da modularização :contentReference[oaicite:13]{index=13}.

---

## 🧠 Boas Práticas

- Respeite as **dependências unidirecionais**: camadas superiores só acessam as inferiores :contentReference[oaicite:14]{index=14}.  
- Defina **interfaces claras** entre camadas (ex.: Contracts, DTOs).  
- Considere dividir lógica e dados via **camada de serviços (application layer)** para evitar sobrecarga na camada de negócios :contentReference[oaicite:15]{index=15}.

---

## 📋 Exemplo de Organização em C#

```text
/src
  /Presentation     ← controla UI/Web/API
  /Application      ← orquestra lógicas e transfere dados
  /Domain           ← regras de negócio, entidades, validações
  /Infrastructure   ← acesso a DB, logging, integrações
Presentation chama Application → que chama Infrastructure/Data

Infrastructure retorna dados do DB

Application processa e retorna objetos ao Presentation

🔚 Conclusão
A arquitetura em camadas é um padrão clássico que promove organização, isolamento e reuso. Ideal para projetos de médio a grande porte, mas exige disciplina. Em ambientes cloud ou microsserviços, adaptações (ex.: camadas distribuídas, CQRS, hexagonal) podem ser interessantes.