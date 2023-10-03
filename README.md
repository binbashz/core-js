
## Core-js: Biblioteca de JavaScript para Compatibilidad

**Core-js** es una biblioteca JavaScript que se utiliza para proporcionar funciones y características de JavaScript moderno en navegadores y entornos que no las admiten nativamente. Es comúnmente utilizado en proyectos de desarrollo web para garantizar que el código JavaScript funcione de manera consistente en diversos navegadores.

### Para qué sirve Core-js

Core-js es una biblioteca que ofrece polyfills (implementaciones de funciones y características) para estándares de JavaScript modernos, desde características antiguas de ES5 hasta características de vanguardia. Su utilidad principal es garantizar la compatibilidad y el funcionamiento de tu código JavaScript en una amplia variedad de navegadores y entornos. Algunos de los propósitos comunes de Core-js incluyen:

1. **Compatibilidad**: Permite utilizar características de JavaScript moderno incluso en navegadores más antiguos que no las admiten de forma nativa.

2. **Consistencia**: Asegura que tu código funcione de manera consistente en todos los navegadores y entornos.

3. **Modularidad**: Core-js es modular, lo que significa que puedes cargar solo las funciones que necesitas en tu proyecto, lo que ayuda a mantener el tamaño del paquete bajo control.

4. **Integración**: Se integra fácilmente con herramientas como Babel y otros transpiladores para facilitar el desarrollo de aplicaciones modernas.

### Pasos generales de instalación

1. **Instalación a través de npm** (Node Package Manager):

   - Abre una terminal en el directorio de tu proyecto.
   - Ejecuta el siguiente comando para instalar Core-js:

     ```bash
     npm install core-js
     ```

2. **Importación en tu proyecto**:

   - En tu código JavaScript, importa las funciones o características específicas que necesitas desde Core-js. Por ejemplo:

     ```javascript
     import 'core-js/stable'; // Importa las características estables
     import 'regenerator-runtime/runtime'; // Importa el runtime de generadores (si es necesario)
     ```

3. **Configuración (opcional)**:

   - Puedes configurar Core-js para que se ajuste a tus necesidades específicas, como seleccionar las características que deseas incluir o excluir.

4. **Uso en tu código**:

   - Utiliza las funciones y características de Core-js en tu código como lo harías normalmente. Core-js se encargará de proporcionar las implementaciones necesarias según sea necesario para garantizar la compatibilidad.

La configuración y los detalles específicos pueden variar según el proyectoy y las necesidades.

### Pensamientos de @zloirock

Introducción

