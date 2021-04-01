---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# curso-em-video-python
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

DESAFIO 85: 

'''
crie um programa onde o usuario possa digitar sete valores numericos e cadastre-os em
uma lista unica que mantenha separados os valores pares e impares. no final, mostre os
valores pares e impares com ordem crescente.
'''

n = [[],[]]
valor = 0
for c in range(1,8):
    valor = int(input(f'digite o {c} valor:'))
    if valor % 2 == 0:
        n[0].append(valor)
    else:
        n[1].append(valor)
print(f'-=' * 30)
n[0].sort()
n[1].sort()
print(f'os valores digitados foram: {n[0]}')
print(f'os valores impares digitados foram: {n[1]}')

DESAFIO 86:

'''
crie um programa que crie uma matriz de dimensão 3x3 e preencha com valores lidos pelo
teclado. no final, mostre a matriz na tela, com a formação correta.
'''

matriz = [[0,0,0],[0,0,0],[0,0,0]]
for l in range(0,3):
    for c in range(0,3):
        matriz[l][c] = int(input(f'digite um valor para [{l},{c}]:'))
print('=-' * 30)
for l in range(0,3):
    for c in range(0,3):
        print(f'[{matriz[l][c]:^5}]',end='')
    print()
    
DESAFIO 87:

'''
aprimore o desafio anterior, mostrando no final:
- a soma de todos os valores pares digitados.
- a soma dos valores de terceira coluna.
- o maior valor da segunda coluna.
'''

matriz = [[0,0,0],[0,0,0],[0,0,0]]
spar = mai = scol = 0
for l in range(0,3):
    for c in range(0,3):
        matriz[l][c] = int(input(f'digite um valor para {l},{c};'))
print(f'-=' * 30)
for l in range(0,3):
    for c in range(0,3):
        print(f'[{matriz[l][c]:^5}]',end='')
        if matriz[l][c] % 2 == 0:
            spar += matriz[l][c]
    print()
print('-=' * 30)
print(f'a soma dos valores pares é {spar}')
for l in range(0,3):
    scol += matriz[l][c]
print(f'a soma dos valores da terceira coluna é: {scol}.')
for c in range(0,3):
    if c == 0:
        mai = matriz[1][c]
    elif matriz[1][c] > mai:
        mai = matriz[1][c]
print(f'o maior valor da segunda linha é {mai}')

DESAFIO 88:

'''
faça um programa que ajude um jogador da mega sena a criar palpites. o programa vai
perguntar quantos jogos serão gerados e vai sortear 6 numeros entre 1 e 60 para cada
jogo, cadastrando tudo em uma lista composta.
'''

from random import randint
from time import sleep
lista = list()
jogos = list()
print(f'-=' * 30)
print(f'                    JOGA NA MEGASENA!       ')
print(f'-=' * 30)
quant = int(input(f'quantos jogos voce quer que eu sorteie:'))
tot = 0
while tot <= quant:
    cont = 0
    while True:
        num = randint(1,60)
        if num not in lista:
            lista.append(num)
            cont += 1
        if cont >= 6:
            break
    lista.sort()
    jogos.append(lista[:])
    lista.clear()
    tot += 1
print('-=' * 3,f'SORTEANDO {quant} JOGOS', '-=' * 3)
for i, l in enumerate(jogos):
    print(f'jogo {i+1}: {l}')
    sleep(2)
print(f'-=' * 5, '< BOA SORTE! >','-=' * 5)

DESAFIO 89:

'''
crie um programa que leia o nome e duas notas de varios alunos e guarde tudo em uma lista
composta. no final, mostre um boletim contendo a media de cada um e permita que o usuario
possa mostrar as notas de cada aluno individualmente.
'''

#VOLTAR NESSE EXERCICIO, ADICIONANDO UMA FORMA DE CALCULAR AS NOTAS INFINITAMENTE!

ficha = list()
while True:
    nome = str(input('nome:'))
    nota1 = float(input('nota 1:'))
    nota2 = float(input('nota 2:'))
    media = (nota1 + nota2) / 2
    ficha.append([nome,[nota1,nota2],media])
    resp = str(input(f'quer continuar? [S/N]'))
    if resp in 'Nn':
        break
