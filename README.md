# Rock_Paper_ScissorGame
This game will allow you to choose one option among Rock, Paper &amp; Scissor and Computer also will take the input randomly. At first, users have to declare how many times they want to choose options in a round. By comparing the user's and computer's choices scores will be displayed for both.

import java.util.*;

public class RpS {
    public static void main(String[] args) {
        String[] options = {"Rock", "Paper", "Scissors"};
        Scanner in = new Scanner(System.in);
        Random rand = new Random();
        int times = 0;
        int score = 0;
        int comscore = 0;

        System.out.println(".............Welcome to Rock,Paper,Scissors Game!.............");
        System.out.print("How many times do you want to play in a round ? : ");
        int maxt = in.nextInt();
        System.out.println("You want to play " + maxt + " times in a round.");

        while (times < maxt) {
            // Display options
            System.out.println("Choose your move: ");
            for (int i = 0; i < options.length; i++) {
                System.out.println((i + 1) + ". " + options[i]);
            }
            // Get user's choice
            int userChoice = in.nextInt();
            if (userChoice < 1 || userChoice > 3) {
                System.out.println("Invalid choice!! Please choose a number between 1 and 3.");
                continue;
            }
            // Map user's choice to array index conversion
            String userMove = options[userChoice - 1];
            System.out.println("Your choice: " + userMove);
            // Generating computer's move
            int computerChoice = rand.nextInt(3);
            String computerMove = options[computerChoice];
            System.out.println("Computer's choice: " + computerMove);
            // Determine the winner
            if (userMove.equals(computerMove)) {
                System.out.println("It's a tie!");
            } else if ((userMove.equals("Rock") && computerMove.equals("Scissors")) ||
                    (userMove.equals("Paper") && computerMove.equals("Rock")) ||
                    (userMove.equals("Scissors") && computerMove.equals("Paper"))) {
                System.out.println("You win!");
                score++; //update player's new score
            } else {
                System.out.println("Computer wins!");
                comscore++; // update computer's score
            }
            times++;
            // if maxt and times became equal then it will print final score.
            if (times == maxt) {
                System.out.println("Your final score: " + score );
                System.out.println("Computer's final score: " + comscore );
                // Ask if the user wants to play again or not.
                System.out.println("Do you want to play again? (yes/no)");
                String playAgain = in.next().toLowerCase();
                if (!playAgain.equals("yes")) {
                    break;  // Exit the loop if the user does not want to play again
                } else {
                    times = 0;  // Reset the counter for a new round
                    System.out.println("Play for next round!");
                }
            }
        }
        in.close();
    }
}