Hola, soy [@zloirock](https://enlace_al_perfil_de_zloirock), un desarrollador de código abierto a tiempo completo. En este documento, compartiré algunos pensamientos y reflexiones sobre diversos temas relacionados con el ecosistema de JavaScript y el proyecto core-js.

## Problemas en el Ecosistema de JavaScript

En esta sección, @zloirock discute los problemas que ha identificado en el ecosistema de JavaScript. Esto puede incluir problemas con la adopción de estándares, la falta de mantenimiento de proyectos de código abierto, o cualquier otro problema relevante.

## ¿Cómo podemos arreglarlo?

Aquí, el autor propone posibles soluciones o ideas para abordar los problemas mencionados anteriormente. Puede ser una discusión sobre cómo mejorar la colaboración en proyectos de código abierto o cómo impulsar la adopción de estándares modernos de JavaScript.

## Conclusión

En la conclusión, @zloirock resume sus pensamientos y reflexiones, y puede hacer un llamado a la acción o destacar la importancia de abordar los problemas en el ecosistema de JavaScript.

# core-js


## ¿Qué es core-js?
Es el polyfill más popular y universal de la biblioteca estándar de JavaScript, que brinda soporte para el último estándar y las propuestas de ECMAScript, desde características antiguas de ES5 hasta características de vanguardia como ayudas de iterador y características de plataforma web estrechamente relacionadas con ECMAScript, como structuredClone.

Es el proyecto de polyfill más complejo y completo. Al momento de publicar esta publicación, core-js contiene alrededor de medio millar de módulos polyfill con diferentes niveles de complejidad (desde Object.hasOwn hasta Array.prototype.at hasta URL, Promise o Symbol) que están diseñados para funcionar juntos. Con una arquitectura diferente, cada uno de ellos podría ser un paquete separado; sin embargo, no es tan conveniente.

Es sumamente modular: puede elegir fácilmente (o incluso automáticamente) cargar solo las funciones que utilizará. Se puede utilizar sin contaminar el espacio de nombres global (alguien llama a este caso de uso "ponyfill").

Está diseñado para la integración con herramientas y proporciona todo lo necesario para ello; por ejemplo, @babel/preset-env, @babel/transform-runtime y funciones SWC similares se basan en core-js.

Es una de las razones principales por las que los desarrolladores podrían usar funciones modernas de ECMAScript en su proceso de desarrollo todos los días durante muchos años, pero la mayoría de los desarrolladores simplemente no saben que tienen esta posibilidad porque la usan indirectamente según lo proporcionan sus transpiladores core-js, frameworks/paquetes intermedios como babel-polyfill, etc.

Alrededor de 9 mil millones de descargas de NPM / 250 millones de descargas de NPM por mes, 19 millones de repositorios GitHub dependientes (global ⋃ puro): cifras grandes, sin embargo, no muestran la distribución real de core-js. Comprobémoslo.

Escribí un script simple que verifica el uso de core-js en la lista de sitios web principales de Alexa. Podemos detectar casos evidentes de core-js uso y versiones usadas (sólo modernas).

### Uso
En este momento, este script que se ejecuta en los 1000 sitios web TOP detecta el uso de core-js en el 52% de los sitios web probados. Dependiendo de la fase de la luna (la lista, los sitios web, etc. no son constantes), los resultados pueden variar en un pequeño porcentaje. Sin embargo, se trata simplemente de una detección ingenua en las páginas de inicio de sitios web utilizando un navegador moderno que pierde muchos casos; la comprobación manual muestra que se trata de decenas de por ciento adicionales. Por ejemplo, dejemos las páginas de inicio de algunos sitios web de la captura de pantalla anterior donde este script no encontró, sin repetir para cada sitio web de la empresa (al principio, MS que ya está en la captura de pantalla) (tenga paciencia, después de la serie de capturas de pantalla core-js, El número de imágenes disminuirá):

- WhatsApp
- LinkedIn
- Netflix
- QQ
- eBay
- Apple
- Fandom
- Pornhub
- PayPal
- Binance
- Spotify

Con una verificación manual de este tipo, puede encontrar core-js entre el 75 y el 80% de los 100 sitios web principales, mientras que el script lo encontró entre el 55 y el 60%. En una muestra más grande, el porcentaje, por supuesto, disminuye.

![core js](https://github.com/binbashz/core-js/assets/124454895/1e5ebc8a-5eaf-4ee5-848a-3008504c0b4a)


Wappalyzer permite detectar tecnologías utilizadas, incluida core-js, con un complemento de navegador y anteriormente ha mostrado resultados interesantes, pero ahora en su sitio web, los resultados públicos de todas las tecnologías más populares se limitan a solo unos 5 millones de positivos. Las estadísticas basadas en los resultados de Wappalyzer están disponibles aquí y se muestran core-js en el 41% y el 44% de 8 millones de páginas probadas en dispositivos móviles y 5 millones de computadoras de escritorio. En este momento, Build With se muestra core-js en el 54% de los 10.000 sitios TOP (sin embargo, no estoy seguro de si su detección está completa y veo el gráfico desde otra realidad).

De todos modos, podemos decir con seguridad que core-js lo utilizan la mayoría de los sitios web populares. Incluso si core-js no se utiliza en el sitio principal de ninguna gran corporación, definitivamente se usa en algunos de sus proyectos.

## ¿Qué bibliotecas JS están más extendidas en los sitios web? No es React, Lodash ni ninguna otra biblioteca o marco de trabajo del que más se habla, estoy bastante seguro solo de jQuery "bueno y antiguo".

Y core-js no se trata solo de la interfaz de un sitio web (se usa en casi todos los lugares donde se usa JavaScript), pero creo que son estadísticas más que suficientes.

### GitHub
Sin embargo, por las razones anteriores, casi nadie recuerda que usa core-js.

### ¿Por qué publico esto? No, no para mostrar lo genial que soy, sino para mostrar lo mal que está todo. Sigue leyendo.

## Comencemos la siguiente parte con una xkcd imagen popular.

![xkcd](https://imgs.xkcd.com/comics/standards.png)

## Comienzo
Cambié mi pila de desarrollo a JavaScript completo en 2012. Era una época en la que JavaScript todavía era demasiado básico: IE todavía era más popular que cualquier otra cosa, los navegadores de la era ES3 todavía ocupaban una parte importante de la web, la última versión de NodeJS era 0,7: recién estaba comenzando su camino. JavaScript todavía no estaba adaptado para escribir aplicaciones serias y los desarrolladores resolvieron la falta de sintaxis del lenguaje requerida con compiladores de lenguajes como CoffeeScript y la falta de una biblioteca estándar requerida con jQuery.

Como recién comencé en este mundo, no me molestó tanto el mal diseño de los lenguajes como los más experimentados, en lugar de eso, me emocioné con las oportunidades que JavaScript proporcionaba y esperaba que con el tiempo se eliminaran sus deficiencias.

Eso es lo que sucedió. Hoy en día, JavaScript es un lenguaje completamente diferente que se parece más a TypeScript que a ECMAScript 5, el estándar que estaba en uso en ese momento. El desarrollo de JavaScript es realmente asombroso: es el lenguaje más popular, y no solo en términos de la web; se está utilizando para la programación de servidores y aplicaciones de escritorio.

ECMAScript, la base de JavaScript, se está desarrollando incluso más rápido, y sus propuestas más audaces ya se han adoptado en las últimas versiones. Hace 5 años, muchas características de hoy solo eran sueños, pero hoy las tenemos en la especificación. Además, las propuestas para el futuro están prácticamente garantizadas: incluso si la propuesta no tiene un consenso completo en TC39 (el comité de desarrollo de ECMAScript) en un momento dado, todavía hay muchas oportunidades para que obtenga apoyo debido a la importancia de los proponentes y simplemente porque las propuestas son promovido por los desarrolladores más influyentes de JavaScript y organizaciones que representan a una gran cantidad de usuarios. En resumen, ECMAScript no es solo un lenguaje popular, sino también en constante desarrollo y desarrollo, que tiene una importancia crítica en la actualidad.

### El ecosistema está roto
Entonces, ¿cuál es el problema? El problema es que, con todo su desarrollo y popularidad, el ecosistema de JavaScript, lamentablemente, está roto.

Hace unos años, no tenía ninguna razón para preocuparme por el futuro de JavaScript. Hoy, a pesar de toda la belleza del lenguaje y su entorno, estoy preocupado. El problema es que casi nadie sabe cómo se resuelven los problemas actuales del ecosistema de JavaScript, incluidos los problemas graves que de hecho son simples de resolver. En cambio, los problemas se están intensificando cada vez más, porque las personas están trabajando en la solución equivocada. Incluso aquellos que entienden los problemas no pueden trabajar juntos, porque los proyectos que proporcionan las mismas funciones en realidad son competidores: quieren una mayor cantidad de estrellas y, por lo tanto, de alguna manera deben demostrar que son "mejores", pero no en la calidad de los proyectos, sino simplemente en ser "números uno".

Así es como funciona el ecosistema de JavaScript: alguien crea un proyecto, por ejemplo, un marco de trabajo para el desarrollo de aplicaciones, lo publica, el proyecto se convierte en popular, y otras personas comienzan a crear alternativas porque quieren su parte del pastel. Por lo tanto, en lugar de trabajar juntos para crear una solución sólida, todos los proyectos compiten por atención y recursos, lo que lleva a la fragmentación y la duplicación de esfuerzos.

### Ejemplos de problemas
Vamos a ver algunos ejemplos de problemas en el ecosistema de JavaScript.

#### 1. Módulos
JavaScript finalmente obtuvo un sistema de módulos nativo con las especificaciones ES6. Sin embargo, a pesar de que los navegadores modernos lo admiten, la mayoría de los proyectos aún usan sistemas de módulos de terceros como CommonJS o AMD. Esto crea una confusión innecesaria y obstaculiza la adopción de la forma nativa de trabajar con módulos.

#### 2. Build Tools
El mundo de las herramientas de construcción en JavaScript es un desastre. Hay muchas opciones diferentes, cada una con su propia configuración y estilo. Esto dificulta que los desarrolladores nuevos y experimentados se sumerjan en un proyecto existente y comiencen a trabajar de inmediato.

#### 3. Framework Fatigue
El ecosistema de JavaScript está saturado de marcos y bibliotecas. Si bien tener opciones es bueno, la excesiva cantidad de opciones puede llevar a la fatiga del marco. Los desarrolladores pueden sentirse abrumados por la cantidad de decisiones que deben tomar sobre qué herramientas y bibliotecas utilizar en sus proyectos.

#### 4. Falta de Convenios
En otros lenguajes y comunidades, existen convenciones y estándares comunes que facilitan la colaboración y la integración de proyectos. En JavaScript, la falta de convenciones hace que sea más difícil para los proyectos funcionar juntos de manera cohesiva.

### ¿Por qué está roto el ecosistema?
Entonces, ¿por qué el ecosistema de JavaScript está roto? Hay varias razones para esto.

#### 1. Velocidad del Cambio
JavaScript cambia rápidamente, y esto puede hacer que sea difícil para los proyectos mantenerse al día. Los desarrolladores a menudo se sienten presionados para adoptar las últimas tecnologías y herramientas, lo que puede llevar a una fragmentación y una falta de estabilidad.

#### 2. Competencia
Como mencioné anteriormente, la competencia entre proyectos es feroz en el mundo de JavaScript. Todos quieren ser la próxima gran cosa y obtener la mayor cantidad de estrellas en GitHub. Esto puede llevar a una falta de colaboración y a la duplicación de esfuerzos.

#### 3. Falta de Liderazgo
A diferencia de otros ecosistemas de software, JavaScript carece de un liderazgo centralizado que establezca estándares y promueva la colaboración. En su lugar, los proyectos a menudo son dirigidos por individuos o pequeños grupos de desarrolladores con sus propias agendas.

#### 4. Incentivos Erróneos
Los incentivos en el mundo de JavaScript a menudo están mal alineados. Los desarrolladores y los proyectos son recompensados por la adquisición de seguidores y estrellas en lugar de la calidad del código y la colaboración.

#### 5. Dificultades Técnicas
Algunos problemas en el ecosistema de JavaScript son técnicamente difíciles de resolver. Por ejemplo, la adopción de un sistema de módulos nativos en lugar de sistemas de módulos de terceros puede ser complicada debido a la necesidad de mantener la compatibilidad con proyectos existentes.

### ¿Cómo podemos arreglarlo?
Entonces, ¿cómo podemos arreglar el ecosistema de JavaScript? Aquí hay algunas ideas.

#### 1. Establecer Estándares
Una de las primeras cosas que podemos hacer es establecer estándares comunes para el desarrollo en JavaScript. Esto incluiría convenciones para el uso de módulos, herramientas de construcción, nombres de proyectos y más. Los estándares pueden ayudar a unificar el ecosistema y facilitar la colaboración entre proyectos.

#### 2. Fomentar la Colaboración
En lugar de competir entre sí, los proyectos en el ecosistema de JavaScript deberían fomentar la colaboración. Esto podría incluir la consolidación de proyectos similares en lugar de crear alternativas, la colaboración en herramientas de construcción y la creación de estándares comunes.

#### 3. Promover el Mantenimiento
El mantenimiento de proyectos es crucial para la estabilidad del ecosistema. Los proyectos deben ser recompensados por mantener y mejorar el código existente en lugar de centrarse únicamente en la adquisición de nuevos usuarios.

#### 4. Educación
La educación es fundamental para abordar muchos de los problemas en el ecosistema de JavaScript. Los desarrolladores deben estar informados sobre las mejores prácticas y los estándares comunes, y las herramientas de construcción deben ser más accesibles para los desarrolladores nuevos y experimentados.

#### 5. Liderazgo Centralizado
Aunque JavaScript es conocido por su descentralización, un liderazgo centralizado podría ayudar a establecer estándares y promover la colaboración. Esto podría ser una organización independiente o una mayor participación de TC39 en la gestión del ecosistema.

#### 6. Cambio de Incentivos
Los incentivos en el mundo de JavaScript deben cambiar para recompensar la calidad del código y la colaboración en lugar de la popularidad y las estrellas en GitHub.

### Conclusión
El ecosistema de JavaScript es increíblemente poderoso, pero también está roto. Los problemas actuales, como la falta de estándares, la competencia feroz y la falta de colaboración, están obstaculizando el potencial del lenguaje. Para arreglarlo, debemos trabajar juntos como comunidad para establecer estándares, fomentar la colaboración y cambiar nuestros incentivos. Solo entonces podremos aprovechar al máximo el poder de JavaScript y construir un ecosistema más saludable y sostenible.
