# codsoft-Task01

import java.util.Random;
import java.util.Scanner;
public class GuessingGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int numberOfRounds = 0;
        int numberOfWins = 0;
        int totalAttempts = 0;
        while (true) {
            int numberToGuess = random.nextInt(100) + 1;
            int numberOfAttempts = 0;
            boolean won = false;

            while (numberOfAttempts < 10) {
                System.out.println("Guess a number between 1 and 100:");
                int guess = scanner.nextInt();
                numberOfAttempts++;

                if (guess < numberToGuess) {
                    System.out.println("Too low!");
                } else if (guess > numberToGuess) {
                    System.out.println("Too high!");
                } else {
                    System.out.println("Correct! You won in " + numberOfAttempts + " attempts.");
                    won = true;
                    numberOfWins++;
                    break;
                }
            }

            if (!won) {
                System.out.println("You didn't guess the number. The number was " + numberToGuess + ".");
            }

            System.out.println("Do you want to play again? (yes/no)");
            String playAgain = scanner.next();

            if (playAgain.equalsIgnoreCase("no")) {
                break;
            }

            numberOfRounds++;
            totalAttempts += numberOfAttempts;
        }

        scanner.close();

        System.out.println("Game over!");
        System.out.println("Total rounds: " + numberOfRounds);
        System.out.println("Total wins: " + numberOfWins);
        System.out.println("Total attempts: " + totalAttempts);
    }
}
