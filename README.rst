==================================
Documentación de la comunidad PyVE
==================================

Repositorio de documentación de la comunidad Python Venezuela

.. contents :: :local:

Obtener y compilar la documentación
===================================

El almacenamiento de este material está disponible en un repositorio Git 
en la cuenta de PythonVE en GitHub.com "`pyve.documentacion`_". 
Si usted tiene una credenciales en este servidor y desea convertirse en 
un colaborador ejecute el siguiente comando: ::

  $ git clone git@github.com:pyve/pyve.documentacion.git pyve.documentacion

Si usted no tiene las credenciales de acceso al repositorio Git en la 
cuenta de PythonVE en GitHub.com "`pyve.documentacion`_" o simplemente 
solo desea obtener y compilar esta documentación ejecute el siguiente comando: ::

  $ git clone https://github.com/pyve/pyve.documentacion.git pyve.documentacion

Crear `entorno virtual de Python`_ para reconstruir este proyecto: ::

  # aptitude install git-core build-essential python-dev python-setuptools texlive-full
  # easy_install virtualenv
  $ cd $HOME ; mkdir $HOME/virtualenv ; cd $HOME/virtualenv
  $ virtualenv --no-site-packages --python=/usr/bin/python sphinx
  $ source $HOME/virtualenv/sphinx/bin/activate
  
Ahora puede generar la documentación de HTML, usando `zc.buildout`_ con los siguiente comandos: ::

  (sphinx)$ cd pyve.documentacion/
  (sphinx)$ python bootstrap.py
  (sphinx)$ ./bin/buildout -vN
  (sphinx)$ ./bin/sphinx

Ahora se puede abrir ``pyve.documentacion/build/html/index.html`` desde 
su navegador Web favorito.

Para obtener la documentación en PDF ejecute los siguientes comandos: ::

  (sphinx)$ cd ./pyve.documentacion/build
  (sphinx)$ make latex
  (sphinx)$ make latexpdf

Ahora se puede abrir ``pyve.documentacion/build/latex/DocumentacionPyVE.pdf`` 
con sus programas de visor de PDF favorito (Evince, Acrobat Reader, ...)

.. tip::
    Si tienes algún problema al general la documentación en formato PDF, puedes 
    consultar el siguiente enlace http://jimmyg.org/blog/2009/sphinx-pdf-generation-with-latex.html


Reglas de redacción
===================

En primer lugar, debe aprender los `fundamentos de Sphinx`_ que es un 
reStructuredText extendido.


Codificación de caracteres
==========================

Su editor debe codificar el texto en **utf-8** si le gusta lo que está leyendo. 
Si su editor de texto favorito no reconoce esta codificación 
(en la actualidad, eso es bien extraño), entonces cambie de editor de texto.

.. admonition::
   Truco

   Para ``vi``, ``emacs`` y algunos otros editores de texto soportan
   utf-8 de forma automática al abrir un archivo de Sphinx, el lugar en
   primera línea de la siguiente marca (como en este archivo)::

     .. -*- coding: utf-8 -*-


Desplazamientos y indentaciones
===============================

El uso del carácter de tabulación en el texto fuente para las distintas
desplazamientos y indentaciones está **estrictamente prohibido**. Utilice siempre
espacios para este fin. Todos los editores de texto ofrecen opciones avanzadas
para insertar espacios al pulsar la tecla TAB. No tiene
excusa si es necesario.

Estilos de subrayado
====================

Sphinx y ReStructuredText no imponer estilo de subrayado para
diferentes niveles de secciones de un documento. Todo se deja a la discreción
editores. Para mantener la coherencia nosotros adoptamos la siguiente convención: ::

  ==============================================
  Titulo de capitulo (uno solo por cada archivo)
  ==============================================
  ...
  Sección del nivel 1
  ===================
  ...
  Sección del nivel 2
  -------------------
  ...
  Sección del nivel 3
  ...................
  ...
  Sección del nivel 4
  ~~~~~~~~~~~~~~~~~~~
  ...
  Sección del nivel 5
  :::::::::::::::::::
  ...
  Sección del nivel 6
  *******************
  ...
  Sección del nivel 7
  +++++++++++++++++++

