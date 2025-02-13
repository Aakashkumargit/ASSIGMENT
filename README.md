class GroceryCalculator:
    def __init__(self):
        self.items = {}

    def add_item(self, name, price, quantity):
        if name in self.items:
            self.items[name]['quantity'] += quantity
        else:
            self.items[name] = {'price': price, 'quantity': quantity}
        print(f"Added {quantity} x {name} at ₹{price} each.")

    def remove_item(self, name):
        if name in self.items:
            del self.items[name]
            print(f"Removed {name} from the list.")
        else:
            print(f"{name} not found in the list.")

    def calculate_total(self):
        total = sum(item['price'] * item['quantity'] for item in self.items.values())
        return total

    def show_items(self):
        if not self.items:
            print("No items in the list.")
        else:
            print("\nGrocery List:")
            for name, details in self.items.items():
                print(f"{name}: {details['quantity']} x ₹{details['price']} = ₹{details['quantity'] * details['price']}")
            print(f"Total Cost: ₹{self.calculate_total()}\n")


def main():
    calc = GroceryCalculator()
    while True:
        print("\nOptions: 1. Add Item  2. Remove Item  3. Show Items  4. Calculate Total  5. Exit")
        choice = input("Enter choice: ")
        
        if choice == '1':
            name = input("Enter item name: ")
            price = float(input("Enter item price: "))
            quantity = int(input("Enter quantity: "))
            calc.add_item(name, price, quantity)
        elif choice == '2':
            name = input("Enter item name to remove: ")
            calc.remove_item(name)
        elif choice == '3':
            calc.show_items()
        elif choice == '4':
            print(f"Total Cost: ₹{calc.calculate_total()}")
        elif choice == '5':
            print("Exiting... Goodbye!")
            break
        else:
            print("Invalid choice, please try again.")


if __name__ == "__main__":
    main()
