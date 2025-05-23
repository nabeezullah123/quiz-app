

import random

class Question:
    def __init__(self, prompt, options, answer):
        self.prompt = prompt
        self.options = options
        self.answer = answer  # correct option text

def run_quiz(questions):
    random.shuffle(questions)  # Shuffle the question order
    score = 0

    for i, q in enumerate(questions, start=1):
        shuffled_options = q.options[:]
        random.shuffle(shuffled_options)  # Shuffle option order

        print(f"\nQuestion {i}: {q.prompt}")
        for idx, opt in enumerate(shuffled_options):
            print(f"  {idx + 1}. {opt}")
        
        try:
            user_input = int(input("Your answer (1-4): ")) - 1
            if shuffled_options[user_input] == q.answer:
                print("✅ Correct!")
                score += 1
            else:
                print(f"❌ Wrong! Correct answer: {q.answer}")
        except (ValueError, IndexError):
            print("⚠️ Invalid input. Skipping question.")

    print(f"\n🏁 Quiz Finished! Your Score: {score}/{len(questions)}")

# -----------------------
# General Knowledge Questions
# -----------------------
questions = [
    Question("What is the largest continent in the world?", ["Asia", "Africa", "Europe", "Antarctica"], "Asia"),
    Question("Who is the father of the Indian Constitution?", ["Jawaharlal Nehru", "B. R. Ambedkar", "Mahatma Gandhi", "Sardar Patel"], "B. R. Ambedkar"),
    Question("Which gas do plants absorb from the atmosphere?", ["Oxygen", "Carbon Dioxide", "Nitrogen", "Hydrogen"], "Carbon Dioxide"),
    Question("Which planet is closest to the Sun?", ["Earth", "Venus", "Mercury", "Mars"], "Mercury"),
    Question("Who invented the light bulb?", ["Alexander Graham Bell", "Isaac Newton", "Thomas Edison", "Nikola Tesla"], "Thomas Edison"),
    Question("Which country is known as the Land of the Rising Sun?", ["China", "Japan", "South Korea", "Thailand"], "Japan"),
    Question("Which is the longest river in the world?", ["Amazon", "Yangtze", "Mississippi", "Nile"], "Nile"),
    Question("In which year did India gain independence?", ["1942", "1945", "1947", "1950"], "1947")
]

# Start the quiz
run_quiz(questions)
