# AD-3.-Diagramas-UML-Entornos-de-Desarrollo-
Repositorio para la asignatura de entornos de desarrollo donde hay que realizar un diagrama de casos de uso y un diagrama de clases.Gestión de Equipos y Jugadores

**Autor:** Lorena Sánchez Erroz<br>
**Perfil GitHub:** LorenaSanchezErroz<br>
**Link del repositorio:** https://github.com/LorenaSanchezErroz/AD-3.-Diagramas-UML-Entornos-de-Desarrollo-.git<br>

A pesar de que el contexto del trabajo completo es la Gestión de Torneos de eSports, al no tener conocimientos sobre esto y sólo tener que realizar el modelado de un sistema de gestión de equipos y de jugadores, he decido enfocar esta sección en el supuesto de un equipo de baloncesto o liga de baloncesto.

## Análisis del diagrama de clases
**Actores** <br>
- <ins>Administrador</ins>: he denominado este actor como “administrador” ya que estamos modelando un sistema de gestión de jugadores y equipos, en el cual se ejecutan funciones que realiza un administrador (registrar equipos, añadir jugadores y consultar listas).
Como no hay mención de ningún otro usuario, como por ejemplo federación, seguidor, jugador, club, etc., considero como único actor principal “administrador”. Este podría ser administrador de un club/equipo.

**Casos de Uso**<br>
Teniendo en cuenta el enunciado, los casos de uso principales son:<br>
- <ins>Registrar Equipo</ins>: el administrador crea el equipo.<br>
- <ins>Añadir Jugador al Equipo</ins>: El administrador agrega un jugador a un equipo*.<br>
- <ins>Consultar Lista de Equipos y Jugadores</ins>: el administrador consulta los equipos y los jugadores.<br>
*duda: cuando se habla en este caso de equipo me surge la duda si se refiere aun equipo/club en sí o a un equipo en una determinada categoría.

**Relaciones entre Casos de Uso**<br>
Para “Añadir Jugador al Equipo” creo necesario saber si existe ese equipo, con el fin de que no se añadan jugadores a un equipo inexistente. Por ello, creo necesaria una relación de inclusión (<< include >>) de “Añadir Jugador al Equipo” hacia un caso de uso “Comprobar Existencia de Equipo”.

# Análisis del diagrama de clases
**Entidades**<br>
Para el diagrama de clases se han identificado las siguientes entidades:<br>
- <ins>Equipo</ins>: representa a un equipo, en este caso de baloncesto.<br>
- <ins>Jugador</ins>: representa a un jugador que pertenece al equipo.<br>
- <ins>Administrador</ins>: gestiona los equipos y los jugadores.<br>
- <ins>Categoría</ins>: aunque no se menciona en el enunciado, en el contexto del baloncesto es común que los equipos pertenezcan a categorías como prebenjamín, benjamín, alevín, infantil, cadete, junior, sub-22 y senior. Además, en España, la pirámide de competiciones va desde la liga ACB (la más alta) hasta las divisiones regionales. Por esta razón, creo necesario incluir esta entidad para que el diagrama sea más completo.

**Clases**<br>
Teniendo en cuenta lo anteriormente relatado, el diagrama estaría compuesto por las siguientes clases, con sus correspondientes atributos y métodos:<br>

_Clase Jugador_<br>
 - <ins>Atributos</ins>:<br>
        •	idJugador : int (identificador único).<br>
        •	nombreJugador : String (nombre del jugador).<br>
        •	apellidosJugador : String (apellidos del jugador).<br>
        •	fechaNacimiento : Date (es necesario para determinar la categoría por edad).<br>
        •	paisOrigen : String (necesario para aplicar reglas de cupos y jugadores de formación. En vez de ser tipo String podría sede la clase Pais; para no  tener que crear otra clase, lo he dejado con String).<br>
        •	posición : String (base, escolta, alero, ala-pivot, pivot. También se podría crear una clase de Posicion).<br>
        •	equipo : Equipo (equipo al que pertenece).<br>
 - <ins>Métodos</ins>:<br>
    Métodos inherentes de la clase*:<br>
        •	getIdJugador() : int  setIdJugador(id : int) : void.<br>
        •	getNombreJugador() : String, setNombreJugador(nombre : String) : void.<br>
        •	getApellidosJugador() : String, setApellidosJugador(apellidos : String) : void.<br>
        •	getFechaNacimiento() : Date, setFechaNacimiento(fecha : Date) : void.<br>
        •	getPaisOrigen() : String, setPaisOrigen(país : String) : void.<br>
        •	getPosicion() : String, setPosicion(posicion : String) : void.<br>
        •	getEquipo : Equipo, setEquipo(equipo : Equipo) : void.<br>
        •	toString() : String.<br>
    *duda: no sé si también se han de introducir los métodos hashCode() y equals().<br>

