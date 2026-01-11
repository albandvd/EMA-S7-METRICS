# Metrics Exercice 1 

## Compilation

``` bash
# Compilation avec maven 
…/BankApplication/jay-bank master ? ❯ mvn compile

…/BankApplication/jay-bank master ? ❯ tree
.
├── pom.xml
├── src
│   ├── main
│   │   └── java
│   │       └── bankAccountApp
│   │           ├── ACHServiceImpl.java
│   │           ├── ACHService.java
│   │           ├── BankAccountApp.java
│   │           ├── BankAccount.java
│   │           ├── Bank.java
│   │           └── Person.java
│   └── test
│       └── java
│           └── bankAccountApp
│               ├── ACHServiceTest.java
│               ├── AllTests.java
│               ├── BankAccountTest.java
│               ├── BankTest.java
│               └── PersonTest.java
└── target
    ├── classes
    │   └── bankAccountApp
    │       ├── ACHService.class
    │       ├── ACHServiceImpl.class
    │       ├── BankAccountApp.class
    │       ├── BankAccount.class
    │       ├── Bank.class
    │       └── Person.class
    ├── generated-sources
    │   └── annotations
    └── maven-status
        └── maven-compiler-plugin
            └── compile
                └── default-compile
                    ├── createdFiles.lst
                    └── inputFiles.lst

17 directories, 20 files
```

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

bankAccountApp.BankAccountApp 2 1 0 3 36 1 0 3 2 2.0000 491 0.0000 0 0.0000 0.5000 0 0 244.5000
 ~ public static void main(String[] args): 40
 ~ public void <init>(): 1

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

| Class | LOC (approx.) | NOM | Short description of responsibility |
|-------|---------------|-----|--------------------------------------|
| Bank | 413 | 14 | Manages bank accounts collection, performs operations like find, delete, add accounts, and calculates statistics (average, max, min balance) |
| BankAccount | 477 | 21 | Represents a bank account with holder info, balance, and withdrawal limit; handles deposits and withdrawals |
| Person | 325 | 23 | Represents a person with personal attributes (name, gender, age, height, weight, hair color, eye color, email); includes validation and getters/setters |
| BankAccountApp | 491 | 2 | Main application class that provides the user interface and orchestrates interactions between Bank and BankAccount objects |

## Do you feel its size roughly matches its responsibility?

The size of the classes does not always match their responsibilities.
While the Bank class is reasonably sized for managing a collection of accounts, the BankAccount and Person classes appear large for domain entities and may contain too much validation or auxiliary logic.
The BankAccountApp class is clearly oversized, with a high number of lines of code concentrated in very few methods, suggesting poor separation of concerns.