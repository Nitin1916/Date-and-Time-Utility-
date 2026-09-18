# Date-and-Time-Utility-
Calculate days between two dates ,working days,format dates ,time between left etc using date time library.

from datetime import datetime

def calculate_age():
    dob = input("Enter DOB (DD-MM-YYYY): ")
    try:
        birth_date = datetime.strptime(dob, "%d-%m-%Y")
        today = datetime.today()

        age = today.year - birth_date.year

        if (today.month, today.day) < (birth_date.month, birth_date.day):
            age -= 1

        print("Age:", age, "years")

    except ValueError:
        print("Invalid date format!")

def days_between_dates():
    d1 = input("Enter First Date (DD-MM-YYYY): ")
    d2 = input("Enter Second Date (DD-MM-YYYY): ")

    try:
        date1 = datetime.strptime(d1, "%d-%m-%Y")
        date2 = datetime.strptime(d2, "%d-%m-%Y")

        diff = abs((date2 - date1).days)
        print("Days Difference:", diff)

    except ValueError:
        print("Invalid date!")

def working_days():
    start = input("Enter Start Date (DD-MM-YYYY): ")
    end = input("Enter End Date (DD-MM-YYYY): ")

    try:
        start_date = datetime.strptime(start, "%d-%m-%Y")
        end_date = datetime.strptime(end, "%d-%m-%Y")

        if start_date > end_date:
            start_date, end_date = end_date, start_date

        count = 0
        current = start_date

        while current <= end_date:
            if current.weekday() < 5:
                count += 1
            current = current.replace(day=current.day) + (current - current)

        current = start_date
        count = 0

        from datetime import timedelta

        while current <= end_date:
            if current.weekday() < 5:
                count += 1
            current += timedelta(days=1)

        print("Working Days:", count)

    except ValueError:
        print("Invalid date!")

def format_datetime():
    now = datetime.now()

    print("\nCurrent Date & Time Formats:")
    print("DD-MM-YYYY :", now.strftime("%d-%m-%Y"))
    print("MM/DD/YYYY :", now.strftime("%m/%d/%Y"))
    print("24-Hour :", now.strftime("%H:%M:%S"))
    print("12-Hour :", now.strftime("%I:%M:%S %p"))

while True:
    print("\n===== DATE & TIME UTILITY =====")
    print("1. Calculate Age")
    print("2. Days Between Dates")
    print("3. Working Days")
    print("4. Format Date & Time")
    print("5. Exit")

    choice = input("Enter Choice: ")

    if choice == "1":
        calculate_age()
    elif choice == "2":
        days_between_dates()
    elif choice == "3":
        working_days()
    elif choice == "4":
        format_datetime()
    elif choice == "5":
        print("Thank You!")
        break
    else:
        print("Invalid Choice!")