_Clase Equipo_<br>
- <ins>Atributos</ins>:<br>
        •	idEquipo : String (identificador único).<br>
        •	nombreEquipo : String (nombre del equipo).<br>
        •	categoría : Categoria (categoría a la que pertenece el equipo).<br>
        •	fechaAlta : Date (fecha de creación del equipo).<br>
        •	jugadores : List<Jugador> (lista de jugadores de ese equipo).<br>
 - <ins>Métodos</ins>:<br>
    Métodos inherentes de la clase:<br>
        •	getIdEquipo() : String, setIdEquipo(id : String) : void.<br>
        •	getNombreEquipo() : String, setNombreEquipo(nombre : String) : void.<br>
        •	getCategoria() : Categoria , setCategoria(categoria : Categoria) : void.<br>
        •	getFechaAlta() : Date, setFechaAlta(fecha : Date) : void.<br>
        •	getJugadores() : List<Jugador>, setJugadores(jugadores : List<Jugador>) : void.<br>
        •	toString() : String.<br>
    Métodos de la clase:<br>
        •	añadirJugador(jugador : Jugador) : void. (para añadir jugador al equipo).<br>
        •	eliminarJugador(jugador : Jugador) : void. (para eliminar jugador del equipo).<br>

_Clase Categoria_
- <ins>Atributos</ins>:<br>
        •	idCategoria : String (identificador único).<br>
        •	nombreCategoria : String (prebenjamín, benjamín, etc.).<br>
        •	edadMin : int (edad mínima para la categoría).<br>
        •	edaMax : int (edad máxima para la categoría).<br>
 - <ins>Métodos</ins>:<br>
    Métodos inherentes de la clase:<br>
        •	getIdCategoria() : String, setIdCategoria(id : String) : void.<br>
        •	getNombreCategoria() : String, setNombreCategoria(nombre : String) : void.<br>
        •	getEdadMin() : int, setEdadMin(edad : int) : void.<br>
        •	getEdadMax() : int, setEdadMax(edad : int) : void.<br>
        •	toString() : String.<br>

_Clase Administrador_ <br>
Administrador de equipos del club. En esta caso especifico que sólo hay un administrador. En caso contrario, si hay más de un administrador, habría que añadir un atributo administrador:Administrador a la clase Equipo.
- <ins>Atributos</ins>:<br>
        •	idAdministrador : int (identificador único).<br>
        •	nombreAdministrador: String (nombre del administrador del equipo).<br>
        •	email : String (dirección de contacto con el administrador).<br>
        •	equipos : List<Equipo> (lista de equipos gestionados).<br>
 - <ins>Métodos</ins>:<br>
    Métodos inherentes de la clase:<br>
        •	getIdAdministrador() : int, setIdAdministrador(id : int) : void.<br>
        •	getnombreAdministrador() : String, setNombreAdministrador(nombre : String) : void.<br>
        •	getEmail() : String, setEmail(email : String) : void.<br>
        •	getEquipos : List<Equipo>, setEquipos(equipos : List<Equipo>) : void.<br>
        •	toString() : String.<br>
    Métodos de la clase:<br>
        •	registrarEquipo(equipo : Equipo) : void (para registrar equipo).<br>
        •	consultarListaEquipos() : List<Equipo> (para ver lista de equipos).<br>
        •	consultarListaJugadores() : List<Jugador> (para ver lista de jugadores).<br>

**Relaciones entre clases**<br>
*Jugador <--> Equipo:*<br>
Tienen una relación de 1 a muchos, en el que un equipo de una categoría puede estar integrado por muchos jugadores y un jugador pertenece a un equipo de una determinada categoría.<br>
Su tipo de relación es de agregación ya que los jugadores son parte del equipo. Sin embargo, si el equipo elimina un jugador del equipo este jugador sigue existiendo en el sistema y puede ser añadido a otro equipo. A su vez, el equipo no desaparece porque se eliminen jugadores.

*Equipo <--> Administrador:*<br>
Tienen una relación de 1 a muchos, en la cual un equipo es gestionado por un administrador y un administrador puede gestionar muchos equipos.<br>
Su tipo de relación es de asociación ya que uno no forma parte del otro y no existe dependencia para su existencia.<br>

*Equipo <--> Categoria:*<br>
Tienen una relación de 1 a muchos, ya que un equipo pertenece a una categoría, pero muchos equipos pueden pertenecer a una misma categoría.<br>
Su tipo de relación es de asociación ya que uno no forma parte del otro y no existe dependencia para su existencia.<br>

## Conclusión<br>
Me ha resultado muy interesante realizar este trabajo.  Me ha ayudado a asimilar algunos conceptos de la programación ya estudiados, así como a analizar y visualizar la estructura de un sistema, con sus posibles necesidades e interacciones. <br>
Al principio hice un diagrama de casos de uso más extenso donde añadía otros casos de uso, como registro de jugadores, creación de lista de jugadores y equipos, lo que me llevaba a revisar también su existencia o comprobar que estos estén en la lista, así como los casos de uso de añadir jugadores y equipos a sus respectivas listas. Esto hacía el diagrama más complejo, además de encontrar alguna redundancia, y pensé que lo más adecuado era simplificar y centrarme en las tres funciones que me pedía el enunciado. <br>
Después, a la hora de buscar entidades para el diagrama pensé en la posibilidad de crear otras clases, como Pais o Posicion, y en añadirles más atributos, pero habría hecho el diagrama mucho más extenso y no creo que fuese el cometido de esta actividad.


