import json # import the json module

def add_book(books):
    title = input("Enter book title: ")
    author = input("Enter author: ")
    isbn = input("Enter ISBN: ")
    quantity = int(input("Enter quantity: "))
    books[isbn] = {"title": title, "author": author, "quantity": quantity}
    print(f"Book '{title}' added successfully.")

def borrow_book(books):
    identifier = input("Enter book title or ISBN to borrow: ")
    found = False
    for isbn, details in books.items():
        if identifier.lower() == details["title"].lower() or identifier == isbn:
            if details["quantity"] > 0:
                details["quantity"] -= 1
                print(f"Book '{details['title']}' borrowed successfully.")
                found = True
                break
            else:
                print(f"Book '{details['title']}' is currently unavailable.")
                found = True
                break
    if not found:
        print("Book not found.")

def return_book(books):
    identifier = input("Enter book title or ISBN to return: ")
    found = False
    for isbn, details in books.items():
        if identifier.lower() == details["title"].lower() or identifier == isbn:
            details["quantity"] += 1
            print(f"Book '{details['title']}' returned successfully.")
            found = True
            break
    if not found:
        print("Book not found.")

def view_available_books(books):
    if not books:
        print("No books available in the library.")
        return
    print("Available Books:")
    for isbn, details in books.items():
        print(f"Title: {details['title']}, Author: {details['author']}, ISBN: {isbn}, Quantity: {details['quantity']}")

def search_book(books):
    query = input("Enter book title or author to search: ").lower()
    found = False
    for isbn, details in books.items():
        if query in details["title"].lower() or query in details["author"].lower():
            print(f"Title: {details['title']}, Author: {details['author']}, ISBN: {isbn}, Quantity: {details['quantity']}")
            found = True
    if not found:
        print("Book not found.")

def save_data(books, filename="library_books.txt"):
    try:
      with open(filename, 'w') as f:
          json.dump(books, f)
      print("Data saved successfully!")
    except Exception as e:
      print(f"Error saving data: {e}")

def load_data(filename="library_books.txt"):
    try:
        with open(filename, 'r') as f:
            books = json.load(f)
        print("Data loaded successfully!")
        return books
    except FileNotFoundError:
        print("No saved data found. Starting with an empty library.")
        return {}
    except json.JSONDecodeError:
        print("Error decoding saved data. Starting with an empty library.")
        return {}

def main():
    books = load_data()

    while True:
        print("\nLibrary Menu:")
        print("1. Add Book")
        print("2. Borrow Book")
        print("3. Return Book")
        print("4. View Available Books")
        print("5. Search for a Book")
        print("6. Save and Exit")

        choice = input("Enter your choice (1-6): ")

        if choice == '1':
            add_book(books)
        elif choice == '2':
            borrow_book(books)
        elif choice == '3':
            return_book(books)
        elif choice == '4':
            view_available_books(books)
        elif choice == '5':
            search_book(books)
        elif choice == '6':
            save_data(books)
            print("Exiting the program. Goodbye!")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
