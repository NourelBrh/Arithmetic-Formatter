# Arithmetic-Formatter
def arithmetic_arranger(problems, show_answers=False):
    if len(problems) > 5:
        return "Error: Too many problems."

    arranged_problems = ""
    top_line = ""
    bottom_line = ""
    dash_line = ""
    answer_line = ""

    for problem in problems:
        parts = problem.split()
        operand1 = parts[0]
        operator = parts[1]
        operand2 = parts[2]

        if operator != '+' and operator != '-':
            return "Error: Operator must be '+' or '-'."

        if not operand1.isdigit() or not operand2.isdigit():
            return "Error: Numbers must only contain digits."

        if len(operand1) > 4 or len(operand2) > 4:
            return "Error: Numbers cannot be more than four digits."

        max_width = max(len(operand1), len(operand2))
        top_line += operand1.rjust(max_width + 2) + '    '
        bottom_line += operator + ' ' + operand2.rjust(max_width) + '    '
        dash_line += '-' * (max_width + 2) + '    '

        if show_answers:
            if operator == '+':
                answer = str(int(operand1) + int(operand2))
            else:
                answer = str(int(operand1) - int(operand2))
            answer_line += answer.rjust(max_width + 2) + '    '

    arranged_problems += top_line.rstrip() + '\n'
    arranged_problems += bottom_line.rstrip() + '\n'
    arranged_problems += dash_line.rstrip() + '\n'

    if show_answers:
        arranged_problems += answer_line.rstrip() + '\n'

    return arranged_problems.rstrip()
