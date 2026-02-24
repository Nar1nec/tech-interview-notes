

MRO — это порядок, в котором Python ищет методы при множественном наследовании.

```python
class A:
    def method(self):
        print("A")
class B(A):
    def method(self):
        print("B")
class C(A):
    def method(self):
        print("C")
class D(B, C):
    pass
# Проверяем MRO
print(D.__mro__)
# (<class '__main__.D'>, <class '__main__.B'>, 
#  <class '__main__.C'>, <class '__main__.A'>, <class 'object'>)
d = D()
d.method()  # "B" (идет по MRO)
# Более сложный пример (ромбовидное наследование)
class Animal:
    def speak(self):
        print("Animal speaks")
class Dog(Animal):
    def speak(self):
        print("Woof!")
class Cat(Animal):
    def speak(self):
        print("Meow!")
class DogCat(Dog, Cat):
    pass
pet = DogCat()
pet.speak()  # "Woof!" (сначала Dog)
print(DogCat.__mro__)
# (DogCat, Dog, Cat, Animal, object)
# Python использует C3-линеаризацию
# Правила:
# 1. Дети всегда перед родителями
# 2. Порядок классов при наследовании важен
```
