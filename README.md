# GameofSnake
This is a simple two-player console-based Snake Dice Game written in Java. The game simulates dice rolls and uses basic snake game rules. The first player to reach a score of 100 wins the game — but beware of snake bites that can reset your progress!
import java.util.Scanner;
import java.util.Random;

public class GameofSnake {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Random rand = new Random();

        int player1Score = 0;
        int player2Score = 0;
        int currentPlayer = 1;

        System.out.println("🎲 Welcome to the Game of Snake!");
        System.out.println("Snake positions: 33, 66, 99");

        while (true) {
            System.out.println("\nPlayer " + currentPlayer + ", press Enter to roll the dice...");
            sc.nextLine();

            int dice = rand.nextInt(6) + 1;
            System.out.println("Player " + currentPlayer + " rolled: " + dice);

            if (currentPlayer == 1) {
                player1Score += dice;

                if (player1Score == 33 || player1Score == 66 || player1Score == 99) {
                    player1Score = 0;
                    System.out.println("🐍 Snake bite! Player 1 score reset to 0.");
                }

                if (player1Score >= 100) {
                    System.out.println("🎉 Player 1 wins with score: " + player1Score);
                    break;
                }
            } else {
                player2Score += dice;

                if (player2Score == 33 || player2Score == 66 || player2Score == 99) {
                    player2Score = 0;
                    System.out.println("🐍 Snake bite! Player 2 score reset to 0.");
                }

                if (player2Score >= 100) {
                    System.out.println("🎉 Player 2 wins with score: " + player2Score);
                    break;
                }
            }

            System.out.println("Current Scores => Player 1: " + player1Score + " | Player 2: " + player2Score);

            currentPlayer = (currentPlayer == 1) ? 2 : 1; // Switch player
        }

        sc.close();
    }
}
