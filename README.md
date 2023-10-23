# Bank-Application
Java code for showing and preforming transactions in Bank Application
import java.util.*;
public class Main{
    public static void main(String args[]){
        Scanner sc=new Scanner(System.in);
        BankAccount bank1 = new BankAccount("RAM","01");
        bank1.showMenu();
    }
}
 class BankAccount{
    int balance;
    int prevtransac;
    String customerName;
    String customerId;
    BankAccount(String cname,String cid){
        customerName=cname;
        customerId=cid;
    }
    void deposit(int amount){
        if(amount!=0){
            balance=balance+amount;
            prevtransac=amount;
        }
    }
    void withdraw(int amount){
        if(amount<balance){
            balance=balance-amount;
            prevtransac=-amount;
        }
        else if(amount>balance){
            System.out.println("Insufficient amount:");
        }
        else{
            System.out.println("no balance in the account");
        }
    }
    void getPreviousTransaction(){
        if(prevtransac>0){
            System.out.println("Deposited:"+prevtransac);
        }
        else if(prevtransac<0){
            System.out.println("withdrawn:"+Math.abs(prevtransac ));
        }
        else{
            System.out.println("no transaction is occured!");
        }
    }
    void showMenu(){
        char option = '\0';
        Scanner sc=new Scanner(System.in);
        System.out.println("welcome"+customerName);
        System.out.println("your ID is:"+customerId);
        System.out.println(" ");
        System.out.println("A.Check Balance");
        System.out.println("B.Deposit");
        System.out.println("C.Withdraw");
        System.out.println("D.previous transaction");
         System.out.println("E.Exit");
         
        do{
             System.out.println("========");
              System.out.println("enter the option:");
               System.out.println("========");
            option = sc.next().charAt(0);
            Character.toUpperCase(option);
            switch(option){
                case 'A':
                     System.out.println("=========");
                      System.out.println("Balance is:"+balance);
                     
                       System.out.println("========");
                      System.out.println();
                      break;
                case 'B':
                     System.out.println("========");
                      System.out.println("Enter the amount to deposit");
                       System.out.println("==========");
                       int amount=sc.nextInt();
                       deposit(amount);
                       System.out.println();
                       break;
                case 'C':
                     System.out.println("======");
                      System.out.println("enter the amount to withdraw");
                       System.out.println("=====");
                       int amount2=sc.nextInt();
                       withdraw(amount2);
                       System.out.println();
                       break;
                case 'D':
                     System.out.println("======");
                     getPreviousTransaction();
                       System.out.println("=====");
                       System.out.println();
                       break;
                case 'E':
                    System.out.println("======");
                    break;
                default:
                    System.out.println("invalid option!please try again");
            
            }
        }
        while(option!='E'); 
        
    }
    }
