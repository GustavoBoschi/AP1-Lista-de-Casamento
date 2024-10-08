# AP1-Lista-de-Casamento
Uma lista de Casamento feita em Python para a AP1 (Avaliação Parte 1) da Faculdade Impacta, para a matéria de Técnicas de Programação

Toda a atividade foi realizada no Google Collab

# Atividade AP1

**Vocês deverão entregar um arquivo .py que é o módulo que vocês utilizaram. Além disso, enviar um notebook .ipynb com 3 exemplos de uso mostrando que o código funcionou**.

Contexto da atividade:


1. Quando a função for iniciada, solicitaremos que informe o Nome do Convidado;
2. Assim que o nome for escrito, perguntaremos se o convidado é do Noivo ou da Noiva;
3. Se o nome já existir **na lista de quem convidou**, pediremos para que o nome seja escrito de outra forma; caso contrário, adicionaremos o respectivo nome na lista de quem fez o convite;
4. A função deve seguir sendo chamada recursivamente. O critério de parada será o texto "ACABOU".
5. Quando o código for encerrado, o retorno deverá ser: Convidados do noivo (e retorna quem foi convidado **exclusivamente** pelo noivo), Convidados da noiva (e retorna quem foi convidado **exclusivamente** pela noiva) e Convidado por Ambos (e retorna quem foi convidado por ambos). Além dos nomes, o deverá retornar a quantidade de pessoas convidadas no total.

#Resposta

Os códigos dessa Ap1 foram desenvolvidos por **Gustavo Boschini Rossetti, Rafael Nesterur, Rafael Torolho e Vinicius Dias Campos**.

Nesta atividade, trouxemos dois códigos. A explicação de cada um está acima dos códigos. Decidimos fazer um segundo código para esta atividade com o propósito de nos desafiarmos a fazer algo um pouco mais elaborado, que ainda funciona como o código pedido.

Você poderá encontrar a explicação do código mais parecido com os requisitos enviados com o título de **Primeiro Código**, e o código que fizemos com o propósito de nos desafiarmos está com o título de **Segundo Código**. Nessas "abas", você encontrará uma breve explicação sobre cada um deles.

O **ap1_listacasamento.py** é do primeiro código e o **ap1_convcasamento.py** é referente ao segundo código. Por favor, faça o upload dos dois arquivos para efetuar os testes. Decidimos fazer eles em bibliotecas separadas para ficar melhor dividido na hora da correção.

No forms, só é possivel enviar um arquivo .py, então colocarei o link do arquivo do outro .py aqui

Por favor, faça a instalação do arquivo em .py para testar nosso segundo código também, qualquer erro, só copiar o local do arquivo e colocar no lugar do local do arquivo presente no código, muito obrigado

#Primeiro Código

Aqui, você poderá testar o código para ver se ele está funcionando de maneira adequada. Colocamos entre os testes formatações de prints vazios e prints escritos como testes para ficar visualmente mais limpo e facilitar a visualização dos testes realizados neste código.

Este código é o mais parecido com os requisitos enviados. Ele atende ao exemplo enviado junto com a atividade e tudo o que precisa fazer é escrever 1 ou 2 para o convidado ser adicionado na lista do noivo ou da noiva, respectivamente.

O código abaixo já segue com 3 exemplos para o teste ser realizado. No entanto, sinta-se livre para mudar os nomes contidos no código ou fazer novos testes. Com o input na escolha de noivo ou noiva, é possível executar diferentes testes dentro dos testes já colocados no código.

```
import sys

sys.path.insert(0,'/content/ap1_listacasamento.py')

import ap1_listacasamento

print("Teste 1")
convidados = ["Arthur", "Arthur", "Arthur", "Arthur Figueira", "Maria", "ACABOU"]
ap1_listacasamento.lista_convidados(convidados)
print("")
print("Teste 2")
convidados = ["Gustavo", "Nesterur", "Torolho", "Vinicius", "Fulano", "Ciclano", "Fulano", "Ciclano", "ACABOU"]
ap1_listacasamento.lista_convidados(convidados)
print("")
print("Teste 3")
convidados = ["Maria", "Eduarda", "Maria Eduarda", "Maria Eduarda", "ACABOU"]
ap1_listacasamento.lista_convidados(convidados)
```

# AP1_ListaCasamento.py

Para melhor vizualição e praticidade, o código que está dentro de **ap1_listacasamento.py** é o código inserido abaixo, mas sinta-se livre para entrar no arquivo e ver o código.

