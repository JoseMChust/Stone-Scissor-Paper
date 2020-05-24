# Stone-Scissor-Paper
As a journey into coding and data science, I want to develop some basic AI to play against

The used IDE is PyCharm

from random import randint
import numpy as np

victoriaPlayer = 0
victoriaMaquina = 0
empates = 0



file1 = open("/Users/JoseManuelChustBalag/Desktop/REQUESTS/BP channel/Decisions.txt","r")

resolution = np.array((["T", "L", "W"], ["W", "T", "L"], ["L", "W", "T"]))


totalLinias = 0
i =0

options = ["Stone", "Paper", "Scissors"]

ficheroRondas = open("/Users/JoseManuelChustBalag/Desktop/REQUESTS/BP channel/Rondas.txt","a")

def Rondas(ganador):

    ficheroRondas.write("At the round {},{}\n".format(totalLinias,ganador))


def ResultadosFinales ():
    print("The final results are:"
            "\n The player has got {} victories"
            "\n The machines has got {} victories"
            "\n There have been {} ties".format(victoriaPlayer, victoriaMaquina,empates))

    ficheroRondas.write("\n \n "
            "\nThe final results are:"
            "\n The player has got {} victories"
            "\n La maquina tiene {} victorias"
            "\n There have been {} ties".format(victoriaPlayer, victoriaMaquina,empates))

for i in file1:
    totalLinias +=1
    player = int(i)

    playerOption = options[player]

    maquina = randint(0,2)
    maquinaOption = options[maquina]

    print("The player chose {}".format(playerOption))
    print ("The machine chose {}".format(maquinaOption))

    if resolution[player,maquina] =="W":
        print("Player wins")
        victoriaPlayer += 1
        Rondas(ganador = "has won this round")

    elif resolution[player,maquina] =="L":
        print("Machine wins")
        victoriaMaquina += 1
        Rondas( ganador="has won this round")

    else:
        print ("TIE")
        empates +=1
        Rondas(ganador="there has been a tie")


ResultadosFinales()

file1.close()

ficheroRondas.close()
