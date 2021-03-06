Title: Diagramas de Secuencia
Summary: Secuencia
Tags: desarollo

# Diagramas de Secuencia
Los **diagramas de secuencias** son un tipo de diagrama utilizado para modelar interacciones entre objectos en un sistema.

Para comprender qué es un diagrama de secuencia, es importante saber cuál es el rol de UML. UML o el lenguaje unificado de modelado es un conjunto de herramientas de modelado que dirige la creación y notación de muchos tipos de diagramas, incluidos los diagramas de comportamiento, diagramas de interacción y diagramas de estructura.

Los diagramas de secuencia son un tipo de diagrama de interacción porque describen cómo un grupo de objetos trabaja en conjunto y en qué orden lo hacen. Tanto los desarrolladores de software como los empresarios usan estos diagramas para comprender los requisitos de un sistema nuevo o documentar un proceso existente. Los diagramas de secuencia a veces se conocen como diagramas de eventos o escenarios de eventos.

## Usos de los diagramas de secuencia
Los diagramas de secuencia pueden ser diagramas de referencia útiles para las empresas y otras organizaciones. Intenta dibujar un diagrama de secuencia para:

-   Representa los detalles de un caso de uso en UML.
-   Modelar la lógica de una operación, una función o un procedimiento sofisticados.
-   Ver cómo las tareas se mueven entre los objetos o componentes de un proceso.
-   Planificar y comprender la funcionalidad detallada de un escenario actual o futuro.

## Nomenclatura

**Participantes** Son roles que describen la forma en que un objeto se comporta en contexto.

**Caja de activación** Representan el tiempo que un objeto necesito para completar una tarea.

**Mensajes** son lineas horizontales que representan comunicación entre objetos.
Los mensajes pueden ser **síncronos** (flecha completa ->) y **Asíncronos** ( flecha abierta ->>). Por convención los mensajes de respuesta se hacen en linea punteada (-->).

**Línea de vida** son las lineas verticales que indican la presencia del objecto en el tiempo.


## Sintaxis para generar diagramas de secuencias.
Existen varias herramientas para generar diagramas de secuencia, la mayoría utilizan la misma sintaxis y es lo que vamos a revisar ahora.

En este caso estamos hablando de una librería JS llamada [js-sequence-diagrams](https://bramp.github.io/js-sequence-diagrams/) que se inspiró en [websequencediagrams.com](websequencediagrams.com) y en un plugin de [atom](https://atom.io/) llamado [diagrams](https://atom.io/packages/diagrams).

<script src="themes/js/webfont.js"></script>
<script src="themes/js/snap.svg-min.js"></script>
<script src="themes/js/underscore-min.js"></script>
<script src="themes/js/sequence-diagram-min.js"></script>

~~~
# Esto es un comentario
# Uso básico
Title: Esto es un título
A->B: Linea Normal
B-->C: Linea punteada
C->>D: Flecha abierta
D-->>A: Flecha abierta punteada
# Agregar notas
Note left of A: Nota a la\n izquierda de A
Note right of A: Nota a la\n derecha de A
Note over A: Nota sobre A
Note over A,B: Note sobre A y B
~~~
<div id="diagram1"></div>
<script>
    var diagram = Diagram.parse("Title: Esto es un título\n"+
    "A->B: Linea Normal\n"+
    "B-->C: Linea punteada\n"+
    "C->>D: Flecha abierta\n"+
    "D-->>A: Flecha abierta punteada\n"+
    "Note left of A: Nota izq de A\n"+
    "Note right of A: Nota der de A\n"+
    "Note over A: Nota sobre A\n"+
    "Note over A,B: Note sobre A y B");
    var options = {theme: "simple",css_class: "simple"};
    diagram.drawSVG("diagram1", options);
</script>
### Re-ordenar los Participantes
A veces es necesario mover los participantes de orden, esto se puede hacer listandolos en el inicio de la declaración.
~~~
# re-ordenar los participantes
participant C
participant B
participant A
Note over A,B,C: Al listar los participantes\n puedes cambiar su orden
A->B: Linea Normal
B-->C: Linea punteada
C->>D: Flecha abierta
~~~

<div id="diagram2"></div>
<script>
    var diagram2 = Diagram.parse("participant C\n"+
    "participant B\n"+
    "participant A\n"+  
    "Title: Al listar los participantes puedes cambiar su orden\n"+
    "A->B: Linea Normal\n"+
    "B-->C: Linea punteada\n"+
    "C->>D: Flecha abierta");
    var options2 = {theme: "simple",css_class: "simple"};
    diagram2.drawSVG("diagram2", options2);
</script>
Referencias:
[wikipedia](https://es.wikipedia.org/wiki/Diagrama_de_secuencia),
[lucidchart](https://www.lucidchart.com/pages/es/diagrama-de-secuencia),
[microsoft](https://msdn.microsoft.com/es-es/library/dd409377.aspx),
[js-sequence-diagrams](https://bramp.github.io/js-sequence-diagrams/)
