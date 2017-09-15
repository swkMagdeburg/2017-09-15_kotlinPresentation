---
title: Kotlin
separator: <!--s-->
verticalSeparator: <!--v-->
theme: solarized
highlight-theme: monokai
revealOptions:
  controls: false
  slideNumber: false
  transition: 'slide'
  backgroundTransition: 'fade'
---

<!-- Alle gennanten Personen sind frei erfunden, und jegliche Ähnlichkeit mit lebenden oder realen Personen sind rein zufällig. -->

# Kotlin

<!--s-->
# Was ist Kotlin?

<!--v-->
## Kotlin ist
* eine Programmiersprache
* objektorientiert
* funktional

<!--v-->
## Kotlin ist
Interoperabel mit Java
* Mischsprachige Java+Kotlin-Projekte
* Aufruf von Java-Libraries aus Kotlin-Code heraus
* Aufruf von Kotlin-Libraries aus Java-Code heraus

<!--v-->
## Kotlin ist
production-ready
* Entwickler: JetBrains
* in Entwicklung seit 2010
* Version 1.0 seit 2016
* unter Apache2 - Lizenz

<!--v-->
## Kotlin
läuft auf
* JVM
* Android (denn Bytecode ist Java6-kompatibel)
* im Browser (Compile nach JavaScript)
* **native** (über LLVM-Backend)

<!--v-->
## Warum ...
... noch eine JVM-Sprache?
* Syntax ist Java um 10 Jahre vorraus
* Code ist präziser, kompakter, einfacher!
* entwickelt mit Fokus für industriellen Einsatz:
  * Stabilität
  * Performance
  * Interoperabelität

