## Pasta: minhasoperacoes/

# minhasoperacoes/__init__.py
__all__ = ["operacoes", "utils"]

# minhasoperacoes/operacoes.py
def soma(a, b):
    return a + b

def subtracao(a, b):
    return a - b

def multiplicacao(a, b):
    return a * b

def divisao(a, b):
    if b == 0:
        return "Erro: divisão por zero."
    return a / b

# minhasoperacoes/utils.py
def exibir_resultado(operacao, resultado):
    print(f"Resultado da {operacao}: {resultado}")

## Arquivo principal: main.py
from minhasoperacoes import operacoes, utils

op = input("Escolha uma operação (+, -, *, /): ")
num1 = float(input("Digite o primeiro número: "))
num2 = float(input("Digite o segundo número: "))

if op == "+":
    resultado = operacoes.soma(num1, num2)
    utils.exibir_resultado("soma", resultado)
elif op == "-":
    resultado = operacoes.subtracao(num1, num2)
    utils.exibir_resultado("subtração", resultado)
elif op == "*":
    resultado = operacoes.multiplicacao(num1, num2)
    utils.exibir_resultado("multiplicação", resultado)
elif op == "/":
    resultado = operacoes.divisao(num1, num2)
    utils.exibir_resultado("divisão", resultado)
else:
    print("Operação inválida.")

## Exercício 1: Escrever parâmetros em um arquivo
# script1.py
filename = input("Digite o nome do arquivo: ")
params = input("Digite os parâmetros separados por espaço: ").split()

with open(filename, "w", encoding="utf-8") as f:
    for param in params:
        f.write(param + "\n")

print("Parâmetros escritos com sucesso!")

## Exercício 2: Verificar número de parâmetros
# script2.py
import sys

with open("config.txt", "r", encoding="utf-8") as f:
    config = f.read().strip()
    num_params = int(config.split("=")[1])

if len(sys.argv) - 1 != num_params:
    print("Erro: número de parâmetros inválido!")
    sys.exit(1)

print("Parâmetros aceitos:", sys.argv[1:])

## Exercício 3: Criar arquivo resultado.txt a partir de arquivos
# script3.py
import sys

with open("config.txt", "r", encoding="utf-8") as f:
    config = f.read().strip()
    num_files = int(config.split("=")[1])

if len(sys.argv) - 1 != num_files:
    print("Erro: número de arquivos inválido!")
    sys.exit(1)

with open("resultado.txt", "w", encoding="utf-8") as result_file:
    for filename in sys.argv[1:]:
        with open(filename, "r", encoding="utf-8") as f:
            result_file.write(f.read() + "\n")

print("Arquivo resultado.txt criado com sucesso!")
