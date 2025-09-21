# projeto_01
lista_de_tarefas = []

def adicionar_tarefas():
    nome_tarefa = input("Digite o nome da tarefa: ")
    prioridade_tarefa = input("Digite a prioridade da tarefa(Alta,Média,Baixa): ")
    categoria_tarefa = input("Digite a categoria da tarefa: ")
    
    nova_tarefa = {
            "Nome": nome_tarefa,
            "Prioridade": prioridade_tarefa,
            "Categoria": categoria_tarefa,
            "Status": "Pendente"
            }
    
    lista_de_tarefas.append(nova_tarefa)
    print(f"{nova_tarefa['Nome']} adicionado com  sucesso")

def listar_tarefas():

    if not lista_de_tarefas:
        print("Nenhuma tarefa cadastrada.")
        return
    print("\n======= LISTA DE TAREFAS =======")
    for i, element in enumerate(lista_de_tarefas, start=1):
        print(f"""
Tarefa {i}:
    Nome      : {element['Nome']}
    Prioridade: {element['Prioridade']}
    Categoria : {element['Categoria']}
    Status    : {element['Status']}
""")
    print("================================\n")
                
def concluir_tarefas():
    tarefa_concluida = input("Digite o nome da tarefa que deseja marcar como concluída: ")
    encontrada = False

    for element in lista_de_tarefas:
        if element['Nome'] == tarefa_concluida:
            element['Status'] = "Concluída"
            print(f"Tarefa {element['Nome']} marcada como concluída.")
            encontrada = True

    if not encontrada:
        print("Tarefa não encontrada.")

def excluir_tarefas():
    tarefa_a_ser_excluida = input("Digite o nome da tarefa que você deseja excluir: ")
    removida = False
    
    for element in lista_de_tarefas[:]:
        if element['Nome'] == tarefa_a_ser_excluida:
            lista_de_tarefas.remove(element)
            print(f"{element['Nome']} excluído com sucesso")
            removida = True

    if not removida:
            print("Tarefa não encontrada.")

def filtrar_tarefas():
    if not lista_de_tarefas:
        print("Tarefa não encontrada.")
        return

    opcao = input("""
Como deseja filtrar?
1- Por Prioridade
2- Por Categoria
ESCOLHA: """)

    filtradas = []

    if opcao == "1":
        prioridade = input("Digite a prioridade (Alta, Média, Baixa): ")
        for o in lista_de_tarefas:
            if o['Prioridade'].lower() == prioridade.lower():
                filtradas.append(o)
    
    elif opcao == "2":
        categoria = input("Digite a categoria: ")
        for o in lista_de_tarefas:
            if o['Categoria'].lower() == categoria.lower():
                filtradas.append(o)
    
    else:
        print("Opção inválida.")
        return
    
    if filtradas:
        print("\n======= TAREFAS FILTRADAS =======")
        for i, element in enumerate(filtradas, start=1):
            print(f"""
Tarefa {i}:
    Nome      : {element['Nome']}
    Prioridade: {element['Prioridade']}
    Categoria : {element['Categoria']}
    Status    : {element['Status']}
""")
        print("=================================\n")
    else:
        print("Nenhuma tarefa encontrada com esse filtro.")


while True:

    menu = input("""

============================
    ECOLHA UMA OPÇÃO:
1- ADICIONAR NOVA TAREFA
2- VER TAREFAS ADICIONADAS
3- MARCAR COMO CONCLUÍDO
4- EXCLUIR TAREFA
5- FILTRAR TAREFA
0- SAIR
=============================

""")

    match menu:

        case "1":
            adicionar_tarefas()

        case "2":
            listar_tarefas()

        case "3":
            concluir_tarefas() 

        case "4":
            excluir_tarefas()

        case "5":
            filtrar_tarefas()

        case "0":
            print("Fim do programa")
            break

        case _:
            print("Opção inválida")
