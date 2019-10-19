# Comenzando en tensorflow usando Katacoda
https://katacoda.com/courses/tensorflow/playground

## AGENDA
1) Cómo usar los conceptos de TensorFlow Core

### Cómo usar los conceptos de TensorFlow Core
#### CONCEPTO#1: Python
<p>Para comenzar a trabajar con Python Shell, ejecute el siguiente comando</p>
1) <code>python</code> <br />
<code>quit()</code> para salir de la Shell.

<p>Para comenzar a trabajar con TensorFlow, primero debe importarlo para dar acceso a Python a todos sus recursos</p>
2) <code>import tensorflow as tf</code>
<br />
Más adelante, cada vez que desee utilizar clases, métodos o símbolos de TensorFlow, simplemente debe referirse a la variable <code>tf</code>.


#### CONCEPTO#2: Tensor
Matriz de cualquier cantidad de dimensiones
 
#### CONCEPTO#3: Computational Graph
Significa que primero está construyendo su gráfico computacional y luego una vez que tiene todos los elementos juntos, lo ejecuta.
3) 
<code>
input1 = tf.constant(2.0)
input2 = tf.constant(5.0)
</code>

<br /><br />
Debido a que todavía estamos construyendo el gráfico, imprimir las entradas no mostrará los valores almacenados. Se mostrarán una vez que se evalúen los nodos.
4) 
<code>
  print(input1, input2)
</code>

#### CONCEPTO#4: Sesion
Para evaluar el gráfico computacional, o cualquier nodo para el caso, debe ejecutarlo dentro de una sesión. La sesión se puede crear con el siguiente código:
5)<code>sess = tf.Session()</code>

<br />
Una vez que la sesión está activada, puede usar el método <code>run</code> para obtener los valores. Intenta hacerlo para entradas constantes:
6)<code>print(sess.run([input1, input2]))</code>

Tenga en cuenta que esta vez el resultado son los valores numéricos reales esperados: 2.0 y 5.0.
Para terminar el gráfico necesitamos el tercer nodo y el método add.
7)<code>add_node = tf.add(input1, input2) </code>

Como anteriormente, puede ver diferentes salidas dependiendo de si el nodo fue o no evaluado.
8)<code>print(add_node)</code><br />
9)<code>print(sess.run(add_node))</code>
La primera línea muestra la información del tensor, la segunda, el resultado de agregar el cálculo: 7.0.

#### CONCEPTO#4: Placeholders
A diferencia de las constantes, donde proporciona el valor al definir el nodo, un `marcador de posición` espera los valores cuando se evalúa el gráfico. <br />
10)
<code>
p1 = tf.placeholder(tf.float32)
p2 = tf.placeholder(tf.float32)
</code>
<br /><br />
Acabamos de definir dos marcadores de posición que esperan valores flotantes. El nodo de adición se puede construir utilizando el método add o el operador +.
<br />
11)<code>add_ph = p1 + p2</code>
<br /><br />

La evaluación del gráfico que se construye con marcadores de posición difiere del que se construye solo con constantes. Para empezar, espera los valores de marcadores de posición en el parámetro feed_dict. Es un diccionario de nombres de marcadores de posición y valores correspondientes. Luego puede ejecutar el mismo gráfico con diferentes configuraciones.
12)
<code>
print(sess.run(add_ph, {p1: 2, p2: 5}))
print(sess.run(add_ph, {p1: 1.2, p2: 3.5}))
print(sess.run(add_ph, {p1: [1, 2], p2: [5, 8]}))
</code>
<br /><br />
#### CONCEPTO#4: Variables
Si desea trabajar con los parámetros que pueden cambiar sus valores al ejecutar el gráfico computacional, debe considerar el uso de variables. En el proceso de capacitación de aprendizaje automático, el objetivo es ajustar algunos coeficientes para que se ajusten mejor a la función optimizada.

Consideremos un modelo lineal simple y descubramos cómo puede cambiar manualmente los valores de las variables. Proporcionaremos valores x e y de los puntos de datos en los marcadores de posición:
13)
<code>
x = tf.placeholder(tf.float32)
y = tf.placeholder(tf.float32)
</code>

<br /><br />
El modelo lineal tiene una forma de f(x)= a*x+b. A y B son los parámetros. Utilizaremos variables para definirlas y asignar algunos valores predeterminados.
14)
<code>
a = tf.Variable([1], dtype=tf.float32)
b = tf.Variable([-2], dtype=tf.float32)
</code>
<br /><br />
15) <code>linear_model = a*x + b</code>

<br /><br />
Para ejecutar el gráfico computacional, primero debe inicializar las variables. Sus valores no se asignarán como a las constantes a menos que lo haga explícitamente:
16)
<code>
init = tf.global_variables_initializer()
sess.run(init)
</code>

<br /><br />
Ahora el modelo está listo para ser evaluado. Tenga en cuenta que debido a que el modelo lineal no tiene en cuenta los valores y, no es necesario proporcionarlos en el parámetro feed_dict.
17)
<code>
 print(sess.run(linear_model, {x:[0,1,2,3,4,5]}))
</code>

<br /><br />
Para calcular el error, puede usar el siguiente código
18)
<code>
squared_deltas = tf.square(linear_model - y)
loss = tf.reduce_sum(squared_deltas)
</code>

<br /><br />
Ejecutemos los cálculos con los valores de los marcadores de posición:
19)
<code>
feed_dict = {
  x:[0,1,2,3,4,5],
  y:[-1,-.5,0,.5,1,1.5] }
print(sess.run(loss, feed_dict))
</code>
Como puede ver, el número es alto, así que tratemos de ajustar la línea un poco mejor (línea marrón):
20)
<code>
assignA = tf.assign(a, [.25])
assignB = tf.assign(b, [0])
sess.run([assignA, assignB])
</code>

Entonces la función de pérdida con los mismos valores para los marcadores de posición daría el siguiente resultado.
21) <code>print(sess.run(loss, feed_dict))</code>

El valor es mejor, pero aún no es perfecto. Con los datos proporcionados podemos encontrar la coincidencia perfecta, ya que los puntos de datos forman la línea.
22) 
<code>
 assignA = tf.assign(a, [.5])
assignB = tf.assign(b, [-1])
sess.run([assignA, assignB])
print(sess.run(loss, feed_dict))
 </code>
 
En los escenarios del mundo real, el punto no sería la línea perfecta. La tarea de optimización sería encontrar los parámetros que mejor se ajustan a los datos (pero no idealmente) y el proceso en sí no sería manual. En el próximo tutorial, presentaremos una forma automatizada de ajustar las variables que utilizan los algoritmos de aprendizaje automático.
 
