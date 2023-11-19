# internship-task
//codsoft task 1 for number guessing game
//program written by Sapana Jagtap

import java.util.Random;
import java.util.Scanner;

class NumberGuessingGame {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        int rangeStart = 1;
        int rangeEnd = 100;
        int maxAttempts = 5;
        int score = 0;

        boolean playAgain = true;

        while (playAgain) {
            int targetNumber = random.nextInt(rangeEnd - rangeStart + 1) + rangeStart;
            int attempts = 0;
            boolean correctGuess = false;
            System.out.println("welcome to the Number Guessing Game!")
            System.out.println("choose your number between " + rangeStart + " and " + rangeEnd + ".");
            System.out.println("You have " + maxAttempts + " attempts to guess the number.");

            while (attempts < maxAttempts && ! correctGuess) {
                System.out.print("Enter your guess: ");
                int guess = scanner.nextInt();

                if (guess == targetNumber) {
                    System.out.println("Congratulations! You guessed the correct number.");
                    correctGuess = true;
                    score++;
                } else if (guess < targetNumber) {
                    System.out.println("Too low! Try again.");
                } else {
                    System.out.println("Too high! Try again");
                }

                attempts++;
            }

            if (!correctGuess) {
                System.out.println("Sorry, you have run out of attempts. The correct number was " + targetNumber + ".");
            }

            System.out.print("Play again? (1 for yes, 0 for no): ");
            int playChoice = scanner.nextInt();
            if (playChoice == 0) {
                playAgain = false;
            }
        }

        System.out.println("Your final score is: " + score);
        scanner.close();
    }
}
