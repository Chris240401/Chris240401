Hi , Mi nombre es Christian Ramírez
La programación es un lenguaje universal que te permite crear software, aplicaciones y sitios web. Puedes aprender diferentes lenguajes de programación

presento mi proyecto 

** Ejercicio de Automatización E2E **


⏩
Comience
Comience a usar VS Code, IntelliJ, Maven, Gradle, NPM,
GitHub Codespaces, Docker o la línea de comandos

💡
Ejemplos
Ejemplos y demostraciones de integraciones con otros frameworks.

📺
Vídeos de inicio rápido
Guías paso a paso para principiantes para empezar desde cero
Kárate
Automatización de pruebas realizadaSimple.
  
  


Karate es la única herramienta de código abierto que combina la automatización de pruebas de API, simulacros , pruebas de rendimiento e incluso la automatización de la interfaz de usuario en un marco único y unificado . La sintaxis es neutral en cuanto al lenguaje y fácil incluso para quienes no son programadores. Las afirmaciones y los informes HTML están integrados y puede ejecutar pruebas en paralelo para mayor velocidad.

También hay un ejecutable independiente multiplataforma para equipos que no se sienten cómodos con Java. No es necesario compilar el código. Simplemente escriba pruebas en una sintaxis simple y legible , cuidadosamente diseñada para HTTP, JSON, GraphQL y XML. Y puede combinar la automatización de pruebas de API y UI dentro del mismo script de prueba.

También existe una API de Java para aquellos que prefieren integrar mediante programación las ricas capacidades de automatización y afirmación de datos de Karate.


![image](https://github.com/Chris240401/Chris240401/assets/154774787/48662a8d-d287-4463-a0cc-29eda16acc72)


Características

-Basado en el popular estándar Cucumber/Gherkin, con soporte IDE y opciones de coloración de sintaxis
-No se requieren conocimientos de Java e incluso los no programadores pueden escribir pruebas.
-Los scripts son texto sin formato, no requieren ningún paso de compilación ni IDE, y los equipos pueden colaborar utilizando Git/SCM estándar.

Referencias
Pruebas API con Karate : vídeo + demostraciones de Peter Thomas (creador/desarrollador principal de Karate)
Introducción a todas las funciones de Karate : vídeo + demostraciones de Peter Thomas (creador/desarrollador principal de Karate)


Empezando
Si es un desarrollador de Java, Karate requiere al menos Java 11 y luego Maven , Gradle o un IDE de Java que incorpore cualquiera de ellos para poder instalarse. Tenga en cuenta que Karate funciona bien en OpenJDK.

Si es nuevo en la programación o la automatización de pruebas, se recomienda el complemento oficial de IntelliJ .

Si no desea utilizar Java, se recomienda la extensión Karate para Visual Studio Code , y los programadores de JavaScript, .NET, Ruby y Python se sentirán como en casa.

Tanto el complemento oficial de Visual Studio Code como el de IntelliJ admiten la depuración paso a paso de las pruebas de Karate.

experto
Todo lo que necesitas está disponible en el karate-coreartefacto. Puede ejecutar pruebas con esto directamente , pero los equipos pueden elegir la variante JUnit (que se muestra a continuación) que incorpora JUnit 5 y mejora ligeramente la experiencia en IDE .

<dependency>
    <groupId>com.intuit.karate</groupId>
    <artifactId>karate-junit5</artifactId>
    <version>1.4.1</version>
    <scope>test</scope>
</dependency>
Gradle
Alternativamente para Gradle :

    testCompile 'com.intuit.karate:karate-junit5:1.4.1'
Consulte también la wiki para saber cómo usar Karate con Gradle .

Núcleo de Karate "Fat JAR"
Si mezcla Karate en un proyecto Maven o Gradle con muchas otras dependencias, puede tener problemas debido a conflictos de dependencias. Por ejemplo, muchos proyectos Java dependen directa (o indirectamente) de Netty, Thymeleaf o ANTLR, etc.

Si enfrenta problemas como "clase no encontrada", simplemente ingrese la karate-coredependencia y use el all clasificador en su pom.xml(o build.gradle).

Por ejemplo, cuando se utiliza Maven:

<dependency>
  <groupId>com.intuit.karate</groupId>
  <artifactId>karate-core</artifactId>
  <version>${karate.version}</version>
  <classifier>all</classifier>
  <scope>test</scope>
</dependency>
Tenga en cuenta que para proyectos muy complicados puede considerar usar un perfil de Maven para que las dependencias relacionadas con las pruebas no choquen con sus dependencias en tiempo de desarrollo. Por supuesto, es una opción tener las pruebas de Karate en un proyecto y una carpeta independientes de Maven, sin dejar de estar en el mismo repositorio de Git.

Inicio rápido
Puede que le resulte más fácil utilizar el arquetipo Karate Maven para crear un proyecto de esqueleto con un solo comando. Luego puede omitir las siguientes secciones, ya que se crearán para usted la pom.xmlestructura de directorios recomendada, la prueba de muestra y los corredores JUnit 5 .

Si está detrás de un proxy corporativo, o especialmente si su instalación local de Maven ha sido configurada para apuntar a un repositorio dentro de su red local, es posible que el siguiente comando no funcione. Una solución alternativa es desactivar temporalmente o cambiar el nombre de su settings.xmlarchivo Maven y volver a intentarlo.

Puede reemplazar los valores de com.mycompanyy myprojectsegún sus necesidades.

mvn archetype:generate \
-DarchetypeGroupId=com.intuit.karate \
-DarchetypeArtifactId=karate-archetype \
-DarchetypeVersion=1.4.1 \
-DgroupId=com.mycompany \
-DartifactId=myproject
Esto creará una carpeta llamada myproject(o el nombre que le hayas asignado).

Soporte IDE
Consulte la wiki- IDE Support .

Estructura de carpetas
Un script de prueba de Karate tiene la extensión de archivo .featureque es el estándar seguido de Cucumber. Eres libre de organizar tus archivos utilizando las convenciones habituales de paquetes de Java.

La tradición de Maven es tener archivos fuente que no sean Java en una src/test/resourcesestructura de carpetas separada, pero le recomendamos que los mantenga al lado de sus *.javaarchivos. Cuando tiene un proyecto grande y complejo, terminará con algunos archivos de datos (por ejemplo *.js, *.json, *.txt) también y es mucho más conveniente ver los archivos *.javay *.featurey todos los artefactos relacionados en el mismo lugar.

Esto se puede lograr fácilmente con el siguiente ajuste en su <build>sección maven.

<build>
    <testResources>
        <testResource>
            <directory>src/test/java</directory>
            <excludes>
                <exclude>**/*.java</exclude>
            </excludes>
        </testResource>
    </testResources>        
    <plugins>
    ...
    </plugins>
</build>
Esto es muy común en el mundo de los usuarios de Maven y tenga en cuenta que se trata de pruebas y no de código de producción.

Alternativamente, si usa Gradle, agregue la siguiente sourceSetsdefinición

sourceSets {
    test {
        resources {
            srcDir file('src/test/java')
            exclude '**/*.java'
        }
    }
}
Con lo anterior implementado, no tiene que seguir cambiando entre sus carpetas src/test/javay src/test/resources, puede tener todos sus códigos de prueba y artefactos debajo src/test/javay todo funcionará como se esperaba.

Una vez que te acostumbres a esto, es posible que incluso empieces a preguntarte por qué los proyectos necesitan una src/test/resourcescarpeta.

Ejemplo de arranque de primavera
Soumendra Daas ha creado un buen ejemplo y una guía que puedes utilizar como referencia aquí: hello-karate. Esto demuestra un proyecto Java Maven + JUnit 5 configurado para probar una aplicación Spring Boot .

Convenciones de nombres
Dado que se trata de pruebas y no de código Java de producción, no necesita estar sujeto a la com.mycompany.foo.barconvención ni a la explosión innecesaria de subcarpetas que se produce. Le sugerimos que tenga una jerarquía de carpetas de solo uno o dos niveles de profundidad, donde los nombres de las carpetas identifiquen claramente qué 'recurso', 'entidad' o API es el servicio web bajo prueba.

Por ejemplo:

src/test/java
    |
    +-- karate-config.js
    +-- logback-test.xml
    +-- some-reusable.feature
    +-- some-classpath-function.js
    +-- some-classpath-payload.json
    |
    \-- animals
        |
        +-- AnimalsTest.java
        |
        +-- cats
        |   |
        |   +-- cats-post.feature
        |   +-- cats-get.feature
        |   +-- cat.json
        |   \-- CatsRunner.java
        |
        \-- dogs
            |
            +-- dog-crud.feature
            +-- dog.json
            +-- some-helper-function.js
            \-- DogsRunner.java
Suponiendo que utiliza JUnit, existen algunas buenas razones para la convención de nomenclatura recomendada (mejor práctica) y la elección de ubicación de archivos que se muestran arriba:

