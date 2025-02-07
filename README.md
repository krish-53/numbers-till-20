def validate_aadhar(aadhar):
    return len(aadhar) == 12 and aadhar.isdigit()

def validate_mobile(mobile):
    return len(mobile) == 10 and mobile.isdigit()

registered_aadhars = set()

while True:
    print("\n=== Voting System Registration ===")
    
    name = input("Enter your name: ").strip()
    
    while True:
        try:
            age = int(input("Enter your age: "))
            if age < 18:
                print("Sorry, you must be 18 or older to vote!")
                break
            elif age > 120:
                print("Please enter a valid age!")
                continue
            break
        except ValueError:
            print("Please enter a valid number for age!")
    
    if age < 18:
        choice = input("\nDo you want to continue with next voter? (yes/no): ").lower()
        if choice != 'yes':
            break
        continue
    
    while True:
        mobile = input("Enter your mobile number (10 digits): ")
        if validate_mobile(mobile):
            break
        print("Invalid mobile number! Please enter 10 digits only.")
    
    while True:
        aadhar = input("Enter your Aadhar number (12 digits): ")
        if not validate_aadhar(aadhar):
            print("Invalid Aadhar number! Please enter 12 digits only.")
            continue
        if aadhar in registered_aadhars:
            print("This Aadhar number is already registered!")
            continue
        break
    
    registered_aadhars.add(aadhar)
    
    print("\nRegistration Successful!")
    print(f"Name: {name}")
    print(f"Age: {age}")
    print(f"Mobile: {mobile}")
    print(f"Aadhar: {aadhar}")
    
    choice = input("\nDo you want to continue with next voter? (yes/no): ").lower()
    if choice != 'yes':
        break

print("\nThank you for using the Voting System!") 
