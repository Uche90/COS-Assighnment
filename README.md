''' 
    COS-Assignment by Obi Promise Uche
    Reg no: 20204924028
'''

def get_grade_point(score):
    if score > 100 or score < 0:
        return None
    elif score >= 70:
        return 5.00, "A"
    elif score >= 60:
        return 4.00, "B"
    elif score >= 50:
        return 3.00, "C"
    elif score >= 45:
        return 2.00, "D"
    elif score >= 40:
        return 1.00, "E"
    else:
        return 0.00, "F"

def collect_scores():
    subject_scores = {}
    subject_names = [
        "Mathematics", "Physics", "Chemistry", "Biology",
        "COS", "CYB", "CSC", "Statistics"
    ]

    print("Input your scores:\n")

    while True:
        try:
            for name in subject_names:
                while True:
                    score = int(input(f"{name} score (0–100): "))
                    if 0 <= score <= 100:
                        subject_scores[name] = score
                        break
                    else:
                        print("Score must be between 0 and 100.")
            break
        except ValueError:
            print("Input must be a valid integer. Try again.")
    return subject_scores

def calculate_gpa(subject_scores):
    grade_points = []
    print("\nUser Result:\n")

    for subject, score in subject_scores.items():
        gp, grade = get_grade_point(score)
        if gp is None:
            print(f"{subject}: Invalid score {score}")
        else:
            grade_points.append(gp)
            print(f"{subject}: {grade}")

    if grade_points:
        gpa = sum(grade_points) / len(grade_points)
        print(f"\nUser GPA (out of 5.00): {gpa:.2f}")
    else:
        print("\nNo valid scores to calculate GPA.")


scores = collect_scores()
calculate_gpa(scores)
