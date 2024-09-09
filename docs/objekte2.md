# Klassen und Objekte II

Wir machen weiter mit eigenen Datentypen und erstellen uns Objekte, die von diesen Typen sind. Wir werden im Folgenden

- eigene Datentypen in neuen Datentypen verwenden, 
- mehrere Konstruktoren in der Klasse definieren,
- in Methoden Objekte erzeugen und diese auch zurückgeben und
- das Schlüsselwort `this` kennenlernen. 

## Eigene Datentypen in eigenen Datentypen verwenden

Wir beginnen damit, eigene Datentypen in neuen Datentypen zu verwenden, da dies eine gute Wiederholung ist. Angenommen, wir haben unsere Klasse [`Adresse`](objekte1.md#ein-erster-eigener-datentyp-adresse) in einem package `themen.objekte` erstellt und wir wollen die kommenden Klassen in einem package `themn.objekte2` erstellen. In diesem package erstellen wir uns eine neue Klasse `Person` mit folgenden Objektvariablen:

- `name` vom Typ `String`,
- `vorname` vom Typ `String` und
- `adresse` vom Typ `Adresse`. 

Wir fügen auch gleich noch den Konstruktor hinzu und bereiten die `print()`-Methode vor:

=== "themen/objekte2/Person.java"
	```java linenums="1"
	package themen.objekte2;		// extra anders als bei Adresse, um import zu lernen

	import themen.objekte.Adresse;	// das Paket ist bei Ihnen vielleicht anders

	public class Person
	{
		// ------- Objektvariablen -----------
		private String name;
		private String vorname;
		private Adresse adresse;
		
		// ------- Konstruktor -----------
		public Person(String pName, String pVorname, Adresse pAdresse)
		{
			name = pName;
			vorname = pVorname;
			adresse = pAdresse;
		}
		
		// ------- Objektmethoden -----------
		public void print()
		{
			// wie sieht die Ausgabe aus?
			// wie kann ich die Adresse ausgeben?
		}
	}
	```

- In Zeile `10` verwenden wir [die von uns geschriebene](objekte1.md#ein-erster-eigener-datentyp-adresse) Klasse `Adresse`. Wir haben extra mal die Klasse `Person` in einem anderen Paket (`themen.objekte2` - siehe Zeile `1`) erstellt, als die Klasse `Adresse` (`themen.objekte` - ist bei Ihnen sicherlich ein anderes Paket), um zu zeigen, wie wir Klassen aus anderen Paketen importieren (siehe Zeile `3`).
- der Konstruktor (Zeilen `13-18`) sieht aus, wie erwartet. Wir initialisieren alle Objektvariablen mit den als Parameter übergebenen Werten. 
- in den Zeilen `21-25` haben wir auch schon die `print()`-Methode vorbereitet. Darin wollen wir alle Informationen über das jeweilige `Person`-Objekt ausgeben. Für `name` und `vorname` ist das sicherlich einfach. Aber wie kommen wir an die Informationen von `adresse`? 

Wir erstellen uns in einer Testklasse zunächst Objekte der Klasse `Person`. 

### `Person`-Objekte erzeugen

Um Objekte von `Person` erstellen zu können, benötigen wir Objekte des Typs `Adresse`, da diese dem Konstruktor als Parameter übergeben werden müssen. Beachten Sie auch hier, dass wir die Klasse `Adresse` dazu aus dem package `themen.objekte` importieren. 

=== "themen/objekte2/Testklasse.java"
	```java linenums="1"
	package themen.objekte2;

	import themen.objekte.Adresse;

	public class Testklasse
	{

		public static void main(String[] args)
		{
			Adresse adresse1 = new Adresse("Wilhelminenhofstr.", 75, 12459, "Berlin");			
			Adresse adresse2 = new Adresse("Treskowallee", 8, 10318, "Berlin");	
			
			Person maria = new Person("Musterfrau", "Maria", adresse1);
			Person max = new Person("Mustermann", "Max", adresse2);

		}
	}
	```

### Objektmethoden aufrufen

Zunächst erweitern wir unsere `print()`-Methode in `Person`:

=== "print() in Person.java erweitern"
	```java linenums="20"
	// ------- Objektmethoden -----------
	public void print()
	{
		System.out.println(vorname + " " + name); 
		// wie kann ich die Adresse ausgeben?
	}
	```

In der `Testklasse` rufen wir die `print()`-Methode für die beiden `Person`-Objekte auf:


=== "main() in Testklasse.java erweitern"
	```java linenums="8"
	public static void main(String[] args)
	{
		Adresse adresse1 = new Adresse("Wilhelminenhofstr.", 75, 12459, "Berlin");			
		Adresse adresse2 = new Adresse("Treskowallee", 8, 10318, "Berlin");	
		
		Person maria = new Person("Musterfrau", "Maria", adresse1);
		Person max = new Person("Mustermann", "Max", adresse2);
		
		maria.print();
		max.print();
	}
	```

Die Ausgabe erfolgt wie gewünscht:

```bash
Maria Musterfrau
Max Mustermann
```

Wie können wir nun auch die Adressen von `maria` und `max` ausgeben? Die Antwort ist: mithilfe der Objektmethoden von `Adresse`. Schauen wir uns die Objektmethoden von `Adresse` nochmal an (siehe auch [hier](objekte1.md#getxxx-methoden-getter)):


=== "Objektmethoden von Adresse.java"
	```java linenums="20"
	// --- Objektmethoden ------
	public String getAdresse()
	{
		return strasse + " " + nummer + " in " + postleitzahl + " " + wohnort;
	}
	
	public String getStrasse()
	{
		return strasse;
	}
	
	public int getNummer()
	{
		return nummer;
	}
	
	public int getPostleitzahl()
	{
		return postleitzahl;
	}
	
	public String getWohnort()
	{
		return wohnort;
	}
	```

Alle diese Methoden sind `public` und können von allen Klassen aufgerufen werden. Wir nutzen in der `print()`-Methode von `Person` die Objektmethode `getAdresse()` von `Adresse`, könnten aber auch alle anderen Objektmethoden verwenden. 

=== "print() in Person.java erweitern"
	```java linenums="20"
	// ------- Objektmethoden -----------
	public void print()
	{
		// adresse ist vom Typ Adresse und besitzt die Objektmethode getAdresse()
		System.out.println(vorname + " " + name + " wohnt in " + adresse.getAdresse()); 
	}
	```

Erneutes Ausführen der `Testklasse` erzeugt nun folgende Ausgabe:

```bash
Maria Musterfrau wohnt in Wilhelminenhofstr. 75 in 12459 Berlin
Max Mustermann wohnt in Treskowallee 8 in 10318 Berlin
```

Die Objekteigenschaft `adresse` der Klasse `Person` ist vom Typ Adresse. Um ein Objekt der Klasse `Person` zu erzeugen, muss dem Konstruktor der Klasse `Person` ein Objekt der Klasse `Adresse` übergeben werden - das erwartet der Konstruktor als Parameter. Jedes Objekt vom Typ `Person` "besitzt" somit ein eigenes Objekt von Typ `Adresse`, welches in `adresse` gespeichert ist. Für dieses Objekt können alle Objekteigenschaften aus `Adresse` aufgerufen werden (z.B. auch `getStrasse()`, `getNummer()`, `getPostleitzahl()` und `getWohnort()`). 

### Getter für `Person` erzeugen

Wir erstellen uns für die Klasse `Person` getter (also `getXXX()`-Methoden) für die Objektvariablen:

=== "themen/objekte2/Person.java"
	```java linenums="1"
	package themen.objekte2;		// extra anders als bei Adresse, um import zu lernen

	import themen.objekte.Adresse;	// das Paket ist bei Ihnen vielleicht anders

	public class Person
	{
		// ------- Objektvariablen -----------
		private String name;
		private String vorname;
		private Adresse adresse;
		
		// ------- Konstruktor -----------
		public Person(String pName, String pVorname, Adresse pAdresse)
		{
			name = pName;
			vorname = pVorname;
			adresse = pAdresse;
		}
		
		// ------- Objektmethoden -----------
		public void print()
		{
			// adresse ist vom Typ Adresse und besitzt die Objektmethode getAdresse()
			System.out.println(vorname + " " + name + " wohnt in " + adresse.getAdresse()); 
		}
		
		public String getName()
		{
			return name;
		}

		public String getVorname()
		{
			return vorname;
		}

		public Adresse getAdresse()
		{
			return adresse;
		}
	}
	```

Die Implementierungen der Getter sind so, wie wir sie bereits kennen. Wir nennen die Methoden `get` und hängen jeweils in *camel-case*-Schreibweise den Namen der Objektvariablen an, also `getName()`, `getVorname()` und `getAdrese()`. Der Rückgabetyp der Methode entspricht stets dem Typ der Variablen, also für `name` und `vorname` ist der Rückgabetyp der Methoden `getName()` und `getVorname()` jeweils `String` und der Rückgabetyp von `getAdresse()` ist wie der Typ von `adresse`, nämlich `Adresse`. 

Wir betrachten nun besonders die Methode `getAdresse()` der Klasse `Person` und rufen diese in der `Testklasse` auf. 

=== "main() in Testklasse.java erweitern"
	```java linenums="1"
	public static void main(String[] args)
	{
		Adresse adresse1 = new Adresse("Wilhelminenhofstr.", 75, 12459, "Berlin");			
		Adresse adresse2 = new Adresse("Treskowallee", 8, 10318, "Berlin");	
		
		Person maria = new Person("Musterfrau", "Maria", adresse1);
		Person max = new Person("Mustermann", "Max", adresse2);
		
		maria.print();
		max.print();
		
		Adresse mariasAdresse = maria.getAdresse(); // getAdresse() von Person
		Adresse maxAdresse = max.getAdresse(); 		// getAdresse() von Person
		
		System.out.println(mariasAdresse.getAdresse()); // getAdresse() von Adresse
		System.out.println(maxAdresse.getAdresse()); 	// getAdresse() von Adresse
	}
	```

- In Zeile `19` rufen wir die soeben erstelle Methode `getAdresse()` für das `Person`-Objekt `maria` auf. Die Rückgabe dieser Objektmethode ist die `adresse` von `maria`, also ein Objekt vom Typ `Adresse`, welches wir in der Referenzvariablen `mariasAdresse` vom Typ `Adresse` speichern. 
- In Zeile `20` passiert das gleiche mit dem `Person`-Obejkt `max`. In der Variablen `maxAdresse` vom Typ `Adresse` ist nun das `Adresse`-Objekt von `max` gespeichert. 
- für diese beiden `Adresse`-Objekte können wir nun alle Objektmethoden aus `Adresse` aufrufen. In Zeile `22` wird z.B. die `getAdresse()`-Methode des Objektes `mariasAdresse` aufgerufen und in Zeile `23` die `getAdresse()`-Methode des `Adresse`-Objektes `maxAdresse`. 

Beachten Sie, dass es **zwei** Methoden mit dem **gleichen Namen** gibt! Es existiert eine `getAdresse()`-Methode für den Datentyp `Adresse`. Diese Methode kann von Objekten des Typs `Adresse` aufegrufen werden und gibt einen `String` zurück. Außerdem gibt es eine `getAdresse()`-Methode für den Datentyp `Person`. Diese kann von Objekten des Datentyps `Person` aufgerufen werden und gibt eine `Adresse` zurück. 

### Aneinanderreihung von Aufrufen von Objektmethoden

Wir hätten in der `main()`-Methode der `Testklasse` auch folgende Anweisungen ausführen können:

=== "main() in Testklasse.java erweitern"
	```java linenums="1" hl_lines="19 20"
	public static void main(String[] args)
	{
		Adresse adresse1 = new Adresse("Wilhelminenhofstr.", 75, 12459, "Berlin");			
		Adresse adresse2 = new Adresse("Treskowallee", 8, 10318, "Berlin");	
		
		Person maria = new Person("Musterfrau", "Maria", adresse1);
		Person max = new Person("Mustermann", "Max", adresse2);
		
		maria.print();
		max.print();
		
		Adresse mariasAdresse = maria.getAdresse(); // getAdresse() von Person
		Adresse maxAdresse = max.getAdresse(); 		// getAdresse() von Person
		
		System.out.println(mariasAdresse.getAdresse()); // getAdresse() von Adresse
		System.out.println(maxAdresse.getAdresse()); 	// getAdresse() von Adresse

		// ginge auch
		System.out.println(maria.getAdresse().getAdresse()); // getAdresse() von Person und von Adresse
		System.out.println(max.getAdresse().getAdresse());	 // getAdresse() von Person und von Adresse
	}
	```

Die Anweisung `maria.getAdresse()` gibt, wie gesagt, ein `Adresse`-Objekt zurück. Wir müssen dieses Objekt nicht zwingend zwischenspeichern (so, wie in Zeile `12`), sondern können auch gleich für dieses Objekt eine Objektmethode aufrufen, nämlich z.B. die Methode `getAdresse()` des Typs `Adresse`, welche einen `String` zurückgibt, der durch `println()` ausgegeben wird. Das gleiche passiert in Zeile `20` mit dem `Person`-Objekt `max`, für das zunächst die `getAdresse()`-Methode aus `Person` aufgerufen wird, welche ein `Adresse`-Objekt zurückgibt und für diese `Adresse`-Objekt wird die Objektmethode `getAdresse()` des Typs `Adresse` aufgerufen. 

Wir sehen bereits an diesem einfachen Beispiel, dass eine solche Hintereinanderreihung von Aufrufen von Objektmethoden leicht für Verwirrung Sorgen kann und schwer zu verstehen ist. Hier kommt noch gesondert hinzu, dass verschiedene Methoden gleich heißen. Eine solche Hintereinanderreihung von Objektmethoden sollten wir möglichst vermeiden. Wir könnten unserer `Person`-Klasse z.B. eine Methode `getAdresseString()` hinzufügen, die uns die Adresse als `String` zurückgibt:

=== "themen/objekte2/Person.java"
	```java linenums="1" hl_lines="42-45"
	package themen.objekte2;		// extra anders als bei Adresse, um import zu lernen

	import themen.objekte.Adresse;	// das Paket ist bei Ihnen vielleicht anders

	public class Person
	{
		// ------- Objektvariablen -----------
		private String name;
		private String vorname;
		private Adresse adresse;
		
		// ------- Konstruktor -----------
		public Person(String pName, String pVorname, Adresse pAdresse)
		{
			name = pName;
			vorname = pVorname;
			adresse = pAdresse;
		}
		
		// ------- Objektmethoden -----------
		public void print()
		{
			// adresse ist vom Typ Adresse und besitzt die Objektmethode getAdresse()
			System.out.println(vorname + " " + name + " wohnt in " + adresse.getAdresse()); 
		}
		
		public String getName()
		{
			return name;
		}

		public String getVorname()
		{
			return vorname;
		}

		public Adresse getAdresse()
		{
			return adresse;
		}

		public String getAdresseString()
		{
			return adresse.getAdresse();
		}
	}
	```

Dann könnten wir in der `main()`-Methode der `Testklasse` 


=== "main() in Testklasse.java erweitern"
	```java linenums="29"
	public static void main(String[] args)
	{
		/* gekuerzt - siehe oben */

		System.out.println(maria.getAdresseString());
		System.out.println(max.getAdresseString());
	}
	```

die neue Objektmethode aus `Person` aufrufen und bekämen die Adresse als `String` zurück. 

## Das Schlüsselwort `this`

Wir wissen jetzt schon, dass Objektmethoden immer nur von Objekten aufgerufen werden können. Wir können z.B. nicht einfach nur `getAdresseString()` aus der Klasse `Person` aufrufen, sondern benötigen ein Objekt der Klasse `Person`, welches die Objektmethode aufruft. 

> Objektmethoden können nur von einem Objekt aufgerufen werden!

In dem obigen Beispiel hatten wir z.B. die Objekte `maria` und `max` vom Typ `Person`, die beide jeweils (für sich) die Objektmethode `getAdresseString()` aufgerufen haben. 

Wenn wir uns also den Aufruf einer Objektmethode anschauen, dann wissen wir auch immer:

> Wenn eine Objektmethode aufgerufen wird, dann immer durch genau ein konkretes Objekt. 

Innerhalb der Klasse `Person` wissen wir nicht, von welchem konkreten Objekt eine Objektmethode aufgerufen wird. Die Referenzvariablen `max` und `maria` sind z.B. innerhalb der Klasse `Person` nicht sichtbar (es sind lokale Variablen der `main()`-Methode von `Testklasse`). Wir wissen aber, dass es ein aufrufendes Objekt gibt (denn nur für ein konkretes Objekt kann eine Objektmethode aufgerufen werden). Dieses konkrete Objekt können wir innerhalb der Klasse referenzieren - das machen wir mit dem Schlüsselwort `this`. `this` steht also für das konkrete Objekt, das die Methode (gerade) aufruft. 

> `this` ist das aufrufende Objekt. (genauer: die *Referenz* auf das aufrufende Objekt)

Schauen wir uns zur Wiederholung nochmal die Klasse [Circle](objekte1.md#ein-weiterer-datentyp-circle) an. In der dazugehörigen `Testklasse` hatten wir zwei Objekte der Klasse `Circle` erstellt und diese Objekte haben Objektmethoden aufgerufen:

=== "Testklasse.java"
	```java linenums="1"
	public class Testklasse
	{

		public static void main(String[] args)
		{
			Circle c1 = new Circle(5.0);
			Circle c2 = new Circle(3.5);
			
			c1.print();
			System.out.println();	
			c2.print();
			
			System.out.println("c1 groesser als c2 ? " + c1.isBigger(c2));		
			System.out.println("c1 kleiner als c2  ? " + c1.isSmaller(c2));		
			System.out.println("c1 gleich c2       ? " + c1.isEqual(c2));
			System.out.println();
		}
	}
	```

In den Zeilen `6` und `7` werden die beiden `Circle`-Objekte erzeugt. In Zeile `9` ruft das `c1`-Objekt die `print()`-Methode auf und in Zeile `11` ruft das `c2`-Objekt die `print()`-Methode auf. Innerhalb der Klasse wäre dann `this` einmal das `c1`-Objekt (nämlich bei `c1.print()`) und ein anderes Mal ist `this` das `c2`-Objekt, nämlich bei `c2.print()`. Bei den Aufrufen `c1.isBigger(c2)`, `c1.isSmaller(c2)` und `c1.isEqual(c2)` ist das aufrufende Objekt immer `c1`. 

Wozu benötigen wir `this` überhaupt? Bis jetzt kamen wir ohne `this` aus. Aber schauen wir uns nur einmal den Konstruktor von `Circle` an:

=== "Circle.java"
	```java linenums="1"
	public class Circle
	{
		// ------- Objektvariable ---------------
		private double radius;
		
		// --------- Konstruktor ----------------
		public Circle(double pRadius)
		{
			radius = pRadius;
		}
	}
	```

Im Konstruktor wird die Objektvariable `radius` mit dem Wert des Parameters `pRadius` initialisiert. Die Objektvariable `radius` ist [global](objekte1.md#objektvariablen-sind-global), d.h. wir haben in jeder Methode der Klasse Zugriff auf diese Variable. Objektvariablen werden innerhalb der Klasse (nicht innerhalb einer Methode) deklariert und sind deshalb in dem gesamten Anweisungsblock der Klasse, also in der gesamten Klasse sichtbar. Wir können **in allen Methoden** der Klasse auf die Objektvariablen zugreifen. 

Der Parameter `pRadius` ist eine lokale Variable. Diese Variable wird in der Methode deklariert und ist auch nur dort sichtbar. Sie existiert auch nur, solange die Methode ausgeführt wird. Was passiert aber, wenn wir den Parameter genau wir die Objektvariable nennen?

=== "Circle.java"
	```java linenums="1"
	public class Circle
	{
		// ------- Objektvariable ---------------
		private double radius;
		
		// --------- Konstruktor ----------------
		public Circle(double radius)	// Parameter heisst wie die Objektvariable
		{
			radius = radius;			// Achtung!!! nur Parameter sichtbar - sogenanntes shadowing!!!
		}
	}
	```

Wenn der Parameter genau so heißt, wie die Objektvariable, gibt es einen Namenskonflikt. Wir können in der Methode auf die Objektvariable zugreifen (sie ist ja global), es gibt aber auch eine lokale Variable mit dem gleichen Namen `radius`. Woher soll der Compiler (oder die Laufzeitumgebung) nun wissen, ob wir die Objektvariable `radius` meinen oder die lokale Variable `radius`? 

Tatsächlich, stehen in der Anweisung `radius = radius;` in Zeile `9` beide `radius` für den Parameter, d.h. wir weisen dem Parameter `radius` dort den Wert des Parameters `radius` zu. Das ist erstens nicht gewollte und zweitens unsinnig. Die Objektvariable `radius` wird durch den Parameter `radius` **überschattet** - sogenanntes *shadowing*. Wenn wir in diesem Falle die Objektvariable `radius` meinen, dann **müssen** wir `this.radius` schreiben. 

> Mit `this.` können wir innerhalb der Klasse auf alle Objekteigenschaften (Objektvariablen und Objektmethoden) zugreifen. 

Die korrekte Implementierung des Konstruktors lautet also:

=== "Circle.java"
	```java linenums="1"
	public class Circle
	{
		// ------- Objektvariable ---------------
		private double radius;
		
		// --------- Konstruktor ----------------
		public Circle(double radius)	// Parameter heisst wie die Objektvariable
		{
			this.radius = radius;		// Objektvariable = Parameterwert;
		}
	}
	```

Jetzt wird der Objektvariablen `this.radius` der Wert des Parameters `radius` zugewiesen. 

Ab jetzt referenzieren wir **alle Objekteigenschaften** innerhalb der Klasse mit `this`! Wir passen zunächst die Implementierung von `Circle` an:

=== "Circle.java"
	```java linenums="1"
	public class Circle
	{
		// ------- Objektvariable ---------------
		private double radius;
		
		// --------- Konstruktor ----------------
		public Circle(double radius)	// Parameter heisst wie die Objektvariable
		{
			this.radius = radius;		// hier muss this
		}
		
		// ----- Getter der Objektvariablen -----
		public double getRadius()
		{
			return this.radius;			// hier kann this - sollte ab jetzt aber immer
		}
		
		// ----- weitere Objektmethoden ---------
		public double getDiameter()
		{
			return 2.0 * this.radius;
		}
		
		public void print()
		{
			System.out.println("Radius         : " + this.radius);
			System.out.println("Durchmesser    : " + this.getDiameter());	// Aufruf Objektmethode
			System.out.println("Umfang         : " + this.circumference());	// Aufruf Objektmethode
			System.out.println("Flaecheninhalt : " + this.area());			// Aufruf Objektmethode
			System.out.println();
		}
		
		public double circumference()
		{
			return Math.PI * this.getDiameter();
		}
		
		public double area()
		{
			return Math.PI * this.radius * this.radius;
		}
		
		public boolean isSmaller(Circle c)
		{
			return (this.radius < c.radius);
		}
		
		public boolean isBigger(Circle c)
		{
			return (this.radius > c.radius);
		}
		
		public boolean isEqual(Circle c)
		{
			return !this.isSmaller(c) && !this.isBigger(c);
		}
	}
	```

Wir sehen, dass wir überall dort, wo wir auf Objekteigenschaften zugreifen, die Referenz `this.` davor gesetzt haben. das sollten wir von un ab in Zukunft auch immer so handhaben, da der Code dann leichter erweiterbar ist (wir müssen uns nicht darum kümmern, ob eine neue lokale Variable eventuell genau so heißt, wie eine Objektvariable) und er ist auch besser lesbar, denn wir können leichter zwischen Methoden anderer Klassen und eigenen unterscheiden. 

Betrachten wir die Implementierung der Methode `isSmaller()` nochmal genauer:

```java
public boolean isSmaller(Circle c)
{
	return (this.radius < c.radius);
}
```

Angenommen, wir haben, wie oben in dem Beispiel, in der `main()`-Methode den Aufruf `c1.isSmaller(c2)`. Dann ist `c1` das aufrufende Objekt dieser Objektmethode und steht innerhalb der Klasse für das `this`. Das Objekt `c2` wird als Parameter übergeben und steht in der Implementierung für das Objekt `c` der Klasse `Circle`. Innerhalb der Methode werden die Werte von `radius` vom aufrufenden Objekt `this` und vom Parameter `c` miteinander verglichen. 

Wir passen auch unsere Klasse `Person` entsprechend an:

=== "Person.java mit `this`"
	```java linenums="1" 
	package themen.objekte2;		

	import themen.objekte.Adresse;

	public class Person
	{
		// ------- Objektvariablen -----------
		private String name;
		private String vorname;
		private Adresse adresse;
		
		// ------- Konstruktor -----------
		public Person(String name, String vorname, Adresse adresse)
		{
			this.name = name;
			this.vorname = vorname;
			this.adresse = adresse;
		}
		
		// ------- Objektmethoden -----------
		public void print()
		{
			// adresse ist vom Typ Adresse und besitzt die Objektmethode getAdresse()
			System.out.println(this.vorname + " " + this.name + " wohnt in " + this.adresse.getAdresse()); 
		}
		
		public String getName()
		{
			return this.name;
		}

		public String getVorname()
		{
			return this.vorname;
		}

		public Adresse getAdresse()
		{
			return this.adresse;
		}

		public String getAdresseString()
		{
			return this.adresse.getAdresse();
		}
	}
	```

Insbesondere innerhalb der Mthode `getAdresseString()` erkennen wir gut, dass wir darin nicht auf die `getAdresse()`-Methode von `Person` zugreifen, sondern auf die `getAdresse()`-Methode von `Adresse`. Wir haben auch die Parameter des Konstruktors anegpasst, denn es ist völlig üblich, die Parameter so zu nennen, wie die Objektvariablen, die damit initialisiert werden sollen. Aber dann **muss** vor den Objektvariablen auch jeweils `this.` stehen!

??? question "Integrieren Sie auch in den Klassen `Adresse` und `Point` die `this.`-Referenz!"

## Mehrere Konstruktoren

Es kann vorkommen, dass wir gar nicht allen Objektvariablen einen Wert im Konstruktor übergeben wollen. Wenn wir für eine Objektvariable keinen Wert im Konstruktor übergeben, dann soll dieser Objektvariablen ein Standardwert zugewiesen werden. Ein einfaches Beispiel wäre, dass wir für unsere Klasse `Circle` einen Konstruktor haben, dem ein Wert für `radius` übergeben wird und einen Konstruktor, der parameterlos ist, dem also kein Wert für `radius` übergeben wird. In diesem Fall soll `radius` den Wert `1.0` annhmen, also der [Einheitskreis](https://de.wikipedia.org/wiki/Einheitskreis) sein. 

Diese Anforderung erfüllen wir, indem wir zwei Konstruktoren definieren:

=== "Circle.java mit zwei Konstruktoren"
	```java linenums="1" hl_lines="12-15"
	public class Circle
	{
		// ------- Objektvariable ---------------
		private double radius;
		
		// --------- Konstruktoren ----------------
		public Circle(double radius)	// Parameter heisst wie die Objektvariable
		{
			this.radius = radius;		// hier muss this
		}
		
		public Circle()					// parameterlos
		{
			this.radius = 1.0;			// Standardwert - Einheitskreis
		}
		
		/* alle anderen Methoden bleiben, wie sie sind - siehe oben */
	}
	```

Jetzt können Objekte von `Circle` sowohl unter Verwendung des parametrisierten Konstruktors, als auch unter Verwendung des parameterlosen Konstruktors erzeugt werden:

=== "Testklasse.java - Auszug main()-Methode"
	```java
	Circle c1 = new Circle(5.0);
	Circle c2 = new Circle(3.5);
	Circle c3 = new Circle();		// parameterloser Konstruktor - Einheitskreis
	
	c1.print();	
	c2.print();
	c3.print();
	```

ergibt folgende Ausgabe:

```bash
Radius         : 5.0
Durchmesser    : 10.0
Umfang         : 31.41592653589793
Flaecheninhalt : 78.53981633974483

Radius         : 3.5
Durchmesser    : 7.0
Umfang         : 21.991148575128552
Flaecheninhalt : 38.48451000647496

Radius         : 1.0
Durchmesser    : 2.0
Umfang         : 6.283185307179586
Flaecheninhalt : 3.141592653589793
```

Das Prinzip, das hierbei angewendet wird, nennt sich *Überladen von Methoden*. 

### Überladen von Methoden

Das *Überladen von Methoden* erfolgt immer dann, wenn Methoden gleichen Namens existieren. Wichtig ist, dass sich diese Methoden in ihrer Parameterliste unterscheiden.

Was bedeutet, dass sich Parameterlisten von Methoden unterscheiden? Methoden haben eine **unterschiedliche Parameterliste**, wenn

- sich die Anzahl der Parameter unterscheidet oder wenn
- sich die Typen bzw. die Typreihenfolge der Parameter unterscheiden. 

Angenommen, unsere Methode heißt `method`, dann haben folgende Methoden eine unterschiedliche Parmaterliste:

1. `method(int number)`					// nur ein Parameter
2. `method(int nr1, int nr2)`			// zwei Parameter int, int
3. `method(double nr1, double nr2)` 	// zwei parameter double, double
4. `method(int nr1, double nr2)`		// zwei Parameter int, double
5. `method(double nr1, int nr2)` 		// zwei parameter double, int

Die Methode `method` wäre also in diesem Fall (wenn es jeweils noch passende Implementierungen dazu gibt), fünf Mal *überladen*. Dem Compiler muss beim Aufruf klar sein, welche der jeweiligen Methoden er aufrufen muss. Das ist durch unterschiedliche Parameterlisten gegeben. Folgende Beispiele zeigen dies:

- `method(3.0, 3);` 	// ruft Methode 5. auf
- `method(3, 3);`		// ruft Methode 2. auf
- `method(3.0, 3.0);`	// ruft Methode 3. auf
- `method(3);`			// ruft Methode 1. auf
- `method(3, 3.0);`		// ruft Methode 4. auf

Die Namen der Parameter spielen **keine** Rolle. Beispielsweise wäre `method(int number1, int number2)` ein Dopplung zu Methode 2. Das programm ließe sich gar nicht übersetzen. Auch der Rückgabetyp wird nicht zur Unterscheidung der *Methodensignatur*  hinzugezogen. Die beiden Methoden `int method(int nr1, int nr2)` und `double method(int nr1, int nr2)` wären ebenfalls eine Dopplung. Woher soll der Compiler beim Aufruf von z.B.  `method(3, 3);` wissen, welche der beiden Methoden ausgeführt werden soll, die die ein `int` zurückgibt oder die, die ein `double` zurückgibt. 

> Zur Methodensignatur gehören der Name der Methode und die Parameterliste.

> Für alle Methoden einer Klasse müssen sich deren Methodensignaturen unterscheiden, also entweder deren Namen oder deren Parameterlisten. 

### Mehrere Konstruktoren in `Point`

Für unsere Klasse [`Point`](objekte1.md#eine-weiterer-datentyp-point) wollen wir ebenfalls mehrere Konstruktoren definieren:

- Konstruktor mit zwei Paramtern (haben wir schon) --> `x` und `y` werden mit den Parameterwerten initialisiert
- Konstruktor mit einem Parameter --> `x` und `y` bekommen den gleichen Wert, den des Parameters
- Konstruktor ohne Parameter --> `x` und `y` bekommen jeweils den Wert `0`

=== "Point.java Ausschnitt nur Konstruktoren"
	```java
	public class Point
	{
		// --- Objektvariablen -----------
		private int x;
		private int y;
		
		// --- Konstruktoren ---------------
		public Point(int x, int y)
		{
			this.x = x;
			this.y = y;
		}
		
		public Point(int value)
		{
			this.x = value;
			this.y = value;
		}
		
		public Point()
		{
			this.x = 0;
			this.y = 0;
		}

		/* restliche Methoden bleiben gleich - hier gekuerzt 	*/
		/* siehe oben.  										*/ 
	```


### Mehrere Konstruktoren in `Person`

Der Konstruktor in `Person` sieht derzeit so aus:

```java
public Person(String name, String vorname, Adresse adresse)
{
	this.name = name;
	this.vorname = vorname;
	this.adresse = adresse;
}
```

Das heißt, wir erwarten ein Objekt vom Typ `Adresse`, um ein Objekt vom Typ `Person` erstellen zu können. Es könnte ja aber sein, dass ein solches Objekt (noch) gar nicht existiert und wir selbst ein solches Objekt innerhalb unserer Konstruktors erstellen müssen. Wir bräuchten dafür nur alle Informationen, um das Objekt erstellen zu können, also 

- eine Strasse (`String`), 
- eine Hausnummer (`int`),
- ein Wohnort (`String`) und
- eine Postleitzahl (`int`).

Wir erstellen uns einen Konstruktor, der dafür Werte übergibt (und auch für `name` und `vorname`):

```java
public Person(String name, String vorname, String strasse, int nummer, int postleitzahl, String wohnort)
{
	this.name = name;
	this.vorname = vorname;
	this.adresse = new Adresse(strasse, nummer, postleitzahl, wohnort);
}
```

Es wird also kein existierendes `Adresse`-Objekt dem Konstruktor übergeben, sondern erst im Konstruktor eines erstellt. Die restliche Implementierung der Klasse `Person` ändert sich aber nicht, da sich ja auch für `adresse` nichts geändert hat - die Variable zeigt auf ein `Adresse`-Objekt. 

### Objekterzeugende Methoden

Genau die gleiche Lösung können wir verwenden, wenn eine `Person` umzieht, also ihre `Adresse` ändert. `umzug()` ist dabei auf jeden Fall eher eine Eigenschaft der Klasse `Person`, als der Klasse `Adresse`! Wir erweitern die Klasse `Person` um zwei `umzug()`-Methoden. Die eine erwartet ein (neues) `Adresse`-Objekt und die andere bekommt Werte für die Erstellung eines neuen `Adresse`-Objektes übergeben:

=== "Person.java - Auszug: umzug()-Methoden"
	```java linenums="1"
	public void umzug(Adresse neueAdresse)
	{
		this.adresse = neueAdresse;
	}
	
	public void umzug(String neueStrasse, int neueNummer, int neuePostleitzahl, String neuerWohnort)
	{
		this.adresse = new Adresse(neueStrasse, neueNummer, neuePostleitzahl, neuerWohnort);
	}
	```

Der Aufruf in der `main()`-Methode könnte dann so aussehen:

```java
public static void main(String[] args)
{
	Adresse adresse1 = new Adresse("Wilhelminenhofstr.", 75, 12459, "Berlin");			
	Adresse adresse2 = new Adresse("Treskowallee", 8, 10318, "Berlin");	
	
	Person maria = new Person("Musterfrau", "Maria", adresse1);	
	System.out.println(maria.getAdresseString());
	maria.umzug(adresse2);
	System.out.println(maria.getAdresseString());
	maria.umzug("Rudower Chaussee", 25, 12489, "Berlin");
	System.out.println(maria.getAdresseString());
}
```

mit folgender Ausgabe:

```bash
Wilhelminenhofstr. 75 in 12459 Berlin
Treskowallee 8 in 10318 Berlin
Rudower Chaussee 25 in 12489 Berlin
```

### Objekterzeugende Methoden mit Objekt als Rückgabe

Wir betrachten zur Wiederholung erneut die Klasse `Point`. Wir erinnern uns: ein `Point` bestand aus einer `x`- und einer `y`-Koordinate. Wir hatten verschiedene Objektmethoden für `Point` erstellt - siehe [hier](objekte1.md#eine-weiterer-datentyp-point). 

Angenommen, wir wollen zwei Punkte addieren - z.B. ein `Point p1` und ein `Point p2`. Die Idee dabei ist, dass die Summe der beiden `x`-Werte (`p1.x + p2.x`) einen neuen `x`-Wert und die Summe der beiden `y`-Werte (`p1.y + p2.y`) einen neuen `y`-Wert ergibt. 

Wir starten einen ersten Versuch und implementieren eine `add()`-Methode wie folgt:

```java
public void add(Point p)
{
	this.x = this.x + p.x;
	this.y = this.y + p.y;
}
```  

Der Aufruf in einer `Testklasse` mit:

```java
Point p1 = new Point(1, 2);
Point p2 = new Point(2, 4);

p1.print();
p1.add(p2);
p1.print();
```

führt zu folgender Ausgabe:

```bash
[ x=1, y=2 ]
[ x=3, y=6 ]
```

Das heißt, durch die Addition mit `p2` hat sich das `p1`-Objekt geändert. Die Frage ist, ob das beabsichtigt ist und eine eindeutige Antwort *ja* oder *nein* kann hier nicht gegeben werden. Es ist nicht ganz klar, ob sich das aufrufende Objekt selbst verändern sollte, wenn es mit einem anderen `Point` addiert wird. Insbesondere macht es einen Unterschied, ob wir `p1.add(p2)` aufrufen oder `p2.add(p1)`. Im ersten Fall ist nach der Addition `p1 -> [ x=3, y=6 ]` und `p2 -> [ x=2, y=4 ]`. Im zweiten Fall ist nach der Addition `p1 -> [ x=1, y=2 ]` und `p2 -> [ x=3, y=6 ]`. Wir erreichen also einen anderen Gesamtzustand des Systems. 

Es spricht Vieles dafür, die Implementierung zu ändern und die beiden sich addierenden Punkte unverändert zu lassen und stattdessen einen neuen `Point` zu erzeugen:

```java
public Point add(Point p)
{
	int newX = this.x + p.x;
	int newY = this.y + p.y;
	return new Point(newX, newY);
}
```

Das heißt, wir ermitteln erneut die Summen `this.x + p.x` bzw. `this.y + p.y`, doch anstelle mit diesen Summen das aufrufende Objekt zu ändern, wird ein neues `Point`-Objekt erstellt. Wenn man sich nun den Gesamtzustand des gesamten Systems nach der Addition von `p1` und `p2` anschaut, dann ist es egal, ob wir `p1.add(p2)` oder ob wir `p2.add(p1)` aufgerufen haben. Wir haben nach der Addition drei Point-Objekte mit den Werten `p1 -> [ x=1, y=2 ]`, `p2 -> [ x=2, y=4 ]` und ein neues `Point`-Objekt mit `[ x=3, y=6 ]`.

Obiges Beispiel aus der Testklasse würde dann so aussehen:

```java
Point p1 = new Point(1, 2);
Point p2 = new Point(2, 4);

p1.print();
Point p3 = p1.add(p2);	// kann auch p2.add(p1), ist egal
p3.print();
```

mit der Ausgabe

```bash
[ x=1, y=2 ]
[ x=3, y=6 ]
```

Wesentlichster Unterschied zur ersten Variante ist, dass sich weder `p1` noch `p2` durch die Addition geändert haben. Wenn wir das Ziel verfolgen, möglichst unveränderliche Objekte zu erzeugen, dann ist die zweite Lösung auf jeden Fall die bessere. So oder so haben wir eine Methode kennengelernt, in der ein Objekt der Klasse erzeugt und dieses Objekt zurückgegeben wird. Solche Objekte kommen nicht selten vor - und nun kennen wir ein Beispiel. Weitere Beispiele werden wir in der Aufgabe *Bruch* erzeugen.  


!!! success 
	Wir haben eigene Datentypen in der Definition eigener Datentypen verwendet. Wir haben das Schlüsselwort `this` kennengerlernt, mit dem wir innerhalb der Klasse das aufrufende Objekt referenzieren können. Wir haben das Überladen von Methoden betrachtet und Konstruktoren in Klassen mehrfach überladen. Das Überladen von Methoden lässt sich auf alle Methoden anwenden. Darüber hinaus haben wir Methoden erstellt, in denen Objekte erzeugt werden. Zuletzt gibt eine solche Methode das von ihr erzeugte Objekt auch zurück. 



