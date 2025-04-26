# AD-3.-Diagramas-UML-Entornos-de-Desarrollo-
Repositorio para la asignatura de entornos de desarrollo donde hay que realizar un diagrama de casos de uso y un diagrama de clases.Gestión de Equipos y Jugadores

**Autor:** Lorena Sánchez Erroz
**Perfil GitHub:** LorenaSanchezErroz
**Link del repositorio:** https://github.com/LorenaSanchezErroz/AD-3.-Diagramas-UML-Entornos-de-Desarrollo-.git

A pesar de que el contexto del trabajo completo es la Gestión de Torneos de eSports, al no tener conocimientos sobre esto y sólo tener que realizar el modelado de un sistema de gestión de equipos y de jugadores, he decido enfocar esta sección en el supuesto de un equipo de baloncesto o liga de baloncesto.

## Análisis del diagrama de clases
**Actores**
<ins>Administrador:</ins> he denominado este actor como “administrador” ya que estamos modelando un sistema de gestión de jugadores y equipos, en el cual se ejecutan funciones que realiza un administrador (registrar equipos, añadir jugadores y consultar listas).
Como no hay mención de ningún otro usuario, como por ejemplo federación, seguidor, jugador, club, etc., considero como único actor principal “administrador”. Este podría ser administrador de un club/equipo.

**Casos de Uso**
Teniendo en cuenta el enunciado, los casos de uso principales son:
<ins>Registrar Equipo:</ins>el administrador crea el equipo.
<ins>Añadir Jugador al Equipo:</ins>El administrador agrega un jugador a un equipo*.
<ins>Consultar Lista de Equipos y Jugadores:</ins>el administrador consulta los equipos y los jugadores.
*duda: cuando se habla en este caso de equipo me surge la duda si se refiere aun equipo/club en sí o a un equipo en una determinada categoría.

**Relaciones entre Casos de Uso**
Para “Añadir Jugador al Equipo” creo necesario saber si existe ese equipo, con el fin de que no se añadan jugadores a un equipo inexistente. Por ello, creo necesaria una relación de inclusión (<<include>>) de “Añadir Jugador al Equipo” hacia un caso de uso “Comprobar Existencia de Equipo”.

# Análisis del diagrama de clases
**Entidades**
Para el diagrama de clases se han identificado las siguientes entidades:
<ins>Equipo:</ins>representa a un equipo, en este caso de baloncesto.
<ins>Jugador:</ins>representa a un jugador que pertenece al equipo.
<ins>Administrador:</ins>gestiona los equipos y los jugadores.
<ins>Categoría:</ins>aunque no se menciona en el enunciado, en el contexto del baloncesto es común que los equipos pertenezcan a categorías como prebenjamín, benjamín, alevín, infantil, cadete, junior, sub-22 y senior. Además, en España, la pirámide de competiciones va desde la liga ACB (la más alta) hasta las divisiones regionales. Por esta razón, creo necesario incluir esta entidad para que el diagrama sea más completo.

**Clases**
Teniendo en cuenta lo anteriormente relatado, el diagrama estaría compuesto por las siguientes clases, con sus correspondientes atributos y métodos:
_Clase Jugador_
    -	<ins>Atributos:</ins>
        •	idJugador : int (identificador único).
        •	nombreJugador : String (nombre del jugador).
        •	apellidosJugador : String (apellidos del jugador).
        •	fechaNacimiento : Date (es necesario para determinar la categoría por edad).
        •	paisOrigen : String (necesario para aplicar reglas de cupos y jugadores de formación. En vez de ser tipo String podría sede la clase Pais; para no  tener que crear otra clase, lo he dejado con String).
        •	posición : String (base, escolta, alero, ala-pivot, pivot. También se podría crear una clase de Posicion).
        •	equipo : Equipo (equipo al que pertenece).
    -	<ins>Métodos:</ins>
    Métodos inherentes de la clase*:
        •	getIdJugador() : int  setIdJugador(id : int) : void.
        •	getNombreJugador() : String, setNombreJugador(nombre : String) : void.
        •	getApellidosJugador() : String, setApellidosJugador(apellidos : String) : void.
        •	getFechaNacimiento() : Date, setFechaNacimiento(fecha : Date) : void.
        •	getPaisOrigen() : String, setPaisOrigen(país : String) : void.
        •	getPosicion() : String, setPosicion(posicion : String) : void.
        •	getEquipo : Equipo, setEquipo(equipo : Equipo) : void.
        •	toString() : String.
    *duda: no sé si también se han de introducir los métodos hashCode() y equals().

