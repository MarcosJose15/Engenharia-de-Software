# Polimorfismo em C# / .NET

O **polimorfismo** é um dos quatro pilares da Programação Orientada a Objetos, e refere-se à capacidade de objetos de classes diferentes responderem a chamadas de um mesmo método de formas específicas :contentReference[oaicite:1]{index=1}.

---

## 🔍 O que é Polimorfismo?

- Do grego "muitas formas": métodos com o mesmo nome executam diferentes comportamentos, conforme o tipo do objeto :contentReference[oaicite:2]{index=2}.
- Permite que uma referência de tipo base execute o método correto da classe derivada em tempo de execução (ligação dinâmica) :contentReference[oaicite:3]{index=3}.

---

## ⚙️ Tipos de Polimorfismo em C#

### 1. Polimorfismo Estático (em tempo de compilação)

- **Sobrecarga de método (method overloading)**: várias versões de um método com nomes iguais e assinaturas diferentes :contentReference[oaicite:4]{index=4}.

```csharp
public class Calculadora {
    public int Somar(int a, int b) => a + b;
    public int Somar(int a, int b, int c) => a + b + c;
}

var calc = new Calculadora();
calc.Somar(2, 3);      // usa versão com 2 parâmetros
calc.Somar(2, 3, 4);   // usa versão com 3 parâmetros
2. Polimorfismo Dinâmico (em tempo de execução)
Sobrescrita de método (method overriding): a classe base define um método virtual, e as subclasses usam override para implementar comportamentos específicos 
Wikipédia
+9
Microsoft Learn
+9
Tutkit.com
+9
.

csharp
Copiar
Editar
public class Animal {
    public virtual void EmitirSom() => Console.WriteLine("Som genérico");
}

public class Cachorro : Animal {
    public override void EmitirSom() => Console.WriteLine("Au au!");
}

public class Gato : Animal {
    public override void EmitirSom() => Console.WriteLine("Miau!");
}

var animais = new List<Animal> { new Cachorro(), new Gato() };
foreach (var a in animais) a.EmitirSom();
// Saída:
// Au au!
// Miau!
3. Polimorfismo via Interfaces e Classes Abstratas
Interfaces: múltiplas implementações do mesmo método em classes diferentes 
Nile Bits
Reddit
.

Classes abstratas: fornecem métodos abstratos que devem ser implementados nas subclasses.

csharp
Copiar
Editar
public interface IDrawable { void Draw(); }

public class Circle : IDrawable {
    public void Draw() => Console.WriteLine("Círculo desenhado");
}

public class Rectangle : IDrawable {
    public void Draw() => Console.WriteLine("Retângulo desenhado");
}

List<IDrawable> formas = new() { new Circle(), new Rectangle() };
formas.ForEach(f => f.Draw());
✅ Benefícios
Reduz condicionais (if/else ou switch) baseados em tipo 
Tutkit.com
+1
Microsoft Learn
+1
.

Torna o código mais flexível e extensível.

Facilita manutenção e compreensão, essencial em padrões de projeto como Strategy, Factory, etc 
DIO
+1
Medium
+1
Wikipédia
.

⚠️ Cuidados
Método base deve ser virtual/abstract, e o derivado, override.

Evite hierarquias profundas.

Polimorfismo aumenta acoplamento entre classes.