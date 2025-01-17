# Aufgaben

Hier finden Sie die Aufgaben. Die Abgabefristen der einzelnen Aufgaben stehen [hier](index.md#planung). Beachten Sie die nachfolgenden Hinweise zum Hochladen der Aufgaben. 

## Hinweise zur Abgabe der Aufgaben

Die Aufgaben laden Sie in [Moodle](https://moodle.htw-berlin.de/course/view.php?id=29156) unter dem Reiter "Aufgaben" hoch. Dort ist für jede Aufgabe eine Moodle-Aufgabe erstellt. Beachten Sie, dass ein Hochladen nach Ablauf der Abgabefrist nicht mehr möglich ist. 

----

***Bitte laden Sie weder Lösungen hoch, die Sie mithilfe von KI erstellt haben, noch die Lösung, die vollständig der Lösung aus dem Tutorium entspricht! Ein Hochladen einer Lösung ist nicht zwingend notwendig! Es geht mir darum, Ihre Lösungen bzw. Lösungsversuche zu betrachten, um Schwerpunkte in der Vorlesung setzen zu können. Ihnen sollte es darum gehen, möglichst viel selbständig zu programmieren und versuchen, eigene Lösungen zu entwickeln. Am Ende sollen Sie programmieren und nicht fremde Lösungen in Moodle hochladen können. Es ist viel mehr wert, es versucht zu haben und nicht fertig geworden zu sein, als es gar nicht erst selbständig versucht zu haben. Sie lernen Programmieren nur durch Programmieren! Es gibt keinen anderen Weg.***

----



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

??? success "eine mögliche Lösung für Aufgabe1"
	```java linenums="1"
	package aufgaben.aufgabe1;

	public class Aufgabe1 
	{

	    /*
	     * upperHalf: the number of rows in the upper half of the rhombus   
	     * filled: true if the rhombus should be filled, false if it should be unfilled
	     */
	    public static void printRhombus(int upperHalf, boolean filled) 
	    {
	        if (filled) 
	        {
	            printRhombusFilled(upperHalf);
	        } 
	        else 
	        {
	            
	            printRhombusUnfilled(upperHalf);
	        }
	    }

	    /*
	    * printNChars: prints n characters of the given character  
	    * n: the number of characters to print
	    * c: the character to print
	    */
	    private static void printNChars(int n, char c) 
	    {
	        for (int i = 0; i < n; i++) 
	        {
	            System.out.print(c);
	        }
	    }

	    /*
	     * printRhombusUnfilledUpperHalf: prints the upper half of the rhombus
	     * upperHalf: the number of rows in the upper half of the rhombus
	     */
	    private static void printRhombusUnfilledUpperHalf(int upperHalf) 
	    {
	        for (int row = 0; row < upperHalf; row++) 
	        {
	            if(row == 0) 
	            {
	                printNChars(upperHalf, ' ');
	                printNChars(1, '*');
	            } 
	            else 
	            {
	                printNChars(upperHalf-row, ' ');
	                printNChars(1, '*');
	                printNChars(row*2-1, ' ');
	                printNChars(1, '*');
	            }
	            System.out.println();
	        }
	    }

	    /*
	     * printRhombusUnfilledLowerHalf: prints the lower half of the rhombus
	     * upperHalf: the number of rows in the upper half of the rhombus
	     */
	    private static void printRhombusUnfilledLowerHalf(int upperHalf) 
	    {
	        for (int row = upperHalf-1; row >= 0; row--) 
	        {
	            if(row == 0) 
	            {
	                printNChars(upperHalf, ' ');
	                printNChars(1, '*');
	            } 
	            else 
	            {
	                printNChars(upperHalf-row, ' ');
	                printNChars(1, '*');
	                printNChars(row*2-1, ' ');
	                printNChars(1, '*');
	            }
	            System.out.println();
	        }
	    }

	    
	    /*
	     * printRhombusFilledUpperHalf: prints the upper half of the rhombus
	     * upperHalf: the number of rows in the upper half of the rhombus
	     */
	    private static void printRhombusFilledUpperHalf(int upperHalf) 
	    {
	        for (int row = 0; row < upperHalf; row++) 
	        {
	            printNChars(upperHalf-row, ' ');
	            printNChars(row*2+1, '*');
	            System.out.println();
	        }
	    }

	    /*
	     * printRhombusFilledLowerHalf: prints the lower half of the rhombus
	     * upperHalf: the number of rows in the upper half of the rhombus
	     */
	    private static void printRhombusFilledLowerHalf(int upperHalf) 
	    {
	        for (int row = upperHalf-1; row >= 0; row--) 
	        {
	            printNChars(upperHalf-row, ' ');
	            printNChars(row*2+1, '*');
	            System.out.println();
	        }
	    }

	    /*
	     * printRhombusFilled: prints the rhombus
	     * upperHalf: the number of rows in the upper half of the rhombus
	     */
	    private static void printRhombusFilled(int upperHalf) 
	    {
	        printRhombusFilledUpperHalf(upperHalf);
	        printMiddleRowFilled(upperHalf);
	        printRhombusFilledLowerHalf(upperHalf);
	        System.out.println();
	    }

	    /*
	     * printMiddleRowFilled: prints the middle row of the rhombus
	     * upperHalf: the number of rows in the upper half of the rhombus
	     */
	    private static void printMiddleRowFilled(int upperHalf) 
	    {
	        printNChars(2*upperHalf+1, '*');
	        System.out.println();
	    }

	    /*
	     * printMiddleRowUnfilled: prints the middle row of the rhombus
	     * upperHalf: the number of rows in the upper half of the rhombus
	     */
	    private static void printMiddleRowUnfilled(int upperHalf) 
	    {
	        printNChars(1, '*');
	        printNChars(2*upperHalf-1, ' ');
	        printNChars(1, '*');
	        System.out.println();
	    }

	    /*
	     * printRhombusUnfilled: prints the rhombus
	     * upperHalf: the number of rows in the upper half of the rhombus
	     */
	    private static void printRhombusUnfilled(int upperHalf) 
	    {
	        printRhombusUnfilledUpperHalf(upperHalf);
	        printMiddleRowUnfilled(upperHalf);
	        printRhombusUnfilledLowerHalf(upperHalf);
	        System.out.println();
	    }   

	    public static void main(String[] args) 
	    {
	        printRhombus(1, true);
	        printRhombus(1, false);
	        printRhombus(5, true);
	        printRhombus(5, false);
	        printRhombus(10, true);
	        printRhombus(10, false);
	        printRhombus(15, true);
	        printRhombus(15, false);

	    }
	}

	```

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



??? success "eine mögliche Lösung für Aufgabe2"
	```java linenums="1"
	package aufgaben.aufgabe2;

	public class Aufgabe2 
	{

	    /*
	     * lengthOfNumber: returns the length of the number
	     * number: the number to get the length of
	     */
	    public static int lengthOfNumber(int number)
	    {
	        int copyNumber = number;
	        if(number < 0)
	        {
	            copyNumber = -number;
	        }
	        // this is better instead of the first 4 lines above:
	        // int copynumber = number < 0 ? -number : number;  
	        int length = 0;
	        while(copyNumber > 0)
	        {
	            copyNumber /= 10;
	            length++;
	        }
	        return length;  
	    }   

	    /*
	     * firstDigit: returns the first digit of the number
	     * number: the number to get the first digit of
	     */
	    public static int firstDigit(int number)
	    {
	        int copyNumber = number;
	        if(number < 0)
	        {
	            copyNumber = -number;
	        }
	        while(copyNumber > 9)
	        {
	            copyNumber /= 10;
	        }
	        return copyNumber;
	    }

	    /*
	     * powerOf10ToN: returns the power of 10 to the n
	     * n: the power to calculate (n >= 0)
	     */
	    public static int powerOf10ToN(int n)
	    {
	        int result = 1;
	        for(int i = 0; i < n; i++)
	        {
	            result *= 10;
	        }
	        return result;
	    }

	    /*
	     * cutFirstDigit: cuts the first digit of the number
	     * number: the number to cut the first digit of
	     */
	    public static int cutFirstDigit(int number)
	    {
	        int copyNumber = number < 0 ? -number : number;
	        int firstDigit = firstDigit(copyNumber);
	        int length = lengthOfNumber(copyNumber);
	        int result = copyNumber - firstDigit * powerOf10ToN(length - 1);
	        return result;
	    }   

	    /*
	     * secondDigitIsZero: returns true if the second digit is 0
	     * number: the number to check if the second digit is 0
	     */
	    public static boolean secondDigitIsZero(int number)
	    {
	        int copyNumber = number < 0 ? -number : number;
	        if(copyNumber < 10)
	        {
	            return false;
	        }   
	        while(copyNumber > 99) 
	        {
	            copyNumber /= 10;
	        }
	        return copyNumber % 10 == 0;
	    }   

	    public static void main(String[] args) 
	    {

	        System.out.printf("Length of 0     ---> %d\n", lengthOfNumber(0));
	        System.out.printf("Length of 1     ---> %d\n", lengthOfNumber(1));
	        System.out.printf("Length of 9    ---> %d\n", lengthOfNumber(9));
	        System.out.printf("Length of 10    ---> %d\n", lengthOfNumber(10));
	        System.out.printf("Length of 1234  ---> %d\n", lengthOfNumber(1234));
	        System.out.printf("Length of -1234 ---> %d\n", lengthOfNumber(-1234));

	        System.out.printf("First digit of 0     ---> %d\n", firstDigit(0));
	        System.out.printf("First digit of 1     ---> %d\n", firstDigit(1));
	        System.out.printf("First digit of 9     ---> %d\n", firstDigit(9));
	        System.out.printf("First digit of 10    ---> %d\n", firstDigit(10));
	        System.out.printf("First digit of 1234  ---> %d\n", firstDigit(1234));
	        System.out.printf("First digit of -1234 ---> %d\n", firstDigit(-1234));
	        System.out.printf("First digit of 5678  ---> %d\n", firstDigit(5678));

	        System.out.printf("Power of 10 to 0  ---> %d\n", powerOf10ToN(0));
	        System.out.printf("Power of 10 to 1  ---> %d\n", powerOf10ToN(1));
	        System.out.printf("Power of 10 to 2  ---> %d\n", powerOf10ToN(2));
	        System.out.printf("Power of 10 to 3  ---> %d\n", powerOf10ToN(3));
	        System.out.printf("Power of 10 to 4  ---> %d\n", powerOf10ToN(4));  

	        System.out.printf("Cut first digit of 0     ---> %d\n", cutFirstDigit(0));
	        System.out.printf("Cut first digit of 1     ---> %d\n", cutFirstDigit(1));
	        System.out.printf("Cut first digit of 9     ---> %d\n", cutFirstDigit(9));
	        System.out.printf("Cut first digit of -9    ---> %d\n", cutFirstDigit(-9));
	        System.out.printf("Cut first digit of 11    ---> %d\n", cutFirstDigit(11));
	        System.out.printf("Cut first digit of 91    ---> %d\n", cutFirstDigit(91));
	        System.out.printf("Cut first digit of 1234  ---> %d\n", cutFirstDigit(1234));
	        System.out.printf("Cut first digit of -1234 ---> %d\n", cutFirstDigit(-1234));
	        System.out.printf("Cut first digit of 9999  ---> %d\n", cutFirstDigit(9999));
	        System.out.printf("Cut first digit of -9999 ---> %d\n", cutFirstDigit(-9999));
	        System.out.printf("Cut first digit of 1023  ---> %d\n", cutFirstDigit(1023));   
	        System.out.printf("Cut first digit of -1023 ---> %d\n", cutFirstDigit(-1023));

	        System.out.printf("Second digit is zero of 0       ---> %b\n", secondDigitIsZero(0));
	        System.out.printf("Second digit is zero of 1       ---> %b\n", secondDigitIsZero(1));
	        System.out.printf("Second digit is zero of 9       ---> %b\n", secondDigitIsZero(9));
	        System.out.printf("Second digit is zero of 11      ---> %b\n", secondDigitIsZero(11));
	        System.out.printf("Second digit is zero of 101     ---> %b\n", secondDigitIsZero(101));
	        System.out.printf("Second digit is zero of 111     ---> %b\n", secondDigitIsZero(111));
	        System.out.printf("Second digit is zero of 1001    ---> %b\n", secondDigitIsZero(1001));
	        System.out.printf("Second digit is zero of -10234  ---> %b\n", secondDigitIsZero(-10234));
	        System.out.printf("Second digit is zero of 1111    ---> %b\n", secondDigitIsZero(1111));
	        System.out.printf("Second digit is zero of 10000   ---> %b\n", secondDigitIsZero(10000));
	    }
	}
	```



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
		- `A = Math.sqrt(s * (s-a) * (s-b) * (s-c))` (siehe Klasse [Math](hilfsklassen.md#die-klasse-math))
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
		- für die obigen Objekte soll somit gelten:
			```bash
			t1 und t2 gleiche Seiten ? : false
			t1 und t4 gleiche Seiten ? : true
			t1 und t5 gleiche Seiten ? : true
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



??? success "eine mögliche Lösung für Aufgabe3"
	=== "Triangle.java"
		```java linenums="1"
		package aufgaben.aufgabe3;

		public class Triangle 
		{
		    private int a;
		    private int b;
		    private int c;

		    public Triangle(int a, int b, int c) 
		    {
		        this.a = a;
		        this.b = b;
		        this.c = c;
		    }

		    /*
		     * Berechnet den Umfang des Dreiecks    
		     * @return der Umfang des Dreiecks
		     */
		    public int circumference()
		    {
		        return this.a + this.b + this.  c;
		    }

		    /*
		     * Berechnet den Flaecheninhalt des Dreiecks
		     * @return der Flaecheninhalt des Dreiecks
		     */
		    public double area()
		    {
		        double s = (this.a + this.b + this.c) / 2.0;
		        return Math.sqrt(s * (s - this.a) * (s - this.b) * (s - this.c));
		    }

		    /*
		     * Gibt die Informationen des Dreiecks auf die Konsole aus
		     */
		    public void print() 
		    {
		        System.out.printf("Seiten          : a=%d, b=%d, c=%d\n", this.a, this.b, this.c);
		        System.out.printf("Umfang          : %d\n", this.circumference());
		        System.out.printf("Flaecheninhalt  : %f\n", this.area());
		        if(this.equilateral())
		        {
		            System.out.println("Das Dreieck ist gleichseitig.");
		        }
		        else if(this.isosceles())
		        {
		            System.out.println("Das Dreieck ist gleichschenklig.");
		        }
		        else
		        {
		            System.out.println("Das Dreieck ist unregelmaessig.");
		        }
		        if(this.rightAngled())
		        {
		            System.out.println("Das Dreieck ist rechtwinklig.");
		        }
		        else
		        {
		            System.out.println("Das Dreieck ist nicht rechtwinklig.");
		        }
		        System.out.println();
		    }

		    /*
		     * Prueft ob das Dreieck gleichseitig ist
		     * @return true, wenn das Dreieck gleichseitig ist, false sonst
		     */
		    public boolean equilateral()
		    {
		        return this.a == this.b && this.b == this.c;
		    }   

		    /*
		     * Prueft ob das Dreieck gleichschenklig ist
		     * @return true, wenn das Dreieck gleichschenklig ist, false sonst
		     */
		    public boolean isosceles()
		    {
		        return this.a == this.b || this.b == this.c || this.a == this.c;
		    }       

		    /*
		     * Prueft ob das Dreieck rechtwinklig ist
		     * @return true, wenn das Dreieck rechtwinklig ist, false sonst
		     */
		    public boolean rightAngled()
		    {
		        return  this.a * this.a + this.b * this.b == this.c * this.c || 
		                this.a * this.a + this.c * this.c == this.b * this.b || 
		                this.b * this.b + this.c * this.c == this.a * this.a;
		    }  

		    /*
		     * Prueft ob das Dreieck den gleichen Umfang hat
		     * @param t das zu vergleichende Dreieck
		     * @return true, wenn das Dreieck den gleichen Umfang hat, false sonst
		     */
		    public boolean sameCircumference(Triangle t)
		    {
		        return this.circumference() == t.circumference();
		    }  
		    
		    /*
		     * Prueft ob das Dreieck kleiner ist als das andere Dreieck
		     * @param t das zu vergleichende Dreieck
		     * @return true, wenn das Dreieck kleiner ist als das andere Dreieck, false sonst
		     */
		    public boolean isSmaller(Triangle t)
		    {
		        return this.area() < t.area();
		    }   

		    /*
		     * Prueft ob das Dreieck groesser ist als das andere Dreieck
		     * @param t das zu vergleichende Dreieck
		     * @return true, wenn das Dreieck groesser ist als das andere Dreieck, false sonst
		     */
		    public boolean isBigger(Triangle t)
		    {
		        return this.area() > t.area();
		    }  
		    
		    /*
		     * Prueft ob das Dreieck die gleichen Seiten hat
		     * @param t das zu vergleichende Dreieck
		     * @return true, wenn das Dreieck die gleichen Seiten hat, false sonst
		     */
		    public boolean sidesAreEqual(Triangle t)
		    {
		        return this.a == t.a && this.b == t.b && this.c == t.c ||
		               this.a == t.b && this.b == t.c && this.c == t.a ||
		               this.a == t.c && this.b == t.a && this.c == t.b ||
		               this.a == t.a && this.b == t.c && this.c == t.b ||
		               this.a == t.b && this.b == t.a && this.c == t.c ||
		               this.a == t.c && this.b == t.b && this.c == t.a ||
		               this.a == t.a && this.b == t.b && this.c == t.c;
		    }   

		}
		```
	=== "Testklasse.java"
		```java linenums="1"
		package aufgaben.aufgabe3;

		public class Testklasse 
		{

		    public static void main(String[] args) 
		    {
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

		        System.out.println();
		        System.out.println("t1 und t2 gleicher Umfang ? : " + t1.sameCircumference(t2));
		        System.out.println("t1 und t3 gleicher Umfang ? : " + t1.sameCircumference(t3));
		        System.out.println("t2 und t3 gleicher Umfang ? : " + t2.sameCircumference(t3));

		        System.out.println();
		        System.out.println("t1 kleiner als t2 ? : " + t1.isSmaller(t2));
		        System.out.println("t2 kleiner als t1 ? : " + t2.isSmaller(t1));
		        System.out.println("t1 kleiner als t4 ? : " + t1.isSmaller(t4));
		        System.out.println("t4 kleiner als t1 ? : " + t4.isSmaller(t1));

		        System.out.println();
		        System.out.println("t1 groesser als t2 ? : " + t1.isBigger(t2));
		        System.out.println("t2 groesser als t1 ? : " + t2.isBigger(t1));
		        System.out.println("t1 groesser als t4 ? : " + t1.isBigger(t4));
		        System.out.println("t4 groesser als t1 ? : " + t4.isBigger(t1));

		        System.out.println();
		        System.out.println("t1 und t2 gleiche Seiten ? : " + t1.sidesAreEqual(t2));
		        System.out.println("t1 und t4 gleiche Seiten ? : " + t1.sidesAreEqual(t4));
		        System.out.println("t1 und t5 gleiche Seiten ? : " + t1.sidesAreEqual(t5));
		        System.out.println("t1 und t6 gleiche Seiten ? : " + t1.sidesAreEqual(t6));

		        System.out.println();
		        
		    }
		}
		```



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
		- `public String toString()` --> gibt einen Bruch als `String` in der Form `zaehler / nenner` zurück
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
		und führen Sie die `BruchTest`-Klasse aus. Es sollten folgende Ausgaben entstehen:
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



??? success "eine mögliche Lösung für Aufgabe4"
	=== "Bruch.java"
		```java linenums="1"
		package aufgaben.aufgabe4;

		public class Bruch 
		{
		    private int zaehler;
		    private int nenner;

		    /*
		     * Konstruktor fuer einen Bruch mit dem Wert zaehler/nenner
		     * @param zaehler der Zaehler des Bruchs
		     * @param nenner der Nenner des Bruchs
		     */
		    public Bruch(int zaehler, int nenner)
		    {
		        this.zaehler = zaehler;
		        this.nenner = nenner;
		    }

		    /*
		     * Konstruktor fuer einen Bruch mit dem Wert 1/1
		     */
		    public Bruch() 
		    {
		        this.zaehler = 1;
		        this.nenner = 1;
		    }

		    /*
		     * Wandelt den Bruch in einen String um
		     * @return der String
		     */
		    public String toString()
		    {
		        return this.zaehler + "/" + this.nenner;
		    }

		    /*
		     * Berechnet den groessten gemeinsamen Teiler von zahl1 und zahl2
		     * @param zahl1 die erste Zahl
		     * @param zahl2 die zweite Zahl
		     * @return der groesste gemeinsame Teiler von zahl1 und zahl2
		     */
		    public int ggT(int zahl1, int zahl2)
		    {  
		        int a = zahl1 < 0 ? -zahl1 : zahl1;
		        int b = zahl2 < 0 ? -zahl2 : zahl2;
		        while (b > 0) 
		        {
		            int temp = b;
		            b = a % b;
		            a = temp;
		        }
		        return a;
		    }

		    /*
		     * Kuerzt den Bruch
		     * @return der gekuerzte Bruch
		     */
		    public Bruch kuerzen()
		    {
		        int ggt = ggT(this.zaehler, this.nenner);
		        this.zaehler /= ggt;
		        this.nenner /= ggt;
		        return this;
		    }

		    /*
		     * Addiert zwei Brueche
		     * @param b der zu addierende Bruch
		     * @return der addierte Bruch
		     */
		    public  Bruch plus(Bruch b)
		    {
		        int neuerNenner = this.nenner * b.nenner;
		        int neuerZaehler = this.zaehler * b.nenner + b.zaehler * this.nenner;
		        return new Bruch(neuerZaehler, neuerNenner).kuerzen();
		    }

		    /*
		     * Subtrahiert zwei Brueche
		     * @param b der zu subtrahierende Bruch
		     * @return der subtrahierte Bruch
		     */
		    public Bruch minus(Bruch b)
		    {
		        int neuerNenner = this.nenner * b.nenner;
		        int neuerZaehler = this.zaehler * b.nenner - b.zaehler * this.nenner;
		        return new Bruch(neuerZaehler, neuerNenner).kuerzen();
		    }

		    /*
		     * Multipliziert zwei Brueche
		     * @param b der zu multiplizierende Bruch
		     * @return der multiplizierte Bruch
		     */
		    public Bruch mal(Bruch b)
		    {
		        int neuerZaehler = this.zaehler * b.zaehler;
		        int neuerNenner = this.nenner * b.nenner;
		        return new Bruch(neuerZaehler, neuerNenner).kuerzen();
		    }   

		    /*
		     * Dividiert zwei Brueche
		     * @param b der zu dividierende Bruch
		     * @return der dividierten Bruch
		     */
		    public Bruch geteilt(Bruch b)
		    {
		        int neuerZaehler = this.zaehler * b.nenner;
		        int neuerNenner = this.nenner * b.zaehler;
		        return new Bruch(neuerZaehler, neuerNenner).kuerzen();
		    }

		    /*
		     * Prueft ob der Bruch groesser ist als ein anderer Bruch
		     * @param b der zu vergleichende Bruch
		     * @return true, wenn der Bruch groesser ist, false sonst
		     */
		    public boolean istGroesser(Bruch b)
		    {
		        return this.zaehler * b.nenner > this.nenner * b.zaehler;
		    }

		    /*
		     * Prueft ob der Bruch kleiner ist als ein anderer Bruch
		     * @param b der zu vergleichende Bruch
		     * @return true, wenn der Bruch kleiner ist, false sonst
		     */
		    public boolean istKleiner(Bruch b)
		    {
		        return this.zaehler * b.nenner < this.nenner * b.zaehler;
		    }   

		    /*
		     * Prueft ob der Bruch gleich ist wie ein anderer Bruch
		     * @param b der zu vergleichende Bruch
		     * @return true, wenn der Bruch gleich ist, false sonst
		     */
		    public boolean istGleich(Bruch b)
		    {
		        return this.zaehler * b.nenner == this.nenner * b.zaehler;
		    }
		}
		```
	=== "BruchTest.java"
		```java linenums="1"
		package aufgaben.aufgabe4;

		public class BruchTest 
		{

		    public static void main(String[] args) 
		    {
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
		        System.out.printf("%5s - %5s = %5s %n", b1.toString(), b1.toString(), b1.minus(b1).toString());     // nenner sollte ungleich 0 bleiben!
		    
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
		    }
		}
		```




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



??? success "eine mögliche Lösung für Aufgabe5"
	=== "ListElement.java"
		```java linenums="1"
		package aufgaben.aufgabe5;

		public class ListElement 
		{
		    private char value;
		    private boolean hasPredecessor;
		    private boolean hasSuccessor;
		    private ListElement predecessor;
		    private ListElement successor;

		    /*
		     * Konstruktor fuer ein einzelnes Element
		     * @param value der Wert des Elements
		     */
		    public ListElement(char value)
		    {
		        this.value = value;
		        this.hasPredecessor = false;
		        this.hasSuccessor = false;
		        this.predecessor = null;
		        this.successor = null;
		    }

		    /*
		     * Diese Methode dient nur der Ueberlegung. Sie stellt einen einfachen Fall dar.
		     * 
		     * Fuegt ein einzelnes Element vor einem anderen Element in eine Liste ein
		     * @param element das Element, vor das das neue Element eingefuegt werden soll
		     */
		    public void insertSingleListElementBeforeList(ListElement element)
		    {
		        if(!element.hasPredecessor)
		        {
		            this.predecessor = null;
		            this.hasPredecessor = false;
		        }
		        else
		        {
		            this.predecessor = element.predecessor;
		            this.hasPredecessor = true;
		            element.predecessor.successor = this;
		        }
		        this.successor = element;
		        this.hasSuccessor = true;
		        element.predecessor = this;
		        element.hasPredecessor = true;  
		    }

		    /*
		     * Diese Methode dient nur der Ueberlegung. Sie stellt einen weiteren Fall dar.
		     * 
		     * Fuegt eine Liste vor einem anderen einzelnen Element in eine Liste ein
		     * @param element das Element, vor das die neue Liste eingefuegt werden soll
		     */
		    public void insertListBeforeSingleListElement(ListElement element)
		    {
		        ListElement lastInList = this;
		        while(lastInList.hasSuccessor)
		        {
		            lastInList = lastInList.successor;
		        }
		        lastInList.successor = element;
		        lastInList.hasSuccessor = true;
		        element.predecessor = lastInList;
		        element.hasPredecessor = true;
		    }   

		    /*
		     * Dies ist die eigentliche Methode, die eine Liste in eine andere Liste einfuegt.
		     * 
		     * Fuegt eine Liste vor eine andere Liste in eine Liste ein
		     * @param element die Liste, die vor das neue Element eingefuegt werden soll
		     */
		    public void insertListBeforeList(ListElement element)
		    {
		        ListElement lastInThisList = this;        
		        while(lastInThisList.hasSuccessor)
		        {
		            lastInThisList = lastInThisList.successor;
		        }
		        lastInThisList.successor = element;
		        lastInThisList.hasSuccessor = true;
		        if(element.hasPredecessor)
		        {
		            ListElement predecessorOfElement = element.predecessor;
		            predecessorOfElement.successor = this;
		            predecessorOfElement.hasSuccessor = true;
		            this.predecessor = predecessorOfElement;
		            this.hasPredecessor = true; 
		        }
		        element.predecessor = lastInThisList;
		        element.hasPredecessor = true;  
		    }

		    public void insertBefore(ListElement element)
		    {
		        insertListBeforeList(element);
		    }

		    public void print()
		    {
		       System.out.print(this.value);
		       if(this.hasSuccessor)
		       {
		        this.successor.print();
		       }
		       else
		       {
		        System.out.println();
		       }
		    }
		}

		```
	=== "Programmklasse.java"
		```java linenums="1"
		package aufgaben.aufgabe5;

		public class Programmklasse {

		    public static void main(String[] args) 
		    {
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
		        l1.insertBefore(l2);        // W-e
		        System.out.printf("? : %15s", "We == ");l1.print();
		        
		        l5.insertBefore(l6);        // n-a
		        l5.insertBefore(l7);        // na-c
		        l7.insertBefore(l8);        // nac-h
		        l6.insertBefore(l9);        // nach-t
		        System.out.printf("? : %15s", "nacht == ");l5.print();
		        
		        l1.insertBefore(l5);        // We-nacht
		        System.out.printf("? : %15s", "Wenacht == ");l1.print();            
		        
		        l10.insertBefore(l11);      // e-n
		        l9.insertBefore(l10);       // Wenacht-en
		        System.out.printf("? : %15s", "Wenachten == ");l1.print();
		        System.out.printf("? : %15s", "nachten == ");l5.print();
		        
		        l3.insertBefore(l5);        // We-i-nachten
		        System.out.printf("? : %15s", "inachten == ");l3.print();
		        System.out.printf("? : %15s", "Weinachten == ");l1.print();
		        l4.insertBefore(l5);        // Wei-h-nachten
		        System.out.printf("? : %15s", "Weihnachten == ");l1.print();
		    }
		}
		```




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

	- Rufen Sie in der `main()` die beiden Methoden (oder die, die Sie implementiert haben) wie folgt auf:
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


??? success "eine mögliche Lösung für Aufgabe6"
	=== "Aufgabe6.java"
		```java linenums="1"
		package aufgaben.aufgabe6;

		import java.util.Random;

		public class Aufgabe6 
		{
		    /*
		     * fill an array with random numbers between fromInclusive and toInclusive
		     * @param length the length of the array
		     * @param fromInclusive the lower bound of the random numbers
		     * @param toInclusive the upper bound of the random numbers
		     * @return the filled array with random numbers
		     */
		    public static int[] createAndFillArray(int length, int fromInclusive, int toInclusive)
		    {
		        int[] arr = new int[length];
		        Random r = new Random();
		        for(int index = 0; index<length; index++)
		        {
		            arr[index] = r.nextInt(toInclusive + 1 - fromInclusive) + fromInclusive;
		        }
		        return arr;
		    }

		    /*
		     * print an array
		     * @param a the array to print
		     */
		    public static void printArray(int[] a)
		    {
		        System.out.print("[");  
		        for(int index = 0; index<a.length; index++)
		        {
		            if(index < a.length - 1)
		            {
		                System.out.print(a[index] + ", ");
		            }
		            else
		            {
		                System.out.print(a[index]);
		            }
		        }
		        System.out.println("]");
		    }

		    /*
		     * print an array as a table
		     * @param a the array to print
		     */
		    public static void printTable(int[] a)
		    {
		        System.out.printf("%n| %-10s |", "Index : ");
		        for(int index = 0; index<a.length; index++)
		        {
		            System.out.printf(" %3d |", index);
		        }
		        System.out.printf("%n|------------|");
		        for(int index = 0; index<a.length; index++)
		        {
		            System.out.printf("-----|");
		        }
		        System.out.printf("%n| %-10s |", "Wert  : ");
		        for(int index = 0; index<a.length; index++)
		        {
		            System.out.printf(" %3d |", a[index]);
		        }
		        System.out.printf("%n%n");
		    }

		    /*
		     * print an array as a horizontal histogram
		     * @param a the array to print
		     */
		    public static void printHorizontal(int[] a)
		    {
		        System.out.println();
		        for(int index = 0; index<a.length; index++)
		        {
		            System.out.printf("     |%n %3d | ", index);
		            for(int nrOfStars=0; nrOfStars<a[index]; nrOfStars++)
		            {
		                System.out.printf("*");
		            }
		            System.out.printf("%n     |%n");
		        }
		        System.out.printf("%n%n");
		    }   

		    /*
		     * print an array as an upside down histogram
		     * @param a the array to print
		     */
		    public static void printUpsideDown(int[] a)
		    {
		        int maxValue = a.length > 0 ? a[0] : 0;
		        for(int index = 0; index<a.length; index++)
		        {
		            if(a[index] > maxValue)
		            {
		                maxValue = a[index];
		            }
		        }
		        System.out.printf("%n     |");
		        for(int index = 0; index<a.length; index++)
		        {
		            System.out.printf(" %3d   ", index);
		        }
		        System.out.printf("%n-----+");
		        for(int index = 0; index<a.length; index++)
		        {
		            System.out.printf("-------");
		        }

		        for(int row = 0; row<maxValue; row++)
		        {
		            System.out.printf("%n %3d |", row+1);
		            for(int index = 0; index<a.length; index++)
		            {
		                if(a[index] > row)
		                {
		                    System.out.printf("   *   ");   
		                }
		                else
		                {
		                    System.out.printf("       ");
		                }
		            }
		        }
		        System.out.printf("%n%n");
		    }


		    /*
		     * print an array as a vertical histogram
		     * @param a the array to print
		     */
		    public static void printVertical(int[] a)
		    {
		        int maxValue = a.length > 0 ? a[0] : 0;
		        for(int index = 0; index<a.length; index++)
		        {
		            if(a[index] > maxValue)
		            {
		                maxValue = a[index];
		            }
		        }

		        for(int row = maxValue; row>0; row--)
		        {
		            System.out.printf("%n %3d |", row);
		            for(int index = 0; index<a.length; index++)
		            {
		                if(a[index] > row)
		                {
		                    System.out.printf("   *   ");   
		                }
		                else
		                {
		                    System.out.printf("       ");
		                }
		            }
		        }

		        System.out.printf("%n-----+");
		        for(int index = 0; index<a.length; index++)
		        {
		            System.out.printf("-------");
		        }

		        System.out.printf("%n     |");
		        for(int index = 0; index<a.length; index++)
		        {
		            System.out.printf(" %3d   ", index);
		        }
		        System.out.printf("%n%n");

		    }
		    public static void main(String[] args)
		    {
		        Random r = new Random();
		        int length = r.nextInt(10)+10;
		        int[] arr1 = createAndFillArray(length, 20, 30);

		        System.out.printf("%n%n%n----------- printArray -----------------%n%n%n");
		        printArray(arr1);

		        System.out.printf("%n%n%n----------- printTable -----------------%n%n%n");
		        printTable(arr1);

		        System.out.printf("%n%n%n----------- printHorizontal -----------------%n%n%n");
		        printHorizontal(arr1);

		        System.out.printf("%n%n%n----------- printUpsideDown -----------------%n%n%n");
		        printUpsideDown(arr1);  

		        System.out.printf("%n%n%n----------- printVertical -----------------%n%n%n");
		        printVertical(arr1);    
		    }
		}
		```


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



??? success "eine mögliche Lösung für Aufgabe7"
	=== "Aufgabe7.java"
		```java linenums="1"
		package aufgaben.aufgabe7;

		import java.util.Random;

		public class Aufgabe7 
		{

		    /*
		     * checks if a char is in a char array  
		     * @param charArray the char array to check 
		     * @param c the char to check for
		     * @return true if the char is in the array, false otherwise
		     */
		    private static boolean contains(char[] charArray, char c)
		    {

		        for(int i = 0; i<charArray.length; i++)
		        {
		            if(charArray[i] == c)
		            {
		                return true;
		            }
		        }
		        return false;
		    }

		    /*
		     * creates a char array with 25 random chars
		     * chars are small letters and unique
		     * @return the char array
		     */
		    public static char[] createAndFillCharArray()
		    {
		        char[] charArray = new char[25];
		        for(int index = 0; index<charArray.length; index++)
		        {
		            Random r = new Random();
		            char c = (char) (r.nextInt(26) + 97);
		            while(contains(charArray, c))
		            {
		                c = (char) (r.nextInt(26) + 97);
		            }
		            charArray[index] = c;
		        }
		        return charArray;
		    }

		    /*
		     * sorts a char array
		     * @param unsorted the char array to sort
		     * @return the sorted char array
		     */
		    public static char[] sort(char[] unsorted)
		    {
		        char[] sorted = new char[unsorted.length];
		        for(int index = 0; index<unsorted.length; index++)
		        {
		            sorted[index] = unsorted[index];
		        }

		        for(int bubble = 1; bubble<unsorted.length; bubble++)
		        {
		            for(int index = 0; index<unsorted.length - bubble; index++)
		            {
		                if(sorted[index]>sorted[index+1])
		                {
		                    char temp = sorted[index];
		                    sorted[index] = sorted[index+1];
		                    sorted[index+1] = temp;
		                }
		            }
		        }
		        return sorted;
		    }

		    /*
		     * prints a char array
		     * @param array the char array to print
		     */
		    public static void print(char[] array)
		    {
		        System.out.print("[");
		        for(int index = 0; index<array.length; index++)
		        {
		            if(index == array.length - 1)
		            {
		                System.out.print(array[index]);
		            }
		            else
		            {
		                System.out.print(array[index] + ", ");
		            }
		        }
		        System.out.println("]");
		    }

		    /*
		     * gets the missing letter in a char array
		     * missing letter is the first letter in the alphabet that is not in the array
		     * @param ca the char array to check
		     * @return the missing letter
		     */
		    public static char getMissingLetter(char[] ca)
		    {
		        for(int asciiCode = 97; asciiCode<123; asciiCode++)
		        {
		            char letter = (char) asciiCode;
		            if(!contains(ca, letter))
		            {
		                return letter;
		            }
		        }
		        return '!'; // never called for our use case
		    }

		    /*
		     * give a word; for each letter in the word, create a char array with 25 random chars   
		     * get the missing letter for each char array
		     * if the missing letter is not the same as the letter in the word, create a new char array and get the missing letter again
		     * print the letter and the number of times the missing letter was found
		     * @param word the word to find the missing letter in
		     */
		    public static void findWord(String word)
		    {
		        String copyLowerCase = word.toLowerCase();
		        // System.out.println(copyLowerCase);

		        for(int index = 0; index<word.length(); index++)
		        {
		            int count = 1;
		            System.out.print(word.charAt(index));
		            char[] ca = createAndFillCharArray();
		            char missingLetter = getMissingLetter(ca);
		            while(missingLetter != copyLowerCase.charAt(index))
		            {
		                ca = createAndFillCharArray();
		                missingLetter = getMissingLetter(ca);
		                System.out.print(".");
		                count++;
		            }
		            System.out.println(missingLetter + " (" + count + ")");
		        }
		    }

		    public static void main(String[] args) 
		    {
		        for(int asciiValue = 97; asciiValue<123; asciiValue++)
		        {
		            char c = (char) asciiValue;
		            System.out.print(c + " ");
		        }

		        System.out.printf("%n%n----------------- Erzeugen ------------------%n%n");
		        char[] ca1 = createAndFillCharArray();
		        print(ca1);

		        System.out.printf("%n%n----------------- Sortieren ------------------%n%n");        
		        char[] ca2 = sort(ca1);
		        print(ca2);

		        System.out.printf("%n%n----------------- findMissingLetter ------------------%n%n"); 
		        char missingLetter = getMissingLetter(ca2);
		        System.out.println("Missing letter: " + missingLetter);


		        System.out.printf("%n%n----------------- findWord ------------------%n%n"); 
		        findWord("Programmieren");
		    }
		}

		```



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



??? success "eine mögliche Lösung für Aufgabe8"
	=== "SortedArray.java"
		```java linenums="1"
		package aufgaben.aufgabe8;

		public class SortedArray {
		    private int[] s;

		    public SortedArray()
		    {
		        this.s = new int[0];
		    }

		    public SortedArray(int element)
		    {
		        this.s = new int[1];
		        this.s[0] = element;
		    }

		    /*
		     * checks if the element is in the array this.s
		     * @param element the element to check
		     * @return true if the element is in the array this.s, false otherwise
		     */
		    public boolean contains(int element)
		    {
		        for(int index = 0; index<this.s.length; index++)
		        {
		            if(this.s[index] == element)
		            {
		                return true;
		            }
		        }
		        return false;
		    }

		    /*
		     * inserts the element into the array this.s
		     * @param element the element to insert
		     * @return true if the element was inserted, false otherwise
		     */
		    public boolean insert(int element)
		    {
		        if(contains(element))
		        {
		            return false;
		        }
		        int[] copy = new int[this.s.length + 1];
		        int index = 0;
		        while(index < this.s.length && this.s[index] < element)
		        {
		            copy[index] = this.s[index];
		            index++;
		        }
		        copy[index] = element;
		        for(int i = index; i<this.s.length; i++)
		        {
		            copy[i+1] = this.s[i];
		        }
		        this.s = copy;
		        return true;
		    }

		    /*
		     * deletes the element from the array this.s
		     * @param element the element to delete
		     * @return true if the element was deleted, false otherwise
		     */
		    public boolean delete(int element)
		    {
		        if(!contains(element))
		        {
		            return false;
		        }
		        int[] copy = new int[this.s.length - 1];
		        int copyIndex = 0;
		        for(int index = 0; index<this.s.length; index++)
		        {
		            if(this.s[index] != element)
		            {
		                copy[copyIndex] = this.s[index];
		                copyIndex++;
		            }
		        }
		        this.s = copy;  
		        return true;
		    }

		    /*
		     * prints the array this.s
		     */
		    public void print()
		    {
		        System.out.print("[");
		        for(int index = 0; index<this.s.length; index++)
		        {
		            if(index<this.s.length-1)
		            {
		                System.out.print(this.s[index] + ", ");
		            }
		            else
		            {
		                System.out.print(this.s[index]);
		            }
		        }
		        System.out.println("]");
		    }
		}
		```
	=== "SortedArrayTest.java"
		```java linenums="1"
		package aufgaben.aufgabe8;

		public class SortedArrayTest {

		    public static void main(String[] args)
		    {
		        System.out.printf("%n%n------------------------- Test a1 -----------------------------------%n%n");
		        SortedArray a1 = new SortedArray();
		        a1.print();
		        a1.delete(5);       a1.print();
		        a1.insert(5);       a1.print();
		        a1.insert(7);       a1.print();
		        a1.delete(5);       a1.print();
		        a1.insert(6);       a1.print();
		        a1.insert(4);       a1.print();
		        a1.insert(8);       a1.print();
		        a1.delete(8);       a1.print();
		        a1.delete(6);       a1.print();
		        
		        System.out.printf("%n%n------------------------- Test a2 -----------------------------------%n%n");
		        SortedArray a2 = new SortedArray(9);
		        a2.print();
		        a2.insert(5);       a2.print();
		        a2.insert(9);       a2.print();
		        a2.insert(5);       a2.print();
		        a2.insert(4);       a2.print();
		        a2.insert(4);       a2.print();
		        a2.delete(5);       a2.print();
		        a2.delete(9);       a2.print();
		        a2.delete(4);       a2.print();
		        a2.delete(4);       a2.print();
		    }
		}

		```