<!--v-->
## Kotlin kann ...
* Extension Methods <span class="fragment" data-fragment-index="2">(geklaut aus C#)</span>
* Builder <span class="fragment" data-fragment-index="3">(geklaut aus Groovy)</span>
* Operator Overloading <span class="fragment" data-fragment-index="4">(geklaut aus C)</span>
* Lambdas <span class="fragment" data-fragment-index="5">(Python, C#, LISP, Perl, ...)</span>
* Delegated Properties <span class="fragment" data-fragment-index="6">(wahrscheinlich auch geklaut)</span>
* default non-null und Nullable-Operator '`?`'
* implizite Typsierung
* Value Types
* Semikolons sind optional <!-- .element: class="fragment" data-fragment-index="8" -->
* usw. ... <!-- .element: class="fragment" data-fragment-index="7" -->

<!--s-->
<!-- .slide: data-background="https://media.giphy.com/media/zXmbOaTpbY6mA/giphy.gif"-->
<!-- Matrix -->
# `c0d3 p0rn`

<!--s-->
<!-- .slide: data-background="https://media.giphy.com/media/4uFHKBxeuecP6/giphy.gif"-->
<!-- Star Wars irgendwas -->
## Basics

<!--v-->
## Hello World
```java
fun main(args : Array<String>) {
  println("Hello World")
}
```

<!--v-->
## Hello World
```java
fun main(args : Array<String>) {
  println("""|-| 3 |_ |_ 0 - \\/\\/ 0 |2 |_ |)""")
}
```
=> `|-| 3 |_|_ 0 - \\/\\/ 0 |2 |_ |)`

<!--v-->
## Hello World
```java
"\\d{2}\\.\\d{2}\\.\\d{4}"
"""\d{2}\.\d{2}\.\d{4}"""
```

<!--v-->
## Variablen-Definition
```
val zahl = 1 //immutable
zahl = 2 // B00M (Compile-Error)
var andereZahl = 3
andereZahl = 4 // ok
```

<!--v-->
## String Templates
```
val x=5
val y=3
println("$x+$y=${x+y}")
```
5+3=8

<!--v-->
## Methoden
```
fun add(x : Int, y : Int) : Int {
  return x+y
}
```
```
fun add(x : Int, y : Int) : Int = x+y
```
<!-- .element: class="fragment" -->
```
fun add(x : Int, y : Int) = x+y
```
<!-- .element: class="fragment" -->

<!--s-->
<!-- .slide: data-background="https://media.giphy.com/media/7Hiszs0NkF5te/giphy.gif"-->
<!-- Fight Club -->
## Named Parameters

<!--v-->
## Übrigens
Alle gennanten Personen sind frei erfunden, und jegliche Ähnlichkeit mit lebenden oder realen Personen sind rein zufällig.

<!--v-->
## Named Parameters
```
fun printKing(name : String, age : Int = 0,
                  salary : Double = 0.0) =
        println("$name is $age and earns $salary GU (Goldunzen)")
```

```
printKing("Andreas", 33, 9000.0)
```

<!-- .element: class="fragment" -->
"Andreas is 33 and earns 9000.0 GU (Goldunzen)" <!-- .element: class="fragment" -->
```
printKing(9000.0,"Andreas", 33)
```
<!-- .element: class="fragment" -->
B00M <!-- .element: class="fragment" -->

```
printKing(salary = 9000.0, name = "Andreas", age = 33)
```
<!-- .element: class="fragment" -->

<!--v-->
## Named Parameters
```
fun printKing(name : String, age : Int = 0,
                  salary : Double = 0.0) =
        println("$name is $age and earns $salary GU (Goldunzen)")
```
```
printKing(age=32, name="Maik")
```
"Maik is 32 and earns 0.0 GU (Goldunzen)" <!-- .element: class="fragment" -->
```
printKing(9000.0)
```
<!-- .element: class="fragment" -->
B00M <!-- .element: class="fragment" -->

<!--s-->
<!-- .slide: data-background="https://media.giphy.com/media/rIq6ASPIqo2k0/giphy.gif"-->
<!-- Star Trek -->
## data class

<!--v-->
## data class
```
data class Hacker(var name: String, val email: String,
   val company: String)
val bjoern = Hacker("Björn", "bjoern@stro.de", "bjos")
println(bjoern.name) // prints "Björn"
```
* POJO-One-Liner
* enthält: getters, setters, equals(), hashCode(), toString() und copy()

```
bjoern.email = bjoern@swk.de
```
<!-- .element: class="fragment" -->
B00M
<!-- .element: class="fragment" -->
```
bjoern.copy(email = "bjoern@swk.de")
```
<!-- .element: class="fragment" -->
OK
<!-- .element: class="fragment" -->

<!--s-->
<!-- .slide: data-background="https://media.giphy.com/media/2l95D5QEQSACI/giphy.gif"-->
<!-- wahrscheinlich Godzilla? -->
## Destructuring

<!--v-->
## Destructuring
```
data class Hacker(var name: String, val email: String,
   val company: String)

val bjoern = Hacker("Björn", "bjoern@swk.de", "bjos")
val (name, email, company) = bjoern
println(name)
```
<span class="fragment">"Björn"</span>
<span class="fragment"> WHAAAAA...? </span>

```java
val (email, company, name) = bjoern
println(name)
```
<!-- .element: class="fragment" -->
<span class="fragment">"bjos"</span>
<span class="fragment"> WHAAAAA...?</span>

<!--v-->
## Destructuring
```
data class Hacker(var name: String, val email: String,
                  val company: String)
val (name, email, company) = bjoern
// ist äquivalent mit
val name = bjoern.component1()
val email = bjoern.component2()
val company = bjoern.component3()
```
```java
val (name, company) = bjoern
```
<!-- .element: class="fragment" -->
OK
<!-- .element: class="fragment" -->
```java
val (email, company, name, var4) = bjoern
```
<!-- .element: class="fragment" -->
B00M
<!-- .element: class="fragment" -->

<!--v-->
## Destructuring
```
public Tuple<String, Boolean> login() {...}

Tuple<String, Boolean> ret = login();
String leftKeineAhnung = ret.getLeft();
Boolean rightPffWerWeiß = ret.getRight();
```
<span class="fragment">Ich **hasse** Tupel-Datentypen </span>
```
data class User(val name: String, val loginSuccessful: Boolean)
fun login() : User {...}
val (name, loggedIn) = login()
```
<!-- .element: class="fragment" -->

<!--s-->
<!-- .slide: data-background="https://media.giphy.com/media/3o6Mbc2vQcJfLyMNy0/giphy.gif"-->
<!-- Simpsons -->
## smart-casts

<!--v-->
## Typprüfung
```
if(obj is String)
  println(obj)
if(obj !is String)
  println("kein String")
```
'`is`' ist der '`instanceof`'-Operator Kotlins

<!--v-->
## smart-casts
```
fun demo(x : Any) {
    if (x is String)
        println(x.length)
}
```
smart-cast in einen String
```
if(x !is String)
  return
println(x.length)
```
<!-- .element: class="fragment" data-fragment-index="1" -->
ebenfalls smart-cast in einen String
<!-- .element: class="fragment" data-fragment-index="1" -->
```
if(x !is String || x.length == 0) {...}
if(x is String && x.length > 0) {...}
```
<!-- .element: class="fragment" data-fragment-index="2" -->
rechtseitiger smart-cast in 'if()'-Blöcken
<!-- .element: class="fragment" data-fragment-index="2" -->

<!--v-->
## when
```
when(x) {
  is String -> print("ist ein String")
  is Int -> print("ist Zahl")
  else -> print("keine Ahnung")
}
```
'when' ersetzt den 'switch'-Operator
<!-- .element: class="fragment" -->
```
when (x) {
    in 1..10 -> print("...")
    in isValidNumber(x) -> print("...")
    else -> print("...")
}
```
<!-- .element: class="fragment" -->

<!--v-->
## explizite casts
```
val x = y as String
```
unsafe cast: wirft evtl. eine Exception (bspw. when y '`null`' ist)
```
val x = y as? String
```
safe cast: x ist null, falls y kein String ist

<!--s-->
<!-- .slide: data-background="https://media.giphy.com/media/l2JdYkTPVG9gRbvhK/giphy.gif"-->
<!-- schon wieder Simpsons -->
## Nullables

<!--v-->
## Nullables
```
Optional<Integer> result = findMaxAgeInMillis(emptyCollection);
```
* Optionals sind Kompromiss zum Null-Handling
* in Kotlin stattdessen sprachinhärente Variante '`?`'

<!--v-->
## Nullables
```
val result? = findMaxAgeInMillis(emptyCollection);
```
* Kotlin ausgelegt auf die Eliminierung von NPE's
* mögl. Ursachen sind nur:
  * expliziter Aufruf von '`throw NullPointerException()`'
  * Nutzung des '`!!`'-Operators
  * externer Java-Code wirft eine NPE
  * Dateninkonsistenzen während der Initialisierung

<!--v-->
## Nullables
```
val b : String = null
```
B00M <!-- .element: class="fragment" -->
```
val b : String? = null
val c : String = b
```
<!-- .element: class="fragment" -->
B00M: c ist nicht nullable <!-- .element: class="fragment" -->
```
fun findMaxAgeInMillis(set : Set<Integer>?) : Integer? {...}
var c : Integer = findMaxAgeInMillis(Collections.emptySet())
```
<!-- .element: class="fragment" -->
B00M
<!-- .element: class="fragment" -->

<!--v-->
## dereferenzieren von Nullables
```
var jens :String? = "trinkt Bier"
var laenge = jens.length
```
B00M: "Only safe (?.) or non-null asserted (!!.) calls are allowed on a nullable receiver of type String?"
<!-- .element: class="fragment" -->
```
var laenge = if (jens != null) jens.length else -1
```
<!-- .element: class="fragment" -->
OK <!-- .element: class="fragment" -->
```
var laenge : Int? = jens?.length // länge oder null
```
<!-- .element: class="fragment" -->
OK <!-- .element: class="fragment" -->

<!--v-->
## dereferenzieren von Nullables

```
var jens :String? = "trinkt Bier"
var laenge : Int = jens?.length ?: -1 // länge oder -1
```
<!-- .element: class="fragment" -->
OK ('?:' Elvis-Operator) <!-- .element: class="fragment" -->

```
jens = null
var laenge = jens!!.length
```
<!-- .element: class="fragment" -->
OK (wirft aber garantiert eine NPE) <!-- .element: class="fragment" -->
```
var kingOfKingOfSwkMd : String? = swkMD?.king[0]?.king[0]?.name
```
<!-- .element: class="fragment" -->
OK (kingOfKingOfSwkMd ist null) <!-- .element: class="fragment" -->

<!--s-->
<!-- .slide: data-background="https://media.giphy.com/media/F7enXW5ijlgC4/giphy.gif"-->
<!-- Ghost in the Shell (Movie 1995) -->
## Method Extensions

<!--v-->
## Method Extensions
Erweiterung bestehender Klassen ohne die Notwendigkeit einer Vererbung oder des Decorator-Patterns.

<!--v-->
## Method Extensions
```
class Andreas {
    fun freundin() = "Sandra"
}

fun Andreas.firma() = "advanto"

val andreas = Andreas()
println(andreas.firma())
```
"advanto"
<!-- .element: class="fragment" -->
```
fun Andreas.freundin() = this.firma() // ätsch!
println(andreas.freundin())
```
<!-- .element: class="fragment" -->
"Sandra"
<!-- .element: class="fragment" -->
<span class="fragment">WHAAAAA ...!?</span>
<p class="fragment">Bei gleicher Signatur gewinnt immer der Member!</p>

<!--v-->
## Warum Method-Extensions?
```
class StringUtils {
    fun isEmpty(s : String?) = s!=null || s!!.trim() == ""
}
fun String?.isEmpty() = (this != null || this!!.trim() == "" )
```
Code-Completion direkt am Typ
<!-- .element: class="fragment" -->
```
fun Any?.toString() : String =
  if (this == null) "null" else toString()
```
<!-- .element: class="fragment" -->
<span class="fragment">rekursiver Aufruf von toString()?</span>
<p class="fragment">Nein, denn smart-cast von 'Any?' auf 'Any'</p>

<!--s-->
<!-- .slide: data-background="https://media.giphy.com/media/l2Je4zlfxF6z0IWZi/giphy.gif"-->
<!-- immer diese Simpsons -->
## Operator Overloading

<!--v-->
## Operator Overloading
```
data class Point(val x : Int,val y : Int)
operator fun Point.inc() = Point(x+1,y+1)
operator fun Point.dec() = Point(x-1,y-1)

fun main(args: Array<String>) {
    var p = Point(3,4)
    println("$p inc = ${++p}")
    println("$p dec = ${--p}")
}
```
Point(x=3, y=4) inc = Point(x=4, y=5) <br/>
Point(x=4, y=5) dec = Point(x=3, y=4)

* [Operator Overloading Doc](https://kotlinlang.org/docs/reference/operator-overloading.html)

<!--v-->
## Beispiel: Sets
```
val tobiMag = setOf("Tokio Hotel","Mathe","Sport")
val maikMag = setOf("Kuchen","Basteln","Tokio Hotel")
```
```
println(tobiMag + maikMag)
```
<!-- .element: class="fragment" -->
[Tokio Hotel, Mathe, Sport, Kuchen, Basteln]
<!-- .element: class="fragment" -->
```
println(tobiMag - maikMag)
```
<!-- .element: class="fragment" -->
[Mathe, Sport]
<!-- .element: class="fragment" -->
```
println( (tobiMag+maikMag)-(maikMag-tobiMag)-(tobiMag-maikMag) )
```
<!-- .element: class="fragment" -->
[Tokio Hotel]
<!-- .element: class="fragment" -->

<!--v-->
## Beispiel: '..' Bereichsdefinition
```
data class Point(val x : Int,val y : Int)
```
```
for(point in Point(1,2)..Point(4,5))
  println(point)
```
<!-- .element: class="fragment" data-fragment-index="1" -->
```
(Point(1,2)..Point(4,5)).forEach { println(it) }
```
<!-- .element: class="fragment" data-fragment-index="1" -->
Iteration über ein Punktebereich
<!-- .element: class="fragment" data-fragment-index="1" -->
```
operator fun Point.rangeTo(other: Point) = TwoDim(this, other)
class TwoDim(val start: Point, val end: Point): Iterable<Point>{
    override fun iterator(): Iterator<Point>=PointIterator(this)
}
class PointIterator(val field: TwoDim) : Iterator<Point> { ... }
```
<!-- .element: class="fragment" data-fragment-index="2" -->

<!--s-->
<!-- .slide: data-background="https://media.giphy.com/media/Z47Ar9QWXkQg/giphy.gif"-->
<!-- nu ist aber langsam Schluss mit Simpsons! -->
## Lambdas

<!--v-->
## Lambdas

```
val orderByGuest = mapOf<String, String>(
  "Andreas" to "Radler", "Maik" to "RichtigesBier",
  "Jens" to "Chardonnay")
orderByGuest.forEach { guest, order -> println("$guest=$order") }
```
* Lambdas: '{ [Parameter] -> [Anweisungsrumpf] }'
```
orderByGuest.forEach { println("${it.key}=${it.value}") }
```
* Impliziter Name 'it' für Einzelparameter
```
orderByGuest.forEach { _, order -> println("$order") }
```
* unnötige Parameter durch Unterstrich '`_`' markieren

<!--v-->
## Lambdas
C# [LINQ](https://msdn.microsoft.com/en-us/library/bb308959.aspx#linqoverview_topic2)
```
string[] names = { "Mario",  "Mandy", "Jens", ... };
IEnumerable<string> query = from s in names
                           where s.Length >= 5
                           orderby s.Length
                           select s.ToUpper();
foreach (string item in query) ...
```
```
// Kotlin
names.filter { it.length >= 5 }.
  sortedBy { it.length }.map { it.toUpperCase() }
// JAVA
names.stream().filter( s -> s.length() >= 5).
  sorted(Comparator.comparingInt(String::length)).
  map(String::toUpperCase);
```
<!-- .element: class="fragment" data-fragment-index="1" -->


<!--v-->
## Lambdas
```
data class Artist(val name: String)
data class Track(val name: String, val artist: Artist,
  val length: Int)
data class Album(val name: String, val tracks: List<Track>)
```
```
var megaHitsLenghts : Map<String,Int> = bjoernsAlbums.
  filter { it.name.matches(Regex(".*MegaHits.*")) }.
  map { it.name to it.tracks.map(Track::length).sum() }.
  toMap()
```
<!-- .element: class="fragment" -->
```
var britneySongs : List<Track> = bjoernsAlbums.flatMap {
  it.tracks.filter { it.artist.name == "Britney Spears" } }
```
<!-- .element: class="fragment" -->

<!--s-->
<!-- .slide: data-background="https://media.giphy.com/media/cwGbD7OgvM8uI/giphy.gif"-->
<!-- Despicable Me (1? 2? keine Ahnung) -->
## Delegated Properties

<!--v-->
## Delegated Properties
Häufig verwendete Fälle in eine Library auslagern, z.B.:
* lazy-Initialisierung
* Listener
* Variablen in einer Map statt im Property speichern
```
val/var <property name>: <Type> by <delegate>
```
<!-- .element: class="fragment" -->
<span class="fragment">**delegate**, denn: 'get()' und 'set()' werden delegiert zur Methode 'getValue()' bzw. 'setValue()'</span>

<!--v-->
## Lazy ohne lazy
```
var value: String? = null
val lazy: String
  get() {
    if (value == null)
      value = initializer()
    return value!!
  }
```

<!--v-->
## Lazy mit lazy
```
val value by lazy(initializer())
```
```
class PropertyNeedsLazyInit(doesLazyInit : () -> String) {
    val value by lazy(doesLazyInit)
}

val pnli = PropertyNeedsLazyInit(
  {print("Blubb macht der "); "Fisch"})
println("Klasse initialisiert")
println(pnli.value)
println(pnli.value)
```
<!-- .element: class="fragment" -->
<p class="fragment">
Klasse initialisiert <br/>
Blubb macht der Fisch <br/>
Fisch
</p>

<!--s-->
# Kotlin lernen
<!-- .slide: data-background="https://media.giphy.com/media/VgY4dDdN1W3NS/giphy.gif"-->
<!-- Friends!!! -->
<!--v-->
# Was fehlt
* neue Sichtbarkeit '`internal`'
* Coroutines ([Java Futures vs. Kotlin Coroutines](https://blog.frankel.ch/concurrency-java-futures-kotlin-coroutines/#gsc.tab=0))
* Interoperabilität mit Java
* Builder
* Typealias
* invoke
* usw.


<!--v-->
# Links
* [Kotlin Dokumentation](https://kotlinlang.org/docs/reference/basic-syntax.html)
* Kotlin-Koans 42 Übungen
  * [online ausprobieren](https://try.kotlinlang.org/#/Kotlin%20Koans/Introduction/Hello,%20world!/Task.kt)
  * [github](https://github.com/Kotlin/kotlin-koans)

<!--s-->
## Fragen?
<!-- .slide: data-background="https://media.giphy.com/media/AU8qGDWpDkCUE/giphy.gif"-->
<!-- Columbo!!11!!1!einseins!!1!!Ölf!! -->
Bitte nur welche, die ich auch beantworten kann!<!-- .element: class="fragment" -->

<!--s-->
<!-- .slide: data-background="https://media.giphy.com/media/xT8qBq71uHPGIR9S2A/giphy.gif"-->
<!--
  What Prime Minister Justin Trudeau Does | According To Kids | CBC Kids
  https://www.youtube.com/watch?v=_pIXFeTufnM
-->
