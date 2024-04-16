class Cliente:
    def __init__(self, nome, cpf):
        self.nome = nome
        self.cpf = cpf


class Conta:
    def __init__(self, cliente, saldo=0):
        self.cliente = cliente
        self.saldo = saldo

    def depositar(self, valor):
        self.saldo += valor
        print(f"Depósito de {valor} realizado. Novo saldo: {self.saldo}")

    def sacar(self, valor):
        if valor <= self.saldo:
            self.saldo -= valor
            print(f"Saque de {valor} realizado. Novo saldo: {self.saldo}")
        else:
            print("Saldo insuficiente.")

    def consultar_saldo(self):
        print(f"Saldo da conta do cliente {self.cliente.nome}: {self.saldo}")


class ContaCorrente(Conta):
    def __init__(self, cliente, saldo=0, limite=0):
        super().__init__(cliente, saldo)
        self.limite = limite

    def sacar(self, valor):
        if valor <= self.saldo + self.limite:
            self.saldo -= valor
            print(f"Saque de {valor} realizado. Novo saldo: {self.saldo}")
        else:
            print("Limite de saque excedido.")


class ContaPoupanca(Conta):
    def __init__(self, cliente, saldo=0, juros=0.01):
        super().__init__(cliente, saldo)
        self.juros = juros

    def aplicar_juros(self):
        juros = self.saldo * self.juros
        self.saldo += juros
        print(f"Juros aplicados. Novo saldo: {self.saldo}")


def menu():
    print("Bem-vindo ao Sistema Bancário!")
    print("1. Criar conta corrente")
    print("2. Criar conta poupança")
    print("3. Depositar")
    print("4. Sacar")
    print("5. Consultar saldo")
    print("6. Aplicar juros (somente para conta poupança)")
    print("0. Sair")

def criar_conta_corrente(cliente):
    limite = float(input("Informe o limite da conta corrente: "))
    return ContaCorrente(cliente, limite=limite)

def criar_conta_poupanca(cliente):
    juros = float(input("Informe a taxa de juros da conta poupança (em decimal): "))
    return ContaPoupanca(cliente, juros=juros)

# Criando um cliente de exemplo
cliente_exemplo = Cliente("Filipe", "123.456.789-00")

# Loop principal do programa
while True:
    menu()
    opcao = input("Escolha uma opção: ")

    if opcao == "1":
        conta = criar_conta_corrente(cliente_exemplo)
        print("Conta corrente criada com sucesso!")

    elif opcao == "2":
        conta = criar_conta_poupanca(cliente_exemplo)
        print("Conta poupança criada com sucesso!")

    elif opcao == "3":
        valor = float(input("Informe o valor a ser depositado: "))
        conta.depositar(valor)

    elif opcao == "4":
        valor = float(input("Informe o valor a ser sacado: "))
        conta.sacar(valor)

    elif opcao == "5":
        conta.consultar_saldo()

    elif opcao == "6" and isinstance(conta, ContaPoupanca):
        conta.aplicar_juros()

    elif opcao == "0":
        print("Obrigado por utilizar o Sistema Bancário!")
        break

    else:
        print("Opção inválida. Por favor, escolha uma opção válida.")
