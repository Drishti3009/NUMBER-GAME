# NUMBER-GAME
# 🎲 Number Guessing Game (Java)  A simple Java-based Number Guessing Game where the computer generates a random number between 1 and 100, and the player has 5 attempts to guess it. The game includes scoring, input validation, and replay options.   ## 🚀 Features - Random number generation (1–100) - Maximum of 5 attempts per round .

import java.util.Random;
import java.util.Scanner;

public class Task1 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int totalScore = 0;

        do {
            int attempts = 0;
            final int MAX_ATTEMPTS = 5;
            int generatedNumber = random.nextInt(100) + 1;
            System.out.println("A random number between 1 and 100 has been generated.");
            boolean correctGuess = false;

            while (attempts < MAX_ATTEMPTS && !correctGuess) {
                System.out.print("Enter your guess (Attempt " + (attempts + 1) + "/" + MAX_ATTEMPTS + "): ");
                int userGuess = 0;

                boolean validInput = false;
                while (!validInput) {
                    try {
                        userGuess = scanner.nextInt();
                        validInput = true; // Valid input received
                    } catch (Exception e) {
                        System.out.println("Please enter a valid integer.");
                        scanner.next(); // Clear the invalid input
                    }
                }
                
                attempts++;

                if (userGuess == generatedNumber) {
                    correctGuess = true;
                    System.out.println("Congratulations! You've guessed the correct number: " + generatedNumber);
                } else if (userGuess < generatedNumber) {
                    System.out.println("Too low!");
                } else {
                    System.out.println("Too high!");
                }
            }

            if (!correctGuess) {
                System.out.println("Sorry, you've reached the maximum attempts. The number was: " + generatedNumber);
            } else {
                totalScore += (MAX_ATTEMPTS - attempts + 1); // scoring based on attempts
            }

            System.out.print("Do you want to play again? (yes/no): ");
        } while (scanner.next().equalsIgnoreCase("yes"));

        System.out.println("Your total score is: " + totalScore);
        scanner.close();
    }
}