```
lista_noivo = set()
lista_noiva = set()
lista_ambos = set()

def lista_convidados(convidados):

    if not convidados:
        return

    convidado = convidados[0]

    if convidado == "ACABOU":
        lista_total = lista_noivo.union(lista_noiva).union(lista_ambos)
        print("")
        print(f"Convidados Noivo: {', '.join(lista_noivo - lista_noiva)}")
        print(f"Convidados Noiva: {', '.join(lista_noiva - lista_noivo)}")
        print(f"Convidados de ambos: {', '.join(lista_ambos)}")
        print(f"Quantidade de convidados: {len(lista_total)}")
        lista_noiva.clear()
        lista_noivo.clear()
        lista_ambos.clear()
        lista_total.clear()
        return

    escolha = int(input("O convidado é do Noivo(1) ou da Noiva(2)? "))

    if escolha == 1:
      if convidado in lista_noivo:
        print("Desculpe, o nome já consta nessa lista, tente novamente")
      elif convidado in lista_ambos:
        print("Desculpe, o nome já consta na lista da noiva, adicionando na lista de ambos, tente novamente")
      elif convidado in lista_noiva:
        lista_noiva.remove(convidado)
        lista_ambos.add(convidado)
      else:
        lista_noivo.add(convidado)

    if escolha == 2:
      if convidado in lista_noiva:
        print("Desculpe, o nome já consta nessa lista, tente novamente")
      elif convidado in lista_ambos:
        print("Desculpe, o nome já consta na lista do noivo, adicionando na lista de ambos, tente novamente")
      elif convidado in lista_noivo:
        lista_noivo.remove(convidado)
        lista_ambos.add(convidado)
      else:
        lista_noiva.add(convidado)

    lista_convidados(convidados[1:])
```

# Segundo Código

Aqui, você encontrará o segundo código que decidimos elaborar para a atividade, com o intuito de deixar esse código mais parecido com uma lista real de casamento, como se um usuário fosse usar este código para fazer a lista de seu casamento. A lógica do código é a mesma, porém, este código contém input para o nome do convidado e um tratamento para que erros ao digitar esses nomes não aconteçam. Por exemplo, ao escrever "Arthur" e "ARTHUR", eles seriam considerados pessoas diferentes, mas, graças ao tratamento de erros que realizamos no código, os nomes escritos podem estar todos em minúsculas ou maiúsculas e serão considerados os mesmos. O mesmo vale para o "ACABOU", onde é possível escrever com maiúsculas ou minúsculas. O código também possui uma estruturação mais bonita no prompt, exibindo mensagens de confirmação a cada processo do código.

Colocamos 3 testes dentro desse código também para serem realizados. Sinta-se livre para realizá-los.

```
import sys

sys.path.insert(0,'/content/ap1_convcasamento.py')

import ap1_convcasamento

print("Teste 1")
ap1_convcasamento.lista_convidados()
print("")
print("Teste 2")
ap1_convcasamento.lista_convidados()
print("")
print("Teste 3")
ap1_convcasamento.lista_convidados()

```

#AP1_ConvCasamento.py

Para melhor vizualição e praticidade, o código que está dentro de **ap1_convcasamento.py** é o código inserido abaixo, mas sinta-se livre para entrar no arquivo e ver o código.

```
lista_noivo = set()
lista_noiva = set()
lista_ambos = set()

def lista_convidados():

    print("")
    print("Caso queira encerrar o processo, escreva (ACABOU)")
    print("")
    convidado = input("Escreva o nome do convidado: ").strip().lower()

    if convidado == "acabou":
      lista_total = lista_noivo.union(lista_noiva).union(lista_ambos)
      print("")
      print(f"Convidados Noivo: {', '.join([nome.title() for nome in lista_noivo - lista_noiva])}")
      print(f"Convidados Noiva: {', '.join([nome.title() for nome in lista_noiva - lista_noivo])}")
      print(f"Convidados de ambos: {', '.join([nome.title() for nome in lista_ambos])}")
      print(f"Quantidade de convidados: {len(lista_total)}")
      print("")
      lista_total.clear()
      lista_noivo.clear()
      lista_noiva.clear()
      lista_ambos.clear()
      return

    escolha = int(input(f"{convidado.title()} é convidado do Noivo(1) ou da Noiva(2)? "))

    if escolha == 1:
      if convidado in lista_noivo:
        print("")
        print(f"Desculpe, {convidado.title()} já consta nessa lista, tente novamente")
      elif convidado in lista_ambos:
        print("")
        print(f"Desculpe, {convidado.title()} já consta na lista da noiva, movendo para lista de ambos, tente outro nome")
      elif convidado in lista_noiva:
        lista_noiva.remove(convidado)
        lista_ambos.add(convidado)
        print("")
        print(f"{convidado.title()} já estava na lista da Noiva, foi movido para a lista de ambos")
      else:
        lista_noivo.add(convidado)
        print("")
        print(f"{convidado.title()} foi adicionado à lista do noivo")

    if escolha == 2:
      if convidado in lista_noiva:
        print("")
        print(f"Desculpe, {convidado.title()} já consta nessa lista, tente novamente")
      elif convidado in lista_ambos:
        print("")
        print(f"Desculpe, {convidado.title()} já consta na lista do noivo, movendo para lista de ambos, tente novamente")
      elif convidado in lista_noivo:
        lista_noivo.remove(convidado)
        lista_ambos.add(convidado)
        print("")
        print(f"{convidado.title()} já estava na lista do Noivo, foi movido para a lista de ambos")
      else:
        lista_noiva.add(convidado)
        print("")
        print(f"{convidado.title()} foi adicionado à lista do noiva")

    lista_convidados()
```

