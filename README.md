import random

class Shifrator:
    def __init__(self, *numbers):
        self.__numbers = numbers
        self.__result = None
        self.__calculate()
    def __calculate(self):
        operation = random.choice(['+', '-', '*', '/'])

        if len(self.__numbers) == 0:
            self.__result = 0
            return

        result = self.__numbers[0]

        for num in self.__numbers[1:]:
            if operation == '+':
                result += num
            elif operation == '-':
                result -= num
            elif operation == '*':
                result *= num
            elif operation == '/' and num != 0:
                result /= num
            else:
                continue

        self.__result = result

    def __str__(self):
        return f'Результат: {self.__result}'

shifrator = Shifrator(10, 5, 3)
print(shifrator)
