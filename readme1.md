import java.util.Scanner;
class BankAccount 
{
    double balance;
    public BankAccount(double initialBalance)
    {
        this.balance=initialBalance;
    }
    public double getBalance()
    {
        return balance;
    }
    public void deposit(double amount) 
    {
        balance+=amount;
    }
    public boolean withdraw(double amount) 
    {
        if (amount<=balance) 
        {
            balance-=amount;
            return true;
        } else 
        {
            System.out.println("Insufficient cash Withdrawal failed.");
            return false;
        }
    }
}
class ATM 
{
    private BankAccount bankAccount;
    private Scanner scanner;
    public ATM(BankAccount bankAccount)
    {
        this.bankAccount=bankAccount;
        this.scanner=new Scanner(System.in);
    }
    public void displayMenu()
    {
        System.out.println("Welcome to the ATM!");
        System.out.println("1.Withdraw");
        System.out.println("2.Deposit");
        System.out.println("3.Check Balance");
        System.out.println("4.Exit");
    }
    public void processOption(int option)
    {
        switch(option) 
        {
            case 1:
                handleWithdrawal();
                break;
            case 2:
                handleDeposit();
                break;
            case 3:
                checkBalance();
                break;
            case 4:
                System.out.println("Thank you for using the ATM.");
                System.exit(0);
                break;
            default:
                System.out.println("Invalid option. Please try again.");
        }
    }
    private void handleWithdrawal()
    {
        System.out.println("Enter the amount to withdraw:");
        double amount=scanner.nextDouble();
        if (amount>0) 
        {
            if (bankAccount.withdraw(amount)) 
            {
                System.out.println("Withdrawal successful. Remaining balance:"+bankAccount.getBalance());
            }
        } 
        else
        {
            System.out.println("Invalid amount. Withdrawal failed.");
        }
    }
    private void handleDeposit()
    {
        System.out.println("Enter the amount to deposit: ");
        double amount=scanner.nextDouble();
        if (amount>0)
        {
            bankAccount.deposit(amount);
            System.out.println("Deposit successful. New balance:"+bankAccount.getBalance());
        } else {
            System.out.println("Invalid amount. Deposit failed.");
        }
    }
    private void checkBalance() 
    {
        System.out.println("Current balance:"+bankAccount.getBalance());
    }

    public static void main(String[] args)
    {
        BankAccount userAccount=new BankAccount(1000.0); 
        ATM atm=new ATM(userAccount);
        while (true)
        {
            atm.displayMenu();
            System.out.println("Enter your choice (1-4):");
            int choice=atm.scanner.nextInt();
            atm.processOption(choice);
        }
    }
}