No utilizar la *Test.javaconvención para las clases JUnit (por ejemplo CatsRunner.java, ) en la carpeta catsy dogsgarantiza que estas pruebas no se recogerán al invocar mvn test(para todo el proyecto) desde la línea de comando . Pero aún puedes invocar estas pruebas desde el IDE, lo cual es conveniente cuando estás en modo de desarrollo.
AnimalsTest.java(el único archivo que sigue la *Test.javaconvención de nomenclatura) actúa como el 'conjunto de pruebas' para todo el proyecto. De forma predeterminada, Karate también cargará todos *.featurelos archivos de los subdirectorios. Pero como some-reusable.featureestá arriba AnimalsTest.java en la jerarquía de carpetas, no será recogido. Que es exactamente lo que queremos, porque some-reusable.featureestá diseñado para ser llamado sólo desde uno de los otros scripts de prueba (quizás pasando algunos parámetros). También puede utilizar etiquetas para omitir archivos.
some-classpath-function.jsy some-classpath-payload.jsonestán en la 'raíz' del 'classpath' de Java , lo que significa que pueden leerse (y reutilizarse) fácilmente desde cualquier script de prueba utilizando el classpath:prefijo, por ejemplo: read('classpath:some-classpath-function.js'). Las rutas relativas también funcionarán.
Para obtener detalles sobre lo que realmente incluye un script o *.featurearchivo, consulte la guía de sintaxis .

Unidad 5
Karate es compatible con JUnit 5 y la ventaja es que puedes tener múltiples métodos en una clase de prueba. Solo se necesita 1 importy, en lugar de una anotación a nivel de clase, se utiliza una API DRY y fluida para expresar qué pruebas y etiquetas desea usar.

Tenga en cuenta que la clase Java no necesita serlo publice incluso los métodos de prueba no necesitan serlo public, por lo que las pruebas terminan siendo muy concisas.

Karate recorrerá subdirectorios y buscará *.featurearchivos. Por ejemplo, si tiene la clase JUnit en el com.mycompanypaquete, también se ejecutarán *.featurelos archivos en com.mycompany.fooy . com.mycompany.barÉsta es una de las razones por las que es posible que desee preferir una estructura de directorios "plana" como se explicó anteriormente .

Aquí hay un ejemplo :

package karate;

import com.intuit.karate.junit5.Karate;

class SampleTest {

    @Karate.Test
    Karate testSample() {
        return Karate.run("sample").relativeTo(getClass());
    }
    
    @Karate.Test
    Karate testTags() {
        return Karate.run("tags").tags("@second").relativeTo(getClass());
    }

    @Karate.Test
    Karate testSystemProperty() {
        return Karate.run("classpath:karate/tags.feature")
                .tags("@second")
                .karateEnv("e2e")
                .systemProperty("foo", "bar");
    }

}
Tenga en cuenta que hay más métodos "constructores" disponibles en la Runner.Builderclase, como reportDir()etc.

Debería poder hacer clic derecho y ejecutar un único método usando su IDE, lo cual debería ser suficiente cuando esté en modo de desarrollo. Pero para poder ejecutar pruebas de JUnit 5 desde la línea de comandos, debe asegurarse de que la última versión del complemento maven-surefire esté presente en su proyecto pom.xml(dentro de la <build>/<plugins>sección):

<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-surefire-plugin</artifactId>
    <version>2.22.2</version>
</plugin>
Para ejecutar un único método de prueba, por ejemplo el testTags()del ejemplo anterior, puede hacer esto:

mvn test -Dtest=SampleTest#testTags
Vea también cómo ejecutar pruebas a través de la línea de comandos y el corredor paralelo .

Informe HTML JUnit
Cuando utiliza el ejecutor JUnit, después de ejecutar cada función, se envía un informe HTML a la target/karate-reportscarpeta y la ruta completa se imprimirá en la consola (ver video ).

html report: (paste into browser to view)
-----------------------------------------
file:///projects/myproject/target/karate-reports/mypackage.myfeature.html
Puede seleccionar (hacer doble clic), copiar y pegar fácilmente esta file:URL en la barra de direcciones de su navegador. Este informe es útil para solucionar problemas y depurar una prueba porque todas las solicitudes y respuestas se muestran en línea con los pasos, junto con los mensajes de error y el resultado de las printdeclaraciones. Simplemente actualice la ventana de su navegador si vuelve a ejecutar la prueba.

Ejecución en seco
Esto le dará el informe HTML habitual que muestra qué funciones se ejecutarán, incluidos todos los pasos mostrados (incluidos los comentarios) para que pueda revisarse. Por supuesto, faltarán las duraciones de tiempo reales y los registros, y todo pasará.

El informe de “ejecución en seco” es útil para revisar la etiqueta "cobertura" de lo que se ejecutará. Por ejemplo, puede obtener un buen informe de "cobertura" de funciones, siempre que tenga un amplio conjunto de etiquetas . por ejemplo @smoke @module=one @module=two, etc.

La Runner.BuilderAPI tiene un dryRun()método para activar esto. Tenga en cuenta que este modo también se puede activar a través de la línea de comandos agregando -Do --dryrunal archivo karate.options.

Línea de comando
Si está utilizando Karate a través del complemento VS Code o el JAR independiente, consulte la guía de uso de CLI .

Línea de comando - Maven
Normalmente, en el modo de desarrollo, utilizará su IDE para ejecutar un *.featurearchivo directamente o mediante la clase JUnit Java complementaria 'runner'. Cuando tenga una clase 'runner' implementada, también será posible ejecutarla desde la línea de comandos.

Tenga en cuenta que el mvn testcomando solo ejecuta clases de prueba que siguen la *Test.java convención de nomenclatura de forma predeterminada. Pero puedes elegir una sola prueba para ejecutarla así:

mvn test -Dtest=CatsRunner
karate.options
Cuando su "ejecutor" de prueba de Java está vinculado a varios archivos de características, que será el caso cuando use el corredor paralelo recomendado , puede limitar su alcance a una sola característica, escenario o directorio a través de la línea de comandos, lo cual es útil en desarrollo. -modo. Observe cómo se pueden especificar incluso etiquetas para excluir (o incluir):

Tenga en cuenta que cualquiera Featureo Scenariocon la etiqueta especial@ignore se omitirá de forma predeterminada.

mvn test "-Dkarate.options=--tags ~@skipme classpath:demo/cats/cats.feature" -Dtest=DemoTestParallel
Se pueden especificar varios archivos de características (o rutas), delimitados por el carácter de espacio. Deberían estar al final del karate.options. Para ejecutar solo un escenario, agregue el número de línea en el que se define el escenario, delimitado por :.

mvn test "-Dkarate.options=PathToFeatureFiles/order.feature:12" -Dtest=DemoTestParallel
Dado que se esperan rutas al final de las opciones de la línea de comandos, si desea anular solo las etiquetas, utilice el =signo para aclarar los valores de los argumentos. Por ejemplo:

mvn test -Dkarate.options='-t=@dev -t=@src' -Dtest=ExamplesTest
Línea de comando: Gradle
Para Gradle, debe extender la tarea de prueba para permitir que se karate.optionspase al tiempo de ejecución (de lo contrario, Gradle los consumirá). Para hacer eso, agregue lo siguiente:

test {
    // pull karate options into the runtime
    systemProperty "karate.options", System.properties.getProperty("karate.options")
    // pull karate env into the runtime
    systemProperty "karate.env", System.properties.getProperty("karate.env")
    // ensure tests are always run
    outputs.upToDateWhen { false }
}
Y luego el comando anterior en Gradle se vería así:

./gradlew test --tests *CatsRunner
o

./gradlew test -Dtest.single=CatsRunner
Conjuntos de pruebas
La forma recomendada de definir y ejecutar conjuntos de pruebas e informes en Karate es utilizar el corredor paralelo , que se describe en la siguiente sección. El enfoque de esta sección es más adecuado para solucionar problemas en modo de desarrollo, utilizando su IDE.

Una forma de definir 'conjuntos de pruebas' en Karate es tener una clase JUnit en un nivel 'arriba' (en términos de jerarquía de carpetas) de todos los *.featurearchivos de su proyecto. Entonces, si toma el ejemplo de estructura de carpetas anterior , puede hacer esto en la línea de comandos:

mvn test "-Dkarate.options=--tags ~@skipme" -Dtest=AnimalsTest
Aquí AnimalsTestestá el nombre de la clase Java que designamos para ejecutar los múltiples *.featurearchivos que componen su conjunto de pruebas. Existe una forma sencilla de etiquetar sus pruebas y el ejemplo anterior demuestra cómo ejecutar todas las pruebas excepto las etiquetadas @skipme.

Tenga en cuenta que la etiqueta especial incorporada siempre@ignore se omitirá de forma predeterminada y no es necesario especificarla en ningún lugar.~@ignore

Puede "bloquear" el hecho de que solo desea ejecutar la única clase JUnit que funciona como un conjunto de pruebas, utilizando la siguiente configuración de maven-surefire-plugin :

<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-surefire-plugin</artifactId>
    <version>${maven.surefire.version}</version>
    <configuration>
        <includes>
            <include>animals/AnimalsTest.java</include>
        </includes>
        <systemProperties>
            <karate.options>--tags @smoke</karate.options>
        </systemProperties>            
    </configuration>
</plugin> 
Tenga en cuenta cómo se karate.optionspuede especificar mediante la <systemProperties>configuración.

Para Gradle, simplemente especifica la prueba que será include-d:

