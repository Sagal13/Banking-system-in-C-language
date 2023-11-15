# Air Ticket Booking in C++
#include <iostream>
#include <string>

class Flight {
private:
    std::string flightNumber;
    std::string destination;
    int availableSeats;
    float ticketPrice;

public:
    // Constructor
    Flight(std::string number, std::string dest, int seats, float price)
        : flightNumber(number), destination(dest), availableSeats(seats), ticketPrice(price) {}

    // Function to display flight details
    void displayFlightDetails() {
        std::cout << "Flight Number: " << flightNumber << "\nDestination: " << destination
                  << "\nAvailable Seats: " << availableSeats << "\nTicket Price: $" << ticketPrice << "\n\n";
    }

    // Function to book a ticket
    void bookTicket() {
        if (availableSeats > 0) {
            std::cout << "Enter passenger name: ";
            std::string passengerName;
            std::cin.ignore(); // Clear the input buffer
            std::getline(std::cin, passengerName);

            std::cout << "Ticket booked successfully for " << passengerName << ". Enjoy your flight!\n\n";
            availableSeats--;
        } else {
            std::cout << "Sorry, no available seats for this flight.\n\n";
        }
    }
};

int main() {
    // Create instances of Flight class
    Flight flight1("F101", "New York", 50, 500.0);
    Flight flight2("F202", "London", 40, 600.0);
    Flight flight3("F303", "Tokyo", 30, 700.0);

    int choice;

    do {
        // Display menu
        std::cout << "1. Display Flight Details\n";
        std::cout << "2. Book a Ticket\n";
        std::cout << "3. Exit\n";
        std::cout << "Enter your choice: ";
        std::cin >> choice;

        switch (choice) {
            case 1:
                std::cout << "\nFlight Details:\n";
                flight1.displayFlightDetails();
                flight2.displayFlightDetails();
                flight3.displayFlightDetails();
                break;

            case 2:
                std::cout << "\nEnter flight number to book a ticket: ";
                std::string flightNumber;
                std::cin >> flightNumber;

                if (flightNumber == "F101") {
                    flight1.bookTicket();
                } else if (flightNumber == "F202") {
                    flight2.bookTicket();
                } else if (flightNumber == "F303") {
                    flight3.bookTicket();
                } else {
                    std::cout << "Invalid flight number. Please try again.\n\n";
                }
                break;

            case 3:
                std::cout << "Exiting the program. Thank you!\n";
                break;

            default:
                std::cout << "Invalid choice. Please try again.\n\n";
        }

    } while (choice != 3);

    return 0;
}

