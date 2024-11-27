# Quiz Game Implementation

def display_question(question, options):
    """Display the question and its options."""
    print(question)
    for idx, option in enumerate(options):
        print(f"{idx + 1}. {option}")

def get_user_answer():
    """Get user input and validate it."""
    while True:
        try:
            answer = int(input("Enter the number of your answer: "))
            return answer
        except ValueError:
            print("Invalid input. Please enter a number.")

def check_answer(user_answer, correct_answer):
    """Check if the user's answer is correct."""
    return user_answer == correct_answer

def run_quiz(questions):
    """Run the quiz game."""
    score = 0

    for question, options, correct_answer in questions:
        display_question(question, options)
        
        while True:  # Loop until a valid answer is provided
            user_answer = get_user_answer()

            # Validate user input
            if user_answer < 1 or user_answer > len(options):
                print("Invalid choice. Please try again.")
                continue  # Ask the question again

            # Check if the answer is correct (correct_answer is 1-based)
            if check_answer(user_answer, correct_answer):
                print("Correct!\n")
                score += 1
            else:
                print(f"Incorrect! The correct answer was: {options[correct_answer - 1]}\n")
            break  # Exit the loop after a valid answer

    return score

def display_final_score(score, total_questions):
    """Display the final score."""
    print(f"Your final score is: {score}/{total_questions}")

def main():
    """Main function to run the quiz."""
    questions = [
        ("What is the capital of india?", ["U.P", "A.P", "Delhi", "Telangana"], 3),
        ("Which code are you using for project?", ["Java", "Python", "C", "C++"], 2),
        ("What is the capital of telangana?", ["Adilabad", "Hyderabad", "Khammam", "Nalgonda"], 2)
    ]

    total_questions = len(questions)
    score = run_quiz(questions)
    display_final_score(score, total_questions)

if name == "main":
    main()# project-1-
