def check_password_strength(password):
    # Initial score
    score = 0
    
    # Check length
    if len(password) >= 8:
        score += 1
    else:
        print("Password should be at least 8 characters long.")
    
    # Check if it contains digits
    if any(char.isdigit() for char in password):
        score += 1
    
    # Check if it contains lowercase letters
    if any(char.islower() for char in password):
        score += 1
    
    # Check if it contains uppercase letters
    if any(char.isupper() for char in password):
        score += 1

    # Determine password strength
    if score == 4:
        return "Strong Password"
    elif score == 3:
        return "Medium Strength Password"
    else:
        return "Weak Password"

# Main function to test password
def main():
    password = input("Enter your password: ")
    result = check_password_strength(password)
    print(result)

if __name__ == "__main__":
    main()