test {
    include 'animals/AnimalsTest.java'
    // pull karate options into the runtime
    systemProperty "karate.options", System.properties.getProperty("karate.options")
    // pull karate env into the runtime
    systemProperty "karate.env", System.properties.getProperty("karate.env")
    // ensure tests are always run
    outputs.upToDateWhen { false }
}
El gran inconveniente del enfoque anterior es que no se pueden ejecutar pruebas en paralelo. El enfoque recomendado para los informes de Karate en una configuración de integración continua se describe en la siguiente sección, que puede generar el formato XML JUnit que la mayoría de las herramientas de CI pueden consumir. También se puede emitir el formato Cucumber JSON , lo que le brinda muchas opciones para generar informes atractivos utilizando complementos de Maven de terceros.

Y lo más importante: puede ejecutar pruebas en paralelo sin tener que depender de hacks de terceros que introducen generación de código y configuración "inflada" en su pom.xmlo build.gradle.

Ejecución paralela
Tenga en cuenta que se realiza un seguimiento de algunos análisis de usuarios solo cuando ve el informe HTML de Karate integrado.

Karate puede ejecutar pruebas en paralelo y reducir drásticamente el tiempo de ejecución. Esta es una característica "básica" y no depende de JUnit, Maven o Gradle.

Para aquellos que ejecutan Karate en proyectos que no son Java a través de la línea de comandos, tengan en cuenta que pueden configurar el número de subprocesos mediante --threadso -Tcomo se explica aquí .

