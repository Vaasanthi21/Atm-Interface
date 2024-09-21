# Atm-Interface
import java.util.*;
interface Atm
{
     void withdrawing(int amount);
     void depositing(int amount);
     int Checkbalance();
}
class AtmInterface implements Atm
{
    private int balance;
    AtmInterface(int balance)
    {
        this.balance=balance;
    }
    public void withdrawing(int amount)
    {
        int balance=Checkbalance();
        if(balance<=1500)
        {
            System.out.println("Insufficient Balance Cannot be Withdrawl");
        }
        else
        {
            balance=balance-amount;
            System.out.print("The amount $ "+ amount + " has been withdrawn and The Balance is: " + balance);
        }
    }
    public void depositing(int amount)
    {
        int balance=Checkbalance();
        balance=balance+amount;
        System.out.println("The amount $ " + amount +" has been Deposited and The Balance is:" + balance);
    }
    public int Checkbalance(){
        return balance;
    }
    
    
}
class Main{
    public static void main(String[] args)
    {
        System.out.println("Welcome To the Atm Interface......");
        Scanner v=new Scanner(System.in);
        int balance=1500;
        AtmInterface a=new AtmInterface(balance);
        boolean Continue=true;
        int amount;
        while(Continue)
        {
            System.out.println("Enter The Option that you want to Perform:");
            System.out.println("1.WithDrawl\n2.Deposit\n3.Check Balance");
            int option=v.nextInt();
            switch(option)
            {
                case 1:
                {
                        System.out.println("Enter the Amount you want to Withdraw:");
                        amount=v.nextInt();
                        a.withdrawing(amount);
                        break;
                }
                case 2:
                {
                        System.out.println("Enter the Amount you want to deposit:");
                        amount=v.nextInt();
                        a.depositing(amount);
                        break;
                }
                case 3:
                {
                        a.Checkbalance();
                        System.out.println("The Balance is:" + balance);
                        break;
                }
                default :
                {
                    System.out.println("Choose Valid Option");
                    break;
                }
            }
            System.out.println("Do you Want To continue(Yes/No):");
            String m=v.next();
            Continue=m.equalsIgnoreCase("Yes");
        }
       
    }
}
