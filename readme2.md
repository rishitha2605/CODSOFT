import java.util.Random;
import java.util.Scanner;
public class NumberGuessingGame 
{
    public static void main(String[] args)
    {
        Scanner s=new Scanner(System.in);
        Random random=new Random();
        int lowerBound=1;
        int upperBound=100;
        int n=10;
        int score=0;
        System.out.println("Welcome to the Number Guessing Game!");
        System.out.println("I have selected a number between"+lowerBound+" and " +upperBound+".");
        do 
        {
            int targetNumber=random.nextInt(upperBound-lowerBound+1)+ lowerBound;
            int attemptsLeft = n;
            System.out.println("You have " +attemptsLeft+ "attempts to guess the number.");
            while (attemptsLeft>0)
            {
                System.out.println("Enter your guess: ");
                int userGuess=s.nextInt();
                if (userGuess==targetNumber)
                {
                    System.out.println("Congratulations! You guessed the correct number.");
                    score+=attemptsLeft;
                    break;
                } else if (userGuess<targetNumber) 
                {
                    System.out.println("Too low. Try again.");
                } else 
                {
                    System.out.println("Too high. Try again.");
                }
                attemptsLeft--;
                System.out.println("Attempts left:"+attemptsLeft);
            }
            if (attemptsLeft==0)
            {
                System.out.println("Sorry,you've run out of attempts.The correct number was:"+targetNumber);
            }
            System.out.println("Your current score: "+score);
            System.out.println("Do you want to play again? (yes/no):");
        } 
        while (s.next().equalsIgnoreCase("yes"));
        System.out.println("Thanks for playing! Your final score:"+score);
        s.close();
    }
}