print(f'-=' * 30)
print(f'{"no.":<4}{"NOME":<10}{"media":>8}')
print(f'-' * 26)
for i, a in enumerate(ficha):
    print(f'{i<4}{a[0]:<10}{a[2]:>8.1f}')
while True:
    print(f'-' * 35)
    opc = int(input(f'mostrar notas de qual aluno? (999)'))
    if opc == 999:
        break
        print(f'finalizando!...')
    elif opc <= len(ficha) - 1:
        print(f'notas de {ficha[0]} sao {ficha[opc][1]} ')
print(f'<<<< VOLTE SEMPRE! >>>>')

DESAFIO 90:

'''
faça um programa que leia o nome e a media de um aluno, guardando tambem a situação em um
dicionario. no final, mostre o conteudo da estrutura da tela.
'''
situacao = []
nome = str(input('digite o seu nome:'))
n1 = int(input('digite a sua nota1:'))
n2 = int(input('digite a sua nota2:'))
media = (n1 + n2) / 2
passt = {'ESTADO':'APROVADO!'}
passf = {'ESTADO':'REPROVADO!'}
situacao.append(nome)
situacao.append(media)
print(f'o aluno {situacao[0]} teve a media {situacao[1]}!')
if media >= 7:
    print(f'o aluno {situacao[0]} teve a media {situacao[1]} e sua condição é: {passt}')
else:
    print(f'o aluno {situacao[0]} teve a media {situacao[1]} e sua condição é: {passf}')

    #EU QUE FIZ!
    
DESAFIO 91:

'''
crie um programa onde 4 jogadores joguem um dado e tenham resultados aleatorios. guarde
esses resultados em um dicionario. no final, coloque esse dicionario em ordem, sabendo que
o vencedor tirou o maior numero no dado.
'''

from time import sleep
from random import randint
from operator import itemgetter
jogo = {'jogador1': randint(1,6),
        'jogador2': randint(1,6),
        'jogador3': randint(1,6),
        'jogador4': randint(1,6)}
ranking = dict()
print('valores sorteados:')
for k, v in jogo.items():
    print(f'{k} tirou {v} no dado.')
    sleep(1)
ranking = sorted(jogo.items(), key=itemgetter(1),reverse=True)
print('-=' * 30)
print(' == RANKING DOS JOGADORES == ')
for i,v in enumerate(ranking):
    print(f'{i+1} lugar: {v[0]} com {v[1]}.')
    sleep(1)
    
DESAFIO 96:

'''
faça um programa que tenha uma função chamada area(), que receba as dimensões de um
terreno retangular (largura e comprimento) e mostre a area do terreno.
'''


print(f'-' * 30)
print(f'BEM VINDO AO PROGRAMA!')
print(f'-' * 30)
print(f'DIMENSOES DO TERRENO RETANGULAR!')
n1 = int(input('digite a largura do terreno:'))
n2 = int(input('digite o comprimento do terreno:'))
area0 = (n1 * n2)
def area(n1 = 'largura', n2 = 'comprimento'):
    print(n1, n2)
area(f'a largura do terreno é {n1}')
area(f'o comprimento do terreno é {n2}')
area(f'a area do terreno é {area0} metros quadrados!')
print(f'-' * 30)

DESAFIO 113:

'''
reescreva a função leiaint() que fizemos no desafio 104, incluindo agora a possibili
dade da digitação de um numero de tipo invalido. aproveite e crie tambem uma função
leiafloat() com a mesma funcionalidade.
'''

import modulo113
try:
    n = int(input('digite um numero inteiro:'))
    print(f'o numero {modulo113.leiaint(n)} é inteiro!')
except(ValueError, TypeError):
    print(f'ERRO!, tipos da dados invalidos!')
except ZeroDivisionError:
    print(f'ERRO!, numero não divisivel por 0')
finally:
    print(f'FIM DA FUNÇÃO!')


try:
    n = float(input('digite um numero quebrado:'))
    print(f'o numero {modulo113.leiafloat(n)} é quebrado!')
except(ValueError, TypeError):
    print(f'ERRO!, tipos da dados invalidos!')
except ZeroDivisionError:
    print(f'ERRO!, numero não divisivel por 0')
finally:
    print(f'FIM DA FUNÇÃO!')



