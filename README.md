# SistemaBancario1

class Conta:
    def __init__(self, titular):
        self.titular = titular
        self.saldo = 0.0
        self.transacoes = []

    def depositar(self, valor):
        if valor > 0:
            self.saldo += valor
            self.transacoes.append(f"Depósito: R$ {valor:.2f}")
            print(f"Depósito de R$ {valor:.2f} realizado com sucesso!")
        else:
            print("Valor de depósito inválido.")

    def sacar(self, valor):
        if valor > 0 and valor <= self.saldo:
            self.saldo -= valor
            self.transacoes.append(f"Saque: R$ {valor:.2f}")
            print(f"Saque de R$ {valor:.2f} realizado com sucesso!")
        else:
            print("Saldo insuficiente ou valor inválido.")

    def exibir_extrato(self):
        print(f"\nExtrato da conta de {self.titular}:")
        if not self.transacoes:
            print("Nenhuma transação realizada.")
        else:
            for transacao in self.transacoes:
                print(transacao)
        print(f"Saldo atual: R$ {self.saldo:.2f}\n")


def obter_nome():
    while True:
        nome = input("Digite o nome do titular da conta: ")
        if all(c.isalpha() or c.isspace() for c in nome):  
            return nome
        else:
            print("Por favor, digite um nome válido (somente letras e espaços).")


def menu():
    print("Bem-vindo ao sistema bancário!")
    nome = obter_nome()  
    conta = Conta(nome) 

    while True:
        print("\nEscolha uma operação:")
        print("1 - Depósito")
        print("2 - Saque")
        print("3 - Extrato")
        print("4 - Sair")
        
        opcao = input("Digite o número da opção: ")
        
        if opcao == '1':
            valor = float(input("Digite o valor do depósito: R$ "))
            conta.depositar(valor)
        elif opcao == '2':
            valor = float(input("Digite o valor do saque: R$ "))
            conta.sacar(valor)
        elif opcao == '3':
            conta.exibir_extrato()
        elif opcao == '4':
            print("Obrigado por usar o sistema bancário!")
            break
        else:
            print("Opção inválida! Tente novamente.")



menu()
