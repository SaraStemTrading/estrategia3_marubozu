# ESTRATEGIA Nº3: Marubozu en banda media
#### Por Sara STEM
>_El éxito es quererte, querer lo que haces y querer cómo lo haces._ - Maya Angelou.

## Descripción de la estrategia

Esta semana STEM, dedicada a hablar sobre la vela Marubozu, he programado en Python la estrategia con la que empecé a operar en Bolsa. Consiste en comprar tras formarse una vela completa (llamada marubozu o longline) cruzando a la banda media de Bollinger. El stop se mueve a la altura de la media simple de 20 sesiones siempre que el precio haya superado al alza la banda superior de Bollinger. Para el caso bajista es justo al revés. 

En este artículo, he hecho el testeo con el CRUDO en diario, pero al descargar la estrategia en tu ordenador, puedes probar con cualquier otro producto y cualquier otro timeframe, además de poder cambiar los parámetros de capital y gestión de riesgo como quieras para valorar los resultados.

Yo hago mi operativa de Trading cada día con el broker XTB, con el que puedes abrir una cuenta real [aquí](https://www.xtb.com/es/abrir-cuenta-real?cxd=35312_576021&affid=35312&utm_source=affiliate&utm_medium=TextLink&utm_campaign=35312&utm_content=REAL%20GEO&utm_term=Spanish).

### Ejemplo de una entrada
![entrada](https://www.sarastem.com/wp-content/uploads/2022/06/entrada_estrategia3.png)
## Instalación previa

Para descargar esta estrategia, primero debemos tener descargado "Git" y "Python3" en nuestro ordenador. Los podemos encontrar en:

- __Git__: https://git-scm.com/downloads
- __Python3__: https://www.python.org/downloads/

Además, debemos tener un entorno de desarrollo o IDE para poder abrir los archivos escritos en Python. Yo recomiendo Visual Studio Code por su simplicidad de uso. Lo puedes descargar aquí:

- __Visual Studio Code__: https://code.visualstudio.com/download
## Visual Studio Code

Una vez descargado todo, abrimos Visual Studio Code. Pinchamos en "Terminal"->"Nuevo terminal".
Se abrirá un terminal en la parte baja donde escribiremos los siguientes pasos:

1. Entramos en la carpeta donde vamos a alojar el proyecto, por ejemplo el escritorio, y escribimos el siguiente código: 

`cd Desktop`

2. Una vez dentro, clonamos el proyecto escribiendo lo siguiente:

`git clone https://github.com/SaraStemTrading/estrategia2_patron3velas.git`

3. Entramos en la carpeta especificada:

`cd estrategia2_patron3velas`

4. Una vez dentro, desplegamos un entorno virtual del siguiente modo: 

`python -m venv env`

Si no funciona, probamos con:

`python3 -m venv env`

5. Activamos el entorno virtual "env":

En Windows: 

`env\Scripts\activate.bat`

En Mac: 

`source ./env/bin/activate`

Nos fijaremos que estamos dentro del entorno porque aparece __(env)__ en la línea de comandos.

6. Por útlimo, debemos instalar las dependencias para que el algoritmo funcione correctamente.
Esto lo hacemos con la ayuda del archivo __"requirements.txt"__. Para su instalación, escribimos: 

`pip install -r requirements.txt`

7. Finalmente, en el explorador de la izquierda en Visual Studio Code, podemos __abrir la carpeta__ donde hemos instalado el algoritmo (hemos usado el escritorio) para ver todos los archivos.

## Parámetros de la estrategia: archivo .env 

Una vez instalado todo lo anterior, y abierta la carpeta, vamos a reescribir el archivo __.env__, fundamental para la correcta ejecución de nuestra estrategia, ya que tendrá todos los datos iniciales necesarios. En concreto, son los siguientes parámetros:

- __activo__: Aquí debemos poner entre comillas el ticker del activo al que queremos aplicarle la estrategia y ver el backtesting. Yo he usado el CRUDO (BZ=F). Tienes la lista completa en la web de Yahoo Finanzas, dentro del apartado Mercados, puedes buscar el producto que quieras: https://es.finance.yahoo.com.
- __period__: Esto solo se debe rellenar para datos intradía. Aquí debemos poner entre comillas el periodo de tiempo en el que queremos que nos muestre los datos, y debe inferior a 60 días.
Adjunto imagen con los periodos y timeframes disponibles:
![periodyf](https://www.sarastem.com/wp-content/uploads/2022/06/periodsYF.png)
- __interval__: Aquí podremos entre comillas el timeframe que queremos para testear nuestra estrategia. En este caso, he usado un timeframe diario.
- __years__: Esto solo sirve para datos en timeframe diarios. Dejaremos un 1 por defecto. Aquí debemos poner el número de años que queremos testear en nuestra estrategia.
- __periodo_bb__: Aquí debemos poner el número de periodos para el cálculo de las bandas de Bollinger, yo lo he hecho por defecto con 20 periodos.
- __riesgo_op__: Aquí ponemos el riesgo por operación que queremos asumir. Se pone en tantos por uno. Yo he trabajado con un riesgo del 2% sobre el capital en cada operación.
- __capital__: Aquí ponemos el capital con el que queremos testear nuestra estrategia.
- __comision__: Poner aquí la comisión a aplicar por operación, en tantos por uno. He usado 0,2% en cada operación.
- __margen__: Finalmente, ponemos el margen de apalancamiento, en tantos por uno. En mi caso he usado 1:50, es decir, 0,05.

## Funcionamiento del algoritmo
Una vez rellenados los apartados anteriores, podemos ejecutar el código de nuestra estrategia desde Visual Studio Code y valorar los resultados obtenidos, que aparecerán en el terminal de la plataforma. Esto lo haremos escribiendo en el terminal:

`python3 estrategia2_patron3velas.py`

**_Nota:_** Recuerda que para probar otros parámetros en esta estrategia, solo debes modificar el archivo .env

## Resultados
Los resultados de esta estrategia nº2 (con  los parámetros indicados en el archivo .env), se pueden ver en el terminal de Visual Studio Code. En concreto, se verá un dataframe con los siguientes datos:

- __Rentabilidad (%)__
- __Número de operaciones__
- __Ratio de aciertos (%)__
- __Máximo drawdown (%)__

Con toda esta información, puedes hacer pruebas y valorar los resultados para conseguir hacer trading rentable.

**¡Espero que te resulte de utilidad!**

PD: Toda ayuda o sugerencia en el código es bienvenida 😉

**_Sara STEM | Trading Algorítmico_** 👩🏻‍💻
