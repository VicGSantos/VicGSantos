#joguin da forca



import random

animal = ["TIGRE", "CORUJA", "ONÇA", "LEÃO", "ELEFANTE", "URSO", "ZEBRA", "GIRAFA", "CAVALO", "AVESTRUZ", "CAMELO", "COELHO", "LAGARTO", "JACARÉ", "Lobo"]
comida = ["MAÇA", "UVA", "FEIJAO", "ARROZ", "LIMAO", "MELANCIA", "MORANGO", "LARANJA", "BANANA", "ABACAXI", "GOIABA", "CAJU", "MANGA", "PEPINO", "CABELUDINHA"]
roupa = ["TÊNIS", "CAMISA", "SHORTS", "SAIA", "CALÇA", "BLUSA", "JAQUETA", "SANDÁLIA", "VESTIDO", "BERMUDA", "SUÉTER", "CALÇA JEANS", "BOINA", "REGATA", "LUVA"]
cor = ["AZUL", "LARANJA", "ROXO", "VERDE", "VERMELHO", "AMARELO", "PRETO", "BRANCO", "CINZA", "PINK", "MARROM", "BEGE", "TURQUESA", "DOURADO", "PRATA"]


generos = [animal, comida, roupa, cor]
nome_generos = ["animal", "comida", "roupa", "cor"]

while True:
    genero_escolhido = random.choice(generos)  # escolhe o genero
    posicao_genero = generos.index(genero_escolhido)  # revela a posiçao numerica do genero dentro da lista "generos", que ganha um numero como valor
    genero_str = nome_generos[posicao_genero]  # procura o nome do genero na mesma posiçao


    #palavra da partida
    palavra = random.choice(genero_escolhido)  
    mostra_palavra = ["_"] * len(palavra)

    def mostrar():
        print(" ".join(mostra_palavra))

    #começo
    vida = 5
    print("--------------------------------")
    print(f"Vamos jogar o jogo da forca, você só tem 5 vidas :), o genero é:")
    print()
    print("  " + genero_str)
    print()
    mostrar()
    print("--------------------------------")

    #tentativas
    while True:
        if vida > 0:
            if "_" in mostra_palavra:
                comparacao = "".join(mostra_palavra)

                letraLow = input()
                letraUp = letraLow.upper()

                if len(letraLow) != 1 or not letraLow.isalpha():
                    print("Por favor, digite apenas uma letra.")
                    continue

                for i in range(len(palavra)):
                    if palavra[i] == letraUp:
                        mostra_palavra[i] = letraUp

                if "".join(mostra_palavra) == comparacao:
                    vida -= 1

                print("--------------------------------")
                print("  " + genero_str)
                print()
                mostrar()
                print(f"vida: {vida}")
                print("--------------------------------")

            else:
                print("Ganhou, parabens!")                
                break
                
        else:
            #perdeu, ruim
            print("Perdeu kkkkkkkkkkk, podre")   
            print("Tentar novamente?")
            resposta = input("S ou N? ").upper()
            if resposta == "S":
                break
    print("Tentar novamente?")       
    resposta = input("S ou N? ").upper()
    if resposta == "N":
        print("END GAME")
        break
