# Library Management System in python
class Book:
    def __init__(self, title, author, available_copies):
        self.title = title
        self.author = author
        self.available_copies = available_copies

    def display_info(self):
        print(f"Title: {self.title}\nAuthor: {self.author}\nAvailable Copies: {self.available_copies}\n")


class Library:
    def __init__(self):
        self.books = []

    def add_book(self, book):
        self.books.append(book)
        print(f"Book '{book.title}' added to the library.")

    def display_books(self):
        if not self.books:
            print("No books in the library.")
        else:
            print("Books in the Library:")
            for book in self.books:
                book.display_info()

    def borrow_book(self, title):
        for book in self.books:
            if book.title.lower() == title.lower() and book.available_copies > 0:
                book.available_copies -= 1
                print(f"Book '{title}' borrowed successfully.")
                return
        print(f"Book '{title}' not available for borrowing.")

    def return_book(self, title):
        for book in self.books:
            if book.title.lower() == title.lower():
                book.available_copies += 1
                print(f"Book '{title}' returned successfully.")
                return
        print(f"Book '{title}' not found in the library.")

def main():
    library = Library()

    # Adding initial books to the library
    book1 = Book("The Catcher in the Rye", "J.D. Salinger", 5)
    book2 = Book("To Kill a Mockingbird", "Harper Lee", 3)
    book3 = Book("1984", "George Orwell", 2)

    library.add_book(book1)
    library.add_book(book2)
    library.add_book(book3)

    while True:
        print("\nLibrary Management System")
        print("1. Display Books")
        print("2. Borrow a Book")
        print("3. Return a Book")
        print("4. Add a Book")
        print("5. Exit")
        
        choice = input("Enter your choice: ")

        if choice == '1':
            library.display_books()
        elif choice == '2':
            title = input("Enter the title of the book you want to borrow: ")
            library.borrow_book(title)
        elif choice == '3':
            title = input("Enter the title of the book you want to return: ")
            library.return_book(title)
        elif choice == '4':
            title = input("Enter the title of the book: ")
            author = input("Enter the author of the book: ")
            available_copies = int(input("Enter the number of available copies: "))
            new_book = Book(title, author, available_copies)
            library.add_book(new_book)
        elif choice == '5':
            print("Exiting the Library Management System. Goodbye!")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()


