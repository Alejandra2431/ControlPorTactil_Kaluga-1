Informe Control por Táctil 

Objetivo 

Implementar un sistema de control para el LED RGB de la ESP32-S2-Kaluga-1  

Mediante los botones táctiles, utilizando interrupciones que encolan eventos hacia una tarea de FreeRTOS para asegurar una operación fluida y sin bloqueos. 

Conexiones  

La placa de extensión se conectó al Touch FPC Connector de la ESP32-S2-Kaluga-1 utilizando el cable plano (FPC) de 20 pines. Para garantizar que los pines queden dedicados exclusivamente al subsistema táctil, todos los microinterruptores (DIP switches) deben encontrarse en posición OFF. También, el LED RGB se conecta al GPIO45, requiriendo que el jumper correspondiente esté colocado físicamente en la placa. 

Compilación y flasheo 

El proyecto fue desarrollado utilizando ESP-IDF desde Visual Studio Code. Se utilizó la opción Build, Flash and Monitor de la extensión de ESP-IDF, que permitió compilar el firmware, cargarlo en la placa y se abrir el monitor serie para observar su funcionamiento.. 

Resultado observado 

El sistema muestra en el monitor serie los valores de benchmark y los ubrales calibrados para cada botón activo. Al presionar los botones táctiles asignados, la rutina de interrupción encola el evento de manera instantánea y segura, permitiendo que la tarea procese la acción para modificar el estado, color, brillo o modo de parpadeo LED RGB. La consola registra el canal pulsado, su estado y la métrica exacta de latencia entre la interrupción y la tarea, cumpliendo con los requerimientos de la arquitectura asíncrona. 

Extensiones implementadas 

Además de los requisitos mínimos, se incorporaron las siguientes funcionalidades opcionales: 

Pulsación larga vs corta 

Medir e imprimir latencia ISR  

Deslizamiento: detectar el orden VOL_DOWN → PLAY → VOL_UP. 