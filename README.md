# ScriptVectoresyMovimientoRecta

 Práctica 3: C#. Programación de Scripts

Vectores-y-Movimiento

1. Ejercicio 1
    Creo la variable __objetivo__ de tipo Vector3, dándole los valores _(-1.0f, 2f, 0.25f)_;
    para simular el vuelo de un avión, trasladando el objeto multiplicando la variable __objetivo__ por Time.deltaTime;

    ![Ejercicio 1](https://github.com/almadacv/ScriptVectoresyMovimientoRecta/blob/main/Gif/_E1_1.gif)

2. Ejercicio 2
    Duplicando los valores de X,Y y Z de la variable objetivo, la velocidad de traslación aumenta.
    Cuando _normalizamos_ el vector, la velocidad de traslación se mantiene constante, para modificar la velocidad de traslación utilizamos la variable __Speed__, que multiplicamos por el vector normalizado. Debido a las variaciones entre la representación de un cuadro y el otro, utilizamos _Time.deltaTime_ para suavizar el movimiento del objeto.

    ![Ejercicio 2](https://github.com/almadacv/ScriptVectoresyMovimientoRecta/blob/main/Gif/_E2_Dupl_1.gif)

3. Ejercicio 3,4 , 5 y 6
    Para saber la posición del objetivo con respecto al cual nos vamos a mover, utilizamos el siguiente bloque de código:

    ```
    goal = GameObject.Find("/CapsuleGoal").transform; 
    this.transform.LookAt(goal.position);
    ```

    Hacemos la diferencia entre las posiciones del objetivo y nuestra posición actual y realizamos una traslación a las coordenadas obtenidas, hacendo uso da variable Speed, para tenermos control de la velocidad de movimiento.

    ![Ejercicio 3](https://github.com/almadacv/ScriptVectoresyMovimientoRecta/blob/main/Gif/_E3.gif)

4. Ejercicio 4

    ![Ejercicio 4](https://github.com/almadacv/ScriptVectoresyMovimientoRecta/blob/main/Gif/_E4.gif)

5. Ejercicio 5

    ![Ejercicio 5](https://github.com/almadacv/ScriptVectoresyMovimientoRecta/blob/main/Gif/_E5.gif)

6. Ejercicio 6

    ![Ejercicio 6](https://github.com/almadacv/ScriptVectoresyMovimientoRecta/blob/main/Gif/_E6.gif)

    Completando los pasos 4,5 y 6, tenemos el código:

    ```
    Vector3 direction = goal.position - this.transform.position;
    Debug.Log(goal.position);
    Debug.Log(this.transform.position);
    Debug.DrawRay(this.transform.position, direction, Color.red);
    if (direction.magnitude > accuracy)
    this.transform.Translate(direction.normalized * speed * Time.deltaTime, Space.World); 
    ```

7. Ejercicio 7
    Para mover el cubo, asigné movimiento de traslación, para cada una de las flechas,multiplicando pelo _Time.deltaTime_ para suavizar os movimentos.

    ej.

    ```
    if (Input.GetKey(KeyCode.UpArrow))
    {
        this.transform.Translate(Vector3.forward * Time.deltaTime * SpeedDeMov);
    }
    ```

    ![Ejercicio 7](https://github.com/almadacv/ScriptVectoresyMovimientoRecta/blob/main/Gif/_E7.gif)

8. Ejercicio 8
     - A)  Los objetos permanecen inmóviles, no podemos moverlos. Las leyes de la física no se aplican a ellos.

    ![Ejercicio 8.A]( https://github.com/almadacv/ScriptVectoresyMovimientoRecta/blob/main/Gif/A.gif )

     - B)  Las esferas están sujetas a las leyes de la física, por lo que se ven afectadas por una gravedad diferente a la del cubo. Al chocar el cubo con las esferas obtenemos resultados extraños, la física no se aplica correctamente.

    ![Ejercicio 8.B]( https://github.com/almadacv/ScriptVectoresyMovimientoRecta/blob/main/Gif/B_1_1.gif )

     - C)  todos los objetos tienen física, por lo que la gravedad los atrae hacia el suelo. Cuando el cubo choca con la esfera, la mueve, al igual que la otra esfera.

    ![Ejercicio 8.C]( https://github.com/almadacv/ScriptVectoresyMovimientoRecta/blob/main/Gif/C_massa1.gif )

     - D)  Tenemos un resultado similar en el punto C, pero a pesar de que la esfera tiene mayor masa, tanto ella como el cubo caen al mismo tiempo, rodando con mayor velocidad que antes en el punto C.

    ![Ejercicio 8.D](https://github.com/almadacv/ScriptVectoresyMovimientoRecta/blob/main/Gif/Dmassa10.gif )

     - E)  Todos los objetos están sujetos a las leyes de la física, pero el cubo no choca con la esfera, sino que perfora el cubo y el suelo. Cuando la esfera choca con el personaje, rebota en la otra esfera, de acuerdo con las leyes de la física.

    ![Ejercicio 8.E](https://github.com/almadacv/ScriptVectoresyMovimientoRecta/blob/main/Gif/E.gif )

     - F)  Similar al punto anterior, las esferas siguen las leyes de la física, pero el cubo no, a pesar de tener el componente RigidBody, no cambia de posición al chocar con la esfera.

    ![Ejercicio 8.F](https://github.com/almadacv/ScriptVectoresyMovimientoRecta/blob/main/Gif/F.gif )

     - G)  Todos los objetos siguen las leyes de la física. se ven afectados por la gravedad y cambian de posición cuando chocan.

    ![Ejercicio 8.G](https://github.com/almadacv/ScriptVectoresyMovimientoRecta/blob/main/Gif/G.gif )

     - H)  Similar al punto anterior, los objetos se ven afectados por las leyes de la física, pero al restringir las rotaciones del cubo, el cubo se traslada al chocar con las esferas, pero no gira.

    ![Ejercicio 8.H](https://github.com/almadacv/ScriptVectoresyMovimientoRecta/blob/main/Gif/H.gif )

9. Ejercicio 9

    Reutilicé el código usado en el ejercicio 7 y agregué rotaciones. Para rotar usé el número 1 e o numero 2y el `transform.Rotate`.
    ej.

    ```
    if (Input.GetKey(KeyCode.Keypad1))
    {
        this.transform.Rotate(Vector3.up, SpeedDeMov + Time.deltaTime);
    }

    if (Input.GetKey(KeyCode.Keypad2))
    {
        this.transform.Rotate(Vector3.up, -SpeedDeMov + Time.deltaTime);
    }
    ```

    tenemos la variable _SpeedDeMov_ para controlar la velocidad a traves del inspector.
    ```public float SpeedDeMov = 1.0f;```

    ![Ejercicio 9](https://github.com/almadacv/ScriptVectoresyMovimientoRecta/blob/main/Gif/_E9.gif)

10. Ejercicio 10

    En el cubo, creé un método __AddScore()__, responsable de agregar puntos al puntaje y mostrar el puntaje en la consola. En cada cilindro adjunto un script que _OnTriggerEnter_, cambia el color del cilindro a rojo, llama al método __AddScore()__ y muestra en la consola el nombre del cilindro en el que chocó el cubo.  En _OnTriggerExit_, cambiamos el color del cilindro a color blanco.

    ![Ejercicio 10](https://github.com/almadacv/ScriptVectoresyMovimientoRecta/blob/main/Gif/_E10.gif)
