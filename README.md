import java.util.Scanner;
import java.util.Random;

public class NumberGuessingGame1 {
    public static void main(String[] args) {
        Random rand = new Random();
        Scanner sc = new Scanner(System.in);
        boolean playAgain = true;
        int totalScore = 0;

        System.out.println("WELCOME! Enjoy this game.");

        while (playAgain) {
            int randomNumber = rand.nextInt(100) + 1; // Random number between 1 and 100
            int attempts = 0;
            int maxAttempts = 10;
            boolean hasWon = false;

            System.out.println("I have picked a number between 1 and 100. Try to guess it!");

            while (attempts < maxAttempts && !hasWon) {
                System.out.print("Enter your guess: ");
                int playerGuess = sc.nextInt();
                attempts++;

                if (playerGuess < 1 || playerGuess > 100) {
                    System.out.println("Please guess a number between 1 and 100.");
                } else if (playerGuess > randomNumber) {
                    System.out.println("Nope! The number is higher. Guess again.");
                } else if (playerGuess < randomNumber) {
                    System.out.println("Nope! The number is lower. Guess again.");
                } else {
                    hasWon = true;
                    totalScore++;
                    System.out.println("Correct! You guessed the number in " + attempts + " tries.");
                }

                if (attempts == maxAttempts && !hasWon) {
                    System.out.println("Sorry, you've used all your attempts. The number was: " + randomNumber);
                }
            }

            System.out.println("\nScoreboard:");
            System.out.println("Total rounds played: " + totalScore);
            System.out.println("Total attempts this round: " + attempts);
            System.out.println("Total correct guesses: " + totalScore);

            System.out.print("Do you want to play again? (yes/no): ");
            String response = sc.next();
            playAgain = response.equalsIgnoreCase("yes");
        }

        System.out.println("Thanks for playing! Your final score: " + totalScore);
        sc.close();
    }
}

