# User_Expenses
An program that calculate user's expenses, finds the highest and the lowest expense.
# Using reduce method to apply a function cumulatively to a list
from functools import reduce

# Defining a function to get user expenses
def user_expenses():

    # Creating an empty list to store user expenses
    Expenses = []

    # Asking the user to enter the type of expenses and the amount by using an infinite loop "while True"
    while True:
        Expense_type = input("Enter the type of the expense or 'finished': ")

        # Adding a break statement to stop the loop when the user finishes
        if Expense_type.lower() == 'finished':
            break
        try:
            # Asking the user to enter the amount related to the type of expense
            amount = float(input(f"Enter the amount for {Expense_type}: "))
        except ValueError:
            print("Please enter a valid number for the amount.")
            continue

        # Creating an append method to add the expense type and the amount
        Expenses.append({'type': Expense_type, 'amount': amount})  

    return Expenses

# Defining a main function to analyze the expenses, calculate the total and find the highest and lowest expense
def analyze_expenses(Expenses):
    if not Expenses:
        print("No expenses to analyze.")
        return

    # Calculating the total of expenses
    Total_Expenses = reduce(lambda acc, exp: acc + exp['amount'], Expenses, 0)

    # Printing the total of the expenses
    print(f"The total of the expenses is: ${Total_Expenses:.2f}")
    
    # Finding the highest expense 
    Highest_expense = max(Expenses, key=lambda exp: exp['amount'])

    # Printing the highest expense
    print(f"The highest expense is: {Highest_expense['type']} - ${Highest_expense['amount']:.2f}")
    
    # Finding the lowest expense
    Lowest_expense = min(Expenses, key=lambda exp: exp['amount'])

    # Printing the lowest expense
    print(f"The lowest expense is: {Lowest_expense['type']} - ${Lowest_expense['amount']:.2f}")

# Running the program
def main():

    # This function asks the users for their expenses
    Expenses_of_user = user_expenses()

    # This function analyzes the inputs and displays the results
    analyze_expenses(Expenses_of_user)  

# Calling the main to execute the program
main()
