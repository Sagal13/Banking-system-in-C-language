# Banking-system-in-C-language
#include <stdio.h>

// Function to display the menu
void displayMenu() {
    printf("\n1. Create Account\n");
    printf("2. Deposit Money\n");
    printf("3. Withdraw Money\n");
    printf("4. Display Balance\n");
    printf("5. Exit\n");
}

// Function to create a new account
void createAccount(float *balance) {
    printf("Enter initial balance: ");
    scanf("%f", balance);
    printf("Account created successfully!\n");
}

// Function to deposit money
void depositMoney(float *balance) {
    float amount;
    printf("Enter deposit amount: ");
    scanf("%f", &amount);
    *balance += amount;
    printf("Deposit successful! Current balance: %.2f\n", *balance);
}

// Function to withdraw money
void withdrawMoney(float *balance) {
    float amount;
    printf("Enter withdrawal amount: ");
    scanf("%f", &amount);
    if (*balance >= amount) {
        *balance -= amount;
        printf("Withdrawal successful! Current balance: %.2f\n", *balance);
    } else {
        printf("Insufficient funds!\n");
    }
}

// Function to display account balance
void displayBalance(float balance) {
    printf("Your current balance: %.2f\n", balance);
}

int main() {
    float balance = 0;
    int choice;

    do {
        displayMenu();
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                createAccount(&balance);
                break;
            case 2:
                depositMoney(&balance);
                break;
            case 3:
                withdrawMoney(&balance);
                break;
            case 4:
                displayBalance(balance);
                break;
            case 5:
                printf("Exiting the program. Goodbye!\n");
                break;
            default:
                printf("Invalid choice. Please try again.\n");
        }
    } while (choice != 5);

    return 0;
}
