# CapstoneProjectControlStructures
This Python program, was built for a small financial company that asked to create a system to allows users to access two different financial calculators: \
A investment calculator. \
A home loan repayment calculator.
## Installation
You will need PyCharm to run this project.\
Copy the files finance_calculators.py to the root file of your new project in PyCharm
## Usage
For the development of this software, math import, loops, validations, conditional statements, and menu with a sud menu were created. \
The components will be described below highlighting their purposes.
### Main program
#### MAin Menu with sub menu
```Python
#  print program greeting to user, request user input and store it in a variable
print("hyperion finance services".upper())
name = str(input("What is your name: "))

#  while loop to take in the input of the selected option by the user and store it in a variable
while True:
    finance_selector = input(f"""Welcome {name.title()}\n
Choose either 'investment' or 'bond' from the menu below to proceed:\n    
investment - to calculate the amount of interest you'll earn on your investment
bond - to calculate the amount you'll have to pay on a home loan\n    
Enter your choice: """).lower()

    #  conditional statement to check for empty input
    if not finance_selector:
        print("You haven’t entered anything!\nPlease enter either 'investment' or 'bond'.\n")

    #  conditional statement to check that the value input is non-numeric and is 'investment' or 'bond' only
    elif not finance_selector.isnumeric() and finance_selector == "investment" or finance_selector == "bond":

        if finance_selector == "investment":
            #  request user to input the deposit, the interest rate, and the years of investment and
            #  store these in variables
            deposit = float(input("Enter the amount of money been deposited: "))
            interest_rate = float(input("Enter interest rate: "))
            investment_years = int(input("Enter the number of years you plan on investing: "))

            #  while loop to take in the input of the selected option by the user and store it in a variable
            while True:
                interest = input("Choose either 'simple' or 'compound' interest: ")

                #  conditional statement to check for empty input
                if not interest:
                    print("You haven’t entered anything!\nPlease enter either 'simple' or 'compound' interest.\n")

                #  conditional statement to check that the value input is non-numeric and is 'simple' or 'compound' only
                elif not interest.isnumeric() and interest == "simple" or interest == "compound":

                    if interest == "simple":
                        # calculating simple interest amount and print the result
                        A = deposit * (1 + (interest_rate / 100) * investment_years)
                        print(f"\nYour simple investment return is: £{round(A, 2)}\nThanks for using our services")

                    elif interest == "compound":
                        #  calculating compound interest amount and print the result
                        A = deposit * math.pow((1 + (interest_rate / 100)), investment_years)
                        print(f"\nYour compound investment return is: £{round(A, 2)}\nThanks for using our services")

                    break

                else:
                    #  print out a message informing the user of incorrect input
                    print("I did not understand that...!\nTry again entering either 'simple' or 'compound'\n")

        elif finance_selector == "bond":
            #  request user to input the value of the house, the interest rate, and the number of months thatwill take
            #  to repay the bond, and store these in variables
            current_house_value = float(input("Enter the current value of your house: "))
            interest_rate = float(input("Enter interest rate: "))
            repayment_months = int(input("Enter the number of months you plan to take to repay the bond: "))

            #  calculating the monthly interest rate
            monthly_interest_rate = (interest_rate / 100) / 12

            #  calculating the monthly repayment amount on the bond
            x = (monthly_interest_rate * current_house_value) / (
                    1 - math.pow((1 + monthly_interest_rate), (- repayment_months)))
            print(f"\nYour monthly repayment amount is: £{round(x, 2)}\nThanks for using our services")

        break

    else:
        #  print out a message informing the user of incorrect input
        print("I did not understand that...!\nTry again using either 'investment' or 'bond'\n")
```
## Contributing
Pull requests are welcome. For any changes, please open an issue first to discuss what you would like to change.
Please make sure to update tests as appropriate.
## Credits
© Angel De Sousa