No es necesario ni deseable ir más allá del nivel 4. Cuando la generación del 
documento allá completado, el nivel de las secciones básicas de un archivo
depende del nivel de anidamiento del archivo en la estructura general de
documento. Para generar el HTML, no es un problema, pero en LaTeX limita
la superposición de las secciones a 6 niveles.

Contribuciones a esta documentación
===================================

Wow, estás contento con tu excelente trabajo. Y le gustaría compartirlo con
todo el mundo. Al igual que cuando "contribuidor" de código fuente, las pruebas
unitarias no deben mostrar ningún error, compruebe en primer lugar:

* Que el comando ``make html`` o ``./bin/sphinx`` no genere ningún error o advertencia.
* Que su redacción no posea ningún error de ortografía.
* Los enlaces de hipertexto que se ha agregado o cambiado (glosario, enlaces
  externos explícitos, referencias a las secciones, ...) funcionan correctamente.

Imágenes
========

Aparte de las capturas de pantalla, las imágenes Sphinx se inserta en el documento 
debe ir acompañada de su versión "Fuente" en un formato público interoperables, y 
para que el editor pueda abrir el archivo fuente que este disponible. Las imágenes 
deben estar preferentemente en el formato PNG.

Además, durante cada inserción o cambio de imagen, usted **debe** verificar y ajustar 
si es necesario la representación PDF, a sabiendas de las limitaciones la imagen a 
tamaño del papel final.

**Ejemplo de uso relacionado a imágenes:** ::

   .. gs-map.mm: imagen de mapa mental de los servicios de GenericSetup. Creado con FreeMind

   .. image:: gs-map.png
      :width: 636px
      :align: center
      :alt: imagen de mapa mental de los servicios de GenericSetup

**Ejemplo de uso relacionado captura de pantalla o ilustraciones:** ::

   .. figure::  screenshot.jpg
      :align:   center
      :alt: Captura de pantalla del programa de mapa mental

**Aplicaciones gráficas recomendadas**

Para realizar diagramas de sus clase puede usar : `Graphviz`_


Ejemplos de documentación en Sphinx
===================================

* `Python documentation`_
* `Zope documentation`_
* `Plone Developer Documentation`_
* `D:YAML documentation`_


Algunas de las herramientas recomendadas
========================================

Emacs : usted puede agregar a emacs el módulo `rst.el`_ que añade un par de 
comandos y la sintaxis de la documentación a los escritores simpatizantes 
de Sphinx y reStructuredText.


FAQ
===

**Pregunta :** He añadido una entrada del índice o un nuevo término en el glosario y
no se actualiza cuando compilo el documento.

**Respuesta :** El índice de Sphinx es a veces es desorientado y la gestión de la dependencia
a veces, mejor. Por lo tanto, todo se debe reiniciar ejecutando el comando ``make clean`` 
dentro del directorio ``pyve.documentacion/sphinx/build/``.


.. _pyve.documentacion: https://github.com/pyve/pyve.documentacion
.. _entorno virtual de Python: http://readthedocs.org/docs/plone-spanish-docs/en/latest/python/creacion_entornos_virtuales_python.html
.. _zc.buildout: http://readthedocs.org/docs/plone-spanish-docs/en/latest/buildout/replicacion_proyectos_python.html
.. _fundamentos de Sphinx: http://sphinx.pocoo.org/contents.html
.. _Graphviz: http://www.graphviz.org/
.. _rst.el: http://svn.berlios.de/svnroot/repos/docutils/trunk/docutils/tools/editors/emacs/rst.el
.. _Python documentation: http://docs.python.org/
.. _Zope documentation: http://docs.zope.org/zope2/index.html
.. _Plone Developer Documentation: http://collective-docs.plone.org/
.. _D:YAML documentation: http://dyaml.alwaysdata.net/static/html/doc_0.4/index.html
