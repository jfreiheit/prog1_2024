# Aufgaben

Hier finden Sie die Aufgaben. Die Abgabefristen der einzelnen Aufgaben stehen [hier](index.md#planung). Beachten Sie die nachfolgenden Hinweise zum Hochladen der Aufgaben. 

## Hinweise zur Abgabe der Aufgaben

Die Aufgaben laden Sie in [Moodle](https://moodle.htw-berlin.de/course/view.php?id=29156) unter dem Reiter "Aufgaben" hoch. Dort ist für jede Aufgabe eine Moodle-Aufgabe erstellt. Beachten Sie, dass ein Hochladen nach Ablauf der Abgabefrist nicht mehr möglich ist. 


### Eclipse

Sie sind in der Wahl Ihrer Entwicklungsumgebung frei. Ich verwende in der Veranstaltung Eclipse. Dafür gelten die folgenden Hinweise: 

- Achten Sie darauf, dass Sie die Quelldateien (also die `.java`-Dateien aus dem `src`-Verzeichnis) hochladen. 
- Ihre Klassen erstellen Sie immer in einem package `aufgaben.aufgabeX`. Das heißt, Aufgabe1 ist im package `aufgaben.aufgabe1`, Aufgabe2 im package `aufgaben.aufgabe2` usw. 
- In Ihrem `workspace`gibt es dann einen Ordner für Ihr Java-Projekt, z.B. `WS24` (je nachdem, wie Sie Ihr Java-Projekt genannt haben) und darin befindet sich ein `bin`- und ein `src`-Ordner. In dem `src`-Ordner befindet sich dann ein Ordner `aufgaben` und darin ein Ordner `aufgaben1` (für Aufgabe1). Darin befindet sich Ihre `.java`-Datei, die Sie hochladen sollen. Angenommen, Sie haben Ihre Klasse `Aufgabe1` genannt, dann heißt die Klasse also `Aufgabe1.java`. Sie folgen also dem Pfad `workspace`--> *Java-Projekt* (z.B. `WS24`) --> `src` --> `aufgaben` --> `aufgabe`*X*.
- Wenn Ihre Lösung aus mehreren Klassen (mehreren `.java`-Dateien) besteht, können Sie entweder die Dateien einzeln hochladen oder Sie zippen Ihre Dateien (am besten dann den `aufgabeX`-Ordner und laden das `.zip`-File hoch. 
- In Ihrer Lösung (Ihrer/n Klasse/n) fügen Sie direkt oberhalb Ihrer Klassendefinition einen JavaDoc-Kommentar ein (`/** ... */`). Dieser enthält ein `@author`-Tag. dahinter schreiben Sie Ihren Namen. Das sieht dann z.B. so aus:
	```java
	package aufgaben.aufgabe1;

	/**
	 * 
	 * @author Jörn Freiheit
	 * 
	 * Diese Klasse gibt auf die Konsole ein Rhombus (eine Raute) aus.
	 * Der Rhombus ist entweder gefuellt oder ungefuellt. 
	 *
	 */
	public class Aufgabe1
	{
		// hier Ihre Implementierung
	}
	```
- Sie können Ihre Aufgaben zu zweit lösen. Tragen Sie dann hinter das `@author`-Tag beide Namen ein und **laden Sie bitte beide** die Lösung in Moodle hoch!


## Aufgaben


??? "<a id="aufgabe-1"></a>Aufgabe1 - Rhombus"
	- Erstellen Sie eine Klasse `Aufgabe1` mit `main()`-Methode im package `aufgaben.aufgabe1` 
	- Implementieren Sie eine Methode `public static void printRhombus(int upperHalf, boolean filled){}`
	- Ist der Parameterwert von `filled` `true`, dann soll ein Rhombus (eine Raute) wie folgt auf die Konsole ausgegeben werden:
		```bash
		      *
		     ***
		    *****
		   *******
		  *********
		 ***********
		  *********
		   *******
		    *****
		     ***
		      *
		```
	- Ist der Parameterwert von `filled` `false`, dann soll der Rhombus ungefüllt sein, also so:
		```bash
		      *
		     * *
		    *   *
		   *     *
		  *       *
		 *         *
		  *       *
		   *     *
		    *   *
		     * *
		      *
		```
	- der Wert für `upperHalf` gibt die Höhe einer Hälfte des Rhombus an. Die Gesamthöhe des Rhombus berechnet sich aus `
		```java
		int height = 2 * upperHalf +1;
		```
	- In unserem oben gezeigten Beispiel ist der Wert von `upperHalf` `5` und die Gesamthöhe des Rhombus `11`. 
	- Die obere Ausgabe ist also durch die Anweisung `printRhombus(5, true);` und die untere durch die Anweisung `printRhombus(5, false);` entstanden.
	- Die Berechnung der Höhe aus dem Parameterwert `upperHalf` hat die Vorteile, 
		- dass die Höhe dadurch immer eine ungerade Zahl ist (was notwendig ist) und 
		- dass Sie den Wert `upperHalf` gut verwenden können (was ebenfalls notwendig ist, wie Sie merken werden)
	- **Tipps:**: 

		- Fangen Sie auf keinen Fall gleich an zu programmieren, sondern überlegen sich mithilfe von Zettel und Stift z.B. die Antworten auf folgende Fragen:

			- Wieviele Zeilen hat der Rhombus insgesamt für einen gegebenen Wert von `upperHalf`?
			- Wenn die obere Hälfte des Rhombus gezeichnet wird und Sie sind in Zeile `i`, wieviele Leerzeichen werden zunächst ausgegeben und wieviele Sterne folgen dann?
			- Wieviele Sterne müssen Sie in der mittleren Zeile ausgeben?
			- Wenn die untere Hälfte des Rhombus gezeichnet wird und Sie sind in Zeile `i`, wieviele Leerzeichen werden zunächst ausgegeben und wieviele Sterne folgen dann?
		- Zerlegen Sie den Rhombus gedanklich in drei Teile: eine obere Hälfte, die mittlere Zeile und eine untere Hälfte.
		- Schreiben Sie sich zwei weitere Methoden `public static void printRhombusFilled(int upperHalf){}` und `public static void printRhombusUnfilled(int upperHalf){}`, die Sie entsprechend des Wertes von `filled` aufrufen. In der einen Methode erstellen Sie die ausgefüllte Raute und in der anderen die ungefüllte. Dann wird Ihr Programm nicht zu unübersichtlich. Fangen Sie am besten mit der ausgefüllten an, die ist etwas leichter. 
	- Das Programm soll für beliebige (nicht so große - max. Wert `50`) positive Zahlen (also `> 0`) von `upperHalf` funktionieren. Insbesondere sind die Tests für `upperhalf == 1` interessant. 
	- Viel Spaß und viel Erfolg!



??? "<a id="aufgabe-2"></a>Aufgabe2 - Numbers"
	- Erstellen Sie eine Klasse `Aufgabe2` mit `main()`-Methode im package `aufgaben.aufgabe2`.
	- Bei der Lösung der Aufgabe soll nicht der Datentyp `String` verwendet werden! 
	- Implementieren Sie eine Methode `public static int lengthOfNumber(int number){}`. Diese Methode gibt die Länge von `number` zurück, d.h. die Anzahl der Ziffern in der Zahl. **Beachten Sie**: für `number == 0` soll jedoch `0` zurückgegeben werden. <br/>
		**Beispiele:** <br/>
			```
			number  --> Rückgabewert
			0 		--> 0
			1 		--> 1
			9 		--> 1
			10 	    --> 2
			1234    --> 4
			-1234   --> 4
			```

	- Implementieren Sie eine Methode `public static int firstDigit(int number){}`. Diese Methode gibt die erste Ziffer von `number` zurück.  <br/>
		**Beispiele:** <br/>
			```
			number  --> Rückgabewert
			0 		--> 0
			1 		--> 1
			9 		--> 9
			10 	    --> 1
			1234    --> 1
			-1234   --> 1
			5678    --> 5
			```

	- Implementieren Sie eine Methode `public static int powerOf10ToN(int n){}`. Diese Methode gibt den Wert für `10 ^ n` zurück. Sie können davon ausgehen, dass `n >= 0` gilt.  <br/>
		**Beispiele:** <br/>
			```
			n       --> Rückgabewert
			0 		--> 1
			1 		--> 10
			2 		--> 100
			3 	    --> 1000
			4       --> 10000
			```

	- Implementieren Sie eine Methode `public static int cutFirstDigit(int number){}`. Diese Methode entfernt von `number` die erste Ziffer.  Für `-10 < number < 10` wird `0` zurückgegeben. <br/>
		**Beispiele:** <br/>
			```
			number  --> Rückgabewert
			0 		--> 0
			1 		--> 0
			9 		--> 0
			-9 	    --> 0
			11      --> 1
			91      --> 1
			1234    --> 234
			-1234   --> -234
			9999    --> 999
			-9999   --> -999
			1023    --> 23  // Achtung! führende Nullen in der verbleibenden Zahl entfallen
			```

	- Implementieren Sie eine Methode `public static boolean secondDigitIsZero(int number){}`. Diese Methode gibt ein `true` zurück, wenn die zweite Ziffer in `number` eine `0` ist. Sonst `false`. <br/>
		**Beispiele:** <br/>
			```
			number  --> Rückgabewert
			0 		--> false
			1 		--> false
			9 		--> false
			11 	    --> false
			101     --> true
			111     --> false
			1001    --> true
			-10234  --> true
			1111    --> false
			10000   --> true
			```

	- Testen Sie alle Methoden ausführlich in der `main()`-Methode.
	
	- Viel Spaß und viel Erfolg!




??? "<a id="aufgabe-3"></a>Aufgabe 3 - Triangle"
	- Wir erstellen uns einen neuen Datentyp `Triangle`

	- Erstellen Sie im package `aufgaben.aufgabe3` eine Klasse `Triangle` ohne `main()`-Methode und eine Klasse `Testklasse` mit `main()`-Methode. 

	- In der Klasse `Triangle` erstellen Sie drei Objektvariablen `a`, `b` und `c` jeweils vom Typ `int` und alle `private`. Das sollen die Seiten unseres Dreiecks sein. 

	- Erstellen Sie einen Konstruktor, dem drei Parameterwerte übergeben werden `pa`, `pb` und `pc` alle vom Typ `int`. Mit diesen Werten werden die Objektvariablen initialisiert. 

	- Schreiben Sie eine Objektmethode `print()`, die die Seitenlängen des Dreiecks in der folgenden Form ausgibt:
		```bash
		Seiten          : a=3, b=4, c=5
		```
		für den Fall, dass die Seitenlängen `3`, `4` und `5` sind. 

	- Wenn Sie jetzt in der `main()`-Methode der `Testklasse` folgende Anweisungen ausführen
		```java 
		Triangle t1 = new Triangle(3, 4, 5);
		Triangle t2 = new Triangle(4, 4, 7);
		Triangle t3 = new Triangle(5, 5, 5);
		Triangle t4 = new Triangle(4, 5, 3);
		Triangle t5 = new Triangle(4, 3, 5);
		Triangle t6 = new Triangle(3, 4, 5);
		
		t1.print();
		t2.print();
		t3.print();
		t4.print();
		t5.print();
		t6.print();
		```
		dann sollte die Ausgabe ungefähr so aussehen:
		```bash
		Seiten          : a=3, b=4, c=5
		Seiten          : a=4, b=4, c=7
		Seiten          : a=5, b=5, c=5
		Seiten          : a=4, b=5, c=3
		Seiten          : a=4, b=3, c=5
		Seiten          : a=3, b=4, c=5
		```

	- Erstellen Sie in der Klasse `Triangle` eine Objektmethode `public int circumference()`, die den Umfang des Dreiecks zurückgibt (also die Summe der drei Seitenlängen).

	- Erstellen Sie in der Klasse `Triangle` eine Objektmethode `public double area()`, die den Flaecheninhalt des Dreiecks zurückgibt.  Der Flächeninhalt `A` eines Dreiecks lässt sich nach der [Heron'schen Formel](https://de.wikipedia.org/wiki/Satz_des_Heron) wie folgt berechnen:
		- `A = Math.sqrt(s * (s-a) * (s-b) * (s-c)) (siehe Klasse [Math](hilfsklassen.md#die-klasse-math))
		- wobei `s = (a + b + c) / 2`
		- Achten Sie darauf, dass Sie stets mit `double` rechnen!
		- Beachten Sie, dass in einem Dreieck keine Seite länger sein darf als die Summe der beiden anderen. Für die oben in der `main()`-Methode erstellten Objekte gilt das aber. Wir müssen deshalb nichts weiter beachten. 

	- Erweitern Sie die Objektmethode `print()` nun so, dass auch der Umfang und der Flaecheninhalt in der folgenden Form ausgegeben werden (Sie können in die `print()`-methode auch die Leerzeile integrieren):
		```bash
		Seiten          : a=3, b=4, c=5
		Umfang          : 12
		Flaecheninhalt  : 6.0

		Seiten          : a=4, b=4, c=7
		Umfang          : 15
		Flaecheninhalt  : 6.777720855862979

		Seiten          : a=5, b=5, c=5
		Umfang          : 15
		Flaecheninhalt  : 10.825317547305483

		Seiten          : a=4, b=5, c=3
		Umfang          : 12
		Flaecheninhalt  : 6.0

		Seiten          : a=4, b=3, c=5
		Umfang          : 12
		Flaecheninhalt  : 6.0

		Seiten          : a=3, b=4, c=5
		Umfang          : 12
		Flaecheninhalt  : 6.0
		```

	- Erstellen Sie in der Klasse `Triangle` eine Objektmethode `public boolean equilateral()`, die ein `true` zurückgibt, wenn das Dreieck gleichseitig ist (also alle Seiten des Dreiecks gleich lang sind) und `false` sonst.

	- Erstellen Sie in der Klasse `Triangle` eine Objektmethode `public boolean isosceles()`, die ein `true` zurückgibt, wenn das Dreieck gleichschenklig ist (also zwei Seiten des Dreiecks gleich lang sind) und `false` sonst.

	- Erweitern Sie die Objektmethode `print()` nun so, dass die Prüfungen, ob sich um ein gleichseitiges oder gleichschenkliges (oder unregelmäßiges) Dreieck handelt, in der folgenden Form ausgegeben werden:
		```bash
		Seiten          : a=3, b=4, c=5
		Umfang          : 12
		Flaecheninhalt  : 6.0
		Das Dreieck ist unregelmaessig.

		Seiten          : a=4, b=4, c=7
		Umfang          : 15
		Flaecheninhalt  : 6.777720855862979
		Das Dreieck ist gleichschenklig.

		Seiten          : a=5, b=5, c=5
		Umfang          : 15
		Flaecheninhalt  : 10.825317547305483
		Das Dreieck ist gleichseitig.

		Seiten          : a=4, b=5, c=3
		Umfang          : 12
		Flaecheninhalt  : 6.0
		Das Dreieck ist unregelmaessig.

		Seiten          : a=4, b=3, c=5
		Umfang          : 12
		Flaecheninhalt  : 6.0
		Das Dreieck ist unregelmaessig.

		Seiten          : a=3, b=4, c=5
		Umfang          : 12
		Flaecheninhalt  : 6.0
		Das Dreieck ist unregelmaessig.
		```

	- Erstellen Sie in der Klasse `Triangle` eine Objektmethode `public boolean sameCircumference(Triangle t)`, die ein `true` zurückgibt, wenn das aufrufende Objekt den gleichen Umfang hat wie `t` und `false` sonst.

	- Erstellen Sie in der Klasse `Triangle` eine Objektmethode `public boolean isSmaller(Triangle t)`, die ein `true` zurückgibt, wenn das aufrufende Objekt einen kleineren Flächeninhalt hat, als `t` und `false` sonst.

	- Erstellen Sie in der Klasse `Triangle` eine Objektmethode `public boolean isBigger(Triangle t)`, die ein `true` zurückgibt, wenn das aufrufende Objekt einen größeren Flächeninhalt hat, als `t` und `false` sonst.

	- Testen Sie in der `main()`-Methode der `Testklasse` die drei zuletztgeschriebenen Methoden, so dass folgende Ausgaben erzeugt werden:
		```bash
		t1 und t2 gleicher Umfang ? : false
		t1 und t3 gleicher Umfang ? : false
		t2 und t3 gleicher Umfang ? : true

		t1 kleiner als t2 ? : true
		t2 kleiner als t1 ? : false
		t1 kleiner als t4 ? : false
		t4 kleiner als t1 ? : false

		t1 groesser als t2 ? : false
		t2 groesser als t1 ? : true
		t1 groesser als t4 ? : false
		t4 groesser als t1 ? : false
		```
	- ---

	- **Wenn Sie das geschafft haben, dann haben Sie die Aufgabe erfüllt! Herzlichen Glückwunsch! Die folgende(n) Aufgabe(n) sind optional :**

	- ---

	- Erstellen Sie in der Klasse `Triangle` eine Objektmethode `public boolean sidesAreEqual(Triangle t)`, die ein `true` zurückgibt, wenn das aufrufende Objekt die gleichen Seitenlängen hat wie `t` und `false` sonst.
		- Beachten Sie, dass folgende Dreiecke mit z.B. dem Dreieck (`a=3, b=4, c=5`) gleich sein sollen: (`a=3, b=4, c=5`), aber auch (`a=4, b=5, c=3`), aber auch (`a=5, b=3, c=4`) --> die "Benennung" der Seiten ist also egal
		- Jedoch soll z.B. (`a=4, b=3, c=5`) nicht gleich zu (`a=3, b=4, c=5`) sein
		- für die obigen Objekte soll somit gelten:
			```bash
			t1 und t2 gleiche Seiten ? : false
			t1 und t4 gleiche Seiten ? : true
			t1 und t5 gleiche Seiten ? : false
			t1 und t6 gleiche Seiten ? : true
			```
			Erzeugen Sie diese Ausgabe in `main()`.

	- Erstellen Sie in der Klasse `Triangle` eine Objektmethode `public boolean isRightAngled()`, die ein `true` zurückgibt, wenn das Dreieck rechtwinklig ist und `false` sonst.
		- der [Satz des Pythagoras](https://de.wikipedia.org/wiki/Satz_des_Pythagoras) besagt, dass in einem rechtwinkligen Dreieck gilt: `a^2 + b^2 = c^2`
		- es gilt aber auch die Umkehrung, d.h. wenn von 2 Seiten die Summe der Quadrate dem Quadrat der dritten Seite entspricht, dann ist das Dreieck rechtwinklig 
	- Erweitern Sie die Objektmethode `print()` nun so, dass die Prüfungen, ob sich um ein rechtwinkliges Dreieck handelt, in der folgenden Form ausgegeben werden:
		```bash
		Seiten          : a=3, b=4, c=5
		Umfang          : 12
		Flaecheninhalt  : 6.0
		Das Dreieck ist unregelmaessig.
		Das Dreieck ist rechtwinklig.

		Seiten          : a=4, b=4, c=7
		Umfang          : 15
		Flaecheninhalt  : 6.777720855862979
		Das Dreieck ist gleichschenklig.
		Das Dreieck ist nicht rechtwinklig.

		Seiten          : a=5, b=5, c=5
		Umfang          : 15
		Flaecheninhalt  : 10.825317547305483
		Das Dreieck ist gleichseitig.
		Das Dreieck ist nicht rechtwinklig.

		Seiten          : a=4, b=5, c=3
		Umfang          : 12
		Flaecheninhalt  : 6.0
		Das Dreieck ist unregelmaessig.
		Das Dreieck ist rechtwinklig.

		Seiten          : a=4, b=3, c=5
		Umfang          : 12
		Flaecheninhalt  : 6.0
		Das Dreieck ist unregelmaessig.
		Das Dreieck ist rechtwinklig.

		Seiten          : a=3, b=4, c=5
		Umfang          : 12
		Flaecheninhalt  : 6.0
		Das Dreieck ist unregelmaessig.
		Das Dreieck ist rechtwinklig.
		```
	
	- Viel Spaß und viel Erfolg!




??? "<a id="aufgabe-4"></a>Aufgabe 4 - Bruch"
	- Wir erstellen uns einen neuen Datentyp `Bruch`

	- Erstellen Sie im package `aufgaben.aufgabe4` eine Klasse `Bruch` ohne `main()`-Methode und eine Klasse `BruchTest` mit `main()`-Methode. 

	- In der Klasse `Bruch` erstellen Sie zwei Objektvariablen `zaehler` und `nenner` jeweils vom Typ `int` und `private`. 

	- Implementieren Sie für die Klasse `Bruch` zwei verschiedene Konstruktoren
		- parameterlos --> `zaehler` und `nenner` erhalten jeweils den Wert `1`
		- mit zwei Parametern (`int zaehler, int nenner`) --> entspr. Werte der Objektvariablen 

	- Implementieren Sie folgende Objektmethoden
		- `public Bruch plus(Bruch b)` --> gibt den gekürzten Bruch aus der Addition eines Bruchs mit `b` zurück
		- `public Bruch minus(Bruch b)` --> gibt den gekürzten Bruch aus der Subtraktion eines Bruchs mit `b` zurück
		- `public Bruch mal(Bruch b)` --> gibt den gekürzten Bruch aus der Multiplikation eines Bruchs mit `b` zurück
		- `public Bruch geteilt(Bruch b)` --> gibt den gekürzten Bruch aus der Division eines Bruchs mit `b` zurück
		- `public Bruch kuerzen()` --> gibt den gekürzten Bruch zurück (Sie brauchen dazu den `ggT`)
		_ `public String toString()` --> gibt einen Bruch als `String` in der Form `zaehler / nenner` zurück
		- `public int ggT(int zahl1, int zahl2)` --> gibt den größten gemeinsamen Teiler (ggT) der beiden Zahlen `zahl1` und `zahl2` als `int` zurück - siehe [Euklidischer Algorithmus](algorithmen.md#beispiel-euklidischer-algorithmus)

	- Geben Sie in die `main()`-Methode der `BruchTest`-Klasse mindestens folgende Anweisungen ein:
		```java 
		Bruch b1 = new Bruch(3,7);
		Bruch b2 = new Bruch(4,8);
		Bruch b3 = new Bruch(2,5);
		Bruch b4 = new Bruch(5,11);
		Bruch b5 = new Bruch();
		
		System.out.printf("%n%n------------------------- Rechnen -----------------------------------%n%n");
		System.out.printf("%5s + %5s = %5s %n", b1.toString(), b2.toString(), b1.plus(b2).toString());
		System.out.printf("%5s - %5s = %5s %n", b3.toString(), b4.toString(), b3.minus(b4).toString());
		System.out.printf("%5s * %5s = %5s %n", b1.toString(), b3.toString(), b1.mal(b3).toString());
		System.out.printf("%5s / %5s = %5s %n", b2.toString(), b1.toString(), b2.geteilt(b1).toString());
		System.out.printf("%5s + %5s = %5s %n", b5.toString(), b4.toString(), b5.plus(b4).toString());	
		System.out.printf("%5s - %5s = %5s %n", b1.toString(), b1.toString(), b1.minus(b1).toString());		// nenner sollte ungleich 0 bleiben!	
		``` 
		und führen Sie die `BruchTest`-Klasse aus. Es sollten folgende Augaben entstehen:
		```bash
		------------------------- Rechnen -----------------------------------

		  3/7 +   4/8 = 13/14 
		  2/5 -  5/11 = -3/55 
		  3/7 *   2/5 =  6/35 
		  4/8 /   3/7 =   7/6 
		  1/1 +  5/11 = 16/11
		  3/7 -   3/7 =   0/1 
		```
	- ---

	- **Wenn Sie das geschafft haben, dann haben Sie die Aufgabe erfüllt! Herzlichen Glückwunsch! Die folgende(n) Aufgabe(n) sind optional :**

	- ---

	- Implementieren Sie folgende Objektmethoden
		- `public boolean istGroesser(Bruch b)` --> gibt `true` zurück, wenn der aufrufende Bruch größer als `b` ist, `false` sonst
		- `public boolean istKleiner(Bruch b)` --> gibt `true` zurück, wenn der aufrufende Bruch kleiner als `b` ist, `false` sonst
		- `public boolean istGleich(Bruch b)` --> gibt `true` zurück, wenn der aufrufende Bruch gleich `b` ist, `false` sonst

	- Geben Sie in die `main()`-Methode der `BruchTest`-Klasse mindestens folgende weitere Anweisungen ein:
		```java 
		System.out.printf("%n%n------------------------- Vergleichen -----------------------------------%n%n");
		System.out.printf("%5s  > %5s ? %b %n", b1.toString(), b2.toString(), b1.istGroesser(b2));
		System.out.printf("%5s  < %5s ? %b %n", b1.toString(), b2.toString(), b1.istKleiner(b2));
		System.out.printf("%5s == %5s ? %b %n", b1.toString(), b2.toString(), b1.istGleich(b2));
		System.out.printf("%5s  > %5s ? %b %n", b3.toString(), b4.toString(), b3.istGroesser(b4));
		System.out.printf("%5s  < %5s ? %b %n", b3.toString(), b4.toString(), b3.istKleiner(b4));
		System.out.printf("%5s == %5s ? %b %n", b3.toString(), b4.toString(), b3.istGleich(b4));
		System.out.printf("%5s  > %5s ? %b %n", b5.toString(), b5.toString(), b5.istGroesser(b5));
		System.out.printf("%5s  < %5s ? %b %n", b5.toString(), b5.toString(), b5.istKleiner(b5));
		System.out.printf("%5s == %5s ? %b %n", b5.toString(), b5.toString(), b5.istGleich(b5));
		``` 
		und führen Sie die `BruchTest`-Klasse aus. Es sollten folgende weitere Augaben entstehen:
		```bash
		------------------------- Vergleichen -----------------------------------

		  3/7  >   4/8 ? false 
		  3/7  <   4/8 ? true 
		  3/7 ==   4/8 ? false 
		  2/5  >  5/11 ? false 
		  2/5  <  5/11 ? true 
		  2/5 ==  5/11 ? false 
		  1/1  >   1/1 ? false 
		  1/1  <   1/1 ? false 
		  1/1 ==   1/1 ? true 
		```
	
	- Viel Spaß und viel Erfolg!





??? "<a id="aufgabe-5"></a>Aufgabe 5 - Doppelt-verkettete Liste"
	- Wir erstellen uns einen neuen Datentyp `ListElement`. Dieser Datentyp wird für ein Element aus einer doppelt verketteten Liste verwendet. Eine Liste kann aus vielen `ListElement`-Elementen bestehen. Ein `ListElement` hat einen Vorgänger (`predecessor`) und einen Nachfolger (`successor`) in der Liste. Nur das erste Element hat keinen Vorgänger und das letzte Element hat keinen Nachfolger.

	- Erstellen Sie im package `aufgaben.aufgabe5` eine Klasse `ListElement` ohne `main()`-Methode und eine Klasse `Programmklasse` mit `main()`-Methode. 

	- In der Klasse `ListElement` erstellen Sie fünf nur in der Klasse sichtbare Objektvariablen:
	 	- `value` vom Typ `char` 
	 	- `hasPredecessor` vom Typ `boolean` 
	 	- `hasSuccessor` vom Typ `boolean`
	 	- `predecessor` vom Typ `ListElement` und
	 	- `successor` vom Typ `ListElement`

	- Implementieren Sie für die Klasse `ListElement` einen Konstruktor, dem ein Zeichen (`char`) als Parameter übergeben wird. Dieses Zeichen wird verwendet, um der Objektvariablen `value` einen Wert zuzuweisen. Setzen Sie außerdem die Objektvariablen `hasPredecessor` und `hasSuccessor` jeweils auf `false`. 

	- Implementieren Sie die Objektmethode `public void insertBefore(ListElement element)`. Durch Aufruf dieser Methode soll das aufrufende `ListElement`-Objekt **vor** das `ListElement`-Objekt `element` in die Liste eingefügt werden. Dabei sind mehrere Dinge zu beachten:
		- Angenommen, wir haben zwei einzelne `ListElement`-Objekte `l1` und `l2`. Dann entsteht durch `li.insertBefore(l2)` die Liste `l1 <--> l2`. Das heißt, `l2` wird der `successor` von `l1` und `l1` wird der `predecessor` von `l2`. Setzen Sie entsprechend auch die Variablenwerte für `hasSuccessor` und `hasPredecessor`.

		- Angenommen, wir haben ein einzelnes `ListElement`-Objekt `l1` und eine Liste aus lauter `ListElement`-Objekten `l2 <--> l3 <--> l4 <--> l5`. Dann 
			- ensteht durch `l1.insertBefore(l2)` die Liste `l1 <--> l2 <--> l3 <--> l4 <--> l5` und alles ist, wie im Fall zuvor, d.h. `l1` ist der `predecessor` von `l2` und `l2` ist der `successor` von `l1`.
			- entsteht durch `l1.insertBefore(l3)` die Liste `l2 <--> l1 <--> l3 <--> l4 <--> l5`. Das bedeutet, dass `l3` der `successor` von `l1` wird und `l1` der `predecessor` von `l3`. Der **alte** `predecessor` von `l3` (`l2`) wird der **neue** `predecessor` von `l1` und `l1` wird der **neue** `successor` von `l2`.

		- Angenommen, wir haben eine Liste aus lauter `ListElement`-Objekten `l1 <--> l2 <--> l3` und ein einzelnes `ListElement`-Objekt `l4`. Dann 
			- ensteht sowohl durch `l1.insertBefore(l4)` als auch durch `l2.insertBefore(l4)` als auch durch `l3.insertBefore(l4)` die Liste `l1 <--> l2 <--> l3 <--> l4`.

		- Angenommen, wir haben eine Liste aus lauter `ListElement`-Objekten `l1 <--> l2 <--> l3` und eine Liste aus lauter `ListElement`-Objekten `l4 <--> l5 <--> l6 <--> l7`. Dann 
			- ensteht durch `l1.insertBefore(l4)` die Liste `l1 <--> l2 <--> l3 <--> l4 <--> l5 <--> l6 <--> l7`. Das heißt, es wird die **gesamte** Liste, die mit `l1` beginnt, **vor** `l4` eingefügt (und damit vor die Liste `l4 <--> l5 <--> l6 <--> l7`). 
			- entsteht durch `l1.insertBefore(l6)` die Liste `l4 <--> l5 <--> l1 <--> l2 <--> l3 <--> l6 <--> l7`. 
			- **übrigens**: wenn Sie für die gebebenen Lsten z.B. `l2.insertBefore(l5)` aufrufen, dann fällt `l1` weg, d.h. die entstehende Liste ist `l4 <--> l2 <--> l5 <--> l6 <--> l7`. Sie können sich überlegen, ob das überhaupt ein richtiges Verhalten ist oder ob es ein besseres gibt. 

	- **Tipp:** Beginnen Sie mit der Implementierung des ersten (und einfachsten) Falls. Fügen Sie dann die weiteren Fälle schrittweise hinzu. Sie werden feststellen, dass Sie gar nicht viele Fallunterscheidungen machen müssen. Ich bin z.B. mit einem `if` und einer `while`-Schleife ausgekommen und die gesamte Methode hat nur ca. 10 Zeilen.

	- Implementieren Sie die Objektmethode `public void print()`. Diese Methode soll den `value` des aufrufenden `ListElement`-Objektes auf die Konsole ausgeben (ohne Zeilenumbruch) und dann die `print()`-Methode des `successor`-Elementes aufrufen. Nur wenn das aufrufende `ListElement` keinen `successor` hat (Ende der Liste), wird der Wert des Objektes mit Zeilenumbruch ausgegeben und keine weitere `print()`-Methode aufgerufen. 

	- Geben Sie in die `main()`-Methode der `Programmklasse` mindestens folgende Anweisungen ein:
		```java 
		ListElement l1 = new ListElement('W');
		ListElement l2 = new ListElement('e');
		ListElement l3 = new ListElement('i');
		ListElement l4 = new ListElement('h');
		ListElement l5 = new ListElement('n');
		ListElement l6 = new ListElement('a');
		ListElement l7 = new ListElement('c');
		ListElement l8 = new ListElement('h');
		ListElement l9 = new ListElement('t');
		ListElement l10 = new ListElement('e');
		ListElement l11 = new ListElement('n');
		
		System.out.printf("? : %15s", "W == ");l1.print();
		l1.insertBefore(l2);		// W-e
		System.out.printf("? : %15s", "We == ");l1.print();
		
		l5.insertBefore(l6);		// n-a
		l5.insertBefore(l7);		// na-c
		l7.insertBefore(l8);		// nac-h
		l6.insertBefore(l9);		// nach-t
		System.out.printf("? : %15s", "nacht == ");l5.print();
		
		l1.insertBefore(l5);		// We-nacht
		System.out.printf("? : %15s", "Wenacht == ");l1.print();			
		
		l10.insertBefore(l11);		// e-n
		l9.insertBefore(l10);		// Wenacht-en
		System.out.printf("? : %15s", "Wenachten == ");l1.print();
		System.out.printf("? : %15s", "nachten == ");l5.print();
		
		l3.insertBefore(l5);		// We-i-nachten
		System.out.printf("? : %15s", "inachten == ");l3.print();
		System.out.printf("? : %15s", "Weinachten == ");l1.print();
		l4.insertBefore(l5);		// Wei-h-nachten
		System.out.printf("? : %15s", "Weihnachten == ");l1.print();
		``` 
		und führen Sie die `Programmklasse` aus. Es sollten folgende Augaben entstehen:
		```bash
		? :           W == W
		? :          We == We
		? :       nacht == nacht
		? :     Wenacht == Wenacht
		? :   Wenachten == Wenachten
		? :     nachten == nachten
		? :    inachten == inachten
		? :  Weinachten == Weinachten
		? : Weihnachten == Weihnachten
		```
	- ---

	- **Wenn Sie das geschafft haben, dann haben Sie die Aufgabe erfüllt! Herzlichen Glückwunsch! Die folgende Aufgabe ist optional :**

		- Fügen Sie der Klasse `ListElement` die Objektvariable `private int index` hinzu und sorgen Sie dafür, dass in einer verketteten Liste die `ListElement`-Objekte den jeweils passenden Index entsprechend ihrer Position in der Liste haben (beginnend bei `0`). Also in der Liste `l1 <--> l2 <--> l3 <--> l4 <--> l5` hat `l1` den Index `0`, `l2` den Index `1`, `l3` den Index `2` usw. Wenn Sie dafür selbständig eine Lösung entwickelt haben, dann schicken Sie mir bitte eine E-Mail mit der Lösung.

	- ---

	- Viel Spaß und viel Erfolg!





??? "<a id="aufgabe-6"></a>Aufgabe 6 - Arrays ausgeben"
	- Wir geben Arrays in verschiedenen Arten auf der Konsole aus. 

	- Implementieren Sie eine Methode `public static int[] createAndFillArray(int length, int fromInclusive, int toInclusive)`. Diese Methode soll genau so sein, wie die `createAndFillArray(int length, int bound)`-Methode in [Methoden mit Array als Rückgabe](arrays.md#methoden-mit-array-als-ruckgabe) mit dem einzigen Unterschied, dass wir nicht den `bound` angeben (der sorgt ja dafür, dass wir Zufallswerte aus dem Bereich `[0, 1, ... , bound-1]` erzeugen), sondern `fromInclusive` und `toExclusive`, so dass wir Zufallswerte aus dem Wertebereich `[fromInclusive, ... , toInclusive]` erzeugen. Siehe dazu auch [`nextInt(bound)`](hilfsklassen.md#nextintint-bound).

	- Implementieren Sie eine Methode `public static void printArray(int[] a)` so, dass sie ein `int`-Array in der Form `[ 27, 30, 25, 26, 23, 20, 30, 30, 22, 21, 29, 29, 21, 20 ]` (also Werte durch Komma getrennt in eckigen Klammern) ausgibt. Siehe dazu [Ausgabe von Arrays](arrays.md#ausgabe-der-werte-auf-die-konsole).  

	- Rufen Sie in der `main()` die beiden Methoden wie folgt auf:
		```java
		int length = r.nextInt(10)+10;
		int[] arr1 = createAndFillArray(length, 20, 30);
		
		System.out.printf("%n%n%n----------- printArray -----------------%n%n%n");
		printArray(arr1);
		```

	- Implementieren Sie eine Methode `public static void printTable(int[] a)`. Diese gibt das Array `a` als Tabelle in folgender Form aus:
		```bash
		| Index :    |   0  |   1  |   2  |   3  |   4  |   5  |   6  |   7  |   8  |   9  |  10  |  11  |  12  |  13  |
		|------------|------|------|------|------|------|------|------|------|------|------|------|------|------|------|
		| Wert :     |  27  |  30  |  25  |  26  |  23  |  20  |  30  |  30  |  22  |  21  |  29  |  29  |  21  |  20  |
		```
	
	- Rufen Sie in der `main()` die Methode `printTable()` wie folgt auf:
		```java
		System.out.printf("%n%n%n----------- printTable -----------------%n%n%n");
		printTable(arr1);
		```		

	- Implementieren Sie eine Methode `public static void printHorizontal(int[] a)`. Diese gibt das Array `a` in folgender Form aus:
		```bash
		    | 
		  0 | ***************************
		    | 
		  1 | ******************************
		    | 
		  2 | *************************
		    | 
		  3 | **************************
		    | 
		  4 | ***********************
		    | 
		  5 | ********************
		    | 
		  6 | ******************************
		    | 
		  7 | ******************************
		    | 
		  8 | **********************
		    | 
		  9 | *********************
		    | 
		 10 | *****************************
		    | 
		 11 | *****************************
		    | 
		 12 | *********************
		    | 
		 13 | ********************
		    | 
		```
		Das heißt, für jeden Wert im Array wird die entsprechende Anzahl von Sternen ausgegeben. Ganz links steht jeweils der Index, unter dem der Wert im Array gespeichert wird. 
		
	- Rufen Sie in der `main()` die Methode `printTable()` wie folgt auf:
		```java
		System.out.printf("%n%n%n----------- printHorizontal ------------%n%n%n");
		printHorizontal(arr1);
		```	

	- ---

	- **Wenn Sie das geschafft haben, dann haben Sie die Aufgabe erfüllt! Herzlichen Glückwunsch! Die folgende(n) Aufgabe(n) sind optional :**

	- ---

	- Implementieren Sie eine Methode `public static void printUpsideDown(int[] a)` oder eine Methode `public static void printVertical(int[] a)` (beide gleicher Aufwand). Diese geben das Array `a` in folgender Form aus:
	```bash

	----------- printUpsideDown ------------


	    |   0    1    2    3    4    5    6    7    8    9   10   11   12   13  
	----+----------------------------------------------------------------------
	  1 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	  2 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	  3 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	  4 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	  5 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	  6 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	  7 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	  8 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	  9 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 10 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 11 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 12 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 13 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 14 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 15 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 16 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 17 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 18 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 19 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 20 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 21 |   *    *    *    *    *         *    *    *    *    *    *    *       
	 22 |   *    *    *    *    *         *    *    *         *    *            
	 23 |   *    *    *    *    *         *    *              *    *            
	 24 |   *    *    *    *              *    *              *    *            
	 25 |   *    *    *    *              *    *              *    *            
	 26 |   *    *         *              *    *              *    *            
	 27 |   *    *                        *    *              *    *            
	 28 |        *                        *    *              *    *            
	 29 |        *                        *    *              *    *            
	 30 |        *                        *    *                                




	----------- printVertical --------------


	 30 |        *                        *    *                                
	 29 |        *                        *    *              *    *            
	 28 |        *                        *    *              *    *            
	 27 |   *    *                        *    *              *    *            
	 26 |   *    *         *              *    *              *    *            
	 25 |   *    *    *    *              *    *              *    *            
	 24 |   *    *    *    *              *    *              *    *            
	 23 |   *    *    *    *    *         *    *              *    *            
	 22 |   *    *    *    *    *         *    *    *         *    *            
	 21 |   *    *    *    *    *         *    *    *    *    *    *    *       
	 20 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 19 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 18 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 17 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 16 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 15 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 14 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 13 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 12 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 11 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	 10 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	  9 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	  8 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	  7 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	  6 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	  5 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	  4 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	  3 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	  2 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	  1 |   *    *    *    *    *    *    *    *    *    *    *    *    *    *  
	----+----------------------------------------------------------------------
	    |   0    1    2    3    4    5    6    7    8    9   10   11   12   13  

	```

	- Rufen Sie in der `main()` die beiden Methoden (oder die, die Sie implememntiert haben) wie folgt auf:
		```java
		System.out.printf("%n%n%n----------- printUpsideDown ------------%n%n%n");
		printUpsideDown(arr1);
		System.out.printf("%n%n%n----------- printVertical --------------%n%n%n");
		printVertical(arr1);
		```	

	- **Tipps zum Lösen der Zusatzaufgabe:** 
		- Sie müssen zunächst ermitteln, welcher der größte Wert innerhalb des Arrays ist, denn dieser gibt Ihnen die Anzahl der Zeilen im Diagramm vor.
		- Stellen Sie sich das Problem als eine Matrix aus Zeilen und Spalten vor. Die Spalten lassen sich auf den Index des Arrays mappen und die Zeilen auf die Werte im Array. 

	- Viel Spaß und viel Erfolg!




??? "<a id="aufgabe-7"></a>Aufgabe 7 - Arrays befüllen"
	- Wir befüllen ein `char`-Array, aber das ist leider gar nicht so einfach ;-)

	- **einleitende Vorbetrachtung:** angenommen, wir haben die folgende Schleife: 

		```java linenums="3"
		for(int asciiValue = 97; asciiValue<123; asciiValue++)
		{
			char c = (char) asciiValue;
			System.out.print(c + " ");
		}
		```

	-  Durch diese wird uns das gesamte Alphabet in Kleinbuchstaben ausgegeben:

	  	```bash
	  	a b c d e f g h i j k l m n o p q r s t u v w x y z 
	  	```

	-  Kopieren Sie die Schleife einfach in Ihre `main()`-Methode und führen Sie sie aus, dann erhalten Sie obige Ausgabe. Dahinter steckt, dass wir der `int`-Variablen `asciiValue` den ASCII-Code der Kleinbuchstaben zuweisen (beginnend bei `97` - das ist ein `a`). Siehe z.B. [hier](variablen.md#char). Der letzte kleine Buchstabe `z` hat den ASCII-Wert `122`, deshalb läuft die Schleife auch bis `<123`. In Zeile `3` der Schleife findet eine [Typkonvertierung](variablen.md#typkonvertierung-type-cast) statt. Aus dem `int` wird ein `char`. Dies geschieht durch den Typkonvertierungsoperator `(char)`. In Zeile `4` wird das Zeichen `c` vom Typ `char` ausgegeben. 

	- **Aufgabe** Die Aufgabe ist es nun, ein `char`-Array zu befüllen. Es gelten folgende Bedingungen:
	 	- das Array hat (nur) die Länge `25`
	 	- in dem Array darf es keine Doppelungen geben (also kein Zeichen darf doppelt enthalten sein)
	 	- die Zeichen werden zufällig erzeugt, d.h. mithilfe der Klasse `Random` und der Methode `nextInt(bound)`, die Werte zwischen `97` und einschließlich `122` erzeugen soll

	- Schreiben Sie dafür eine Methode `public static char[] createAndFillCharArray()`
	 	- in dieser Methode erzeugen Sie das `char[]`der Länge `25`,
	 	- ein `Random`-Objekt, mit dem Sie unter Verwendung der `nextInt(bound)`-Methode zufällig Zahlen zwischen `97` und einschließlich `122`erzeugen,
	 	- die erzeugten `int`-Werte konvertieren Sie mithilfe des `(char)`-Typecast-Operators nach `char`,
	 	- dann befüllen Sie das `char[]` --> passen Sie aber auf, dass Sie kein Zeichen hinzufügen, das bereits im Array enthalten ist --> dazu benötigen Sie die `contains()`-Methode:

	- Schreiben Sie eine Methode `public static boolean contains(char[] ca, char c)`. Diese gibt ein `true` zurück, wenn `c` in `ca` enthalten ist und ein `false`, wenn nicht.

	- Schreiben Sie eine Methode `public static char[] sort(char[] a)`. Diese gibt ein `char[]` zurück, welches sortiert ist. Das übergebene Array `a` ist unsortiert. Siehe dazu [Sortieren von Arrays](sortieren.md#sortieren-von-arrays).

	- Schreiben Sie eine Methode `public static void print(char[] a)`, die ein übergebenes `char[]` in der Form

	 	```bash
	 	[ o, g, f, p, a, c, s, i, e, q, h, l, t, r, w, z, v, x, y, u, b, j, k, m, n ]
	 	```

	 	ausgibt. Kennen wir aus Übung 8, aber gute Übung, es nochmal zu machen.

	- Geben Sie in Ihre `main()`-Methode folgende Anweisungen ein:

	 	```java			
		System.out.printf("%n%n----------------- Erzeugen ------------------%n%n");
		char[] ca1 = createAndFillCharArray();
		print(ca1);
		
		System.out.printf("%n%n----------------- Sortieren ------------------%n%n");		
		char[] ca2 = sort(ca1);
		print(ca2); 
		```

		Es sollten Ausgaben in der Form:

		```bash

		----------------- Erzeugen ------------------

		[ o, g, f, p, a, c, s, i, e, q, h, l, t, r, w, z, v, x, y, u, b, j, k, m, n ]


		----------------- Sortieren ------------------

		[ a, b, c, e, f, g, h, i, j, k, l, m, n, o, p, q, r, s, t, u, v, w, x, y, z ]

		```

		erscheinen. Beachten Sie, dass die Einträge im Array zufällig erzeugt wurden. Beachten Sie außerdem, dass ein Buchstabe aus dem Alphabet fehlt, hier z.B. `d` (das Array hat die Länge `25`, das Alphabet hat `26` Buchstaben). 

	- ---

	- **Wenn Sie das geschafft haben, dann haben Sie die Aufgabe erfüllt! Herzlichen Glückwunsch! Die folgende(n) Aufgabe(n) sind optional :**

	- ---

	- Schreiben Sie eine Methode `public static char getMissingLetter(char[] a)`. Dieser Methode wird ein durch die obige Methode `createAndFillCharArray()` erstelltes `char`-Array übergeben. Das Array hat also die Länge `25` hat und aus dem Alphabet fehlt genau ein kleiner Buchstabe. Finden Sie den Buchstaben und geben ihn zurück. 

	- Schreiben Sie eine Methode `public static void findWord(String word)`. Dieser Methode wird eine Zeichenkette übergeben, die nur aus Buchstaben besteht. Sie können annehmen, dass es nur kleine Buchstaben sind, Sie können aber erstmal die `toLowerCase()`-Methode anwenden (siehe [String](hilfsklassen.md#die-klasse-string)). Rufen Sie für jedes Zeichen aus dem String die beiden Methoden `createAndFillCharArray()` und `getMissingLetter()` auf, bis das von der `getMissingLetter()`-Methode zurückgegebene Zeichen dem Zeichen des Strings entspricht, das Sie gerade betrachten. Eine Ausgabe als Beispiel:

		```bash
		P..........p (11)
		r.r (2)
		o..o (3)
		g............g (13)
		r..............................r (31)
		a........a (9)
		m..m (3)
		m...........................................................m (60)
		i....i (5)
		e.....e (6)
		rr (1)
		e......e (7)
		n............n (13)
		```

		Die Ausgabe erfolgte durch den Aufruf von `findWord("Programmieren");`. Ganz links in der Zeile steht immer das Zeichen des Strings, das gerade betrachtet wird. Dann kommen für jeden fehlgeschlagenen Versuch, durch `getMissingLetter()` das `'p' zurück zu bekommen, die Ausgabe eines Punktes. Sollte `getMissingLetter()` das `'p'` zurückgeben, wird es ausgegeben und außerdem noch in Klammern die Anzahl der Versuche. Der Cursor wechselt in die nächste Zeile und das nächste Zeichen des Strings ist dran. 

	- Viel Spaß und viel Erfolg!





??? "<a id="aufgabe-8"></a>Aufgabe 8 - SortedArray"
	- Wir erstellen uns einen neuen Datentyp `SortedArray`

	- **Idee**: Ein Objekt dieser Klasse beschreibt (enthält) ein `int`-Array, in dem 
		- die Elemente aufsteigend sortiert sind und 
		- kein Element doppelt vorkommt.

		Das Array ist stets genau so groß, so viele Elemente es enthält!

	- Erstellen Sie im package `aufgaben.aufgabe7` eine Klasse `SortedArray` ohne `main()`-Methode und eine Klasse `SortedArrayTest` mit `main()`-Methode. 

	- In der Klasse `SortedArray` erstellen Sie eine Objektvariable `s` vom Typ `int[]` (`private`). 

	- Implementieren Sie für die Klasse `SortedArray` zwei verschiedene Konstruktoren
		- parameterlos --> der Konstruktor erzeugt ein leeres Array `s` (mit der Länge `0`)
		- mit einem Parameter (`int element`) --> der Konstruktor erzeugt ein einelementiges Array `s` (mit der Länge `1`), wobei `s[0]` den Wert von `element` annimmt.

	- Implementieren Sie eine Objektmethode `public boolean insert(int element)`. Diese Methode gibt ein `false` zurück, wenn `element` bereits in `s` enthalten ist. Dann wird das `element` **nicht** dem Array hinzugefügt. Die Methode gibt `true` zurück, wenn `element` in `s` eingefügt wurde. Um `element` einzufügen, wird ein neues Array für `s` erzeugt, in dem alle vorherigen Werte aus `s` und das neue `element` (an der richtigen Stelle einsortiert) enthalten sind.

	- Implementieren Sie eine Objektmethode `public boolean delete(int element)`. Diese Methode gibt ein `false` zurück, wenn `element` nicht in `s` enthalten ist. Die Methode gibt `true` zurück, wenn `element` aus `s` gelöscht wurde. Beachten Sie, dass nach Löschen aus `s` die Länge von `s` um eins kleiner ist, als vor dem Löschen. Es muss also auch hier wieder ein neues Array erzeugt werden, welches nach dem Löschen dem "Wert" von `s` entspricht. 

	- Implementieren Sie eine Objektmethode `public void print()`, die das Array `s` in der Form `[ 4, 5, 9 ]` (Beispielwerte) ausgibt. 

	- **Tipp**: 
		- Um zu überprüfen, ob ein `int element` in `s` enthalten ist, sollten Sie sich eine Methode `boolean contains(int element)` schreiben (diese kann `private` sein, wenn sie nur innerhalb der Klasse verwendet werden soll; sogenannte  *Servicemethode*). 
		- Angenommen, Sie haben zwei Arrays: `s = [ 4, 9 ]` und `copy = [ 4, 5, 9]`, dann gilt nach `s = copy;`, dass `s == [ 4, 5, 9 ]`. 

	- Geben Sie in die `main()`-Methode der `SortedArrayTest`-Klasse mindestens folgende Anweisungen ein:
		```java 
		System.out.printf("%n%n------------------------- Test a1 -----------------------------------%n%n");
		SortedArray a1 = new SortedArray();
		a1.print();
		a1.delete(5);		a1.print();
		a1.insert(5);		a1.print();
		a1.insert(7);		a1.print();
		a1.delete(5);		a1.print();
		a1.insert(6);		a1.print();
		a1.insert(4);		a1.print();
		a1.insert(8);		a1.print();
		a1.delete(8);		a1.print();
		a1.delete(6);		a1.print();
		
		System.out.printf("%n%n------------------------- Test a2 -----------------------------------%n%n");
		SortedArray a2 = new SortedArray(9);
		a2.print();
		a2.insert(5);		a2.print();
		a2.insert(9);		a2.print();
		a2.insert(5);		a2.print();
		a2.insert(4);		a2.print();
		a2.insert(4);		a2.print();
		a2.delete(5);		a2.print();
		a2.delete(9);		a2.print();
		a2.delete(4);		a2.print();
		a2.delete(4);		a2.print();	
		``` 
		und führen Sie die `SortedArrayTest`-Klasse aus. Es sollten folgende Augaben entstehen:
		```bash
		------------------------- Test a1 -----------------------------------

		[ ]
		[ ]
		[ 5 ]
		[ 5, 7 ]
		[ 7 ]
		[ 6, 7 ]
		[ 4, 6, 7 ]
		[ 4, 6, 7, 8 ]
		[ 4, 6, 7 ]
		[ 4, 7 ]


		------------------------- Test a2 -----------------------------------

		[ 9 ]
		[ 5, 9 ]
		[ 5, 9 ]
		[ 5, 9 ]
		[ 4, 5, 9 ]
		[ 4, 5, 9 ]
		[ 4, 9 ]
		[ 4 ]
		[ ]
		[ ]
		```
	- Viel Spaß und viel Erfolg!





