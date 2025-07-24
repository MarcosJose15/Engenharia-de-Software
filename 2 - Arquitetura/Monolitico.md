# Arquitetura Monolítica

A **arquitetura monolítica** se caracteriza por um sistema em que todas as funcionalidades — interface de usuário, lógica de negócios e acesso a dados — estão integradas e rodando como um único executável ou processo :contentReference[oaicite:1]{index=1}.

---

## 🧱 O que é?

- **Unidade de implantação única**: toda a aplicação é compilada e executada como um único artefato :contentReference[oaicite:2]{index=2}.  
- **Código fortemente acoplado**: componentes internos se conectam via chamadas locais, dentro do mesmo deploy :contentReference[oaicite:3]{index=3}.  
- **Escalabilidade vertical**: aumentar o desempenho geralmente exige aumentar os recursos da mesma instância :contentReference[oaicite:4]{index=4}.

---

## ✅ Vantagens

1. **Simplicidade de desenvolvimento e deploy**: um único código-fonte e artefato torna fácil iniciar e implantar :contentReference[oaicite:5]{index=5}.  
2. **Teste e depuração facilitados**: chamadas locais simplificam o tracing de erros :contentReference[oaicite:6]{index=6}.  
3. **Melhor desempenho inicial**: sem sobrecarga de rede entre componentes :contentReference[oaicite:7]{index=7}.  
4. **Baixo custo operacional inicial**: menos infraestrutura e complexidade, ideal para startups :contentReference[oaicite:8]{index=8}.

---

## ❌ Desvantagens

1. **Escalabilidade limitada**: não é possível dimensionar apenas partes da aplicação; o monolito cresce inteiro :contentReference[oaicite:9]{index=9}.  
2. **Difícil manutenção conforme cresce**: mudanças isoladas exigem recompilar, testar e redeploy completo :contentReference[oaicite:10]{index=10}.  
3. **Dependência de tecnologia única**: trocar tecnologias ou frameworks requer refatoração de toda a aplicação :contentReference[oaicite:11]{index=11}.  
4. **Risco de falha total**: erro em um módulo pode comprometer tudo :contentReference[oaicite:12]{index=12}.

---

## 🛠 Quando usar

- Projetos **pequenos ou protótipos**: rapidez no desenvolvimento e feedback rápido :contentReference[oaicite:13]{index=13}.  
- **Equipes pequenas** ou com menos necessidade de escalabilidade :contentReference[oaicite:14]{index=14}.  
- **Aplicações com baixo crescimento previsto**, onde uma arquitetura distribuída seria overkill :contentReference[oaicite:15]{index=15}.

---

## ⚖️ Comparação com Microsserviços

| Aspecto          | Monolítico                    | Microsserviços                              |
|------------------|-------------------------------|---------------------------------------------|
| Deploy           | Unidade única                 | Vários serviços independentes               |
| Escalabilidade   | Escala toda a aplicação       | Escala serviços individualmente             |
| Complexidade     | Baixa inicialmente            | Alta, exige orquestração e infraestrutura   |
| Flexibilidade    | Lock-in tecnológico geral     | Liberdade por serviço                       |
| Falhas           | Propaga facilmente            | Contém-se em serviço específico             |

(Comparativo embasado em AWS e Atlassian) :contentReference[oaicite:16]{index=16}.

---

## 🧠 Conclusão

A arquitetura monolítica é **ideal para projetos simples**, startups ou MVPs, devido à sua simplicidade e baixo custo inicial. Porém, à medida que a aplicação cresce — em complexidade, equipe ou demanda —, os **microsserviços** podem ser uma alternativa mais flexível e escalável. É sempre bom começar simples e, se necessário, evoluir a arquitetura ao longo do tempo.