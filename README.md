# Hangman-game-in-Python
A simple Hangman game created using python!

from random import random, shuffle
import math

def createRandom(x):
    return math.floor(random()* x)


def createChecker(letter, word):
    letter = letter.lower()
    for x in range(len(word)):
        currentWord = word[x]
        if(letter == word[x]):
            guess[x] = letter

def letterCount(y):
    if(y > 1):
        print(f"There are {numCorrect} letter '{userGuess}' in the word assigned")
    elif(y == 1):
        print(f"There is {numCorrect} letter '{userGuess}' in the word assigned")
    else:
        print(f"There is no letter '{userGuess}' in the word assigned")


setOfwords = ["weird", "handkerchief", "cemetery", "conscience"]

word = setOfwords[createRandom(len(setOfwords))]

guess = ["-" for x in list(word)]
lives = len(word)

print(f"Death is chasing you and you have to guess the word that he is whispering!\n\n{guess}")

while(lives !=0):
    print(f"\nYou have {lives} tries left")
    userGuess = input("Enter a letter: ")
    lives-=1
    numCorrect = list(word).count(userGuess)
    createChecker(userGuess, word)
    print(guess)
    letterCount(numCorrect)

    if("".join(guess) == word):
        print(f"You guessed the correct word! which is '{word}'")
        break

if(lives == 0 and "".join(guess) != word):
    print(f"You were not able to guess the word '{word}' and death false upon you!")
