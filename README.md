# CodeAlpha_Tasks
#code alpha tasks are here 
#Hangman Game
import random


def choose_word():
    words = ["python", "hangman", "programming", "computer", "game", "algorithm", "openai", "language"]
    return random.choice(words)


def display_word(word, guessed_letters):
    display = ""
    for letter in word:
        if letter in guessed_letters:
            display += letter
        else:
            display += "_"
    return display


def hangman():
    print("Welcome to Hangman!")
    word = choose_word()
    guessed_letters = []
    attempts = 6

    while attempts > 0:
        print("\nAttempts left:", attempts)
        print("Word:", display_word(word, guessed_letters))
        guess = input("Guess a letter: ").lower()

        if len(guess) != 1 or not guess.isalpha():
            print("Please enter a single letter.")
            continue

        if guess in guessed_letters:
            print("You already guessed that letter.")
            continue

        guessed_letters.append(guess)

        if guess not in word:
            print("Incorrect!")
            attempts -= 1

        if "_" not in display_word(word, guessed_letters):
            print("Congratulations! You guessed the word:", word)
            break

    if attempts == 0:
        print("\nSorry, you're out of attempts. The word was:", word)


hangman()
