# Stone-Scissor-Paper

from random import randint
import numpy as np

victoryPlayer = 0
victoryMachine = 0
ties = 0



file1 = open("YOUR DIRECTORY","r")

resolution = np.array((["T", "L", "W"], ["W", "T", "L"], ["L", "W", "T"]))


totalLines = 0
i =0

options = ["Stone", "Paper", "Scissors"]

fileRounds = open("YOUR DIRECTOTY FOR THE NEW FILE", "a")

def rounds(winner):

    fileRounds.write("At the round {},{}\n".format(totalLines, winner))


def finalResults ():
    print("The final results are:"
            "\n The player has got {} victories"
            "\n The machines has got {} victories"
            "\n There have been {} ties".format(victoryPlayer, victoryMachine, ties))

    fileRounds.write("\n \n "
            "\nThe final results are:"
            "\n The player has got {} victories"
            "\n La maquina tiene {} victorias"
            "\n There have been {} ties".format(victoryPlayer, victoryMachine, ties))

for i in file1:
    totalLines +=1
    player = int(i)

    playerOption = options[player]

    machineAI = randint(0, 2)
    machineChoice = options[machineAI]

    print("The player chose {}".format(playerOption))
    print ("The machine chose {}".format(machineChoice))

    if resolution[player, machineAI] == "W":
        print("Player wins")
        victoryPlayer += 1
        rounds(winner="has won this round")

    elif resolution[player, machineAI] == "L":
        print("Machine wins")
        victoryMachine += 1
        rounds(winner="has won this round")

    else:
        print ("TIE")
        ties +=1
        rounds(winner="there has been a tie")


finalResults()

file1.close()

fileRounds.close()
