import csv
import os
from datetime import datetime

FILE_NAME = "budget_data.csv"

# Initialize CSV
def initialize_csv():
    if not os.path.exists(FILE_NAME):
        with open(FILE_NAME, "w", newline="") as file:
            writer = csv.writer(file)
            writer.writerow(["date", "item", "amount", "category", "notes"])

# Add new expense
def add_expense():
    print("\n  Add Expense ")
    date = input("Enter date (YYYY-MM-DD): ")
    item = input("Enter item name: ")
    amount = input("Enter amount: ")
    category = input("Enter category (Food/Travel/Bills/Shopping/Others): ")
    notes = input("Notes (optional): ")

    try:
        float(amount)
    except ValueError:
        print("Invalid amount!")
        return

    with open(FILE_NAME, "a", newline="") as file:
        writer = csv.writer(file)
        writer.writerow([date, item, amount, category, notes])
    
    print("Expense added successfully!")

# View all expenses
def view_expenses():
    print("\n  Expense Records ")
    try:
        with open(FILE_NAME, "r") as file:
            reader = csv.reader(file)
            for row in reader:
                print(row)
    except FileNotFoundError:
        print("No data found!")

# Analytics
def view_analytics():
    print("\n Spending Analytics ")
    category_totals = {}
    total_spend = 0

    try:
        with open(FILE_NAME, "r") as file:
            reader = csv.DictReader(file)
            for row in reader:
                amount = float(row["amount"])
                cat = row["category"]

                total_spend += amount
                category_totals[cat] = category_totals.get(cat, 0) + amount

        print(f"Total Spend: ₹{total_spend}")

        print("\nCategory-wise Summary:")
        for cat, amt in category_totals.items():
            print(f"{cat}: ₹{amt}")

        highest = max(category_totals, key=category_totals.get)
        print(f"\nHighest Spending Category: {highest}")

    except FileNotFoundError:
        print("No data available!")

# Menu
def menu():
    initialize_csv()
    
    while True:
        print("\n=== Personal Budget Tracker ===")
        print("1. Add Expense")
        print("2. View Expenses")
        print("3. View Analytics")
        print("4. Exit")
        
        choice = input("Enter choice: ")

        if choice == "1":
            add_expense()
        elif choice == "2":
            view_expenses()
        elif choice == "3":
            view_analytics()
        elif choice == "4":
            print("Exiting...Goodbye!")
            break
        else:
            print("Invalid choice!")

menu()

