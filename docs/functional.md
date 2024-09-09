# Funktionale Programmierung

Angenommen, wir haben eine Liste aus Zahlen (`Integer`) und wollen jede einzelne Zahl aus dieser Liste auf die Konsole ausgeben. Unser bisheriger Ansatz sieht ungefähr so aus:

=== "bisher"
	```java
	static void printAllNumbersInList(List<Integer> numbers)
	{
		for(int number : numbers) {
			System.out.println(number);
		}
	}
	```

Nun betrachten wir eine andere Methode und nutzen dazu das Interface [Stream](https://docs.oracle.com/javase/8/docs/api/java/util/stream/Stream.html):

=== "funktional mit Streams"
	```java
	static void printAllNumbersInListFunctional(List<Integer> numbers)
	{
		numbers.stream().forEach(System.out::println);
	}
	```

Mehrere Sachen sind neu:

<ol>
<li> Aufruf der Methode <code>stream()</code> für die <code>Collection</code>. <code>numbers</code> ist vom Typ <code>List</code>. <code>List</code> ist ein Interface, das vom Interface <code>Collection</code> erbt. Die Methode <code>stream()</code> gibt einen <code>Stream</code> zurück. </li>
<li> Ein <code>Stream</code> ist ein sogenannter <a href="https://docs.oracle.com/javase/8/docs/api/java/util/Spliterator.html">Spliterator</a> und vereinigt zwei Konzepte: 
	<ol>
   <li> Ein <code>Spliterator</code> ist einerseits ein <code>Iterator</code> und ermöglicht elementweisen Zugriff (<code>hasNext()</code> und <code>next</code> --> siehe <code>forEach()</code>) </li>
   <li> 2.b und es kann den Stream in verschiedene Teile <i>splitten</i> (siehe z.B. <code>filter()</code>). </li>
</ol></li>
 <li> Die Methode <code>println</code> wird anders aufgerufen. 
 	<ol>
   <li> Es fehlen einerseits die Klammern <code>(</code> und <code>)</code> beim Aufruf.</li>
   <li> Anderseits wird die Methode nicht über die Punktschreibweise, sondern mit der neuen Syntax <code>::</code> aufgerufen. Dabei handelt es sich um eine sogenannte <i>Methodenreferenz</i>. Tatsächlich handelt es sich gar nicht um den <i>Aufruf</i> der Methode, aber dazu kommen wir später genauer. </li>
</ol></li>
</ol>

Sie können sich den obigen Code wie folgt erklären: Die Liste wird in einen Stream umgewandelt. Mithilfe von `forEach()` wird jedes einzelne Element aus der Liste betrachtet und an die `println()`-Methode gesendet. Diese gibt jedes einzelne Element auf die Konsole aus. 

## Lambda-Ausdrücke

Im obigen Beispiel haben wir `println` über die Methodenreferenz "aufgerufen". Diese Methode erwartet keinen Parameter. Wir erweitern unser Beispiel zunächst und wollen nur die geraden Zahlen aus der `numbers`-Liste ausgeben lassen. Dazu schreiben wir uns zunächst folgende Methode:

=== "gerade Zahl"
	```java
	static boolean isEven(int number)
	{
		return number%2 == 0;
	}
	```

Mithilfe dieser Methode **filtern** wir nun zunächst den Stream (wir *splitten* den Stream in gerade und ungerade Zahlen und lassen nur die geraden Zahlen "durch"). Dazu nutzen wir die Methode `filter()` (siehe Klasse [Stream](https://docs.oracle.com/javase/8/docs/api/java/util/stream/Stream.html)):


=== "Stream filtern"
	```java
	static void printAllEvenNumbersInListFunctional(List<Integer> numbers)
	{
		numbers.stream()
			.filter(Functional01::isEven)
			.forEach(System.out::println);
	}
	```

Als Parameter übergeben wir der `filter()`-Methode die Methodenreferenz `isEven` (siehe oben) - diese haben wir in der Klasse `Functional01` implementiert. Diese Methode erwartet einen Parameter und "irgendwie" werden jetzt die einzelnen Zahlen aus dem Stream an die `isEven()`-Methode übergeben. Das darumterliegende Prinzip schauen wir uns nun genauer an und verwenden dafür einen sogannten **Lambda-Ausdruck**. 

>> Ein Lambda-Ausdruck mit einem Parameter hat die Form: `parameter -> expression`
>> Ein Lambda-Ausdruck mit mehreren Parametern hat die Form: `(parameter1, parameter2) -> expression`

In obiger Form gibt die `expression` implizit einen Wert zurück (typischer Weise ein `boolean`, je nach Ausdruck). Für komplexere Ausführungen kann auch ein Anweisungsblock definiert werden. Wenn aus diesem Anweisungsblock ein Wert zurückgegeben werden soll, muss darin explizit ein `return` angegeben werden:

>> Ein Lambda-Ausdruck mit komplexerem Code: `(parameter1, parameter2) -> { code }` 

Wir ersetzen nun die Methodenreferenz auf `isEven` in `filter()` und geben stattdessen direkt einen Lambda-Ausdruck an:


=== "Lambda-Ausdruck in filter()"
	```java
	static void printAllEvenNumbersInListFunctional(List<Integer> numbers)
	{
		numbers.stream()
			.filter( number -> number%2 == 0 ) // Lambda-Ausdruck
			.forEach(System.out::println);
	}
	```

Den Parameter haben wir hier `number` genannt. Wir können ihn im Ausdruck frei wählen und müssen ihn nicht deklarieren. Hätten wir ihn z.B. `n` genannt, sähe der Lambda-Ausdruck so aus: `n -> n%2 == 0` und würde genauso funktionieren. 

## `map()`

Wir kennen bereits 2 Methoden über Stream: `forEch()` und `filter()`. Nun betrachten wir eine weitere Methode: `map()`. Mithilfe von `map()` können wir jedes Element eines Streams manipulieren, z.B. jedes Element quadrieren:


=== "map()"
	```java
	static void printSquaresOfAllEvenNumbersInListFunctional(List<Integer> numbers)
	{
		numbers.stream()
			.filter( number -> number%2 == 0 )
			.map(number -> number * number)
			.forEach(System.out::println);
	}
	```


`map()` gibt, genau wie `filter()`, einen `Stream` zurück. `forEch()` hat als Rückgabetyp jedoch `void`! `map()` erwartet als Parameter eine [Function](https://docs.oracle.com/javase/8/docs/api/java/util/function/Function.html), d.h. entweder ein Lambda-Audruck oder eine Methodenreferenz. `filter()` erwartet als Parameter ein [Predicate](https://docs.oracle.com/javase/8/docs/api/java/util/function/Predicate.html). Ein `Predicate` ist eine `Function`, die ein `boolean` zurückgibt. `forEach()` erwartet als Parameter einen [Consumer](https://docs.oracle.com/javase/8/docs/api/java/util/function/Consumer.html). Das ist eine `Function` deren Rückgabetyp `void` ist. 


