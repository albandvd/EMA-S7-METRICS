# Metrics Exercice 3

## CK Metrics plugin

``` bash
…/BankApplication/jay-bank master ? ❯ java -jar ~/Downloads/ckjm_ext.jar target/classes/bankAccountApp/*.class

bankAccountApp.BankAccount 21 1 0 3 44 46 2 2 18 0.6875 477 1.0000 1 0.0000 0.2937 0 0 21.3333
 ~ public void setWithdrawLimit(double withdrawLimit): 1
 ~ public void <init>(int accountNumber, double balance, double withdrawLimit, String dateCreated, String accountHolder): 1
 ~ public String convertToText(bankAccountApp.BankAccount tmp): 1
 ~ public void setAccountHolder(bankAccountApp.Person accountHolder): 2
 ~ public double getBalance(): 1
 ~ public int getAccountNumber(): 1
 ~ public void <init>(double newInitMoneyAmount, double newWithdrawlimit, String newDateCreated, bankAccountApp.Person initHolder): 1
 ~ private boolean isWithdrawalValid(double withdrawAmount): 5
 ~ public String getDateCreated(): 1
 ~ public String toString(): 1
 ~ public void depositMoney(double depositAmount): 2
 ~ public double getInitMoneyAmount(): 1
 ~ public double getWithdrawLimit(): 1
 ~ private void setDateCreated(String dateCreated): 1
 ~ public double getAmountWithdrawn(): 1
 ~ public int loadFromText(String text): 8
 ~ public void <init>(): 1
 ~ public void setAccountNumber(int accNumber): 1
 ~ private void setBalance(double balance): 1
 ~ public bankAccountApp.Person getAccountHolder(): 1
 ~ public boolean withdrawMoney(double withdrawAmount): 2

bankAccountApp.Person 23 1 0 3 39 79 3 0 21 0.7626 325 0.8889 0 0.0000 0.3565 0 0 12.7391
 ~ public void <init>(String accountHolder): 3
 ~ public void <init>(String newName, char newGender, int newAge, float newHeight): 1
 ~ public float getWeight(): 1
 ~ public void setAge(int newAge): 2
 ~ public String getEyeColor(): 1
 ~ public void setName(String newName): 1
 ~ public String getName(): 1
 ~ private void validate(): 1
 ~ public String getEmail(): 1
 ~ public void setEmail(String email): 1
 ~ public void setHairColor(String newHairColor): 5
 ~ public void setWeight(float newWeight): 1
 ~ public String getHairColor(): 1
 ~ public String toString(): 1
 ~ public void setHeight(float height): 1
 ~ public int getAge(): 1
 ~ public void <init>(String newName, char newGender, int newAge, float newWeight, float newHeight, String newHairColor, String newEyeColor, String newEmail): 1
 ~ public void setGender(char newGender): 2
 ~ public char getGender(): 1
 ~ public void setEyeColor(String newEyeColor): 1
 ~ private boolean validateGender(char value): 5
 ~ public void <init>(): 1
 ~ public float getHeight(): 1

bankAccountApp.Bank 14 1 0 4 44 0 2 3 12 0.8333 413 1.0000 0 0.0000 0.3286 0 0 28.0714
 ~ public double getMinimumBalance(): 4
 ~ public void saveAccounts(bankAccountApp.Bank accManager): 8
 ~ public boolean registerAccount(int fromAccountNumber, int fromRoutingNumber, int destinationBank, int toAccountNumber): 1
 ~ public double getMaximumBalance(): 3
 ~ public void deleteAccount(int accountNumber): 3
 ~ public String convertToText(): 2
 ~ public int addAccount(bankAccountApp.BankAccount acc, int isLoadAccount): 4
 ~ protected int getAccountsLoaded(): 1
 ~ public java.util.ArrayList getAccounts(): 1
 ~ public boolean transferAmount(int fromAccountNumber, int fromRoutingNumber, int destinationBank, int toAccountNumber, float amount): 1
 ~ public bankAccountApp.BankAccount findAccount(int accountNumber): 4
 ~ public double getAverageBalance(): 2
 ~ public void <init>(): 1
 ~ protected void setAccountsLoaded(int accountsLoaded): 1
```

| Class | LOC | WMC | CBO | LCOM | 
|-------|-----|-----|-----|------| 
| Bank | 413 | 14 | 3 | 0 | 
| BankAccount | 477 | 21 | 2 | 46 | 
| Person | 325 | 23 | 0 | 79 | 

## Which class has the highest WMC?

Person

## Which class has the highest CBO?

Bank

## Looking at WMC + CBO + LCOM together which one class would you worry about most for future maintenance, and why?

The Person class is the most concerning for maintenance because it has a high WMC and an extremely high LCOM, indicating complex behavior with very low cohesion.