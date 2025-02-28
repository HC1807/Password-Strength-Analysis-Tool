# Password strength checker
A password strength checker is a tool that evaluates the security level of a password based on various criteria, such as length, complexity, and predictability. It helps users create stronger passwords by providing feedback on weaknesses and suggesting improvements.

# How it works

* Length Check – Longer passwords are generally stronger.
* Character Variety – Use of uppercase, lowercase, numbers, and special characters increases strength.
* Common Patterns Detection – Avoids weak passwords like "123456" or "password".
* Dictionary Attack Prevention – Checks against common words and leaked passwords.

# Code
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

    Determine password strength
    if score == 4:
    return "Strong Password"
    elif score == 3:
    return "Medium Strength Password"
    else:
    return "Weak Password"
    def main():
    password = input("Enter your password: ")
    result = check_password_strength(password)
    print(result)

    if __name__ == "__main__":
    main()

# Code explanation
   # Defining the Password Strength Function
    def check_password_strength(password):
* Purpose: This function evaluates a given password based on specific security criteria.
* Functionality: Uses conditional checks to verify password length, digits, and character types.

  # Checking Password Length
      if len(password) >= 8:
      score += 1
      else:
      print("Password should be at least 8 characters long.")
  *Purpose: Ensure the password is at least 8 characters long, which is a standard security requirement.
  *If the condition is met, the score increases by 1.
  *If the password is too short, a warning message is displayed.

  # Checking for Digits in Password
          if any(char.isdigit() for char in password):
          score += 1
  *Purpose: Ensure the password contains at least one numeric digit (0-9).
  *Uses any() to scan the password for numeric characters.
  *Increases the score by 1 if a digit is found.

  # Checking for Lowercase Letters
       if any(char.islower() for char in password):
      score += 1
  *Purpose: Ensure the password includes at least one lowercase letter (a-z).
  *Uses any() to detect lowercase characters.
  *Increases the score by 1 if present

  # Checking for Uppercase Letters
      if any(char.isupper() for char in password):
      score += 1
  *Purpose: Ensure the password contains at least one uppercase letter (A-Z).

  # Determining Password Strength
      if score == 4:
      return "Strong Password"
      elif score == 3:
      return "Medium Strength Password"
      else:
      return "Weak Password"
  * Purpose: Classifies password strength based on the accumulated score.
  *A score of 4 means a Strong Password.
  *A score of 3 means Medium Strength Password.
  *A score of 2 or lower means Weak Password.

# Getting User Input and Running the Function
    def main():
    password = input("Enter your password: ")
    result = check_password_strength(password)
    print(result)

    if __name__ == "__main__":
    main()
*Purpose: Takes user input and checks password strength using check_password_strength().
*Prompts the user to enter a password.
*Calls the function and prints the result.
*Runs the program only if executed as the main script "(if __name__ == "__main__":)".

# Running the Script
    python password_checker.py
    Save the script as password_checker.py.
*Open a terminal or command prompt.
*Navigate to the script directory.
*Enter a password when prompted.
*View the password strength classification.

# Example Output :
* WEAK PASSWORD :
* Enter your password: hello123
* Weak Password

* STRONG PASSWORD :
* Enter your password: P@ssw0rd
* Strong Password








    




