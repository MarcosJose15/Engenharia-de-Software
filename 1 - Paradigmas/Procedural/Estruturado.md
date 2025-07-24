# Paradigma Estruturado / Procedural

O **paradigma estruturado** (ou procedural) é uma vertente do paradigma imperativo, onde programas são organizados como um conjunto de **subrotinas**, **funções** ou **procedimentos**, executados de forma sequencial. Ele promove modularização, legibilidade e redução do uso de saltos incondicionais (`goto`) :contentReference[oaicite:1]{index=1}.

---

## 🧠 Características

- **Sequência**, **condição** e **repetição**: construção de algoritmos com `if/else`, `for`, `while` :contentReference[oaicite:2]{index=2}.
- Modularidade via **procedimentos**: encapsulamento de lógicas reutilizáveis com parâmetros e retorno :contentReference[oaicite:3]{index=3}.
- **Controle de fluxo estruturado** sem `goto` facilita manutenção e compreensão :contentReference[oaicite:4]{index=4}.

---

## ✅ Vantagens vs Desvantagens

**Vantagens**

- Simples, fácil de entender.
- Reutilização de código via sub-rotinas.
- Ótimo para programas de média complexidade.

**Desvantagens**

- Código menos seguro (uso de variáveis globais).
- Difícil escalabilidade em grandes sistemas.
- Falta encapsulamento e abstração comparado à OOP :contentReference[oaicite:5]{index=5}.

---

## 🛠 Exemplo em C#

```csharp
using System;

class Programa
{
    static int SomarPares(int n)
    {
        int soma = 0;
        for (int i = 1; i <= n; i++)
        {
            if (i % 2 == 0)
                soma += i;
        }
        return soma;
    }

    static void ExibirResultado(int n)
    {
        int total = SomarPares(n);
        Console.WriteLine($"Soma dos pares até {n}: {total}");
    }

    static void Main(string[] args)
    {
        Console.Write("Informe o valor máximo: ");
        int n = int.Parse(Console.ReadLine() ?? "0");
        ExibirResultado(n);
    }
}
Análise do exemplo:

SomarPares(n): sub-rotina que calcula e retorna a soma dos números pares até n.

ExibirResultado(n): chama SomarPares e exibe o resultado.

Main: faz leitura do usuário e aciona ExibirResultado.

Este fluxo, separando em funções bem definidas, evidencia o paradigma procedural: sequência de comandos, controle de fluxo com estruturas condicionais e reutilização via funções.

📚 Contexto histórico e comparativo
Dominante até os anos 1990, antes da popularização da OOP
Guia dev
scoutapm.com
.

Procedural é subset do imperativo, focado em rotinas como unidades de lógica
Reddit
+11
Wikipédia
+11
Guia dev
+11
.

Linguagens como C, Pascal, Fortran foram pioneiras nesse paradigma
Guia dev
+7
rocketseat.com.br
+7
treinaweb.com.br
+7
.

🔁 Relação com Orientação a Objetos
O paradigma procedural pode coexistir dentro de linguagens OOP (como C# ou Java), servindo como ferramenta quando não há necessidade de criar objetos. Programadores podem optar por esse estilo por praticidade ou performance
Reddit
Microsoft Learn
.

📌 Conclusão
O paradigma estruturado/procedural é uma base sólida para aprender programação: ajuda a pensar em fluxo de execução, modularidade e reutilização. Apesar de hoje ser comum usar OOP ou paradigmas funcionais, o procedural ainda é relevante, servindo como ponto de partida em muitos sistemas.
```