Puede "elegir" fácilmente funciones y etiquetas para ejecutar y componer conjuntos de pruebas de una manera muy flexible.
Puede utilizar el Resultsobjeto devuelto para comprobar si algún escenario falló e incluso para resumir los errores.
Los informes JUnit XML se pueden generar en la " reportDir" ruta que especifique y puede configurar fácilmente su CI para buscar estos archivos después de una compilación (por ejemplo, en **/*.xmlo **/karate-reports/*.xml). Tenga en cuenta que debe llamar al outputJunitXml(true)método en el Runner"constructor".
Se pueden generar informes JSON de Cucumber.json , excepto que la extensión será en lugar de .xml. Tenga en cuenta que debe llamar al outputCucumberJson(true)método en el Runner"constructor".
Los informes HTML se pueden desactivar llamando a outputHtmlReport(false).
El Runner.path()método "constructor" karate-corees la forma en que se refiere al paquete que desea ejecutar, y se seleccionarán todos los archivos de funciones dentro de los subdirectorios.
Runner.path()toma múltiples parámetros de cadena, por lo que puede hacer referencia a múltiples paquetes o incluso *.featurearchivos individuales y "componer" fácilmente un conjunto de pruebas
p.ejRunner.path("classpath:animals", "classpath:some/other/package.feature")
Para elegir etiquetas , llame a la tags()API; tenga en cuenta que, de forma predeterminada, se omitirá cualquier *.featurearchivo etiquetado con la etiqueta especial (integrada):. @ignoreTambién puede especificar etiquetas en la línea de comandos . El tags()método también toma múltiples argumentos, por ejemplo
esta es una operación "Y":tags("@customer", "@smoke")
y esta es una operación "O":tags("@customer,@smoke")
Existe un reportDir()método opcional si desea personalizar el directorio al que se enviarán los archivos HTML, XML y JSON ; el valor predeterminado estarget/karate-reports
Si desea determinar dinámica y programáticamente las etiquetas y características que se incluirán, la API también acepta List<String>como argumentos los métodos path()ytags()
parallel() tiene que ser el último método llamado y usted pasa la cantidad de subprocesos paralelos necesarios. Devuelve un Resultsobjeto que tiene toda la información que necesita, como el número de pruebas aprobadas o fallidas.
Ejecución paralela de JUnit 5
El siguiente ejemplo supone que JUnit 5 está disponible en el classpath y utiliza la @Testanotación y el assertEquals()método.

Pero si realmente lo desea, puede usar la API Runnery Resultsdirectamente en cualquier clase de Java, e incluso en un método "principal".

Utilice el karate-templateproyecto si desea obtener un ejemplo como parte de un proyecto "esqueleto" funcional.

import com.intuit.karate.Results;
import com.intuit.karate.Runner;
import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

class TestParallel {

    @Test
    void testParallel() {
        Results results = Runner.path("classpath:animals").tags("~@skipme").parallel(5);
        assertEquals(0, results.getFailCount(), results.getErrorMessages());
    }

}
Estadísticas paralelas
Para mayor comodidad, algunas estadísticas se registran en la consola cuando se completa la ejecución, lo que debería verse así:

======================================================
elapsed:   2.35 | threads:    5 | thread time: 4.98 
features:    54 | ignored:   25 | efficiency: 0.42
scenarios:  145 | passed:   145 | failed: 0
======================================================
El corredor paralelo siempre ejecutará Feature-s en paralelo. Karate también ejecutará Scenario-s en paralelo de forma predeterminada. Entonces, si tiene a Featurecon múltiples Scenario-s, se ejecutarán en paralelo, ¡e incluso cada Examplesfila de a Scenario Outlinelo hará!

karate-timeline.htmlTambién se guardará un archivo en el directorio de salida del informe mencionado anteriormente ( target/karate-reportsde forma predeterminada), lo cual es útil para verificar visualmente o solucionar problemas de la efectividad de la ejecución de prueba ( ver video ).

@parallel=false
En casos excepcionales, es posible que desee suprimir el valor predeterminado de -s que se ejecuta en paralelo y se puede utilizar Scenarioel especial . Si lo coloca encima de la palabra clave, se aplicará a todos los -s. Y si solo desea que uno o dos -s NO se ejecuten en paralelo, puede colocar esta etiqueta solo encima de esos -s. Ver ejemplo .tag @parallel=falseFeatureScenarioScenario Scenario

Tenga en cuenta que obligar Scenarioa -s a ejecutarse en una secuencia particular es un antipatrón y debe evitarse en la medida de lo posible.

Informes de las pruebas
Como se mencionó anteriormente, la mayoría de las herramientas de CI podrían procesar la salida XML de JUnit del corredor paralelo y determinar el estado de la compilación, así como generar informes.

La demostración de Karate tiene un ejemplo práctico de la configuración recomendada para corredores paralelos. También detalla cómo se puede utilizar fácilmente una biblioteca de terceros para generar informes muy atractivos, a partir de la salida JSON del corredor paralelo.

Por ejemplo, a continuación se muestra un informe real generado por la biblioteca de código abierto de informes de pepino .



Otro ejemplo de un popular complemento de informes de Maven que es compatible con Karate JSON es Cluecumber .

La demostración también incluye cobertura de código usando Jacoco y algunos consejos incluso para back-ends que no son Java. Algunas soluciones de servidor de informes de terceros se integran con Karate, como ReportPortal.io .

Inicio sesión
Esto es opcional y Karate funcionará sin la configuración de registro implementada, pero el registro predeterminado de la consola puede ser demasiado detallado para sus necesidades.

Karate usa LOGBack que busca un archivo llamado logback-test.xmlen el ' classpath '.

En casos raros, por ejemplo, si está utilizando Karate para crear una aplicación Java, LOGBack buscarálogback.xml

Aquí tienes un ejemplo logback-test.xmlpara que empieces.

<?xml version="1.0" encoding="UTF-8"?>
<configuration>
 
    <appender name="STDOUT" class="ch.qos.logback.core.ConsoleAppender">
        <encoder>
            <pattern>%d{HH:mm:ss.SSS} [%thread] %-5level %logger{36} - %msg%n</pattern>
        </encoder>
    </appender>
  
    <appender name="FILE" class="ch.qos.logback.core.FileAppender">
        <file>target/karate.log</file>
        <encoder>
            <pattern>%d{HH:mm:ss.SSS} [%thread] %-5level %logger{36} - %msg%n</pattern>
        </encoder>
    </appender>    
   
    <logger name="com.intuit.karate" level="DEBUG"/>
   
    <root level="info">
        <appender-ref ref="STDOUT" />
        <appender-ref ref="FILE" />
    </root>
  
</configuration>
Puede cambiar el com.intuit.karatenivel del registrador para INFOreducir la cantidad de registro. Cuando el nivel es DEBUGla solicitud completa y se registran las cargas útiles de respuesta. Si utiliza la configuración anterior, los registros se capturarán en formato target/karate.log.

Si desea mantener el nivel como DEBUG( para informes HTML ) pero suprimir el registro en la consola, puede comentar la STDOUT"raíz" appender-ref:

  <root level="warn">
      <!-- <appender-ref ref="STDOUT" /> -->
      <appender-ref ref="FILE" />
  </root>
U otra opción es usar un ThresholdFilter, para que aún vea registros críticos en la consola:

  <appender name="STDOUT" class="ch.qos.logback.core.ConsoleAppender">
      <filter class="ch.qos.logback.classic.filter.ThresholdFilter">
          <level>WARN</level>
      </filter>
      <encoder>
          <pattern>%d{HH:mm:ss.SSS} [%thread] %-5level %logger{36} - %msg%n</pattern>
      </encoder>
  </appender>
Si desea excluir los registros de su proceso de CI/CD pero mantenerlos en la ejecución de sus usuarios en sus locales, puede configurar su inicio de sesión usando Janino . En tales casos, podría ser conveniente que sus pruebas utilicen karate.logger.debug('your additional info')en lugar de la printpalabra clave para poder mantener los registros en su canalización en INFO.

Para suprimir información confidencial, como secretos y contraseñas, del registro y los informes, consulte Enmascaramiento de registros y detalle de informes .

Configuración
Puedes saltarte esta sección y pasar directamente a la Guía de sintaxis si tienes prisa por empezar a practicar Karate. Todo funcionará incluso si el karate-config.jsarchivo no está presente.

ruta de clases
El 'classpath' es un concepto de Java y es donde se espera que estén de forma predeterminada algunos archivos de configuración, como el de registro . Si utiliza el <test-resources>ajuste de Maven descrito anteriormente (recomendado), la 'raíz' del classpath estará en la src/test/javacarpeta, o de lo contrario estará en src/test/resources.

karate-config.js
La única 'regla' es que al iniciar Karate espera karate-config.jsque exista un archivo llamado en el 'classpath' y contenga una función JavaScript . Se espera que la función devuelva un objeto JSON y todas las claves y valores de ese objeto JSON estarán disponibles como variables de script.

¡Y eso es todo lo que hay que hacer en la configuración de Karate! Puede obtener fácilmente el valor del 'entorno' o 'perfil' actual y luego configurar variables 'globales' usando JavaScript simple. Aquí hay un ejemplo:

function fn() {   
  var env = karate.env; // get java system property 'karate.env'
  karate.log('karate.env system property was:', env);
  if (!env) {
    env = 'dev'; // a custom 'intelligent' default
  }
  var config = { // base config JSON
    appId: 'my.app.id',
    appSecret: 'my.secret',
    someUrlBase: 'https://some-host.com/v1/auth/',
    anotherUrlBase: 'https://another-host.com/v1/'
  };
  if (env == 'stage') {
    // over-ride only those that need to be
    config.someUrlBase = 'https://stage-host/v1/auth';
  } else if (env == 'e2e') {
    config.someUrlBase = 'https://e2e-host/v1/auth';
  }
  // don't waste time waiting for a connection or if servers don't respond within 5 seconds
  karate.configure('connectTimeout', 5000);
  karate.configure('readTimeout', 5000);
  return config;
}
Aquí arriba, puede ver que se utilizan los karate.log()" ayudantes" karate.envy . karate.configure()Tenga en cuenta que se karate-config.jsvuelve a procesar para todos Scenario y, en casos excepcionales, es posible que desee inicializar (por ejemplo, tokens de autenticación) solo una vez para todas sus pruebas. Esto se puede lograr usando karate.callSingle().

Un requisito común es pasar valores de parámetros dinámicos a través de la línea de comando, y puede usar la karate.properties['some.name']sintaxis para pasar una propiedad del sistema a través de opciones de JVM en el formulario -Dsome.name=foo. Consulte la sección sobre números de puerto dinámicos para ver un ejemplo.

Incluso puedes recuperar variables de entorno del sistema operativo a través de la interoperabilidad de Java de la siguiente manera:var systemPath = java.lang.System.getenv('PATH');

Esta decisión de usar JavaScript para la configuración está influenciada por años de experiencia con la configuración de conjuntos de pruebas complicados y la lucha con perfiles de Maven , el filtrado de recursos de Maven y la sopa XML que de alguna manera es convocada por el complemento Maven AntRun .

El enfoque de Karate te libera de Maven, es mucho más expresivo, te permite observar todos los entornos en un solo lugar y sigue siendo un archivo de texto sin formato. Si lo desea, incluso puede crear fragmentos anidados de JSON que 'espacien nombres' sus variables de configuración .

Una forma de apreciar el enfoque de Karate es pensar en lo que se necesita para agregar una nueva variable dependiente del entorno (por ejemplo, una contraseña) a una prueba. En marcos típicos, podría significar cambiar múltiples archivos de propiedades, perfiles de Maven y marcadores de posición, y tal vez incluso enhebrar el valor a través de un marco de inyección de dependencia, antes de que pueda acceder al valor dentro de su prueba.

De hecho, este enfoque es un poco más complicado que *.propertieslos archivos tradicionales, pero necesita esta complejidad. Tenga en cuenta que estas son pruebas (no código de producción) y esta configuración será mantenida más por el equipo de desarrollo o QE en lugar del equipo de 'operaciones' o de operaciones.

Y ya no hay que preocuparse por los perfiles de Maven y si el *.propertiesarchivo "correcto" se ha copiado en el lugar adecuado.

Cambiando el entorno
Sólo hay una cosa que debe hacer para cambiar el entorno: establecer una propiedad del sistema Java.

De forma predeterminada, el valor de karate.envcuándo accede a él dentro de karate-config.js- sería null.

La receta para hacer esto al ejecutar Maven desde la línea de comando es:

mvn test -DargLine="-Dkarate.env=e2e"
O en Gradle:

./gradlew test -Dkarate.env=e2e
Puede consultar la documentación del complemento Maven Surefire para conocer formas alternativas de lograr esto, pero el argLineenfoque es el más simple y debería ser más que suficiente para sus necesidades de integración continua o automatización de pruebas.

Aquí le recordamos que puede ejecutar cualquier prueba JUnit a través de Maven de la siguiente manera:

mvn test -Dtest=CatsRunner
¿Dónde CatsRunnerestá el nombre de la clase JUnit (en cualquier paquete) que desea ejecutar?

Karate es flexible, puedes sobrescribir fácilmente las variables de configuración dentro del "runner" de Java o JUnit, lo cual es muy conveniente cuando estás en modo de desarrollo o en la creación rápida de prototipos.

System.setProperty("karate.env", "pre-prod");
Pero la forma recomendada es utilizar la API karateEnv(name, value)o systemProperty(name, value)en el corredor paralelo .

Para usuarios avanzados, tenga en cuenta que las etiquetas y el karate.envcambio de entorno se pueden "vincular" mediante etiquetas de entorno especiales .

Configuración específica del entorno
Cuando su proyecto se vuelve complejo, puede tener karate-config-<env>.jsarchivos separados que se procesarán para ese valor específico de karate.env. Esto es especialmente útil cuando desea mantener contraseñas, secretos o incluso URL específicas para su entorno de desarrollo local.

Asegúrese de configurar su sistema de administración de código fuente (por ejemplo, Git) para ignorarlo karate-config-*.jssi es necesario.

Siempre debería estar karate-config.jsen la carpeta "raíz", incluso si no tienes ninguna configuración "común". En tales casos, la función no puede hacer nada o devolver un JSON vacío. Aprende más .

Estas son las reglas que usa Karate en el arranque (antes de cada fila Scenarioo en un ):ExamplesScenario Outline

Si se configuró la propiedad del sistema karate.config.dir, Karate buscará en esta carpeta karate-config.jsy, si la encuentra, la procesará.
de lo contrario, si karate-config.jsno se encontró en la ubicación anterior (o karate.config.dirno se configuró), classpath:karate-config.jsse procesará (este es el caso predeterminado/común)
si la karate.envpropiedad del sistema estaba configurada
si karate.config.direstaba configurado, Karate también buscaráfile:<karate.config.dir>/karate-config-<env>.js
De lo contrario (si nokarate.config.dir se configuró), Karate buscaráclasspath:karate-config-<env>.js
si la anulación karate-config-<env>.jsexiste, se procesará y la configuración (entradas JSON) devuelta por esta función anulará cualquier conjunto establecido porkarate-config.js
Consulte la demostración de kárate para ver un ejemplo .

karate-base.js
Los usuarios avanzados que crean marcos sobre Karate tienen la opción de proporcionar un karate-base.jsarchivo que Karate buscará en el archivo classpath:. Esto es útil cuando envía un archivo JAR que contiene funciones reutilizables y código JavaScript/Java y desea "predeterminar" algunas variables de las que los equipos pueden "heredar". Entonces, una regla adicional en el flujo de 'reglas' anterior (antes del primer paso) es la siguiente:

Si classpath:karate-base.jsexiste, Karate procesará esto como fuente de configuración antes que nada.
Guía de sintaxis
Estructura del guión
Los guiones de Karate están técnicamente en formato ' Gherkin ', pero todo lo que necesitas asimilar como alguien que necesita probar servicios web son las tres secciones: Feature, Backgroundy Scenario. Puede haber varios escenarios en un *.featurearchivo y al menos uno debe estar presente. El Backgroundes opcional.

Las variables configuradas usando defen Backgroundse restablecerán antes de cada Scenario . Si está buscando una manera de hacer algo solo una vez por vez Feature, eche un vistazo a callonce. Por otro lado, si espera que una variable en el Backgroundsea modificada por una Scenariopara que las posteriores puedan ver el valor actualizado, no es así como debe pensar en ellas, y debe combinar su 'flujo' en un solo escenario. Tenga en cuenta que debería poder comentar Scenariou omitir algunos tagssin afectar a los demás. Tenga en cuenta que el corredor paralelo ejecutará Scenario-s en paralelo, lo que significa que pueden ejecutarse en cualquier orden. Si está buscando formas de hacer algo solo una vez por función o en todas sus pruebas, consulte Ganchos .

Las líneas que comienzan con a #son comentarios.

Feature: brief description of what is being tested
    more lines of description if needed.

Background:
  # this section is optional !
  # steps here are executed before each Scenario in this file
  # variables defined here will be 'global' to all scenarios
  # and will be re-initialized before every scenario

Scenario: brief description of this scenario
  # steps for this scenario

Scenario: a different scenario
  # steps for this other scenario
También existe una variante de Scenariollamado Scenario Outlinejunto con Examples, útil para pruebas basadas en datos .

Dado-cuándo-entonces
El negocio de las pruebas de servicios web requiere acceso a aspectos de bajo nivel, como encabezados HTTP, rutas URL, parámetros de consulta, cargas útiles JSON o XML complejas y códigos de respuesta. Y Karate te da control sobre estos aspectos con un pequeño conjunto de palabras clave centradas en HTTP como url,,, etc.pathparam

Karate no intenta que las pruebas se realicen en "lenguaje natural", como se espera tradicionalmente que sean las pruebas de Cucumber . Dicho esto, la sintaxis es muy concisa y la convención de que cada paso debe comenzar con Given, o , hace Andque las cosas sean muy legibles. Termina con una aproximación decente de BDD a pesar de que los servicios web por naturaleza son "sin cabeza", sin interfaz de usuario y no son realmente amigables para los humanos.WhenThen

Pepino vs Karate
Karate se basó en Cucumber-JVM hasta la versión 0.8.0, pero el analizador y el motor se reescribieron desde cero en la versión 0.9.0 en adelante. Entonces usamos la misma sintaxis de Gherkin , pero la similitud termina ahí.

Si está familiarizado con Cucumber (JVM), es posible que se pregunte si necesita escribir definiciones de pasos . La respuesta es no .

El enfoque de Karate es que ya se han implementado todas las definiciones de pasos que necesita para trabajar con HTTP, JSON y XML. Y como puedes ampliar Karate fácilmente usando JavaScript , ya no es necesario compilar código Java.

La siguiente tabla resume algunas diferencias clave entre pepino y karate.

▫️	Pepino	Kárate
Definiciones de pasos integradas	No . Debe seguir implementándolos a medida que crezca su funcionalidad. Esto puede resultar muy tedioso , especialmente porque para la inyección de dependencia , usted está solo .	✅Sí . _ No se necesita código Java adicional.
Una sola capa de código para mantener	No . Hay 2 capas. Las especificaciones o archivos de Gherkin*.feature forman una capa y también tendrá las definiciones de pasos de Java correspondientes.	✅Sí . _ Sólo 1 capa de Karate-script (basado en Gherkin).
Especificación legible	Sí . Cucumber se leerá como un lenguaje natural si implementas correctamente las definiciones de pasos.	❌No . _ Aunque el Karate es simple y un verdadero DSL , en última instancia es un minilenguaje de programación . Pero es perfecto para probar servicios web a nivel de solicitudes y respuestas HTTP.
Reutilizar archivos de características	No . Cucumber no admite la posibilidad de llamar (y, por tanto, reutilizar) otros *.featurearchivos desde un script de prueba.	✅Sí . _
Pruebas dinámicas basadas en datos	No . Cucumber's Scenario Outlineespera que Examplescontenga un conjunto fijo de filas.	✅Sí . _ El soporte de Karate para llamar a otros *.featurearchivos le permite usar una matriz JSON como fuente de datos y puede usar JSON o incluso CSV directamente en un archivo Scenario Outline.
Ejecución paralela	No . Existen algunos desafíos (especialmente con los informes) y puede encontrar varias discusiones y proyectos de terceros en la web que intentan cerrar esta brecha.	✅Sí . _ Karate ejecuta Scenario-s pares en paralelo, no solo Feature-s.
Ejecute las rutinas de 'configuración' solo una vez	No . Cucumber tiene una limitación en la que Backgroundlos pasos se vuelven a ejecutar para siempre Scenarioy para peor, incluso para cada Examplesfila dentro de un archivo Scenario Outline. Este ha sido un tema abierto muy solicitado durante mucho tiempo.	✅Sí . _
Motor JavaScript integrado	No . Y debe aplicar su propio enfoque a la configuración específica del entorno y preocuparse por la inyección de dependencias .	✅Sí . _ Defina fácilmente todos los entornos en un solo archivo y comparta variables en todos los escenarios. Capacidad total de secuencias de comandos a través de interoperabilidad JS o Java .
Una cosa buena sobre el diseño de la sintaxis de Gherkin es que los pasos del guión se tratan de la misma manera sin importar si comienzan con la palabra clave Given, o . Lo que esto significa es que eres libre de utilizar lo que tenga sentido para ti. Incluso podrías comenzar con todos los pasos y a Karate no le importará.AndWhenThenWhen

De hecho, Gherkin admite el símbolo general ' *' , en lugar de obligarte a utilizar Given, Wheno Then. Esto es perfecto para aquellos casos en los que realmente no tiene sentido, por ejemplo, la Backgroundsección o cuando usas la sintaxis defo . setCuando analice un guión de prueba, considérelo *como una "viñeta".

Puede leer más sobre la convención Dado-Cuando-Entonces en la documentación de referencia de Cucumber . Dado que Karate utiliza Gherkin, también puedes emplear técnicas basadas en datos , como expresar tablas de datos en guiones de prueba. Otra cosa buena que hereda Karate es el buen soporte IDE para Cucumber que tienen IntelliJ y Eclipse . Por lo tanto, puede hacer cosas como hacer clic derecho y ejecutar un *.featurearchivo (o escenario) sin necesidad de utilizar un ejecutor JUnit.

Para una discusión detallada sobre BDD y cómo el Karate se relaciona con Cucumber, consulte esta publicación de blog: Sí, Karate no es verdadero BDD . La opinión del autor de Karate es que el verdadero BDD es innecesario para las pruebas de API, y esto se explica con más detalle en esta respuesta en Stack Overflow .

Una vez superadas las formalidades, profundicemos directamente en la sintaxis.

Configuración y uso de variables
def
Establecer una variable con nombre
# assigning a string value:
Given def myVar = 'world'

# using a variable
Then print myVar

# assigning a number (you can use '*' instead of Given / When / Then)
* def myNum = 5
Tenga en cuenta que esto defsobrescribirá cualquier variable que estuviera usando el mismo nombre anteriormente. Tenga en cuenta que la rutina de configuración de inicio podría haber inicializado algunas variables incluso antes de que se iniciara el script. Para obtener detalles sobre el alcance y la visibilidad de las variables, consulte Estructura del script .

Tenga en cuenta que urly requestno están permitidos como nombres de variables. Esto es sólo para reducir la confusión para los usuarios nuevos en Karate que tienden a hacer * def request = {}y esperar que el requestcuerpo o, de manera similar, se urlestablezca.

Los ejemplos anteriores son simples, pero en el lado derecho del =símbolo se admiten una variedad de "formas" de expresión. La sección sobre Expresiones de Karate entra en detalles.

assert
Afirmar si una expresión se evalúa comotrue
Una vez definida, puede hacer referencia a una variable por su nombre. Las expresiones se evalúan utilizando el motor JavaScript integrado. La palabra clave afirmar se puede utilizar para afirmar que una expresión devuelve un valor booleano.

Given def color = 'red '
And def num = 5
Then assert color + num == 'red 5'
Todo lo que esté a la derecha de la assertpalabra clave se evaluará como una expresión única.

Algo que vale la pena mencionar aquí es que casi no necesitarás usarlo asserten tus scripts de prueba. En su lugar, normalmente utilizaría la matchpalabra clave, que está diseñada para realizar afirmaciones potentes contra cargas de respuesta JSON y XML.

print
Iniciar sesión en la consola
Puede utilizarlo printpara registrar variables en la consola en medio de un script. Para mayor comodidad, puede tener varias expresiones separadas por comas, por lo que este es el patrón recomendado:

* print 'the value of a is:', a
De manera similar a assert, las expresiones en el lado derecho de a printtienen que ser JavaScript válido. No se admiten las expresiones JsonPath y Karate .

Si usa comas (en lugar de concatenar cadenas usando +), Karate 'imprimirá de forma bonita' las variables, que es lo que normalmente desea cuando trabaja con JSON o XML .

* def myJson = { foo: 'bar', baz: [1, 2, 3] }
* print 'the value of myJson is:', myJson
Lo que da como resultado el siguiente resultado:

20:29:11.290 [main] INFO  com.intuit.karate - [print] the value of myJson is: {
  "foo": "bar",
  "baz": [
    1,
    2,
    3
  ]
}
Dado que XML se representa internamente como un objeto similar a JSON o a un mapa, si realiza una concatenación de cadenas al imprimir, no verá XML, lo que puede resultar confuso al principio. Utilice el formulario delimitado por comas (ver arriba) o el asistente JS (ver más abajo).

karateEl objeto incorporado se explica en detalle más adelante, pero por ahora, tenga en cuenta que también se inyecta en print(e incluso assert) declaraciones, y tiene un prettymétodo útil que toma un argumento JSON y un prettyXmlmétodo que trata con XML. Entonces también podrías haber hecho algo como:

* print 'the value of myJson is:\n' + karate.pretty(myJson)
Consulte también la configurepalabra clave sobre cómo activar la impresión bonita de todas las solicitudes y respuestas HTTP.

Tipos de datos 'nativos'
Los tipos de datos nativos significan que puedes insertarlos en un script sin tener que preocuparte por encerrarlos en cadenas y luego tener que "escapar" de las comillas dobles por todos lados. Se ajustan perfectamente "en línea" dentro de su script de prueba.

JSON
Tenga en cuenta que el analizador es "indulgente", por lo que no es necesario encerrar todas las claves entre comillas dobles.

* def cat = { name: 'Billie', scores: [2, 5] }
* assert cat.scores[1] == 5
Algunos caracteres, como el guión, -no están permitidos en claves JSON "indulgentes" (porque el motor JS los interpreta como un "signo menos"). En tales casos, debe utilizar comillas:{ 'Content-Type': 'application/json' }

Al afirmar valores esperados en JSON o XML, prefiera siempre usar matchen lugar de assert. Los mensajes de falla de coincidencia son mucho más descriptivos y útiles, y obtienes el poder de las expresiones incrustadas y la coincidencia aproximada .

* def cats = [{ name: 'Billie' }, { name: 'Bob' }]
* match cats[1] == { name: 'Bob' }
El soporte nativo de Karate para JSON significa que puedes asignar partes de una instancia JSON a otra variable, lo cual es útil cuando se trata de responsecargas útiles complejas.

* def first = cats[0]
* match first == { name: 'Billie' }
Para manipular o actualizar JSON (o XML) utilizando expresiones de ruta, consulte la setpalabra clave.

XML
Given def cat = <cat><name>Billie</name><scores><score>2</score><score>5</score></scores></cat>
# sadly, xpath list indexes start from 1
Then match cat/cat/scores/score[2] == '5'
# but karate allows you to traverse xml like json !!
Then match cat.cat.scores.score[1] == 5
Expresiones integradas
Karate tiene un enfoque de 'plantilla' de carga útil muy útil. Se puede hacer referencia a variables dentro de JSON, por ejemplo:

Given def user = { name: 'john', age: 21 }
And def lang = 'en'
When def session = { name: '#(user.name)', locale: '#(lang)', sessionUser: '#(user)'  }
Entonces, la regla es: si un valor de cadena dentro de una declaración de objeto JSON (o XML) está encerrado entre #(y ), se evaluará como una expresión JavaScript. Y cualquier variable que esté viva en el contexto se puede utilizar en esta expresión. Así es como funciona para XML:

Given def user = <user><name>john</name></user>
And def lang = 'en'
When def session = <session><locale>#(lang)</locale><sessionUser>#(user)</sessionUser></session>
Esto resulta útil en algunos casos y evita la necesidad de utilizar setpalabras clave o funciones de JavaScript para manipular JSON. Así, obtienes lo mejor de ambos mundos: la elegancia de JSON para expresar datos anidados complejos y, al mismo tiempo, poder conectar valores dinámicamente (que incluso podrían ser otros 'árboles' JSON o XML) en una 'plantilla'.

Tenga en cuenta que las expresiones incrustadas se evaluarán incluso cuando provenga read()de un archivo JSON o XML . Esto es muy útil para la reutilización y las pruebas basadas en datos.

Algunas variables integradas especiales, como $(que es una referencia a la raíz JSON ), se pueden mezclar en expresiones incrustadas JSON.

Un caso especial de expresiones incrustadas puede eliminar una clave JSON (o elemento/atributo XML) si la expresión se evalúa como null.

Reglas para expresiones incrustadas
Funcionan sólo dentro de JSON o XML.
y cuando esté en el lado derecho de una
def
match
configure
y cuando tienes read()un archivo JSON o XML
la expresión tiene que empezar #(y terminar con)
Debido a la última regla anterior, tenga en cuenta que es posible que la concatenación de cadenas no funcione de la forma esperada:

# wrong !
* def foo = { bar: 'hello #(name)' }
# right !
* def foo = { bar: '#("hello " + name)' }
Observe cómo puede lograr la concatenación de cadenas si realmente lo desea, porque cualquier expresión JavaScript válida se puede incluir dentro de una expresión incrustada. Siempre puedes hacer esto en dos pasos:

* def temp = 'hello ' + name
* def foo = { bar: '#(temp)' }
Para su comodidad, se admiten expresiones incrustadas en el lado derecho de una matchdeclaración incluso para literales de "cadena entre comillas":

* def foo = 'a1'
* match foo == '#("a" + 1)'
Y tenga en cuenta que en Karate 1.0 en adelante, se admite la interpolación de cadenas ES6 dentro de "comillas invertidas":

* param filter = `ORDER_DATE:"${todaysDate}"`
JavaScript adjunto
Una alternativa a las expresiones incrustadas (solo para JSON) es encerrar toda la carga útil entre paréntesis, lo que le indica a Karate que la evalúe como JavaScript puro. En muchos casos, esto puede ser mucho más simple que las expresiones incrustadas y los programadores de JavaScript se sentirán como en casa.

El siguiente ejemplo muestra la diferencia entre expresiones incrustadas y JavaScript adjunto:

When def user = { name: 'john', age: 21 }
And def lang = 'en'

* def embedded = { name: '#(user.name)', locale: '#(lang)', sessionUser: '#(user)' }
* def enclosed = ({ name: user.name, locale: lang, sessionUser: user })
* match embedded == enclosed
Entonces, ¿cómo elegirías entre los dos enfoques para crear JSON? Las expresiones incrustadas son útiles cuando tiene readarchivos JSON complejos, porque puede reemplazar automáticamente (o incluso eliminar ) elementos de datos con valores evaluados dinámicamente a partir de variables. Y el JSON seguirá estando "bien formado" y será editable en su IDE o editor de texto. Las expresiones integradas también tienen más sentido en situaciones de validación y de atajos similares a esquemas . También se puede argumentar que el #símbolo es fácil de detectar al observar los scripts de prueba, lo que hace que las cosas sean más legibles y claras.

Expresiones de varias líneas
Las palabras clave def,, y toman entradas setde varias líneas como último argumento. Esto es útil cuando desea expresar un fragmento de texto largo y único en línea, sin tener que dividirlo en un archivo separado . Observe cómo se utilizan comillas triples ( ) para encerrar el contenido. Aquí hay unos ejemplos:matchrequesteval"""

# instead of:
* def cat = <cat><name>Billie</name><scores><score>2</score><score>5</score></scores></cat>

# this is more readable:
* def cat = 
  """
  <cat>
      <name>Billie</name>
      <scores>
          <score>2</score>
          <score>5</score>
      </scores>
  </cat>
  """
# example of a request payload in-line
Given request 
  """ 
  <?xml version='1.0' encoding='UTF-8'?>
  <S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
  <S:Body>
  <ns2:QueryUsageBalance xmlns:ns2="http://www.mycompany.com/usage/V1">
      <ns2:UsageBalance>
          <ns2:LicenseId>12341234</ns2:LicenseId>
      </ns2:UsageBalance>
  </ns2:QueryUsageBalance>
  </S:Body>
  </S:Envelope>
  """

# example of a payload assertion in-line
Then match response ==
  """
  { id: { domain: "DOM", type: "entityId", value: "#ignore" },
    created: { on: "#ignore" }, 
    lastUpdated: { on: "#ignore" },
    entityState: "ACTIVE"
  }
  """
table
Una forma sencilla de crear matrices JSON
Ahora que hemos visto cómo JSON es un tipo de datos "nativo" que Karate entiende, hay una manera muy buena de crear JSON utilizando el soporte para expresar tablas de datos .

* table cats
  | name   | age |
  | 'Bob'  | 2   |
  | 'Wild' | 4   |
  | 'Nyan' | 3   |

* match cats == [{name: 'Bob', age: 2}, {name: 'Wild', age: 4}, {name: 'Nyan', age: 3}]
La matchpalabra clave se explica más adelante, pero debe quedar claro de inmediato lo conveniente que tablees. JSON se puede combinar con la capacidad de llamar a otros *.featurearchivos para lograr pruebas dinámicas basadas en datos en Karate.

Observe que en el ejemplo anterior, los valores de cadena dentro de la tabla deben estar entre comillas. De lo contrario, se evaluarían como expresiones, lo que resulta útil para algunas situaciones dinámicas basadas en datos:

* def one = 'hello'
* def two = { baz: 'world' }
* table json
  | foo     | bar            |
  | one     | { baz: 1 }     |
  | two.baz | ['baz', 'ban'] |
* match json == [{ foo: 'hello', bar: { baz: 1 } }, { foo: 'world', bar: ['baz', 'ban'] }]
Sí, incluso puedes anidar fragmentos de JSON en tablas y todo funciona como es de esperar.

Las celdas vacías o expresiones que se evalúen nulldarán como resultado que la clave se omita del JSON. Para forzar un nullvalor, envuélvalo entre paréntesis:

* def one = { baz: null }
* table json
  | foo     | bar    |
  | 'hello' |        |
  | one.baz | (null) |
  | 'world' | null   |
* match json == [{ foo: 'hello' }, { bar: null }, { foo: 'world' }]
Una forma alternativa de crear datos es utilizar la sintaxis setmúltiple . En realidad, es una "transposición" del tableenfoque y puede resultar muy conveniente cuando hay una gran cantidad de claves por fila o si el anidamiento es complejo. A continuación se muestra un ejemplo de lo que es posible:

* set search
  | path       | 0        | 1      | 2       |
  | name.first | 'John'   | 'Jane' |         |
  | name.last  | 'Smith'  | 'Doe'  | 'Waldo' |
  | age        | 20       |        |         |

* match search[0] == { name: { first: 'John', last: 'Smith' }, age: 20 }
* match search[1] == { name: { first: 'Jane', last: 'Doe' } }
* match search[2] == { name: { last: 'Waldo' } }
text
No analizar, tratar como texto sin formato
No es algo que usarías comúnmente, pero en algunos casos necesitas deshabilitar el comportamiento predeterminado de Karate de intentar analizar cualquier cosa que parezca JSON (o XML) cuando usas expresiones de múltiples líneas /cadenas . Esto es especialmente relevante cuando se manipulan consultas GraphQL , porque aunque se parecen sospechosamente a JSON, no lo son y tienden a confundir las partes internas de Karate. Y como se muestra en el siguiente ejemplo, tener texto 'en línea' es útil especialmente cuando se utiliza y para pruebas basadas en datos que involucran sustituciones de marcadores de posición en cadenas.Scenario Outline:Examples:

Scenario Outline:
  # note the 'text' keyword instead of 'def'
  * text query =
    """
    {
      hero(name: "<name>") {
        height
        mass
      }
    }
    """
  Given path 'graphql'
  And request { query: '#(query)' }
  And header Accept = 'application/json'
  When method post
  Then status 200

  Examples:
    | name  |
    | John  |
    | Smith | 
Tenga en cuenta que si no necesitaba inyectar Examples:en los 'marcadores de posición' incluidos en <y >, leer un archivo con la extensión *.txtpuede haber sido suficiente.

Para la sustitución de marcadores de posición, replacese puede utilizar la palabra clave, pero con la ventaja de que el texto se puede leer desde un archivo o crearse dinámicamente.

Karate es ideal para probar GraphQL debido a lo fácil que es lidiar con respuestas JSON dinámicas y profundamente anidadas. Consulte este ejemplo para obtener más detalles: graphql.feature.


Funciones basadas en datos
Si el argumento pasado a la llamada de un *.featurearchivo es una matriz JSON, sucede algo interesante. La característica se invoca para cada elemento de la matriz. Se espera que cada elemento de la matriz sea un objeto JSON y, para cada objeto, el comportamiento será el descrito anteriormente.

Pero esta vez, el valor de retorno del callpaso será una matriz JSON del mismo tamaño que la matriz de entrada. Y cada elemento de la matriz devuelta será el 'sobre' de variables que resultaron de cada iteración en la que se *.featureinvocó.

A continuación se muestra un ejemplo que combina la tablepalabra clave con la llamada a un archivo *.feature. Observe cómo se utiliza el atajo para 'destilar' la matriz resultante de 'sobres' variables en una matriz que consta únicamente de cargas útiles.get response

* table kittens 
  | name   | age |
  | 'Bob'  |   2 |
  | 'Wild' |   1 |
  | 'Nyan' |   3 |

* def result = call read('cat-create.feature') kittens
* def created = $result[*].response
* match each created == { id: '#number', name: '#string', age: '#number' }
* match created[*].name contains only ['Bob', 'Wild', 'Nyan']
Y así es como cat-create.featurepodría verse:

@ignore
Feature:

Scenario:
  Given url someUrlFromConfig
  And path 'cats'
  And request { name: '#(name)', age: '#(age)' }
  When method post
  Then status 200
Si reemplaza tablequizás con una llamada a función de JavaScript que obtiene algunos datos JSON de alguna fuente de datos, puede imaginar cómo podría realizar pruebas dinámicas basadas en datos.

Aunque son solo unas pocas líneas de código, tómate el tiempo para estudiar detenidamente el ejemplo anterior. Es un gran ejemplo de cómo utilizar eficazmente la combinación única de sintaxis y JsonPath que proporciona Karate.

Mire también los ejemplos de demostración , especialmente para comparar el enfoque anterior con cómo se puede utilizar alternativamente dynamic-params.featureGherkin para pruebas basadas en datos.Scenario Outline:

Variables incorporadas paracall
Aunque todas las propiedades en el argumento tipo JSON pasado se 'desempaquetan' en el ámbito actual como variables 'nombradas' separadas, a veces tiene sentido acceder al argumento completo y esto se puede hacer a través de __arg. Y si se llama en un bucle, también estará disponible una variable incorporada llamada __loopque contendrá el valor del índice del bucle actual. Entonces puedes hacer cosas como esta: * def name = name + __loop- o puedes usar el valor del índice de bucle para buscar otros valores que puedan estar dentro del alcance - en un estilo basado en datos.

Variable	Se refiere a
__arg	el argumento único call(o callonce), será nullsi no hubiera ninguno
__loop	el índice de iteración actual (comienza desde 0) si se llama en un bucle, será -1si no
Consulte esta función de demostración para ver un ejemplo:kitten-create.feature

Valores predeterminados
Algunos usuarios necesitan funciones "invocables" que sean reutilizables incluso cuando la función de llamada no haya definido variables. Normalmente, una variable indefinida produce errores desagradables de JavaScript. Pero existe una forma elegante de especificar un valor predeterminado utilizando la karate.get()API:

# if foo is not defined, it will default to 42
* def foo = karate.get('foo', 42)
Una palabra de precaución: le recomendamos que no abuse de la capacidad de Karate de poder reutilizar funciones. La reutilización a veces puede generar beneficios negativos, especialmente cuando se aplica a la automatización de pruebas. Prefiere la legibilidad a la reutilización. Vea esto como ejemplo .

copy
Para una call(o callonce) - carga útil/estructuras de datos (JSON, XML, tipo mapa o tipo lista), las variables se 'pasan por referencia', lo que significa que los pasos dentro de la característica 'llamada' pueden actualizarlas o 'mutarlas', por ejemplo utilizando la setpalabra clave. En realidad, esta es la intención la mayor parte del tiempo y es conveniente. Si desea pasar un 'clon' a una función 'llamada', puede hacerlo utilizando la copypalabra clave poco utilizada que funciona de manera muy similar a la conversión de tipos . Esto se explica mejor en este ejemplo: copy.feature.

Llamar a funciones de JavaScript
En secciones anteriores de este documento aparecen ejemplos de definición y uso de funciones de JavaScript . Ser capaz de definir y reutilizar funciones de JavaScript es una capacidad poderosa del Karate. Por ejemplo, puedes:

llamar a funciones reutilizables que toman datos complejos como argumento y devuelven datos complejos que se pueden almacenar en una variable
llamar e interoperar con código Java si es necesario
comparta y reutilice utilidades de prueba o funciones de "ayuda" en toda su organización
Para obtener un ejemplo avanzado de cómo puede crear y reutilizar un conjunto común de funciones JS, consulte esta respuesta en Stack Overflow .

En los scripts de la vida real, normalmente también usaría esta capacidad de Karate donde configure headersla función JavaScript especificada usa las variables que resultan de un inicio de sesión para manipular los encabezados de todas las solicitudes HTTP posteriores. Y vale la pena mencionar que la rutina 'bootstrap' de configuración de Karate es en sí misma una función de JavaScript.

Consulte también la evalpalabra clave para conocer una forma más sencilla de ejecutar JavaScript arbitrario que puede resultar útil en algunas situaciones.

Reglas de argumentos de funciones JS paracall
Cuando se usa call(o callonce), solo se permite un argumento. Pero esto no lo limita de ninguna manera, porque de manera similar a como puede llamar a*.feature files , puede pasar un objeto JSON completo como argumento. En el caso de calluna función JavaScript, también puede pasar una matriz JSON o una primitiva (cadena, número, booleano) como argumento único, y se espera que la implementación de la función maneje todo lo que se pase.

En lugar de usar call(o callonce), siempre puedes llamar a las funciones de JavaScript "normalmente" y luego puedes usar más de un argumento.

* def adder = function(a, b){ return a + b }
* assert adder(1, 2) == 3
Tipos de devolución
Naturalmente, sólo se puede devolver un valor. Pero nuevamente, puedes devolver un objeto JSON. Hay dos cosas que pueden suceder con el valor devuelto.

O bien, se puede asignar a una variable como esta.

* def returnValue = call myFunction
O bien, si a callse realiza sin una asignación y la función devuelve un objeto similar a un mapa, agregará cada par clave-valor devuelto como una nueva variable al contexto de ejecución.

# while this looks innocent ...
# ... behind the scenes, it could be creating (or over-writing) a bunch of variables !
* call someFunction
Si bien esto suena peligroso y debe usarse con cuidado (y limita la legibilidad), la razón por la que existe esta característica es para configurar (o sobrescribir) rápidamente un montón de variables de configuración cuando sea necesario. De hecho, este es el mecanismo utilizado cuando karate-config.jsse procesa en el inicio.

Alcance compartido
Este comportamiento en el que todos los pares clave-valor en el objeto similar a un mapa devuelto se agregan automáticamente como variables también se aplica a la llamada de *.featurearchivos . En otras palabras, cuando callo calloncese usa sin un def, el script 'llamado' no solo comparte todas las variables (y configureconfiguraciones) sino que también puede actualizar el contexto de ejecución compartido. Esto es muy útil para resumir esos pasos "comunes" que quizás deba realizar al inicio de varios scripts de prueba, en frases breves. Pero utilícelo con prudencia, porque los scripts llamados ahora sobrescribirán las variables que ya hayan sido definidas.

* def config = { user: 'john', password: 'secret' }
# this next line may perform many steps and result in multiple variables set for the rest of the script
* call read('classpath:common-setup.feature') config
Puede utilizar callonceen lugar de calldentro de Backgrounden caso de que tenga varias Scenariosecciones o Examples. Tenga en cuenta el uso 'en línea' de la función de lectura como atajo arriba. Esto también se aplica a las funciones JS:

* call read('my-function.js')
Estos ejemplos de demostración muy comentados pueden ayudarle a comprender mejor el "alcance compartido" y están diseñados para ayudarle a comenzar a crear flujos de autenticación o "inicio de sesión" reutilizables:

Alcance	Función de llamada	Característica llamada
Aislado	call-isolated-headers.feature	common-multiple.feature
Compartido	call-updates-config.feature	common.feature
Una vez que se sienta cómodo con Karate, puede considerar mover su flujo de autenticación a un flujo único "global" usando karate.callSingle(), considérelo como " calloncecon esteroides".

callvsread()
Dado que esta es una pregunta frecuente, a continuación se resumen las diferentes formas de poder reutilizar código (o datos).

Código	Descripción
* def login = read('login.feature')
* call login	Alcance compartido y la
loginvariable se puede reutilizar
* call read('login.feature')	atajo para lo anterior
sin necesidad de una variable
* def credentials = read('credentials.json')
* def login = read('login.feature')
* call login credentials	Tenga en cuenta que el uso de un archivo JSON devuelve datos , no código "invocable", y aquí se utiliza como argumento.read()


call
* call read('login.feature') read('credentials.json')	Puedes hacer esto en teoría,
pero no es tan legible como lo anterior.
* karate.call('login.feature')	La API JS le permite hacer esto,
pero no será un ámbito compartido.
* def result = call read('login.feature')	callresultado asignado a una variable
y no al alcance compartido
* def result = karate.call('login.feature')	exactamente equivalente a lo anterior!
* if (cond) karate.call(true, 'login.feature')	Si necesita lógica condicional
y alcance compartido , agregue un primer argumento
booleano .true
* def credentials = read('credentials.json')
* def result = call read('login.feature') credentials	como el anterior,
pero con un callargumento
* def credentials = read('credentials.json')
* def result = karate.call('login.feature', credentials)	como el anterior, pero en formato JS API ,
la ventaja del formulario anterior es
que usar un argumento en línea es menos
"desordenado" (ver la siguiente fila)
* def login = read('login.feature')
* def result = call login { user: 'john', password: 'secret' }	el uso de la callpalabra clave hace que
pasar un argumento JSON en línea sea
más "legible"
* call read 'credentials.json'	Dado que " read" resulta ser una
función (que toma un solo
argumento de cadena), esto tiene el efecto
de cargar todas las claves en el archivo JSON
en Shared Scope como variables .
A veces esto puede resultar útil .
* call read ('credentials.json')	Un error común. En primer lugar, JSON
no tiene ningún significado . En segundo lugar, el espacio después de " " hace que esto sea igual a lo anterior.call
read
* karate.set(read('credentials.json'))	Para completar, ¡esto tiene exactamente el mismo efecto que las dos filas anteriores!
Llamando a Java
Hay ejemplos de cómo llamar a clases JVM en la sección sobre Java Interop y en la demostración de carga de archivos . Consulte también la sección sobre utilidades comúnmente necesarias para obtener más ideas.

Llamar a cualquier código Java es así de fácil. Dada esta clase Java personalizada y definida por el usuario:

package com.mycompany;

import java.util.HashMap;
import java.util.Map;

public class JavaDemo {    
    
    public Map<String, Object> doWork(String fromJs) {
        Map<String, Object> map = new HashMap<>();
        map.put("someKey", "hello " + fromJs);
        return map;
    }

    public static String doWorkStatic(String fromJs) {
        return "hello " + fromJs;
    }   

}
Así es como se puede llamar desde un script de prueba a través de JavaScript , y sí, incluso se pueden invocar métodos estáticos:

* def doWork =
  """
  function(arg) {
    var JavaDemo = Java.type('com.mycompany.JavaDemo');
    var jd = new JavaDemo();
    return jd.doWork(arg);  
  }
  """
# in this case the solitary 'call' argument is of type string
* def result = call doWork 'world'
* match result == { someKey: 'hello world' }

# using a static method - observe how java interop is truly seamless !
* def JavaDemo = Java.type('com.mycompany.JavaDemo')
* def result = JavaDemo.doWorkStatic('world')
* assert result == 'hello world'
Tenga en cuenta que JSON se convierte automáticamente a Map(o List) al realizar el cruce a Java. Consulte la cats-java.featuredemostración para ver un ejemplo.

Un nivel adicional de conversión automática ocurre cuando los objetos cruzan el límite entre JS y Java. En el raro caso de que necesite mutar Mapo Listdevolver desde Java pero mientras aún esté dentro de un bloque JS, use karate.toJson()para convertir.

Otro ejemplo es dogs.feature: que en realidad realiza llamadas JDBC (base de datos), y dado que los datos devueltos por el código Java son JSON, la última sección de la prueba se puede usar de manera muy efectiva para afirmaciones de datos.match

Un gran ejemplo de cómo puedes extender Karate, incluso omitir el cliente HTTP pero aun así usar la automatización de pruebas de Karate de manera efectiva, es este ejemplo de gRPC de @thinkerou : karate-grpc. E incluso puede manejar flujos asincrónicos, como escuchar colas de mensajes .

Ejemplo de autenticación básica HTTP
Esto debería dejar claro por qué Karate no proporciona soporte "listo para usar" para ningún esquema de autenticación HTTP en particular. Las cosas están diseñadas para que puedas conectar lo que necesites, sin necesidad de compilar código Java. Puede elegir cómo administrar los valores de configuración específicos de su entorno, como nombres de usuario y contraseñas.

Primero el archivo JavaScript basic-auth.js:

function fn(creds) {
  var temp = creds.username + ':' + creds.password;
  var Base64 = Java.type('java.util.Base64');
  var encoded = Base64.getEncoder().encodeToString(temp.toString().getBytes());
  return 'Basic ' + encoded;
}
Y así es como funciona en un script de prueba usando la headerpalabra clave.

* header Authorization = call read('basic-auth.js') { username: 'john', password: 'secret' }
Puede configurar esto para todas las solicitudes posteriores o generar encabezados dinámicamente para cada solicitud HTTP si configure headers.

callonce
Cucumber tiene una limitación según la cual Backgroundlos pasos se vuelven a ejecutar para cada archivo Scenario. Y si tiene un Scenario Outline, esto sucede para cada fila del Examples. Este es un problema especialmente para las llamadas HTTP costosas y que consumen mucho tiempo, y ha sido un problema abierto durante mucho tiempo .

La palabra clave de Karate calloncese comporta exactamente igual call, pero se garantiza que se ejecutará solo una vez. Los resultados de la primera llamada se almacenan en caché y cualquier llamada futura simplemente devolverá el resultado almacenado en caché en lugar de ejecutar la función (o característica) de JavaScript una y otra vez.

Esto requiere que mueva la "configuración" a un *.featurearchivo separado (o JavaScript). Pero esto tiene mucho sentido para cosas que no forman parte del flujo de prueba "principal" y que normalmente deben ser reutilizables de todos modos.

Entonces, cuando usas la combinación de callonceen a Background, puedes obtener el mismo efecto que usando una @BeforeAllanotación, y puedes encontrar ejemplos en la demostración de karate , como este: callonce.feature.

A calloncese utiliza idealmente sólo para JSON "puro". Es posible que tenga problemas si intenta mezclar funciones JS o código Java. Ver karate.callSingle().

Feature: karate answers 2

Background:
  * url 'http://localhost:8080'

Scenario Outline: given circuit name, validate country
  Given path 'api/f1/circuits/<name>.json'
  When method get
  Then match $.MRData.CircuitTable.Circuits[0].Location.country == '<country>'

 Scenario Outline: given race number, validate number of pitstops for Max Verstappen in 2015
  Given path 'api/f1/2015/<race>/drivers/max_verstappen/pitstops.json'
  When method get
  Then assert response.MRData.RaceTable.Races[0].PitStops.length == <stops>

  Examples:
    | race | stops |
    | 1    | 1     |
    | 2    | 3     |
    | 3    | 2     |
    | 4    | 2     |

    
Scenario Outline: name is ${name.first} ${name.last} and age is ${age}
  * match name.first == "#? _ == 'Bob' || _ == 'Nyan'"
  * match name.last == "#? _ == 'Dylan' || _ == 'Cat'"
  * match title == karate.scenario.name

Examples:
  | name!                               | age |
  | { "first": "Bob", "last": "Dylan" } | 10  |
  | { "first": "Nyan", "last": "Cat" }  | 5   |

  











