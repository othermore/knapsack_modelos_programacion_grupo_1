# Problema de la mochila - Modelos de Programación - Grupo 1
## Flujo de trabajo
### Entorno de desarrollo local
#### Opción Conga + Colab
Instalar siguiendo las [instrucciones que preparó Sonia](Documents/Configuración%20entorno%20Jupyter%20+%20Colab.pdf) si queremos usar Colab. De este modo tendremos una instalación local de Jupyter en un virtual env, y podremos ejecutar las bibliotecas de Ocean. Podremos usar tanto el editor Jupyter como el editor Colab de Google, o configurar Visual Studio u otro entorno que se pueda conectar al kernel de Jupyter para ejecutar el código.


#### Alternativa mínima: Solo Jupyter
Creamos el virtual env y instalamos todas las dependencias que necesitamos
```
python –m venv modelos_computacion

#ELEGIR UNA DE LAS SIGUIENTES OPCIONESdelos_computacion\Scripts\activate # en Windows
. modelos_computacion/bin/activate # en sistemas Unix

pip install dwave-ocean-sdk
pip install yfinance
pip install nbdime
pip install nbstripout
pip install tabulate
pip install pandas
pip install matplotlib
pip install ipykernel
pip install networkx
pip install jupyter-networkx
```

Configuramos el acceso a DWAVE
```
dwave auth login --oob
# UNA VEZ TERMINADO EL PROCESO DE LOGIN
dwave config create --auto-token
```

### Descargar el repositorio git

Dentro del directorio de nuestro virtual env y con el virtual env activo (veremos el nombre del virtual env entre paréntesis antes del prompt del sistema). "proyecto_mochila" es el nombre del directorio que se creará para descargar el repositorio

```
git clone https://github.com/soniamerayogonzalez/knapsack_modelos_programacion_grupo_1.git proyecto_mochila 
nbstripout --install
```

### Arrancando el Jupyter local
Si hemos seguido las instrucciones de Sonia, ya tendremos un Jupyter arrancado (y además aceptará conexiones de Colab). Si no, podemos arrancarlo así (proyecto_mochila es el directorio que se creó antes para descargar el repositorio, si usas otro, cambialó)
```
jupyter notebook proyecto_mochila
```

### Edición de los ficheros
Podemos editar los ficheros de muchas formas. 
- (recomendada) En local, con el servidor Jupyter (localhost:8888)
- Via colab, si hemos seguido las instruciones de Sonia, podemos ejecutar contra el kernel de nuestro jupyter (o del servidor que ha creado Sonia). Pero en ese caso tendremos que trabajar con una copia de los notebooks y luego volver a ponerlos en nuestro directorio para subirlos a git.

### Ejecucion del código
Si hemos hecho todo lo anterior, podremos ejecutar el código sin problema.

### Subiendo los cambios a git
Para subir los cambios a git, trabajaremos con un modelo simplificado (subir directamente a main). Si estás familiarizado con git y lo prefieres, puedes crear tus propios branches y luego hacer los pull request para hacer el merge del branch al branch principal. Pero si no estás muy familiarizado con git, usa el siguiente método:
```
# Sincronizamos el repostiorio (es decir, nos descargamos los últimos cambios que otros hayan subido)
git pull
# Añadimos los cambios locales. Podemos ir fichero a fichero o añadir todo simplemente añadiendo el directorio raiz:
git add .
# Hacemos commit de los cambios
git commit -m "Descripción de los cambios"
# Hacemos el push para meterlo en el repositorio
git push origin main
```

Si en ese proceso te aparece un conflicto, es porque alguien ha subido cambios en los mismos ficheros que tú estás modificando. La mayoría de las veces, git será capaz de combinar los cambios, y te guiará por el proceso. Si no puede hacerlo, te pedirá que lo hagas tú a mano.

### Herramientas útiles.
#### nbstripout
Hemos instalado correctamente nbstripout. Esto hace que antes de subir los notebooks a git, se eliminen todas las celdas de "out", es decir, los resultados de la ejecución. De esa forma se descarga el git y se mantiene limpio, y se evita que aparezcan conflictos y "diffs" muy grandes.

Por si no hubieses instalado nbstripout o no funcionase bien, hay un workflow instalado en el repositorio que detecta automáticamente si hay celdas de salida en los notebooks, y en ese caso te envía un email alertándote. Si usas un flujo de trabajo creando tus propias branches, no podrás hacer el merge hasta que no soluciones eso, pero si trabajas en el branch principal, el merge ya estará hecho (y tendrás que limpiarlo y hacer otro commit).

#### nbdiff
Si tienes que resolver conflictos, el programa nbdiff es muy útil para comparar tu versión con la versión que hay en el repositorio. Simplemente ejecuta en el directorio en el que estés trabajando:
```
nbdiff-web
```
