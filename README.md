# Ana-julia-
Exercício 1 — Cadastro de Produtos com Preço Final
Descrição:
Crie um sistema orientado a objetos para cadastrar produtos de uma loja. Cada produto deverá ter os atributos: codigo, nome, precoBase e percentualLucro. O sistema deverá calcular o preço final de venda com base no preço base e no percentual de lucro. Exiba todos os produtos com seus respectivos dados e o preço final.

Utilize classes, construtores, encapsulamento e métodos para cálculo e exibição dos dados.

using System;
using System.Collections.Generic;

class Produto
{
// Atributos
private int codigo;
private string nome;
private double precoBase;
private double percentualLucro;

// Construtor
public Produto(int codigo, string nome, double precoBase, double percentualLucro)
{
    this.codigo = codigo;
    this.nome = nome;
    this.precoBase = precoBase;
    this.percentualLucro = percentualLucro;
}

// Método para calcular preço final
private double CalcularPrecoFinal()
{
    return precoBase + (precoBase * (percentualLucro / 100));
}

// Método para exibir
public void Exibir()
{
    Console.WriteLine($"Código: {codigo}, Nome: {nome}, Preço Base: {precoBase:C}, Lucro: {percentualLucro}%, Preço Final: {CalcularPrecoFinal():C}");
}
}

class Program
{
static void Main()
{
List produtos = new List();
produtos.Add(new Produto(1, "Camisa", 50.0, 30));
produtos.Add(new Produto(2, "Calça", 100.0, 40));
produtos.Add(new Produto(3, "Tênis", 200.0, 50));

    foreach (var p in produtos)
    {
        p.Exibir();
    }
}
}

Exercício 2 — Sistema de Alunos com Média Final
Descrição:
Implemente um sistema em C# para cadastrar alunos e calcular sua média. Cada aluno terá: matricula, nome, nota1, nota2. O sistema deve calcular a média aritmética simples e informar se o aluno está Aprovado (média >= 6) ou Reprovado.

Use classes, métodos privados para cálculo da média, e métodos públicos para exibição.
using System;
using System.Collections.Generic;

class Aluno
{
private int matricula;
private string nome;
private double nota1;
private double nota2;

public Aluno(int matricula, string nome, double nota1, double nota2)
{
    this.matricula = matricula;
    this.nome = nome;
    this.nota1 = nota1;
    this.nota2 = nota2;
}

private double CalcularMedia()
{
    return (nota1 + nota2) / 2.0;
}

public void Exibir()
{
    double media = CalcularMedia();
    string status = media >= 6 ? "Aprovado" : "Reprovado";
    Console.WriteLine($"Matrícula: {matricula}, Nome: {nome}, Média: {media:F1}, Status: {status}");
}
}

class Program
{
static void Main()
{
List alunos = new List();
alunos.Add(new Aluno(1, "Ana", 8, 7));
alunos.Add(new Aluno(2, "Carlos", 5, 6));
alunos.Add(new Aluno(3, "Julia", 9, 9));

    foreach (var a in alunos)
    {
        a.Exibir();
    }
}
}

Exercício 3 — Registro de Veículos
Descrição:
Construa um programa orientado a objeto para registrar veículos em uma locadora. Cada veículo terá: placa, modelo, ano, valorDiaria. O sistema deve permitir o cadastro e exibir uma lista com o valor estimado para 5 dias de locação para cada veículo.

Crie método para calcular o valor da locação baseado no número de dias (use 5 dias como exemplo).
using System;
using System.Collections.Generic;

class Veiculo
{
private string placa;
private string modelo;
private int ano;
private double valorDiaria;

public Veiculo(string placa, string modelo, int ano, double valorDiaria)
{
    this.placa = placa;
    this.modelo = modelo;
    this.ano = ano;
    this.valorDiaria = valorDiaria;
}

public double CalcularValorLocacao(int dias)
{
    return valorDiaria * dias;
}

public void Exibir()
{
    Console.WriteLine($"Placa: {placa}, Modelo: {modelo}, Ano: {ano}, Diária: {valorDiaria:C}, Valor 5 dias: {CalcularValorLocacao(5):C}");
}
}

class Program
{
static void Main()
{
List veiculos = new List();
veiculos.Add(new Veiculo("ABC-1234", "Corsa", 2010, 80));
veiculos.Add(new Veiculo("XYZ-9876", "Onix", 2020, 150));

    foreach (var v in veiculos)
    {
        v.Exibir();
    }
}
}

Exercício 4 — Sistema Bancário Simples
Descrição:
Crie um sistema simples de conta bancária. Cada cliente deve ter: numeroConta, nome, saldo. O sistema deve permitir depósitos e saques, e exibir o saldo atualizado. Implemente regras simples como não permitir saque maior que o saldo.

Use métodos Depositar(double valor) e Sacar(double valor), e faça tratamento de erro simples.

using System;
using System.Collections.Generic;

class ContaBancaria
{
private int numeroConta;
private string nome;
private double saldo;

public ContaBancaria(int numeroConta, string nome, double saldoInicial)
{
    this.numeroConta = numeroConta;
    this.nome = nome;
    this.saldo = saldoInicial;
}

public void Depositar(double valor)
{
    saldo += valor;
}

public void Sacar(double valor)
{
    if (valor <= saldo)
        saldo -= valor;
    else
        Console.WriteLine("Saque negado. Saldo insuficiente!");
}

public void Exibir()
{
    Console.WriteLine($"Conta: {numeroConta}, Cliente: {nome}, Saldo: {saldo:C}");
}
}

class Program
{
static void Main()
{
ContaBancaria conta = new ContaBancaria(1, "Maria", 500);
conta.Depositar(200);
conta.Sacar(100);
conta.Sacar(700); // tentativa inválida
conta.Exibir();
}
}

Exercício 5 — Cadastro de Livros em uma Biblioteca
Descrição:
Crie um sistema para armazenar livros de uma biblioteca. Cada livro deve ter: isbn, titulo, autor, anoPublicacao. O sistema deverá cadastrar os livros e exibir todos os livros cadastrados em ordem de publicação (do mais antigo para o mais recente).

Use List e o método Sort com comparação baseada no ano.
using System;
using System.Collections.Generic;

class Livro : IComparable
{
private string isbn;
private string titulo;
private string autor;
private int anoPublicacao;

public Livro(string isbn, string titulo, string autor, int anoPublicacao)
{
    this.isbn = isbn;
    this.titulo = titulo;
    this.autor = autor;
    this.anoPublicacao = anoPublicacao;
}

public int CompareTo(Livro outro)
{
    return this.anoPublicacao.CompareTo(outro.anoPublicacao);
}

public void Exibir()
{
    Console.WriteLine($"ISBN: {isbn}, Título: {titulo}, Autor: {autor}, Ano: {anoPublicacao}");
}
}

class Program
{
static void Main()
{
List livros = new List();
livros.Add(new Livro("111", "Dom Casmurro", "Machado de Assis", 1899));
livros.Add(new Livro("222", "O Hobbit", "Tolkien", 1937));
livros.Add(new Livro("333", "Harry Potter", "J.K. Rowling", 1997));

    livros.Sort(); // Ordena por ano

    foreach (var l in livros)

    {
        l.Exibir();
    }
}
}
