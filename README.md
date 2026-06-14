import random

words = ["python", "banana", "school", "planet", "garden"]

word = random.choice(words)
guessed_word = ["_"] * len(word)

wrong_guesses = 0
max_wrong = 6

print("--------------------------- HANGMAN GAME -----------------------------------")

while wrong_guesses < max_wrong and "_" in guessed_word:
    print("\nWord:", " ".join(guessed_word))
    print("Wrong guesses left:", max_wrong - wrong_guesses)

    guess = input("Enter a letter: ").lower()

    if len(guess) != 1:
        print("Enter only one letter.")
        continue

    if guess in word:
        print("Correct!")
        for i in range(len(word)):
            if word[i] == guess:
                guessed_word[i] = guess
    else:
        print("Wrong!")
        wrong_guesses += 1

if "_" not in guessed_word:
    print("\nYou won! The word was:", word)
else:
    print("\nGame Over!")
    print("The word was:", word)