_Clase Equipo_
    -	<ins>Atributos:</ins>
        •	idEquipo : String (identificador único).
        •	nombreEquipo : String (nombre del equipo).
        •	categoría : Categoria (categoría a la que pertenece el equipo).
        •	fechaAlta : Date (fecha de creación del equipo).
        •	jugadores : List<Jugador> (lista de jugadores de ese equipo).
    -	<ins>Métodos:</ins>
    Métodos inherentes de la clase:
        •	getIdEquipo() : String, setIdEquipo(id : String) : void.
        •	getNombreEquipo() : String, setNombreEquipo(nombre : String) : void.
        •	getCategoria() : Categoria , setCategoria(categoria : Categoria) : void.
        •	getFechaAlta() : Date, setFechaAlta(fecha : Date) : void.
        •	getJugadores() : List<Jugador>, setJugadores(jugadores : List<Jugador>) : void.
        •	toString() : String.
    Métodos de la clase:
        •	añadirJugador(jugador : Jugador) : void. (para añadir jugador al equipo).
        •	eliminarJugador(jugador : Jugador) : void. (para eliminar jugador del equipo).

_Clase Categoria_
    -	<ins>Atributos:</ins>
        •	idCategoria : String (identificador único).
        •	nombreCategoria : String (prebenjamín, benjamín, etc.).
        •	edadMin : int (edad mínima para la categoría).
        •	edaMax : int (edad máxima para la categoría).
    -	<ins>Métodos:</ins>
    Métodos inherentes de la clase:
        •	getIdCategoria() : String, setIdCategoria(id : String) : void.
        •	getNombreCategoria() : String, setNombreCategoria(nombre : String) : void.
        •	getEdadMin() : int, setEdadMin(edad : int) : void.
        •	getEdadMax() : int, setEdadMax(edad : int) : void.
        •	toString() : String.

_Clase Administrador_
Administrador de equipos del club. En esta caso especifico que sólo hay un administrador. En caso contrario, si hay más de un administrador, habría que añadir un atributo administrador:Administrador a la clase Equipo.
    -	<ins>Atributos:</ins>
        •	idAdministrador : int (identificador único).
        •	nombreAdministrador: String (nombre del administrador del equipo).
        •	email : String (dirección de contacto con el administrador).
        •	equipos : List<Equipo> (lista de equipos gestionados).
    -	<ins>Métodos:</ins>
    Métodos inherentes de la clase:
        •	getIdAdministrador() : int, setIdAdministrador(id : int) : void.
        •	getnombreAdministrador() : String, setNombreAdministrador(nombre : String) : void.
        •	getEmail() : String, setEmail(email : String) : void.
        •	getEquipos : List<Equipo>, setEquipos(equipos : List<Equipo>) : void.
        •	toString() : String.
    Métodos de la clase:
        •	registrarEquipo(equipo : Equipo) : void (para registrar equipo).
        •	consultarListaEquipos() : List<Equipo> (para ver lista de equipos).
        •	consultarListaJugadores() : List<Jugador> (para ver lista de jugadores).

**Relaciones entre clases**
*Jugador <--> Equipo:*
Tienen una relación de 1 a muchos, en el que un equipo de una categoría puede estar integrado por muchos jugadores y un jugador pertenece a un equipo de una determinada categoría.
Su tipo de relación es de agregación ya que los jugadores son parte del equipo. Sin embargo, si el equipo elimina un jugador del equipo este jugador sigue existiendo en el sistema y puede ser añadido a otro equipo. A su vez, el equipo no desaparece porque se eliminen jugadores.

*Equipo <--> Administrador:*
Tienen una relación de 1 a muchos, en la cual un equipo es gestionado por un administrador y un administrador puede gestionar muchos equipos.
Su tipo de relación es de asociación ya que uno no forma parte del otro y no existe dependencia para su existencia.

*Equipo <--> Categoria:*
Tienen una relación de 1 a muchos, ya que un equipo pertenece a una categoría, pero muchos equipos pueden pertenecer a una misma categoría.
Su tipo de relación es de asociación ya que uno no forma parte del otro y no existe dependencia para su existencia.

## Conclusión
Me ha resultado muy interesante realizar este trabajo.  Me ha ayudado a asimilar algunos conceptos de la programación ya estudiados, así como a analizar y visualizar la estructura de un sistema, con sus posibles necesidades e interacciones. 
Al principio hice un diagrama de casos de uso más extenso donde añadía otros casos de uso, como registro de jugadores, creación de lista de jugadores y equipos, lo que me llevaba a revisar también su existencia o comprobar que estos estén en la lista, así como los casos de uso de añadir jugadores y equipos a sus respectivas listas. Esto hacía el diagrama más complejo, además de encontrar alguna redundancia, y pensé que lo más adecuado era simplificar y centrarme en las tres funciones que me pedía el enunciado. 
Después, a la hora de buscar entidades para el diagrama pensé en la posibilidad de crear otras clases, como Pais o Posicion, y en añadirles más atributos, pero habría hecho el diagrama mucho más extenso y no creo que fuese el cometido de esta actividad.


