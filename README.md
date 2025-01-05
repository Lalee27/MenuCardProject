``` python
class MenuCard:
    def __init__(self):
        # Default menu with items and their prices
        self.menu = {
            "Pizza": 200,
            "Burger": 150,
            "Pasta": 250,
            "Fries": 80
        }
        # Initialize an empty order dictionary
        self.order = {}

    def display_menu(self):
        """Display the menu with items and prices."""
        print("\n --- MENU ---")
        for item, price in self.menu.items():
            print(f"{item}: ₹{price}")

    def place_order(self):
        """Place an order by adding items from the menu to the order list."""
        self.display_menu()
        while True:
            item = input("\nEnter the item name (or type 'done' to finish): ")
            if item.lower() == 'done':
                break
            if item in self.menu:
                if item in self.order:
                    print(f"{item} is already in your order!")
                else:
                    self.order[item] = self.menu[item]
                    print(f"{item} added to your order.")
            else:
                print("Invalid item name. Please select an item from the menu.")

    def view_order(self):
        """View the currently placed order with the total bill."""
        if not self.order:
            print("\nYour order is empty!")
        else:
            print("\n --- ORDER ---")
            total = 0
            for item, price in self.order.items():
                print(f"{item}: ₹{price}")
                total += price
            print(f"\nTotal Bill: ₹{total}")

    def add_item(self):
        """Add a new item to the menu with its price."""
        item = input("\nEnter the new item name: ")
        if item in self.menu:
            print("This item already exists in the menu.")
        else:
            try:
                price = float(input("Enter the price of the item: "))
                if price > 0:
                    self.menu[item] = price
                    print(f"{item} has been added to the menu!")
                else:
                    print("Price must be greater than 0.")
            except ValueError:
                print("Invalid price. Please enter a number.")

    def menu_card_system(self):
        """Main interface for the menu card system."""
        while True:
            print("\n--- Menu Card System ---")
            print("1. View Menu")
            print("2. Place Order")
            print("3. View Order and Bill")
            print("4. Add New Menu Item")
            print("5. Exit")
            try:
                choice = int(input("Enter your choice (1-5): "))
                if choice == 1:
                    self.display_menu()
                elif choice == 2:
                    self.place_order()
                elif choice == 3:
                    self.view_order()
                elif choice == 4:
                    self.add_item()
                elif choice == 5:
                    print("Thank you for using the Menu Card System. Goodbye!")
                    break
                else:
                    print("Invalid choice. Please choose between 1 and 5.")
            except ValueError:
                print("Invalid input. Please enter a number between 1 and 5.")


# Create an instance of MenuCard and run the system
if __name__ == "__main__":
    menu_card = MenuCard()
    menu_card.menu_card_system()
```

# MenuCardProject
