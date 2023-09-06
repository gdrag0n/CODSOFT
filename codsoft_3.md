
import java.util.Scanner;


public class ATMProgram
{
    public static void main(String[] args)
    {
        Acc user = new Acc(53748);
        //initializing private class Acc with balance
        
        Scanner sc = new Scanner(System.in);
        ATM atm = new ATM(user, sc);
        atm.run();
    }
}

class Acc
{
    private double bal;

    public Acc(double principal)
    {
        this.bal = principal;
    }

    public double balance()
    {
        return bal;
    }

    public void add(double amount)
    {
        if (amount > 0)
        {
            bal += amount;
        }

        else
        {
            System.out.println("Please Enter Valid Amount");
        }
    }

    public boolean minus(double amount)
    {
        if (amount > 0 && amount <= bal)
        {
            bal -= amount;
            return true;
        }

        else
        {
            System.out.println("Insufficient amount. Transaction Failed.");
            return false;
        }
    }
}

class ATM
{
    private Acc bankAcc;
    private Scanner sc;

    public ATM(Acc bankAcc, Scanner sc)
    {
        this.bankAcc = bankAcc;
        this.sc = sc;
    }

    public void atmFunc()
    {
        System.out.println("ATM Options:");
        System.out.println("1: Balance");
        System.out.println("2: Deposit");
        System.out.println("3: Withdrawal");
        System.out.println("4: Exit");
        System.out.print("Please select an option: ");
    }

    public void run()
    {
        while (true)
        {
            atmFunc();
            int button = sc.nextInt();
            sc.nextLine();  // consume the leftover newline

            switch (button)
                {
                case 1:
                    System.out.println("Your current balance is Rs. " + bankAcc.balance());

                    break;

                case 2:
                    System.out.print("Enter deposit amount: Rs. ");
                    double depAmnt = sc.nextDouble();
                    sc.nextLine();  // consume the leftover newline

                    bankAcc.add(depAmnt);

                    break;

                case 3:
                    System.out.print("Enter withdrawal amount: Rs. ");
                    double wdrwAmnt = sc.nextDouble();
                    sc.nextLine();  // consume the leftover newline

                    bankAcc.minus(wdrwAmnt);

                    break;

                case 4:
                    System.out.println("Thank you for using this ATM.");

                    return;

                default:
                    System.out.println("Invalid selection. Try Again.");
            }
        }
    }
}
