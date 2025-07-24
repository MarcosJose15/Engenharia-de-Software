# Herança em C# / .NET

A **herança** é um dos pilares da Programação Orientada a Objetos (POO) e permite que uma classe (derivada) reutilize, estenda ou modifique o comportamento de outra classe (base) :contentReference[oaicite:1]{index=1}.

---

## 🔍 O que é herança?

- Representa uma relação **"é um"**: por exemplo, um `Cachorro` é um `Animal` :contentReference[oaicite:2]{index=2}.
- A classe base (ou superclasse) fornece atributos e métodos que são herdados.
- A classe derivada (ou subclasse) obtém esses membros e pode adicionar novos ou sobrescrever existentes :contentReference[oaicite:3]{index=3}.

---

## 📝 Exemplos práticos

### Exemplo simples: veículo e carro

```csharp
public class Vehicle           // classe base
{
    public string Brand = "Ford";

    public void Honk()
    {
        Console.WriteLine("Tuut, tuut!");
    }
}

public class Car : Vehicle    // classe derivada
{
    public string ModelName = "Mustang";
}

class Program
{
    static void Main()
    {
        var myCar = new Car();
        myCar.Honk();  // método herdado
        Console.WriteLine($"{myCar.Brand} {myCar.ModelName}");
    }
}
Car herda Brand e Honk() de Vehicle 
Medium
+15
w3schools.com
+15
Codecademy
+15
.

Exemplo com reuso de construtores
csharp
Copiar
Editar
public class Person
{
    public string Name;
    public int Age;

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }
}

public class Student : Person
{
    public string School;

    public Student(string name, int age, string school)
        : base(name, age)  // reutiliza o construtor da superclasse
    {
        School = school;
    }
}
Usa base(...) para reaproveitar lógica e inicialização da classe pai 
Wikipédia
+6
DEV Community
+6
Caffeine Algorithm
+6
.

🧩 Tipos de herança em C#
Simples: uma derivada herda de uma única base.

Multinível: ClasseC : ClasseB : ClasseA 
Microsoft Learn
+6
Medium
+6
Wikipédia
+6
Microsoft Learn
.

Hierárquica: várias derivadas de uma mesma base 
Caffeine Algorithm
+15
Wikipédia
+15
Medium
+15
.

Interfaces: C# não suporta herança múltipla de classes, mas permite múltiplas interfaces 
YouTube
+12
c-sharpcorner.com
+12
Wikipédia
+12
.

🔁 Sobrescrita de métodos (override)
Para personalizar o comportamento:

Na classe base, declare virtual ou abstract.

Na derivada, use override.

csharp
Copiar
Editar
public class Animal
{
    public virtual void Speak()
    {
        Console.WriteLine("Animal faz som genérico.");
    }
}

public class Dog : Animal
{
    public override void Speak()
    {
        Console.WriteLine("Au au!");
    }
}

static void Main()
{
    Animal a = new Dog();
    a.Speak();  // imprime "Au au!" via polimorfismo
}
Fundamental para o polimorfismo 
programiz.com
+4
Medium
+4
Codecademy
+4
Microsoft Learn
+7
Wikipédia
+7
DEV Community
+7
Wikipédia
+2
DIO
+2
Wikipédia
+2
.

⚠️ Restrições da herança em C#
Herança única: não é possível herdar de mais de uma classe diretamente 
Microsoft Learn
.

Membros private não são herdados.

Construtores e finalizadores não são herdados automaticamente 
Microsoft Learn
.

✅ Vantagens e desvantagens
Vantagens:

Reúso de código

Organização hierárquica

Facilita polimorfismo 
programiz.com
+2
Caffeine Algorithm
+2
DEV Community
+2

Desvantagens:

Acoplamento forte entre base e derivada

Hierarquias profundas podem complicar manutenção 
Microsoft Learn
+15
DEV Community
+15
Wikipédia
+15

🌱 Quando usar herança?
Utilize quando houver clara relação “é um” entre entidades, por exemplo:

Dog : Animal

Student : Person

Para relações do tipo “tem um”, prefira composição sobre herança 
Microsoft Learn
.

🧭 Resumo
Herança permite construir hierarquias, promover reuso e expressar relações conceituais. Deve ser usada com cuidado para evitar acoplamentos desnecessários e manter a flexibilidade do design.