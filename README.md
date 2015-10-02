# Presentación simple utilizando Beamer en LaTeX


[![PDF Status](https://www.sharelatex.com/github/repos/FavioVazquez/Presentacion_Beamer_Simple/builds/latest/badge.svg)](https://www.sharelatex.com/github/repos/FavioVazquez/Presentacion_Beamer_Simple/builds/latest/output.pdf) &#10140; Acá puedes ver el PDF compilado de SimpleBeamer.

Esta es una pequeña presentación hecha en Beamer, con LaTeX. La hago como una simple prueba para que puedan clonarla y a partir de ahí construir sus presentaciones.

**Nota** = Asumiré algún conocimiento básico de LaTeX del lector, y esta no es una guía completa de Beamer, es solo un tutorial y ejemplo simple, para más información pueden buscar en la Web. Particularmente este repositorio lo he hecho en español debido a que no siempre es fácil encontrar información y ejemplos de Beamer en español, y en inglés ya hay mucho escrito.

------------

Esta presentación la he construido utilizando la herramienta Kile de KDE para Windows. Por lo tanto se debe instalar antes MikTeX (utilicé la versión 2.9). Deben asegurarse que tienen instalado el paquete de Beamer en MikTeX o de lo contrario no compilará el archivo.

Pueden descargar el motor de LaTeX, MiKTeX, desde el siguiente link y seguir los pasos de instalación:

http://miktex.org/download

Y utilizando el Package Manager (Manejador de paquetes) de MikTex pueden instalar de forma sencilla Beamer, sugiero que utilicen la herramienta en modo administrador. Es muy probable que por defecto venga instalado Beamer, pero siempre es bueno validar.

También puede utilizarse Kile en linux, y es fácil instalar paquetes con synaptic o cualquier otro manejador de paquetes, pero por defecto ya beamer viene instalado con Kile. Para instalar Kile en Ubuntu solo deben escribi los siguientes comandos en la consola:

```
sudo add-apt-repository ppa:kile/stable
sudo apt-get update
sudo apt-get install kile
```

Y ya tendrán instalado Kile y el compilador de TeX.

Cualquier duda o si requieren más información pueden hacer un Issue, o si desean mejorar algo o encuentran un error no duden en hacer un Pull Request.

-----------

#SimpleBeamer.tex

El archivo es muy simple, y solo muestra algunas funcionalidades simples de Beamer. Si deseas ver un PDF compilado de SimpleBeamer.tex puedes hacerlo aquí [![PDF Status](https://www.sharelatex.com/github/repos/FavioVazquez/Presentacion_Beamer_Simple/builds/latest/badge.svg)](https://www.sharelatex.com/github/repos/FavioVazquez/Presentacion_Beamer_Simple/builds/latest/output.pdf)

Las presentaciones hechas en Beamer comienzan diciéndole al compilador que la clase de documento que realizaremos es Beamer, este comando también recibe el tipo de papel y el tamaño de la letra a utilizar:

```latex
\documentclass[a4paper,10pt]{beamer}
```

Luego se llaman a los paquetes que utilizaremos para renderizar, mejorar la forma y estructura de nuestra presentación, particularmente en SimpleBeamer.tex utilicé:

```latex
\usepackage[utf8]{inputenc}
\usepackage{color}
\usepackage{colortbl}
\usepackage{xcolor}
\usepackage{caption}
\usepackage{ragged2e}
```

La explicación de cada paquete y sus funcionalidades pueden encontrarse fácilmente en la Web. Existen muchos temas (themes) de Beamer, algunos preinstalados con el paquete y algunos que pueden descargarse desde repositorios con plantillas, uno de los temas más populares es [Warsaw](http://deic.uab.es/~iblanes/beamer_gallery/individual/Warsaw-default-default.html), que es el que usé para crear SimpleBeamer.tex. Para hacer uso del tema solo debemos escribir:

```latex
\usetheme{Warsaw}
```

Para comenzar la presentación solo hacen falta los comandos de latex:

```latex
\begin{document}

Láminas...

\end{document}
```

Adentro de esos tags, irá el contenido de la presentación. En Beamer cada lámina nueva se crea utilizando los comanndos:

```
\begin{frame}

Contenido de la lámina...

\end{frame}
```

Para crear la primera lámina que comúnmente lleva tu nombre, el título de la presentación, y algunas otras cosa adicionales, necesitamos los siguientes comandos:

```latex
\begin{frame}
\title{Mi primera presentaci\'on con Beamer}
\author{Tu nombre ac\'a}
\date{}                   % Si se deja en blanco la fecha no mostrará
\maketitle                % Necesario para que se muestre el título, autor y fecha
\end{frame}
```

Para crear un índice solo hace falta utilizar el comando ```\tableofcontents ```, si deseamos que salga reflejado en sección superior izquierda (en el caso de Warsaw), necesitamos crear una sección con el nombre Índice, esto es lo mismo para cada lámina que comienza una sección, si desesamos que aparezca tanto en el índice como en el índice superior izquierdo en cada lámina, debemos hacer uso del comando ``` \section{} ```. Entonces para crear una lámina con el índice:

```latex 
\section[\'Indice]{}

\frame{
  \Large{\'Indice}
  \tableofcontents
}
```

Podemos crear tablas, diferentes tipos de ecuaciones, agregar imágenes, videos, y todo lo que podríamos hacer en un documento LaTeX. Podemos encontrar algunos ejemplos [SimpleBeamer.tex](https://github.com/FavioVazquez/Presentacion_Beamer_Simple/blob/master/SimpleBeamer/SimpleBeamer.tex#L54):

```latex
\section{Tabla y Ecuaci\'on}
\begin{frame}{Tabla y ecuaci\'on}
  
\begin{enumerate}
 \item Tabla Simple
 
\begin{center}
 \begin{tabular}{l c r } 
	    1 & 2 & 3 %
	    \\ 4 & 5 & 6  %
	    \\ 7 & 8 & 9 \\ %
\end{tabular}
\end{center}

 \item Tres formas de crear ecuaciones

\begin{equation}
E = mc^2
\end{equation}

$$
x^2 + y^2 = z^2
$$

\[ x^n + y^n = z^n \]
\end{enumerate}
\end{frame}
```

Algo muy interesante y útil de Beamer son los bloques, particularmente útiles para resaltar código, frases de relevancia, hacer ejemplos, etc. En [SimpleBeamer.tex](https://github.com/FavioVazquez/Presentacion_Beamer_Simple/blob/master/SimpleBeamer/SimpleBeamer.tex#L92) podemos encontrar ejemplos de estos bloques que se crean con los comandos:

```latex
\begin{block}{Bloque}
  Esto es un bloque normal
 \end{block}
 
 \begin{exampleblock}{Bloque ejemplo}
  Esto es un bloque de ejemplos
 \end{exampleblock}
```

Hay que destacar que si se crea la sección y un frame, éstos no se verán reflejados en la tabla de contenidos hasta que exista algo de escrito en ellos. En posteriores presentaciones ejemplos mostraré algunas otras funcionalidades más avanzadas de Beamer.
