# Stone-Scissor-Paper
As a journey into coding and data science, I want to develop some basic AI to play against

The used IDE is PyCharm

from random import randint
import numpy as np

victoriaPlayer = 0
victoriaMaquina = 0
empates = 0



file1 = open("/Users/JoseManuelChustBalag/Desktop/REQUESTS/BP channel/Decisions.txt","r")

resolution = np.array((["e", "M", "J"], ["J", "E", "M"], ["M", "J", "E"]))


totalLinias = 0
i =0

options = ["Piedra", "Papel", "Tijeras"]

ficheroRondas = open("/Users/JoseManuelChustBalag/Desktop/REQUESTS/BP channel/Rondas.txt","a")

def Rondas(ganador):

    ficheroRondas.write("En la Ronda {},{}\n".format(totalLinias,ganador))


def ResultadosFinales ():
    print("Los resultados finales son:"
            "\n El jugador tiene {} victorias"
            "\n La maquina tiene {} victorias"
            "\n Han habido {} empates".format(victoriaPlayer, victoriaMaquina,empates))

    ficheroRondas.write("\n \n "
            "\nLos resultados finales son:"
            "\n El jugador tiene {} victorias"
            "\n La maquina tiene {} victorias"
            "\n Han habido {} empates".format(victoriaPlayer, victoriaMaquina,empates))

for i in file1:
    totalLinias +=1
    player = int(i)

    playerOption = options[player]

    maquina = randint(0,2)
    maquinaOption = options[maquina]

    print("El jugador ha sacador {}".format(playerOption))
    print ("La maquina ha sacador {}".format(maquinaOption))

    if resolution[player,maquina] =="J":
        print("Gana el jugador")
        victoriaPlayer += 1
        Rondas(ganador = "ha ganado el jugador")

    elif resolution[player,maquina] =="M":
        print("Gana la maquina")
        victoriaMaquina += 1
        Rondas( ganador="ha ganado la maquina")

    else:
        print ("EMPATE")
        empates +=1
        Rondas(ganador="ha habido empate")


ResultadosFinales()

file1.close()

ficheroRondas.close()
