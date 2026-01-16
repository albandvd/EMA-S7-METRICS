# Metrics Exercice 3

## SonarQube Analyse 

```
Found 143 issues in 13 files
```

### Issue 1 

Rule name: Change his "try" to try-with-ressources
File and line: Bank.java: 144
Explaination: SonarQube reports this issue because the file streams are not managed using try-with-resources, which can lead to resource leaks and makes the code less safe and harder to maintain.
Fixed code: 

```java
try (FileOutputStream fos = new FileOutputStream(
         "C:\\Users\\jay4k\\Desktop\\stuff\\Bankaccountinfo\\BankAccountinfotext.text");
     OutputStreamWriter osw = new OutputStreamWriter(fos)) {

    for (int i = 0; i < Accounts.size(); i++) {
        BankAccount tmp = Accounts.get(i);
        osw.write(tmp.convertToText(tmp));
    }

} catch (IOException e) {
    System.out.println("Error writing to file");
}
```

### Issue 2 

Rule name: Define a constant insted of duplicating this literal "BALANCE" 3 times
File and line: BankAccountApp.java: 92
Explaination: This issue means the same string literal ("BALANCE") is hard-coded multiple times, which should be replaced by a single constant to avoid duplication errors and make future changes easier.
Fixed code: 
``` java
    // Define the constant
    private static final String CMD_BALANCE = "BALANCE";

    ...

    if (operation.equalsIgnoreCase(CMD_BALANCE)) {
        System.out.println("Balance is: " + acc1.getBalance());
    }

    ... 

    if (operation.equalsIgnoreCase(CMD_BALANCE)) {
        System.out.println("Enter Account Number");
        number = scan.nextInt();
        BankAccount tmpacc = accManager.findAccount(number);
        if (tmpacc == null) {
            System.out.println("Account doesn't exist");
        } else {
            System.out.println("Balance is: " + tmpacc.getBalance());
        }
    }

    ...

    if (!operation.equalsIgnoreCase(CMD_BALANCE) && !operation.equalsIgnoreCase(CMD_DEPOSIT) && !operation.equalsIgnoreCase(CMD_WITHDRAW)) {
        System.out.println("Invalid Command, please try again");
    }
```

### Issue 3

Rule name: Make the enclosing method "static" or remove this set.
File and line: PersonTest.java: 30
Explaination: SonarQube raises this issue because a non-static @Before method modifies static fields, creating shared state between tests; the fix is to remove static from the test fields to ensure proper test isolation.

## Do SonarLint issues appear more often in the classes with higher WMC / CBO you saw earlier, or not really?

SonarLint issues tend to appear more often in classes with higher WMC and CBO.
Classes with high WMC usually contain more complex logic, which increases the chance of code smells.
High CBO indicates strong coupling, often leading to design and maintainability issues flagged by SonarLint. Lower WMC/CBO classes generally show fewer or more minor issues.
