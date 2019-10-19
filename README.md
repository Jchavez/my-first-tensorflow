# Comenzando en tensorflow usando Katacoda
https://katacoda.com/courses/tensorflow/playground

## AGENDA
1) Cómo usar los conceptos de TensorFlow Core

### Cómo usar los conceptos de TensorFlow Core
#### CONCEPTO#1: Python
Para comenzar a trabajar con Python Shell, ejecute el siguiente comando <br />
1) <code>python</code> <br />
Puedes usar <code>quit()</code> para salir de la Shell.

Para comenzar a trabajar con TensorFlow, primero debe importarlo para dar acceso a Python a todos sus recursos
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
