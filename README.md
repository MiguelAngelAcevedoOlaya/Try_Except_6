# CHALLENGE 6

### 1

##### 1-1

En el primer punto le permitimos al usuario introducir los dos números que desee, luego de eso ejectuamos la función que le recuerda al usuario los simbolos que representan a las diferentes operaciones matemáticas y en base a lo que ingrese el usuario devuelve la operación de los dos números.

Todo esto lo hicimos mediante ciclos if y while.

Se incluyeron dos excepciones, una dentro de la función que salta cuando el usuario ingresa algo diferente a las posibles  operaciones (+,-,*,/,//), esto es un raise dentro de las opciones. La otra excepción es al final, el cual salta en caso de que el usuario ingrese algo diferente a un número, este esta enforma de try-except.

```
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

```
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

```
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

```

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

```
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
