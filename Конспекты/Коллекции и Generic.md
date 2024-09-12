## **Что такое дженерики?**

Generic в Java представляют собой особые средства программирования которые позволяют не приводить типы данных явно и работать с различными типами данных одновременно.
Простым языком они могут использоваться в классах, интерфейсах и методах и позволяют принимать нам любой тип данных.

При создании классов, интерфейсов, методов с использованием Generic нам необходимо использовать спец. символ `<T>` или любую другую букву.

```
public class Box<T> {  
    private T value;  
     
    public void set(T value) {  
        this.value = value;  
    }  
     
    public T get() {  
        return value;  
    }  
}
```

В данном случае у нас имеется класс `Box<T>` который может хранить объект с любым типом данных. Этот тип будет определен при создании объекта.

##### **Дженерики решают проблему безопасности типов и повторяемости кода.**

Так же можно ограничивать типы Дженериков `<T extends Account>`
В данном случае мы ограничили использование только классом `Account` и его подтипами.

```
public class Main {  
    public static void main(String[] args) {  
        Account account1 = new Account(1234);  
        Account account2 = new Account(5678);  
        account1.setBalance(35);  
  
        Transaction<Account> tran1 = new Transaction<Account>(account1,account2,10);  
        tran1.execute();  
  
  
    }  
}  
  
class Transaction<T extends Account>{  
    private T from;  
    private T to;  
    private int amount;  
  
    public Transaction(T from, T to, int amount) {  
        this.from = from;  
        this.to = to;  
        this.amount = amount;  
    }  
  
    public void execute(){  
        if (from.getBalance() >= amount){  
            from.setBalance(from.getBalance() - amount);  
            System.out.println("Транзакция на счет " + to.getAccountNumber() + " совершена! Остаток на балансе " + from.getBalance());  
  
        }else{  
            System.out.println("Insufficient Balance");  
        }  
    }  
  
}  
  
class Account{  
    private int balance;  
    public int AccountNumber;  
  
    public Account(int accountNumber) {  
        this.AccountNumber = accountNumber;  
    }  
  
    public void setBalance(int balance) {  
        this.balance = balance;  
    }  
  
    public int getAccountNumber() {  
        return AccountNumber;  
    }  
  
    public int getBalance() {  
        return balance;  
    }  
}
```

