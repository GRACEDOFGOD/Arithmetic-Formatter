# Arithmetic-Formatter

Solution for Arithmetic Formatter
Close
×
PY
def arithmetic_arranger(problems, show_answers=False):
    if len(problems) > 5:
        return 'Error: Too many problems.'

    first_operands = []
    second_operands = []
    operators = []
    results = []
    
    # Validate and process each problem
    for problem in problems:
        parts = problem.split()
        if parts[1] not in ['+', '-']:
            return "Error: Operator must be '+' or '-'."
        if not (parts[0].isdigit() and parts[2].isdigit()):
            return 'Error: Numbers must only contain digits.'
        if len(parts[0]) > 4 or len(parts[2]) > 4:
            return 'Error: Numbers cannot be more than four digits.'

        first_operands.append(parts[0])
        second_operands.append(parts[2])
        operators.append(parts[1])

        # Calculate the result if needed
        if show_answers:
            if parts[1] == '+':
                results.append(str(int(parts[0]) + int(parts[2])))
            else:
                results.append(str(int(parts[0]) - int(parts[2])))

    # Create formatted output
    line1 = ''
    line2 = ''
    line3 = ''
    line4 = ''

    for i in range(len(problems)):
        width = max(len(first_operands[i]), len(second_operands[i])) + 2
        line1 += first_operands[i].rjust(width) + '    '
        line2 += operators[i] + ' ' + second_operands[i].rjust(width - 2) + '    '
        line3 += '-' * width + '    '
        if show_answers:
            line4 += results[i].rjust(width) + '    '

    arranged_problems = line1.rstrip() + '\n' + line2.rstrip() + '\n' + line3.rstrip()
    if show_answers:
        arranged_problems += '\n' + line4.rstrip()

    return arranged_problems

# Test cases
print(arithmetic_arranger(["32 + 698", "3801 - 2", "45 + 43", "123 + 49"]))
print(arithmetic_arranger(["32 + 8", "1 - 3801", "9999 + 9999", "523 - 49"], True))
Close
