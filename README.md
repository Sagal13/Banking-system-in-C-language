# Food ordering Application in C
#include <stdio.h>
#include <stdlib.h>

// Define the structure for a food item
typedef struct {
    char name[50];
    float price;
} FoodItem;

// Function to display the menu
void displayMenu(FoodItem menu[], int size) {
    printf("Menu:\n");
    for (int i = 0; i < size; i++) {
        printf("%d. %s - $%.2f\n", i + 1, menu[i].name, menu[i].price);
    }
    printf("\n");
}

// Function to place an order
void placeOrder(FoodItem menu[], int size) {
    int choice;
    int quantity;
    float totalCost = 0;

    printf("Enter the item number to order (0 to finish): ");
    scanf("%d", &choice);

    while (choice != 0) {
        if (choice < 1 || choice > size) {
            printf("Invalid choice. Please try again.\n");
        } else {
            printf("Enter the quantity: ");
            scanf("%d", &quantity);

            totalCost += menu[choice - 1].price * quantity;

            printf("Added %d %s to your order.\n", quantity, menu[choice - 1].name);
        }

        printf("Enter the item number to order (0 to finish): ");
        scanf("%d", &choice);
    }

    printf("\nTotal Cost: $%.2f\n", totalCost);
}

int main() {
    // Define the menu
    FoodItem menu[] = {
        {"Burger", 5.99},
        {"Pizza", 8.99},
        {"Pasta", 6.99},
        {"Salad", 4.99},
        {"Soda", 1.99}
    };

    int menuSize = sizeof(menu) / sizeof(menu[0]);

    printf("Welcome to the Food Ordering Application!\n\n");

    while (1) {
        printf("Options:\n");
        printf("1. Display Menu\n");
        printf("2. Place an Order\n");
        printf("3. Exit\n");

        int choice;
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                displayMenu(menu, menuSize);
                break;
            case 2:
                placeOrder(menu, menuSize);
                break;
            case 3:
                printf("Thank you for using the Food Ordering Application. Goodbye!\n");
                exit(0);
            default:
                printf("Invalid choice. Please try again.\n");
        }
    }

    return 0;
}


