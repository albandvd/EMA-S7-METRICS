# Metrics Exercice 2

## BankAccount Metrics

```bash 
…/BankApplication/jay-bank master ? ❯ java -jar ~/Downloads/ckjm_ext.jar target/classes/bankAccountApp/BankAccount.class
bankAccountApp.BankAccount 20 1 0 2 43 44 0 2 18 0.6908 462 1.0000 0 0.0000 0.2917 0 0 21.7000
 ~ public void setWithdrawLimit(double withdrawLimit): 1
 ~ public void <init>(int accountNumber, double balance, double withdrawLimit, String dateCreated, String accountHolder): 1
 ~ public String convertToText(bankAccountApp.BankAccount tmp): 1
 ~ public void setAccountHolder(bankAccountApp.Person accountHolder): 2
 ~ public double getBalance(): 1
 ~ public int getAccountNumber(): 1
 ~ public void <init>(double newInitMoneyAmount, double newWithdrawlimit, String newDateCreated, bankAccountApp.Person initHolder): 1
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
 ~ public boolean withdrawMoney(double withdrawAmount): 5
```

## withdrawMoney cyclomatic complexity value

```
 ~ public boolean withdrawMoney(double withdrawAmount): 5
```

## withdrawMoney Code:

```java
public boolean withdrawMoney(double withdrawAmount) {
    // Decision point 1: if condition (compound boolean expression)
    if (withdrawAmount >= 0               // decision: comparison
        && balance >= withdrawAmount       // decision: comparison
        && withdrawAmount < withdrawLimit  // decision: comparison
        && withdrawAmount + amountWithdrawn <= withdrawLimit) { // decision: comparison
        balance = balance - withdrawAmount;
        success = true;
        amountWithdrawn += withdrawAmount;
    } else { // Decision point 2: else branch
        success = false;
    }
    return success;
}
```

The high cyclomatic complexity comes from multiple conditions in a single if, because each condition adds a potential decision path the program could take.To improve readability and reduce perceived complexity, the validation logic can be extracted into a helper method. This helper would encapsulate all withdrawal checks and give them a meaningful name. 

### Refactored code

```java
	private boolean WithdrawPossible(double withdrawAmount) {
		return withdrawAmount >= 0 &&
			   balance >= withdrawAmount &&
			   withdrawAmount + amountWithdrawn <= withdrawLimit;
	}

	public boolean withdrawMoney(double withdrawAmount) {
		if (WithdrawPossible(withdrawAmount)) { // Decision point 1: if
			balance -= withdrawAmount;
			amountWithdrawn += withdrawAmount;
			return true;
		}
		return false;
	}
```

### Cyclomatic complexity after refactoring

```
 ~ private boolean WithdrawPossible(double withdrawAmount): 4
 ~ public boolean withdrawMoney(double withdrawAmount): 2
```

Even though the cyclomatic complexity of withdrawMoney did not decrease numerically, the method is now simpler, clearer, and easier to maintain.