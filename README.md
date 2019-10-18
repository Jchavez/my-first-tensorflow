# my-first-tensorflow
Comenzando en tensorflow usando Katacoda
https://katacoda.com/courses/tensorflow/playground

## AGENDA
1) Cómo usar los conceptos de TensorFlow Core

### Cómo usar los conceptos de TensorFlow Core
#### CONCEPTO#1: Python
1) Para comenzar a trabajar con Python Shell, ejecute el siguiente comando:
<code> python </code>
Puedes usar <code>quit()</code> para salir de la Shell

2) Para comenzar a trabajar con TensorFlow, primero debe importarlo para dar acceso a Python a todos sus recursos
<code>import tensorflow as tf</code>

Más adelante, cada vez que desee utilizar clases, métodos o símbolos de TensorFlow, simplemente debe referirse a la variable <code> tf </code>.


#### CONCEPT#2: Tensor
Matriz de cualquier cantidad de dimensiones
 
#### CONCEPT#3: Computational Graph
Significa que primero está construyendo su gráfico computacional y luego una vez que tiene todos los elementos juntos, lo ejecuta.

3) 
<code>
input1 = tf.constant(2.0)
input2 = tf.constant(5.0)
</code>

y

<code>
  print(input1, input2)
 </code>

#### CONCEPT#4: Sesion
Para evaluar el gráfico computacional, o cualquier nodo para el caso, debe ejecutarlo dentro de una sesión. La sesión se puede crear con el siguiente código:
<code>
  sess = tf.Session()
</code>

Una vez que la sesión está activada, puede usar el método <code> run </code> para obtener los valores. Intenta hacerlo para entradas constantes:
  <code>
print(sess.run([input1, input2]))
  </code>
