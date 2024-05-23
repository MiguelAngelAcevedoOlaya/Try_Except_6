# CHALLENGE 6

### 1

##### 1-1

En el primer punto le permitimos al usuario introducir los dos números que desee, luego de eso ejectuamos la función que le recuerda al usuario los simbolos que representan a las diferentes operaciones matemáticas y en base a lo que ingrese el usuario devuelve la operación de los dos números.

Todo esto lo hicimos mediante ciclos if y while.

Se incluyeron dos excepciones, una dentro de la función que salta cuando el usuario ingresa algo diferente a las posibles  operaciones (+,-,*,/,//), esto es un raise dentro de las opciones. La otra excepción es al final, el cual salta en caso de que el usuario ingrese algo diferente a un número, este esta enforma de try-except.

``` python
def operaciones(numero_1: float, numero_2: float): # Función
  print("QUE OPERACIÓN DESEAS REALIZAR, SEGUN ESO PON EL SIGNO ASOCIADO \n+ = Suma \n- = Resta \n* = Multiplicación \n/ = División (Número 1 / Número 2) \n// = División Entera (Número 1 // Número 2)") #Explicación por si alguien no lo tiene claro
  eleccion = input("Ingresa la operación que quieras asociada a su número: ")
  if eleccion == "+": # Si ingreso suma
    print("ENTRADA: ("+ str(numero_1) +", "+ str(numero_2) +", "+ str(eleccion) +")")
    return(numero_1 + numero_2) # Retorna operación de los dos números
  elif eleccion == "-": # Si ingreso resta
    print("ENTRADA: ("+ str(numero_1) +", "+ str(numero_2) +", "+ str(eleccion) +")")
    return(numero_1 - numero_2) # Retorna operación de los dos números
  elif eleccion == "*": # Si ingreso multiplicación
    print("ENTRADA: ("+ str(numero_1) +", "+ str(numero_2) +", "+ str(eleccion) +")")
    return(numero_1 * numero_2) # Retorna operación de los dos números
  elif eleccion == "/": # Si ingreso división
    print("ENTRADA: ("+ str(numero_1) +", "+ str(numero_2) +", "+ str(eleccion) +")")
    return(numero_1 / numero_2) # Retorna operación de los dos números
  elif eleccion == "//": # Si ingreso división entera
    print("ENTRADA: ("+ str(numero_1) +", "+ str(numero_2) +", "+ str(eleccion) +")")
    return(numero_1 // numero_2) # Retorna operación de los dos números 
  else: # Caso que sea diferente
    raise IndexError("Elemento fuera de rango.") # Saltar error de elemento no incluido en las opciones de ingreso

try: # Se realiza el try para intentar ejecutar ek codigo
  numero_1 = float(input("Ingresa un número: ")) # Ingresar primer número
  numero_2 = float(input("Ingressa tu segundo número: ")) # Ingresar segundo número
  resultado = operaciones(numero_1, numero_2) # Ejecutamos la función
  print("Salida= ("+ str(resultado) +")") # Imprimir resultado de la función
except Exception as e: # Error en caso de que no ingrese números
  print(f"Error: {e}") # Imprime el error
```

#### 1-2

No se valia el slicing, pero y si creo dos listas en la que una ingrese la palabra del usuario de manera correcta y la otra lista que indexse la palabra de manera inversa agregando cada letra en la primera posición. En caso de que las dos listas sean iguales, la función retornara un True que significa que la palabra es palíndroma, en caso de que no sean iguales retornara un False y que la palabra no es palndroma.

Pusimos el normal try-except para comprobar cualquier error existente y un raise en el que buscamos comprobar si lo que se esta ingresando es realmente una letra o el usuario ingreso algun caracter o número.

``` python
def palindromo(palabra): # Función9
  lista = [] # Lista para la palabra
  lista_al_revez = [] # Lista de la palabra al revez
  for n in palabra: # Ciclo for
    lista.append(n) # Agregamos las letras con append a la lista
    lista_al_revez.insert(0, n) # Insertamos las letras de la apalabra al revez, agregandolas en la primera posición
  if lista == lista_al_revez: # Ciclo if para probar si son iguales
    return True # Devuelve que la palabra es palíndromo
  else: # En caso de que no sea igual
    return False # Devuelve que la palabra no es palíndromo

try:
  palabra = input("Ingresa la palabra que desees comprobar: ") # Usuario ingresa palabra
  if not palabra.isalpha():  # Verificar si la entrada contiene solo letras
    raise ValueError("Solo se permiten letras.")
  prim = palindromo(palabra) #Ejecutar función
  if prim == True: # En caso de que sea palindromo la palabra
    print(str(palabra) +" es un palíndromo") # Imprimir si es un palíndromo
  else: # En caso de que no sea palindroma
    print(str(palabra) +" no es un palíndromo") # Imprime que no es un palíndromo
except Exception as e: # Error 
  print(f"Error: {e}") # Imprime el error
```

#### 1-3

Este punto le permite ingresar al usuario los números que desse agregar a la lista, y por medio de ciclos, si el número es uno lo descartamos como no primo, si es dos lo designamos como primo, y en caso tal de que sea mayor a dos, chequeamos con una variable extra si hay un valor que sea capaz de dividir al número diferente de el. En caso tal de que no hay tal valor, el número es primo, y en caso de que si haya o hayan valores, no sera primo.

La excepción la inlcuios al final buscando un error en el que el usuario probabelemnte ingrese algo que no sea un número.

``` python
def primos(lista): # Función
  lista_primos = [] # Lista de primos
  for i in lista: # Recorrer los elemntos de la lista
    if i == 1: # SI el elemento es 1
      continue # Continua porque 1 no es primo 
    elif i == 2: # Si es 2
      lista_primos.append(i) # El 2 al ser primo lo agregamos 
      continue
    else: # En caso de que no sea ni 1 ni 2
      dato = 2 # Inicia en 2, porque ya descartamos el uno y el dos
      contador = 0 # El contador para saber si es primo o no
      while dato < i: # Mientras la variable dato sea menor al número
        if i % dato == 0: # Si la división no da residuo quiere decir que no es primo
          dato = dato + 1 # Aumentamos en uno el dato
          contador = contador + 1 # Aumentamos el contador
        else:
          dato = dato + 1 # Aumentamos en uno el dato
      if contador == 0: # Si no es 0 es primo ya que ningún número lo dividio
        lista_primos.append(i) # Lo agrega a la lista de los primos
      else: # No es primo siguiente número
        continue
  return lista_primos # Devuelva la lista

try:
  datos = int(input("Ingresa el número de datos que deseas agregar: ")) # Ingrese el número de datos que quiere agregar
  lista = [] # Lista vacia
  for n in range(datos): # Ciclo for para agregar el número de datos
    numero = int(input("Ingresa el número: ")) # # Ingresa el entero
    lista.append(numero) # Agregarlo a la lista
  print("Esta es tu lista de números: \n"+ str(lista)) # Imprime la lista
  nums_p = primos(lista) # Ejecutar función
  print("Estos son los números primos: \n"+ str(nums_p)) # Imprimir lista de primos
except Exception as e: # Error en caso de que no ingrese números
  print(f"Error: {e}") # Imprime el error
  print("probalemente no ingresaste un número")
```

#### 1-4

El usuario ingresa los números que desee, y usamos variables vacias y ciclos for, para que vaya chequeando cada suma (dato 1 + dato 2, dato 2 + dato 3........), y va reemplazando si a medida que va probando encunetra una suma mayor, y tambien cambia los valores que proporcionaron esa suma. Al final la función retorna la suma de los datos y cuales fueron esos datos.

La excepción la inlcuios al final buscando un error en el que el usuario probabelemnte ingrese algo que no sea un número.

``` python

def sum_may(datos, lista): # Función
  sum_ma = 0 # Variable de suma mayor
  variable_1 = 0 # Primera variable
  variable_2 = 0 # Segunda variable
  for i in range(datos-1): # Ciclo for que recorre la cantidad de datos de la lista
    suma = lista[i] + lista[i+1] # Suma el primer elemento mas el siguiente
    if suma > sum_ma: # Si la suma de los dos datos es mayor a las sumas previas 
      sum_ma = suma # Reemplaza el valor 
      variable_1 = lista[i] # Reempñaza la variable del primer elemento
      variable_2 = lista[i +1] # Reempñaza la variable del segundo elemento
    else: 
      continue # Si no es igual continua
  return sum_ma, variable_1, variable_2 # Retorna las 3 variables


try:
  datos = int(input("Ingresa el número de datos que deseas agregar: ")) # Ingrese el número de datos que quiere agregar
  lista = [] # Lista vacia
  for n in range(datos): # Ciclo for para agregar el número de datos
    numero = int(input("Ingresa el número: ")) # # Ingresa el entero
    lista.append(numero) # Agregarlo a la lista
  print("Esta es tu lista de números: \n"+ str(lista)) # Imprime la lista
  suma_mayor, numero_1, numero_2 = sum_may(datos, lista) # Ejecutar la función
  print("La mayor suma entre datos consecutivos es "+ str(suma_mayor) +" que es dado por: "+ str(numero_1) +" y "+ str(numero_2) ) # Imprimir resultado
except Exception as e: # Error en caso de que no ingrese números
  print(f"Error: {e}") # Imprime el error
  print("probalemente no ingresaste un número")
```

#### 1-5

El usuario ingresa la lista con valores que el desea, la función crea una lista igual pero con las variables organizadas en orden alfabetico, luego trabajabamos con la lista normal y buscamos si hay palabras repetias, en caso de que si agregamos una lista de palabras repetidas. Ahora con la lista de palabras orgazniadas alfabeticamente buscamos si hay palabras iguales ya que asi serian palabras con iguales caracteres, las que cumplan ese condición las agregamos a la lista de palabras repetidas. ¿Porque dos listas distintas? Al hacer el codigo note que si dejaba repetir muchas veces los ciclos, este repetia palabras que no estaban repetidas, por lo que solo dejamos que se ejecute una vez y al agregarlo a la lista dejamos que solo se agregue una vez impidiendo que las repetidas no sean agregadas. Finalmetne sumamos las dos listas, y esta lista es la que retornamos de la función.

Ingresamos un try al final que esta principalmente por si al momento de ingresar la cantidad de palabras se ingresa un númeoro o caracter. El otro es un raise que agregamos en caso de que al ingresar las palabras, se ingresen números o caracteres.

``` python
def palabras_con_mismos_caracteres(lista): # Lista
  lista_copia = [] # Lista copia
  lista_pal_rep = [] # Lista por si hay palabras repetidas
  lista_repetidos = [] # Lista de caracteres repetidos

  for n in lista: # Ciclo for para cada palabra de la lista
    n = ''.join(sorted(n)) # Organiza la palabra en orden alfabetico (paz = apz)
    lista_copia.append(n) # Se agrega en la lista copia

  for j in range(len(lista)): # Ciclo para dato 1
    for l in range(len(lista)): # Ciclo para dato 2
      if j == l: # Si estan en la misma posición 
        continue # Continuamos, DUHHH seria bobo comparar dos cosas
      else: # En caso de que no
        if lista[j] == lista[l]: # Si hay dos elementos iguales que no sean de la misma posición 
          if lista[j] in lista_pal_rep: # Si ya esta el elemento no lo agrega
            continue # Continua al siguiente dato
          else: # En caso de que no
            lista_pal_rep.append(lista[j]) # Agrega el elemento a la lista de palabras repetidas

  for i in range(len(lista_copia)): # Ciclo 1 para dato 1
    for k in range(len(lista_copia)): # Ciclo para datos 2
      if i == k: # Si estan en la misma posición
        continue # Continuamos, DUHHH seria bobo comparar dos cosas
      else: # En caso de que no
        if lista_copia[i] == lista_copia[k]: # Si hay dos elementos iguales que no sean de la misma posición
          if lista[i] in lista_repetidos: # Si ya esta el elemento no lo agrega
            continue # Continua al siguiente dato
          else: # En caso de que no
            lista_repetidos.append(lista[i]) # Agrega el elemento a la lista de repetidos

  lista_repetidos = lista_repetidos + lista_pal_rep # Sumamos la lista de repetidos con la lista de palabras repetidas
  return lista_repetidos

try:
  datos = int(input("Ingresa las pañabras que deseas agregar: ")) # Ingrese el número de palabras que quiere agregar
  lista = [] # Lista vacia
  for n in range(datos): # Ciclo for para agregar el número de datos
    palabra = input("Ingresa la palabra: ") # Ingresa las palabras
    if not palabra.isalpha():  # Verificar si la entrada contiene solo letras
        raise ValueError("Solo se permiten letras.")
    lista.append(palabra) # Agregarlo a la lista
  print("Esta es tu lista: \n"+ str(lista)) # Imprime la lista
  ejec =  palabras_con_mismos_caracteres(lista) # Ejecuta el resultado   
  print("La lista de palabras que repiten caracteres es: \n"+ str(ejec)) # Imprime el resultado final
except Exception as e: # Error en caso de que no ingrese algo correcto
  print(f"Error: {e}") # Imprime el error
  print("probalemente no ingresaste un número")
```
### 2

This Python code defines several classes representing geometric shapes and entities.

The Point class represents a point in 2D space and includes methods for moving the point and calculating the distance between two points.

The Line class represents a line segment connecting two points and calculates its length.

The Shape class serves as a superclass for geometric shapes. It includes methods for computing the area, perimeter, and inner angles of a shape. This class is not intended to be instantiated directly but serves as a base for subclasses.

The Triangle, Rectangle, Square, Isoceles, Equilateral, Scalene, and Trirectangle classes represent specific types of shapes and inherit from the Shape class. Each subclass implements methods specific to its type, such as checking if the shape meets certain criteria (e.g., being an equilateral triangle or a square) and computing its area, perimeter, and inner angles accordingly.

Overall, these classes provide a modular and extensible way to work with geometric shapes in Python, allowing for easy addition of new shapes and functionality.

Decidi agegarle un unico try que esta principalmente para analizar si el usuario en alguno de los puntos ingreso algo diferente a un número, no incluyo más ya que realmente las otra caractersiticas estan medianamente contrlada con otras opciones al try-except, por ejemplo en caso de ingresar 3 o 4 puntos, si ingresa un número diferente se seguira ejecutando pidinedo que ingrese algo correcto, pero si ingresa algo que no es número saltara el try con error int(), de igual manera si no ingresa 4 puntos que formen cuadrado o rectangulo, el codigo no se ejecutara.
```python
import math

class Point:
    # Definition of the Point class
    definition: str = "Abstract geometric entity that represents a location in space."

    # Constructor method for the Point class
    def __init__(self, x: float = 0, y: float = 0):
        self.x = x
        self.y = y

    # Method to move the point to a new location
    def move(self, new_x: float, new_y: float):
        self.x = new_x
        self.y = new_y

    # Method to reset the point to the origin
    def reset(self):
        self.x = 0
        self.y = 0
    
    # Method to calcule the distance of two points
    def compute_distance(self, point)-> float:
        distance = (((self.x - point.x)**2) + ((self.y - point.y)**2))**(0.5)
        return distance

class Line:
    # Constructor method to initialize the Line object with start and end points
    def __init__(self, start, end):
        self.start = start  # Start point of the line
        self.end = end      # End point of the line
        self.length = start.compute_distance(end)
        

class Shape: # Super class
    def __init__(self, regular: bool, vertices: list, edges: list, inner_angles: list):
        self.regular = regular # The form is regular?
        self.vertices = vertices # Vertices of the form
        self.edges = edges  # Calculate the length of the points
        self.inner_angles = inner_angles # Angles
    
    def compute_area(self): # Funtion to calcule the area
        pass
    
    def compute_perimeter(self): # Funtion to calculate the perimeter
        pass
    
    def compute_inner_angles(self): # Funtion to calculate angles
        pass

class Triangle(Shape): # Class
    def __init__(self, regular:bool, vertices:list, edges:list, inner_angles:list):
        super().__init__(regular, vertices, edges, inner_angles)
        self.compute_perimeter() # Call perimeter 
    
    def compute_perimeter(self):
        if len(self.edges) == 3: # Len of vertices need to be three
            perimeter = self.edges[0] + self.edges[1] + self.edges[2]
            self.perimeter = perimeter
            return perimeter # Return the perimeter
        pass

    def compute_area(self):
        if len(self.edges) == 3:
            s_heron = self.perimeter / 2 # I use the heron formula to calculate the area because it´s funtion for all triangles
            area = (s_heron*(s_heron-self.edges[0])*(s_heron-self.edges[1])*(s_heron-self.edges[2]))**0.5
            return area
        else:
            pass
    
    def compute_inner_angles(self):
        if len(self.edges) == 3: # We use arcoseno to calculate the angles of the traingle, this funtion in all triangles
            angle_a = math.degrees(math.acos((self.edges[1]**2 + self.edges[2]**2 - self.edges[0]**2) / (2 * self.edges[1] * self.edges[2])))
            angle_b = math.degrees(math.acos((self.edges[2]**2 + self.edges[0]**2 - self.edges[1]**2) / (2 * self.edges[0] * self.edges[2])))
            angle_c = math.degrees(math.acos((self.edges[0]**2 + self.edges[1]**2 - self.edges[2]**2) / (2 * self.edges[0] * self.edges[1])))
            self.inner_angles = [angle_a, angle_b, angle_c]
            return self.inner_angles
        else: pass

class Rectangle(Shape): # Class 
    def __init__(self, regular:bool, vertices:list, edges:list, inner_angles:list):
        super().__init__(regular, vertices, edges, inner_angles)
        self.is_rectangle()
    
    def is_rectangle(self): # Try to see if the points that the user enter make a rectangle
        if len(self.edges) == 4:
            sorted_vertices = sorted(self.vertices, key=lambda point: point.x) # Order the points
            if sorted_vertices[0].x == sorted_vertices[1].x:
                if sorted_vertices[2].x == sorted_vertices[3].x:
                    if sorted_vertices[0].y == sorted_vertices[2].y:
                        if sorted_vertices[1].y == sorted_vertices[3].y: # If they are a rectangle
                            width = self.vertices[2].x - self.vertices[0].x # Calculate the width
                            height = self.vertices[1].y - self.vertices[0].y # Calculate the height
                            self.width = width
                            self.height = height
                            return True
                        else:
                            return False # In all other cases the form is not a rectangle, and base of that we don´t need to do the other
                    else: 
                        return False
                else:
                    return False
            else: 
                return False
        else:
            return False
            
    def compute_perimeter(self):
        if len(self.edges) == 4:
            perimeter = (2*self.width + 2*self.height) # Calculate perimeter in base of with and height
            return perimeter
        else:
            pass

    def compute_area(self):
        if len(self.edges) == 4:
            area = self.height * self.width # Caclulate the area of a form with 4 lines
            return area
        else:
            pass
    
    def compute_inner_angles(self):
        if len(self.edges) == 4:
            self.inner_angles = [90, 90, 90, 90] # If is a rectangle, you don´t need to calculate angles, there are 90 
            return self.inner_angles
        else: pass

class Square(Rectangle): # Class Herence
    def __init__(self, regular:bool, vertices:list, edges:list, inner_angles:list):
        super().__init__(regular, vertices, edges, inner_angles)
    
    def is_square(self):
        super().is_rectangle() # Prove if is a rectangle but why?
        if self.is_rectangle == True:
            if self.height == self.width: # To call this things and see if they are equal, in case that not, it´s not a square
                return True # Is square
            else:
                return False # Is´nt an square
        else:
            return False
            
    def compute_perimeter(self):
        return super().compute_perimeter() # Call perimeter from rectangle

    
    def compute_area(self):
        return super().compute_area() # Call area from rectangle
    
    def compute_inner_angles(self):
        return super().compute_inner_angles() # Call inner angles from rectangle
        
class Isoceles(Triangle): # Class Herence
    def __init__(self, regular:bool, vertices:list, edges:list, inner_angles:list):
        super().__init__(regular, vertices, edges, inner_angles)
        
    def is_isoceles(self): # Define if is a isoceles, 2 lines need to be equal
        if self.edges[0] == self.edges[1] or self.edges[0] == self.edges[2] or self.edges[1] == self.edges[2]:
            return True
        else: return False
    
    def compute_perimeter(self):
        return super().compute_perimeter() # Call perimeter in traingle
    
    def compute_area(self):
            return super().compute_area() # Call area in trinagle
    
    def compute_inner_angles(self): # Call inner angles in triangle
        return super().compute_inner_angles()

class Equilateral(Triangle): # Class herence
    def __init__(self, regular:bool, vertices:list, edges:list, inner_angles:list):
        super().__init__(regular, vertices, edges, inner_angles)
        
    def is_equilateral(self): # We need to see if is a equilateral, it is if all the lines are equal
        if self.edges[0] == self.edges[1] and self.edges[1] == self.edges[2]:
            return True
        else: return False
    
    def compute_perimeter(self):
        return super().compute_perimeter() # Call perimeter from triangle

    
    def compute_area(self):
        return super().compute_area() # Call area from triangle
    
    def compute_inner_angles(self):
        return super().compute_inner_angles() # Call inner angles from triangle

class Scalene(Triangle): # Class herence
    def __init__(self, regular:bool, vertices:list, edges:list, inner_angles:list):
        super().__init__(regular, vertices, edges, inner_angles)
        
    def is_scalene(self): # We need to si if is scalen, the three lines are diferente
        if self.edges[0] != self.edges[1] and self.edges[0] != self.edges[2] and self.edges[1] != self.edges[2]:
            return True
        else: return False
    
    def compute_perimeter(self): # Call perimeter from triangle
        return super().compute_perimeter()
    
    def compute_area(self):
        return super().compute_area() # Call area from tringle

    
    def compute_inner_angles(self):
        return super().compute_inner_angles() # Call inner angles from triangle

class Trirectangle(Triangle): #Class herence
    def __init__(self, regular:bool, vertices:list, edges:list, inner_angles:list):
        super().__init__(regular, vertices, edges, inner_angles)

    def is_trirectangle(self): # We need to si if a rectnagle triangle, we considere a few calculate mistake that happens in python
        super().compute_inner_angles()
        for i in self.inner_angles:
            if abs(i - 90) < 0.1:
                return True
        else: return False
            
    def compute_perimeter(self):
        return super().compute_perimeter() # call perimeter from triangle
    
    def compute_area(self): # call area from triangle
        return super().compute_area()
    
    def compute_inner_angles(self): # call inner angles from triangle
        return super().compute_inner_angles()
    
    
try:
    # Ask the user whether they want to input 3 or 4 points
    figure = int(input("You want to enter 3 or 4 points: "))
    flag = True

    # Validate the user input
    while flag == True:
        if figure == 3 or figure == 4:
            break
        else:
            print("IS 3 OR 4 ")
            figure = int(input("You want to enter 3 or 4 points: "))

    # Process based on the number of points entered by the user
    if figure == 3:
        # Obtain the coordinates of three points from the user
        p1 = Point(int(input("Enter the x coordinate of the p1: ")), int(input("Enter the y coordinate of the p1: ")))
        p2 = Point(int(input("Enter the x coordinate of the p2: ")), int(input("Enter the y coordinate of the p2: ")))
        p3 = Point(int(input("Enter the x coordinate of the p3: ")), int(input("Enter the y coordinate of the p3: ")))

        # Create lines using the provided points
        line1 = Line(p1, p2)
        line2 = Line(p2, p3)
        line3 = Line(p3, p1)

        # Create instances of different types of triangles
        triangulo = Isoceles(True, [p1, p2, p3], [line1.length, line2.length, line3.length], [0, 0, 0])
        triangulo_1 = Equilateral(True, [p1, p2, p3], [line1.length, line2.length, line3.length], [0, 0, 0])
        triangulo_2 = Scalene(True, [p1, p2, p3], [line1.length, line2.length, line3.length], [0, 0, 0])
        triangulo_3 = Trirectangle(True, [p1, p2, p3], [line1.length, line2.length, line3.length], [0, 0, 0])
        print(triangulo_3.is_trirectangle())

        # Determine the type of triangle and perform calculations accordingly
        if triangulo.is_isoceles() == True:
            if triangulo_3.is_trirectangle() == True:
                print("The triangle is an isoceles and a rectangle triangle")
                per_trin = triangulo.compute_perimeter()
                print("The perimeter of the triangle is: " + str(per_trin))
                area_trin = triangulo.compute_area()
                print("The area of the triangle is: " + str(area_trin))
                angles_trin = triangulo.compute_inner_angles()
                print("The inner angles of the triangle is: " + str(angles_trin))
            else:
                print("The triangle is an isoceles")
                per_trin = triangulo.compute_perimeter()
                print("The perimeter of the triangle is: " + str(per_trin))
                area_trin = triangulo.compute_area()
                print("The area of the triangle is: " + str(area_trin))
                angles_trin = triangulo.compute_inner_angles()
                print("The inner angles of the triangle is: " + str(angles_trin))

        elif triangulo_1.is_equilateral() == True:
            print("The triangle is an Equilateral")
            per_trin = triangulo_1.compute_perimeter()
            print("The perimeter of the triangle is: " + str(per_trin))
            area_trin = triangulo_1.compute_area()
            print("The area of the triangle is: " + str(area_trin))
            angles_trin = triangulo_1.compute_inner_angles()
            print("The inner angles of the triangle is: " + str(angles_trin))

        elif triangulo_2.is_scalene() == True:
            if triangulo_3.is_trirectangle() == True:
                print("The triangle is an Scalene and a rectangle triangle")
                per_trin = triangulo_2.compute_perimeter()
                print("The perimeter of the triangle is: " + str(per_trin))
                area_trin = triangulo_2.compute_area()
                print("The area of the triangle is: " + str(area_trin))
                angles_trin = triangulo_2.compute_inner_angles()
                print("The inner angles of the triangle is: " + str(angles_trin))
            else: 
                print("The triangle is an Scalene")
                per_trin = triangulo_2.compute_perimeter()
                print("The perimeter of the triangle is: " + str(per_trin))
                area_trin = triangulo_2.compute_area()
                print("The area of the triangle is: " + str(area_trin))
                angles_trin = triangulo_2.compute_inner_angles()
                print("The inner angles of the triangle is: " + str(angles_trin))

    if figure == 4:
        # Obtain the coordinates of four points from the user
        p1 = Point(int(input("Enter the x coordinate of the p1: ")), int(input("Enter the y coordinate of the p1: ")))
        p2 = Point(int(input("Enter the x coordinate of the p2: ")), int(input("Enter the y coordinate of the p2: ")))
        p3 = Point(int(input("Enter the x coordinate of the p3: ")), int(input("Enter the y coordinate of the p3: ")))
        p4 = Point(int(input("Enter the x coordinate of the p4: ")), int(input("Enter the y coordinate of the p4: ")))

        # Sort the points based on their x-coordinate
        listi = [p1, p2, p3, p4]
        listi = sorted(listi, key=lambda p: (p.x, p.y))

        # Create lines using the provided points
        line1 = Line(listi[0], listi[1])
        line2 = Line(listi[0], listi[2])
        line3 = Line(listi[1], listi[3])
        line4 = Line(listi[2], listi[3])
        # Create instances of Rectangle and Square
        rectangulo = Rectangle(True, [listi[0], listi[1], listi[2], listi[3]], [line1.length, line2.length, line3.length, line4.length], [0, 0, 0, 0])
        cuadrado = Square(True, [listi[0], listi[1], listi[2], listi[3]], [line1.length, line2.length, line3.length, line4.length], [0, 0, 0, 0])

        # Check if the figure is a square or a rectangle
        if cuadrado.is_square() == True: # If it's a square
            print("The form is a square")
            per_cua = cuadrado.compute_perimeter() # Compute the perimeter
            print("The perimeter of the square is: " +str(per_cua))
            area_cua = cuadrado.compute_area() # Compute the area
            print("The area of the square is: " +str(area_cua))
            angles_cua = cuadrado.compute_inner_angles() # Compute the inner angles
            print("The inner angles of the square is: " +str(angles_cua))

        elif rectangulo.is_rectangle() == True: # If it's a rectangle
            print("The form is a Rectangle")
            per_rect = rectangulo.compute_perimeter() # Compute the perimeter
            print("The perimeter of the rectangle is: " +str(per_rect))
            area_rect = rectangulo.compute_area() # Compute the area
            print("The area of the rectangle is: " +str(area_rect))
            angles_rect = rectangulo.compute_inner_angles() # Compute the inner angles
            print("The inner angles of the rectangle is: " +str(angles_rect))
        
        else:
            raise TypeError("You dont't enter points that creat a square or rectangle.")
except Exception as e: # Error en caso de que no ingrese números
  print(f"Error: {e}") # Imprime el error
  print("Probably you enter something different for a number")
```
