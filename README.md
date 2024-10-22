#include <iostream>
#include <string>
using namespace std;

class BankAccount {
private:
    string accountNumber; // Private member variable for account number
    double balance;       // Private member variable for balance

public:
    // Constructor that initializes the account number and sets balance to 0
    BankAccount(string accNum) {
        accountNumber = accNum;
        balance = 0.0;
    }

    // Method to deposit an amount to the balance
    void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            cout << "Deposited: Ksh " << amount << ". New balance: Ksh " << balance << endl;
        } else {
            cout << "Invalid deposit amount!" << endl;
        }
    }

    // Method to withdraw an amount from the balance, ensuring it doesn't go below zero
    void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            cout << "Withdrew: Ksh " << amount << ". Remaining balance: Ksh " << balance << endl;
        } else if (amount > balance) {
            cout << "Insufficient balance!" << endl;
        } else {
            cout << "Invalid withdrawal amount!" << endl;
        }
    }

    // Method to get the current balance
    double getBalance() const {
        return balance;
    }
};

int main() {
    // Create a new BankAccount object
    BankAccount account("1234567890");

    // Perform some transactions
    account.deposit(5000);  // Deposit Ksh 5000
    account.withdraw(2000); // Withdraw Ksh 2000
    account.withdraw(4000); // Attempt to withdraw Ksh 4000 (should show insufficient balance)

    // Display final balance
    cout << "Final Balance: Ksh " << account.getBalance() << endl;

    return 0;
}
