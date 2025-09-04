# DIO - Trilha .NET - Programação orientada a objetos
www.dio.me

## Desafio de projeto
Para este desafio, você precisará usar seus conhecimentos adquiridos no módulo de orientação a objetos, da trilha .NET da DIO.

## Contexto
Você é responsável por modelar um sistema que trabalha com celulares. Para isso, foi solicitado que você faça uma abstração de um celular e disponibilize maneiras de diferentes marcas e modelos terem seu próprio comportamento, possibilitando um maior reuso de código e usando a orientação a objetos.

## Proposta
Você precisa criar um sistema em .NET, do tipo console, mapeando uma classe abstrata e classes específicas para dois tipos de celulares: Nokia e iPhone. 
Você deve criar as suas classes de acordo com o diagrama abaixo:

![Diagrama classes](Imagens/diagrama.png)

## Regras e validações
1. A classe **Smartphone** deve ser abstrata, não permitindo instanciar e servindo apenas como modelo.
2. A classe **Nokia** e **Iphone** devem ser classes filhas de Smartphone.
3. O método **InstalarAplicativo** deve ser sobrescrito na classe Nokia e iPhone, pois ambos possuem diferentes maneiras de instalar um aplicativo.

## Solução
O código está pela metade, e você deverá dar continuidade obedecendo as regras descritas acima, para que no final, tenhamos um programa funcional. Procure pela palavra comentada "TODO" no código, em seguida, implemente conforme as regras acima.
 ProjetoCelulares
 Program.cs
 Celular.cs
 Iphone.cs
 Nokia.cs
 namespace ProjetoCelulares
{
    public abstract class Celular
    {
        public string Numero { get; set; }

        public Celular(string numero)
        {
            Numero = numero;
        }

        public abstract void Ligar();
        public abstract void ReceberLigacao();

        public virtual void InstalarAplicativo(string nomeApp)
        {
            Console.WriteLine($"Instalando o aplicativo {nomeApp} no celular genérico...");
        }
    }
}
namespace ProjetoCelulares
{
    public class Iphone : Celular
    {
        public Iphone(string numero) : base(numero) { }

        public override void Ligar()
        {
            Console.WriteLine("Ligando pelo iPhone...");
        }

        public override void ReceberLigacao()
        {
            Console.WriteLine("Recebendo ligação no iPhone...");
        }

        public override void InstalarAplicativo(string nomeApp)
        {
            Console.WriteLine($"Instalando o aplicativo {nomeApp} pela App Store no iPhone...");
        }
    }
}
namespace ProjetoCelulares
{
    public class Nokia : Celular
    {
        public Nokia(string numero) : base(numero) { }

        public override void Ligar()
        {
            Console.WriteLine("Ligando pelo Nokia...");
        }

        public override void ReceberLigacao()
        {
            Console.WriteLine("Recebendo ligação no Nokia...");
        }

        public override void InstalarAplicativo(string nomeApp)
        {
            Console.WriteLine($"Instalando o aplicativo {nomeApp} pela loja da Nokia...");
        }
    }
}
using ProjetoCelulares;

class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("=== Sistema de Celulares ===");

        Celular iphone = new Iphone("1199999-0000");
        Celular nokia = new Nokia("1188888-1111");

        Console.WriteLine("\n--- Testando iPhone ---");
        iphone.Ligar();
        iphone.ReceberLigacao();
        iphone.InstalarAplicativo("Instagram");

        Console.WriteLine("\n--- Testando Nokia ---");
        nokia.Ligar();
        nokia.ReceberLigacao();
        nokia.InstalarAplicativo("WhatsApp");
    }
}
=== Sistema de Celulares ===

--- Testando iPhone ---
Ligando pelo iPhone...
Recebendo ligação no iPhone...
Instalando o aplicativo Instagram pela App Store no iPhone...

--- Testando Nokia ---
Ligando pelo Nokia...
Recebendo ligação no Nokia...
Instalando o aplicativo WhatsApp pela loja da Nokia...

