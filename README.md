import java.util.Scanner;
interface BankAccount 
{
void deposit(double amount) throws Exception;
void withdraw(double amount) throws Exception;
void balanceEnquiry();
}
class Bank implements BankAccount 
{
double balance;
String accountHolderName;
int accountNumber;
public Bank(String accountHolderName, int accountNumber, double initialBalance) 
{
this.accountHolderName = accountHolderName;
this.accountNumber = accountNumber;
this.balance = initialBalance;
}
public void deposit(double amount) 
{
if (amount <= 0) 
{
throw new IllegalArgumentException("Invalid deposit amount");
}
balance = balance + amount;
System.out.println("Amount deposited succesfully");
}
public void withdraw(double amount) throws Exception 
{
if (amount <= 0) 
{
throw new Exception("Invalid withdrawal amount");
}
if (amount > balance) 
{
throw new Exception("Insufficient balance");
}
balance = balance - amount;
System.out.println("Amount withdrawn Successfully");
}
public void balanceEnquiry() 
{
System.out.println("Available balance:Rs." + balance);
}
}
class BankOperations 
{
public static void main(String args[]) 
{
Scanner sc = new Scanner(System.in);
System.out.print("Account holder name:");
String name = sc.nextLine();
System.out.print("Account number:");
int accNo = sc.nextInt();
System.out.print("Initial balance:");
double initBalance = sc.nextDouble();
sc.nextLine(); 
System.out.print("operation:");
String operation = sc.nextLine();
Bank b = new Bank(name, accNo, initBalance);
try 
{
if (operation.equalsIgnoreCase("Deposit")) 
{
System.out.print("Deposit amount:");
double d = sc.nextDouble();
b.deposit(d);
b.balanceEnquiry();
} 
else if (operation.equalsIgnoreCase("Withdraw")) 
{
System.out.print("Withdraw amount:");
double w = sc.nextDouble();
b.withdraw(w);
b.balanceEnquiry();
}
else 
{
System.out.println("Error: Invalid operation");
} 
}
catch (Exception e) 
{
System.out.println("Exception:" + e.getMessage());
System.out.println("Transaction failed");
b.balanceEnquiry();
} 
finally 
{
sc.close();
}
}
}
