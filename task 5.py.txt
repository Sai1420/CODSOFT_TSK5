import random

# Define a list of quiz questions
quiz_questions = [
    {
        "question": "What is the capital of France?",
        "choices": ["London", "Madrid", "Paris", "Rome"],
        "correct_answer": "Paris"
    },
    {
        "question": "Which planet is known as the Red Planet?",
        "choices": ["Mars", "Venus", "Earth", "Jupiter"],
        "correct_answer": "Mars"
    },
    {
        "question": "What is 5 multiplied by 9?",
        "choices": ["42", "45", "50", "55"],
        "correct_answer": "45"
    }
]

# Function to ask a random question from the quiz
def ask_question(question_data):
    question = question_data["question"]
    choices = question_data["choices"]
    correct_answer = question_data["correct_answer"]

    print(question)
    for index, choice in enumerate(choices, start=1):
        print(f"{index}. {choice}")

    user_answer = input("Enter the number of your answer: ")
    if user_answer.isdigit() and 1 <= int(user_answer) <= len(choices):
        user_answer = choices[int(user_answer) - 1]

        if user_answer == correct_answer:
            print("Correct!")
            return 1
        else:
            print(f"Incorrect. The correct answer is: {correct_answer}")
            return 0
    else:
        print("Invalid choice. Skipping this question.")
        return 0

# Main quiz function
def main():
    print("Welcome to the Quiz Game!")
    print("Answer the following questions:")

    score = 0

    random.shuffle(quiz_questions)  # Shuffle the questions for variety

    for question_data in quiz_questions:
        score += ask_question(question_data)
        print()

    print(f"Quiz Completed! Your Score: {score}/{len(quiz_questions)}")

if __name__ == "__main__":
    main()
