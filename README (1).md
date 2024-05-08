
## 🔗 Links
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/joão-vitorsa/)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Mrviitor)
[![E-mail](https://img.shields.io/badge/-Email-000?style=for-the-badge&logo=microsoft-outlook&logoColor=007BFF)](mailto:mrxjoaovitor@gmail.com)

## Sistema bancario em python

menu = """

[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair

=> """

saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3

while True:

    opcao = input(menu)

    if opcao == "d":
        valor = float(input("Informe o valor do depósito: "))

        if valor > 0:
            saldo += valor
            extrato += f"Depósito: R$ {valor:.2f}\n"

        else:
            print("Operação falhou! O valor informado é inválido.")

    elif opcao == "s":
        valor = float(input("Informe o valor do saque: "))

        excedeu_saldo = valor > saldo

        excedeu_limite = valor > limite

        excedeu_saques = numero_saques >= LIMITE_SAQUES

        if excedeu_saldo:
            print("Operação falhou! Você não tem saldo suficiente.")

        elif excedeu_limite:
            print("Operação falhou! O valor do saque excede o limite.")

        elif excedeu_saques:
            print("Operação falhou! Número máximo de saques excedido.")

        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2f}\n"
            numero_saques += 1

        else:
            print("Operação falhou! O valor informado é inválido.")

    elif opcao == "e":
        print("\n================ EXTRATO ================")
        print("Não foram realizadas movimentações." if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("==========================================")

    elif opcao == "q":
        break

    else:
        print("Operação inválida, por favor selecione novamente a operação desejada.")

---------------------------------------------------------------------------------------

[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair

=> d
Informe o valor do depósito: 1000


[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair

=> s
Informe o valor do saque: 1000
Operação falhou! O valor do saque excede o limite.


[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair

=> s
Informe o valor do saque: 100


[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair

=> s
Informe o valor do saque: 500


[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair

=> s
Informe o valor do saque: 100


[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair

=> 10
Operação inválida, por favor selecione novamente a operação desejada.


[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair

=> e

================ EXTRATO ================
Depósito: R$ 1000.00
Saque: R$ 100.00
Saque: R$ 500.00
Saque: R$ 100.00


Saldo: R$ 300.00
==========================================