# guessing_game.py
geussing game
secret_raw = input()
secret_stripped = secret_raw.strip()

if not secret_stripped.isdigit():
    print("Invalid input. Ending game.")
else:
    secret = int(secret_stripped)

    max_raw = input()
    max_stripped = max_raw.strip()

    if not max_stripped.isdigit():
        print("Invalid input. Ending game")
    else:
        max_guesses = int(max_stripped)

        if max_guesses < 1:
            print("Invalid input. Ending game")
        else:
            k = 1
            total_guesses = 0
            won = False
            invalid_guess = False

            while k <= max_guesses:
                guess_raw = input(f"Guess {k} of {max_guesses}: ")
                guess_stripped = guess_raw.strip()

                if not guess_stripped.isdigit():
                    print("Invalid input. Ending game.")
                    invalid_guess = True
                    break

                guess_val = int(guess_stripped)
                total_guesses += guess_val
                avg = total_guesses / k

                if guess_val > secret:
                    print("Too high.")
                    print(f"Average guess so far: {avg:.2f}")

                elif guess_val < secret:
                    print("Too low.")
                    print(f"Average guess so far: {avg:.2f}")

                else:
                    print(f"You got it! Guesses used: {k}")
                    print(f"Average guess so far: {avg:.2f}")
                    won = True
                    break

            k += 1

        if not won and not invalid_guess:
            print(f"Out of guesses. The numnber was {secret}.")
