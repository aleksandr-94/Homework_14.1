# Homework_14.1



class TooManyStudentsError(Exception):
    """Исключение для случая, когда в группе больше 10 студентов."""
    pass


class Group:
    def __init__(self, number):
        self.number = number
        self.students = []

    def add_student(self, student):
        """Добавляет студента в группу."""
        if len(self.students) >= 10:
            raise TooManyStudentsError(f"В группе {self.number} уже 10 студентов. Нельзя добавить больше.")
        self.students.append(student)

    def __str__(self):
        """Возвращает строковое представление группы."""
        return f"Group {self.number}:\n" + "\n".join(str(student) for student in self.students)


class Student:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __str__(self):
        return f"Student: {self.name}, Age: {self.age}"


try:
    group = Group("Python")
    for i in range(12):
        group.add_student(Student(f"Student{i+1}", 20))
        print(f"Добавлен студент {i+1}")
except TooManyStudentsError as e:
    print(f"Ошибка: {e}")

print(group)
