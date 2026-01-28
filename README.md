from abc import ABC, abstractmethod

# Abstract base class
class Employee(ABC):
    def __init__(self, first_name, initial, last_name):
        self._first_name = first_name
        self._initial = initial
        self._last_name = last_name

    @abstractmethod
    def earnings(self):
        pass

    def display(self):
        print(f"{self._first_name} {self._initial} {self._last_name}", end="")

# Derived class: SalaryEmployee
class SalaryEmployee(Employee):
    def __init__(self, first_name, initial, last_name, salary):
        super().__init__(first_name, initial, last_name)
        self.__salary = salary

    def earnings(self):
        return self.__salary

    def display(self):
        super().display()
        print(f" (Salary: {self.earnings()})")

# Derived class: HourlyEmployee
class HourlyEmployee(Employee):
    def __init__(self, first_name, initial, last_name, wage, hours):
        super().__init__(first_name, initial, last_name)
        self.__wage = wage
        self.__hours = hours

    def earnings(self):
        return self.__wage * self.__hours

    def display(self):
        super().display()
        print(f" (Hourly earnings: {self.earnings()})")

# Application to test
if __name__ == "__main__":
    s_emp = SalaryEmployee("John", 'A', "Doe", 5000)
    h_emp = HourlyEmployee("Jane", 'B', "Smith", 20, 160)
    
    s_emp.display()
    h_emp.display()
