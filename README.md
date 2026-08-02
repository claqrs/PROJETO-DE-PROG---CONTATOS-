lista_de_contatos = []
lista_de_contatosF = []

while True:
    print("========== CONTATOS ==========")
    print("1 - ADICIONAR CONTATO
    2 - BUSCAR CONTATO
    3 - CONTATOS FAVORITOS
    4 - ALTERAR CONTATO
    5 - EXCLUIR CONTATO
    6 - LISTAR TODOS OS CONTATOS
    7 - SAIR")

    selecionar = input("Selecionar: ")

    # ADICIONAR CONTATO
   
    if selecionar == "1":

        nome = input("Nome: ")
        numero = input("Número: ")

        lista_de_contatos.append({
            "nome": nome,
            "numero": numero})

        print("Deseja favoritar esse contato?")
        print("1 - Sim")
        print("2 - Não")

        selecionarF = input(": ")

        if selecionarF == "1":
            lista_de_contatosF.append({
                "nome": nome,
                "numero": numero})

        print("Contato adicionado com sucesso!")

  
    # BUSCAR CONTATO

    elif selecionar == "2":

        if len(lista_de_contatos) == 0:
            print("Nenhum contato cadastrado.")

        else:

            Bcontato = input("Digite o nome do contato: ")

            encontrado = False

            for contato in lista_de_contatos:

                if contato["nome"].lower() == Bcontato.lower():

                    print("-------- CONTATO --------")
                    print("Nome:", contato["nome"])
                    print("Número:", contato["numero"])
                    print("-------------------------")

                    encontrado = True

            if not encontrado:
                print("Contato não encontrado.")

   
    # CONTATOS FAVORITOS

    elif selecionar == "3":

        if len(lista_de_contatosF) == 0:
            print("Nenhum contato favoritado.")

        else:

            lista_de_contatosF.sort(key=lambda contato: contato["nome"].lower())

            print("====== FAVORITOS ======")

            for contato in lista_de_contatosF:

                print("-------------------------")
                print("Nome:", contato["nome"])
                print("Número:", contato["numero"])

            print("-------------------------")


    # ALTERAR CONTATO

    elif selecionar == "4":

        if len(lista_de_contatos) == 0:
            print("Nenhum contato cadastrado.")

        else:

            nome_busca = input("Digite o nome do contato que deseja alterar: ")

            encontrado = False

            for contato in lista_de_contatos:

                if contato["nome"].lower() == nome_busca.lower():

                    antigo_nome = contato["nome"]
                    antigo_numero = contato["numero"]

                    print("Contato encontrado!")

                    contato["nome"] = input("Novo nome: ")
                    contato["numero"] = input("Novo número: ")

                    # Atualiza também nos favoritos
                    for favorito in lista_de_contatosF:

                        if favorito["nome"] == antigo_nome and favorito["numero"] == antigo_numero:

                            favorito["nome"] = contato["nome"]
                            favorito["numero"] = contato["numero"]

                    print("Contato alterado com sucesso!")

                    encontrado = True
                    break

            if not encontrado:
                print("Contato não encontrado.")


    # EXCLUIR CONTATO

    elif selecionar == "5":

        if len(lista_de_contatos) == 0:
            print("Nenhum contato cadastrado.")

        else:

            nome_excluir = input("Digite o nome do contato que deseja excluir: ")

            encontrado = False

            for contato in lista_de_contatos:

                if contato["nome"].lower() == nome_excluir.lower():

                    print("Contato encontrado:")
                    print("Nome:", contato["nome"])
                    print("Número:", contato["numero"])

                    confirmar = input("Tem certeza que deseja excluir? (S/N): ")

                    if confirmar.upper() == "S":

                        lista_de_contatos.remove(contato)

                        # Remove dos favoritos, caso exista
                        for favorito in lista_de_contatosF[:]:

                            if favorito["nome"] == contato["nome"] and favorito["numero"] == contato["numero"]:

                                lista_de_contatosF.remove(favorito)

                        print("\nContato excluído com sucesso!")

                    else:
                        print("\nExclusão cancelada.")

                    encontrado = True
                    break

            if not encontrado:
                print("\nContato não encontrado.")

    
    # LISTAR TODOS OS CONTATOS

    elif selecionar == "6":

        if len(lista_de_contatos) == 0:

            print("Nenhum contato cadastrado.")

        else:

            lista_de_contatos.sort(key=lambda contato: contato["nome"].lower())

            print("===== LISTA DE CONTATOS =====")

            for contato in lista_de_contatos:

                print("-------------------------")
                print("Nome:", contato["nome"])
                print("Número:", contato["numero"])

            print("-------------------------")

    # ===========================
    # SAIR
    # ===========================
    elif selecionar == "7":

        print("Programa encerrado!")
        break

    else:

        print("Opção inválida!")
