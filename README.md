# Password Strength Analysis Tool
A password strength checker is a tool that evaluates the security level of a password based on various criteria, such as length, complexity, and predictability. It helps users create stronger passwords by providing feedback on weaknesses and suggesting improvements.

# How it works

* Length Check – Longer passwords are generally stronger.
  
* Character Variety – Use of uppercase, lowercase, numbers, and special characters increases strength.

*  Common Patterns Detection – Avoids weak passwords like "123456" or "password".
  
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
   # Imports
    import re
    import string
    
* Purpose: COMMON_PASSWORDS is a blocklist of well-known weak/leaked passwords. SEQUENTIAL_PATTERNS lists predictable character sequences (number order, alphabet order, keyboard rows) used to catch passwords that look "strong" but follow an obvious pattern.

  # Constants
      COMMON_PASSWORDS = {"123456", "password", ...}
      SEQUENTIAL_PATTERNS = ["0123456789", "abcdefghijklmnopqrstuvwxyz", "qwertyuiop", ...]
  * Purpose: Ensure the password is at least 8 characters long, which is a standard security requirement.
  
# Checking for Special Characters
    def has_special_char(password):
    return any(char in string.punctuation for char in password)

  * Purpose: Ensures the password contains at least one symbol (!, @, #, etc.).
             Scans each character and checks membership in string.punctuation.

  # Checking Against Common/Leaked Passwords

  * Purpose: Flags passwords that appear on well-known weak/leaked password lists.
  
  * Lowercases input first, so casing ("Password" vs "password") doesn't bypass the check
  

  # Checking for Sequential Patterns
       def has_sequential_pattern(password, min_run=4):
    
  * Purpose: Detects predictable runs like "1234", "abcd", or "qwerty" — including reversed order.
  
  * Slides a 4-character window across each known pattern and checks whether that chunk (forward or reversed) appears in the password.
  

  # Checking for Repeated Characters
      def has_repeated_char(password, min_run=4):
      return bool(re.search(r"(.)\1{3,}", password))
      
  * Purpose: Flags passwords with 4 or more of the same character in a row (e.g. "aaaa").
  * Uses a regex backreference to detect repetition without hardcoding every possible character.

  # Defining the Password Strength Function
      def check_password_strength(password):
      
  * Purpose: Evaluates a password across length, character variety, and predictability, returning both a strength label and specific feedback.
  * Functionality: Combines a point-based score with penalties for weak patterns, rather than a simple pass/fail.


# Checking Common Passwords First
    if has_common_password(password):
    return "Weak Password", feedback
* If the password is on the blocklist, it's immediately marked weak — no need to score it further.

# Checking Length

    if len(password) >= 12:
    score += 2
    elif len(password) >= 8:
    score += 1
    else:
    feedback.append(...)
    
* 12+ characters earns 2 points, 8–11 earns 1 point, under 8 earns none and triggers feedback.

  # Checking Character Variety

      if any(char.isdigit() for char in password): score += 1
      if any(char.islower() for char in password): score += 1
      if any(char.isupper() for char in password): score += 1
      if has_special_char(password): score += 1

 * One point each for digits, lowercase, uppercase, and special characters — up to 4 points.

 # Applying Pattern Penalties
       if has_sequential_pattern(password):
       score = max(0, score - 2)
       if has_repeated_char(password):
       score = max(0, score - 1)
   
  * Subtracts points for predictable patterns, with max(0, ...) preventing the score from going negative.

# Determining Password Strength

    if score >= 6: strength = "Strong Password"
    elif score >= 4: strength = "Medium Strength Password"
    else: strength = "Weak Password"

  * Classifies the final score into Strong / Medium / Weak

# Getting User Input and Running the Function
    def main():
    password = input("Enter your password: ")
    strength, feedback = check_password_strength(password)
    print(f"\n{strength}")
    if feedback:
        for item in feedback:
            print(f"  - {item}")

    if __name__ == "__main__":
    main()

  * Prompts for a password, runs the checker, and prints both the strength rating and any improvement suggestions.

# Example Output

    Enter your password: qwerty1234
    Weak Password
    Suggestions:
    -  Add at least one uppercase letter.
    - Add at least one special character (e.g. !, @, #, $).
    - Avoid sequential patterns like '1234' or 'qwerty'.

    Enter your password: Xk9$mQ2vR#pL7
    Strong Password

   











    




