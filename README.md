# Sistema-Banc-rio
# Projeto do Bootcamp Python AI backend developer da DIO
menu = """
\033[1;34mBANCO AMERICANO
Opções:
[1] Depositar 
[2] Sacar
[3] Extrato 
[0] Sair\033[m
"""
saldo = 0
sacado = []
deposito = []
quantidade_de_saque = 0

opcao = 1
while opcao != 0:
    print(menu)
    opcao = int(input('Qual opção você quer? '))
    if opcao == 1:
        depositar = float(input('Quanto você quer depositar? R$ '))
        if depositar > 0:
            saldo = saldo + depositar
            deposito.append(depositar)
        else:
            print('Erro no valor!')
            continue
    if opcao == 2:
        saque = float(input('Quanto você quer sacar? R$ '))
        if quantidade_de_saque < 3 and saque < saldo and saque <= 500:
            quantidade_de_saque = quantidade_de_saque + 1
            saldo = saldo - saque
            sacado.append(saque)
        elif saque > saldo:
            print('\033[1;31mNão foi possível sacar o dinheiro por falta de saldo.\033[m')
            continue
        elif quantidade_de_saque >= 3:
            print('\033[1;31mQuantidade de saque diário excedido.\033[m')
            continue
        elif saque > 500:
            print('\033[1;31mSaque maior que R% 500,00. Valor excedido.\033[m')
            continue
    if opcao == 3:
        print('-' * 40)
        print(f'{"EXTRATO":.^40}')
        print('-' * 40)
        print(f'\033[1;32m{"Depositos":.<30}\033[m', f'\033[1;32mR${"Valor":>7}\033[m')
        for c in range(0, len(deposito)):
            print(f'\033[1;32m{c + 1}º\033[m', f'\033[1;32m{"":.<27}\033[m', f'\033[1;32mR${deposito[c]:>7.2f}\033[m')
        print(f'\033[1;31m{"Saques":.<30}\033[m', f'\033[1;31mR${"Valor":>7}\033[m')
        for j in range(0, len(sacado)):
            print(f'\033[1;31m{j + 1}º\033[m', f'\033[1;31m{"":.<27}\033[m', f'\033[1;31mR${sacado[j]:>7.2f}\033[m')
        print(f'\033[1;34m{"SALDO":.<30}\033[m', f'\033[1;34mR${saldo:>7.2f}\033[m')
        print('-' * 40)
    if opcao == 0:
        print('Obrigado! E volte sempre.')
        break
    else:
        print('\033[1;31mOpção inválida tente novamente.\033[m')
