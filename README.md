import java.util.Scanner;
public class Grade 
{
    public static void main(String[] args)
     {
        Scanner s=new Scanner(System.in);
        System.out.print("Enter the number of subjects:");
        int n=s.nextInt();
        int[] m=new int[n];
        for (int i=0;i<n;i++)
         {
            System.out.print("Enter marks for subject"+(i+1)+":");
            m[i]=s.nextInt();
        }
        int tm= calculateTotalMarks(m);
        double ap= calculateAveragePercentage(tm,n);
        char grade = calculateGrade(ap);
        System.out.println("\nTotal Marks: "+tm);
        System.out.printf("Average Percentage: %.2f%%\n", ap);
        System.out.println("Grade: " + grade);
        s.close();
    }
    private static int calculateTotalMarks(int[] m)
     {
        int tm=0;
        for(int marks:m) 
        {
            tm+= marks;
        }
        return tm;
    }
    private static double calculateAveragePercentage(int tm, int n) {
        return (double)tm/n;
    }
    private static char calculateGrade(double ap) 
    {
        if (ap>= 90) 
        {
            return 'A';
        } else if (ap>= 80) 
        {
            return 'B';
        } else if (ap>= 70) 
        {
            return 'C';
        } else if (ap>= 60) 
        {
            return 'D';
        } else {
            return 'F';
        }
    }
}
