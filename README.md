class A:
    def __init__(self):
        self.attr_a = "Атрибут класу A"
    
def method_a(self):
    return "Метод класу A"

class B:
    def __init__(self):
        self.attr_b = "Атрибут класу B"
    
def method_b(self):
    return "Метод класу B"

class C:
    def __init__(self):
        self.attr_c = "Атрибут класу C"
    
def method_c(self):
    return "Метод класу C"

class D(A, B, C):
    def __init__(self):
        A.__init__(self)
        B.__init__(self)
        C.__init__(self)

print(obj.attr_a)  
print(obj.method_a())
print(obj.attr_b)  
print(obj.method_b())
print(obj.attr_c)  
print(obj.method_c())  
