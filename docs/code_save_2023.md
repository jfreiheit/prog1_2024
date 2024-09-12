# Code aus der Vorlesung

??? question "Vorlesung 23.10.2023 - Datentypen und Variablen"
	```java
	package vorlesungen.vorl1023;

	public class Vorlesung1023
	{
		public static void main(String[] args) 
		{
			// hier hinter koennen Sie schreiben, was Sie moechten
			
			  System.out.println("test test test"); 
			  System.out.println("test test test");
			  
			  int ganzeZahl = 0;
			  boolean wahrheitswert = true;
			  double gleitkommaZahl = 1.0;
			  char zeichen = 'a';
			  String zeichenkette = "Das ist eine Zeichenkette";
			  
			  System.out.println(zeichenkette);
			  
			  ganzeZahl = 5;
			  System.out.println(ganzeZahl);
			  
			  ganzeZahl = 9;
			  System.out.println(ganzeZahl);
			  
			  wahrheitswert = true;
			  gleitkommaZahl = 5.5;
			  
			  gleitkommaZahl = 17.56;
			  
			  double number = 1;
			  System.out.println(number);
			  
			  //int numberInt = 1.0;
			  //System.out.println(numberInt);
			  
			  System.out.println(ganzeZahl);
			  
			  ganzeZahl = ganzeZahl + 1;
			  
			  System.out.println(ganzeZahl);
			  
			  byte test = 127;
			  test = (byte) (test + 1);
			  System.out.println(test);
			 
		}

	}
	```


??? question "Vorlesung 06.11.2023 - Methoden"
	```java
	package vorlesungen.vorl1106;

	public class Vorlesung1106
	{

		public static void main(String[] args)
		{
			int a = 7;
			int b = 4;
			int c = a / b;
			int j = a % b;
			System.out.println(a + " / " + b + " = " + c + " Rest " + j);	// 1
			
			c+=7;
			System.out.println(c);
			
			double d = 7;
			double e = 4;
			double f = d / e;
			System.out.println(f);
			
			int g = 4;
			int h = 5;
			String s = g + h + d + " hallo ";
			System.out.println(s);
			
			j = 6;
			
			boolean k = a != b;
			boolean m = d > e;
			boolean n = !k || m;
			System.out.println(k);
			
			
			int summand1 = 7;
			int summand2 = 4;
			int sum = summand1 + summand2;
			System.out.println("main : " + summand1 + " + " + summand2 + " = " + sum);
			
			summand1 = 17;
			summand2 = 5;
			sum = summand1 + summand2;
			System.out.println("main : " + summand1 + " + " + summand2 + " = " + sum);
			
			summand1 = 21;
			summand2 = 3;
			sum = summand1 + summand2;
			System.out.println("main : " + summand1 + " + " + summand2 + " = " + sum);
			
			
			printSum(7,4);
			printSum(17,5);
			printSum(21,3);
			
			computeSum(11,3);
			int summe1 = computeSum(7,4);
			
			System.out.println(summe1);
			summe1 = computeSum(17,5);
			System.out.println(summe1);
			
			System.out.println("2 gerade ? : " + isEven(2));
			System.out.println("3 gerade ? : " + isEven(3));
			System.out.println("-2 gerade ? : " + isEven(-2));
			System.out.println("-3 gerade ? : " + isEven(-3));
			System.out.println("0 gerade ? : " + isEven(0));
			System.out.println("3333 gerade ? : " + isEven(3333));
			
			boolean isEven = isEven(12345);
			System.out.println(isEven);
			
			boolean isOdd = isOdd(12345);
			System.out.println(isOdd);
			
			int year = 2023;
			System.out.println("2023 false == " + isLeapYear(year));
			year = 2024;
			System.out.println("2024 true == " + isLeapYear(year));
			year = 2100;
			System.out.println("2100 false == " + isLeapYear(year));
			year = 2400;
			System.out.println("2400 true == " + isLeapYear(year));
		}
		
		public static void printSum(int summand1, int summand2)
		{
			//int summe = summand1 + summand2;
			System.out.println("printSum : " + summand1 + " + " + summand2 + " = " + (summand1 + summand2));
		}
		
		public static int computeSum(int summand1, int summand2)
		{
			int summe = summand1 + summand2;
			return summe;
		}
		
		public static boolean isEven(int number)
		{
			int rest = number % 2;
			return (rest == 0);
		}
		
		public static boolean isOdd(int number)
		{
			return !isEven(number);
		}
		
		public static boolean isLeapYear(int year)
		{
			int rest4 = year % 4;
			int rest100 = year % 100;
			int rest400 = year % 400;
			return (rest4 == 0) && ((rest100 != 0) || (rest400 == 0));
		}

	}
	```


??? question "Vorlesung 13.11.2023 - Selektion und Iteration"
	```java
	package vorlesungen.vorl1113;

	public class Vorlesung1113
	{

		public static void main(String[] args)
		{
			System.out.println();
			System.out.println("------ Selektion --------");
			System.out.println();
			
			int a = 7;
			int b = 13;
			System.out.println("a = " + a + ", b = " + b);
			
			int month = 1;
			
			if(month == 1)
			{
				System.out.println("Januar");
			}
			else
			{
				if(month == 2)
				{
					System.out.println("Februar");
				}
			}
			
			int anzahlTage = switch( month ) {
				case 1, 3, 5, 7, 8, 10, 12 -> 31; 
				case 4, 6, 9, 11 -> 30; 
				case 2 -> 28; 
				default -> 0;
			};
			
			System.out.println(anzahlTage);
			
			if( isEven(a) ) 	// kein Semikolon!!!
			{
				System.out.println("true");
				a = a - b;
			}
			else
			{
				System.out.println("false");
				b = b - a;
			}
			
			System.out.println("a = " + a + ", b = " + b);
			
			System.out.println();
			System.out.println("------ Iteration --------");
			System.out.println();
			
			int zaehler = 0;
			
			while( zaehler < 10 )
			{
				System.out.println("zaehler = " + zaehler);
				zaehler = zaehler + 1;
			}
			
			System.out.println("Schleifenende");
			
			int nr1 = 56;
			int nr2 = 48;
			
			while(nr1 != nr2)
			{
				if(nr1 > nr2)
				{
					nr1 = nr1 - nr2;
				}
				else
				{
					nr2 = nr2 - nr1;
				}
				System.out.println("nr1 = " + nr1 +" , nr2 = " + nr2);
			}
			System.out.println("ggT ist " + nr1);
			
			int n = 7;
			System.out.print(n + " ");
			
			while(n > 1)
			{
				if(isEven(n))
				{
					n = n / 2;
				}
				else
				{
					n = 3 * n + 1;
				}
				System.out.print(n + " ");
			}
			
			System.out.println();
			System.out.println("fertig");
			
			
			System.out.println();
			System.out.println("------ for-Schleife --------");
			System.out.println();
			
			printSum(3);
			printSum(13);
			printSum(30);
			System.out.println();
			printRectangle(20, 5);
			

			
		}
		
		public static void printSum(int bis)
		{
			int summe = 0;
			for(int i = 1; i < bis; i++)
			{
				summe = summe + i;
				System.out.print(i + " + ");
			}
			summe = summe + bis;
			System.out.println(bis + " = " + summe);
		}
		
		public static void printRectangle(int width, int height)
		{
			for(int rows = 0; rows < height; rows++)
			{
				for(int stars = 0; stars < width; stars++)
				{
					// System.out.println("rows =  " + rows + ", stars = " + stars);
					System.out.print("* ");
				}
				
				System.out.println();
			}
		}
		
		public static boolean isOdd(int number)
		{
			return (number % 2 != 0);
		}
		
		public static boolean isEven(int number)
		{
			return !isOdd(number);
		}

	}

	```


??? info "Vorlesung 20.11.2023 - Video"
	<iframe src="https://mediathek.htw-berlin.de/media/embed?key=b26db1af5b04a573fdf337102f2e4571&width=720&height=387&autoplay=false&controls=true&autolightsoff=false&loop=false&chapters=false&playlist=false&related=false&responsive=false&t=0&loadonclick=true&thumb=true" data-src="https://mediathek.htw-berlin.de/media/embed?key=b26db1af5b04a573fdf337102f2e4571&width=720&height=387&autoplay=false&controls=true&autolightsoff=false&loop=false&chapters=false&playlist=false&related=false&responsive=false&t=0&loadonclick=true" class="" width="720" height="387" title="Prog1_Vorlesung_2023-11-20" frameborder="0" allowfullscreen="allowfullscreen" allowtransparency="true" scrolling="no" aria-label="media embed code" style=""></iframe>


??? question "Vorlesung 20.11.2023 - Quellcode"
	```java
	package vorlesungen.vorl1120;

	public class Vorlesung1120
	{

		public static void main(String[] args)
		{
			// 5! = 1 x 2 x 3 x 4 x 5 
			// n! = n x (n-1)! fuer n >=1 
			// n! = 1 x 2 x ... x n-1 x n
			
			for(int number = 1; number <= 25; number++)
			{
				int result = fakultaet(number);
				if(result > 0)
				{
				 System.out.println(number + "! = " + result);
				} 
				else 
				{
					System.out.println(number + " : Ueberlauf !!!");
				}
			}
			

			int result = 1;
			int number = 1;
			while(result > 0)
			{
				System.out.println(number + "! = " + result);
				number++;
				result = fakultaet(number);
			}
			
			printFakultaet(16);
			
			printCharNTimes(20, '-');
			int hoehe = 20;
			for(int row = 0; row < hoehe; row++)
			{
				printCharNTimes(hoehe-row, ' ');
				printCharNTimes(row, '*');
				System.out.println();
			}
			printCharNTimes(20, '-');
			System.out.println();
			
			System.out.printf("%n |%25s| %n |%-25s| %n%n", "Hallo FIW!", "linksbuendiger String");
			System.out.printf("|%-12.2f| %n", 1234.5678);
			
			String s = String.format("%5d %-12s", 123, "Hallo");
			System.out.println(s);
			
	/*

	 
	----*
	---***
	--*****
	-*******
	*********

	Anzahl der Sterne in einer Zeile
	1 -> 1
	2 -> 3
	3 -> 5
	4 -> 7

	n -> 2n-1

	Anzahl der Leerzeichen
	hoehe - zeile (falls wir zeile mit 1 beginnen)


	*/

			System.out.printf("%n----------------------%n%n");

			hoehe = 10;
			for(int zeile = 1; zeile <= hoehe; zeile++)
			{
				for(int space = 0; space < (hoehe - zeile); space++)
				{
					System.out.print(" ");
				}
				for(int stars = 0; stars < (2 * zeile -1); stars++)
				{
					System.out.print("*");
				}
				System.out.println();
			}
			
		}
		
		public static int fakultaet(int n)
		{
			int product = 1;
			for(int factor = 1; factor <= n; factor++)
			{
				product = product * factor;
			}
			return product;
			// i = 5;	Fehler! i existiert ausserhalb der for-Schleife nicht
		}
		
		public static void printFakultaet(int n)
		{
			int product = 1;
			for(int factor = 1; factor <= n; factor++)
			{
				product = product * factor;
				//System.out.println(factor + "! = " + product);
				System.out.printf("%2d! = %,16d %n", factor, product);
			}
		}
		
		public static void printCharNTimes(int n, char c)
		{
			for(int i = 0; i < n; i++)
			{
				System.out.print(c);
			}
			//System.out.println();
		}
		
		
		

	}

	```


??? question "Vorlesung 27.11.2023 - Klassen und Objekte (Einführung)"
	=== "Vorlesung1127.java"
		```java
		package vorlesungen.vorl1127;

		public class Vorlesung1127
		{

			public static void main(String[] args)
			{
				//System.out.println("hallo   b allo".length());
				
				Adresse adresse1 = new Adresse("Treskowallee", 8, 10318, "Berlin");	// erste Objekterzeugung: new Konstruktor
				Adresse adresse2 = new Adresse("Wilhelminenhofstr.", 75, 12459, "Berlin");	// zweite Objekterzeugzung

				//System.out.println(adresse1.hausnummer);
				
				/*
				 * kein Zugriff auf die Objektvariablen ausserhalb der
				 * Klasse Adresse mehr moeglich (private)
				
				adresse1.strasse = "Treskowallee";
				adresse1.hausnummer = 8;
				adresse1.plz = 10318;
				adresse1.wohnort = "Berlin";
				
				adresse2.strasse = "Wilhelminenhofstr.";
				adresse2.hausnummer = 75;
				adresse2.plz = 12459;
				adresse2.wohnort = "Berlin";
				 */
				
				System.out.println(adresse1.getAdresse());
				System.out.println(adresse2.getAdresse());
				
				// System.out.println(getAdresse());	// Fehler! Objektmethode
				
				adresse2.strasseUmbennen("Neue Strasse");
				System.out.println(adresse2.getAdresse());
				
				adresse1.strasseUmbennen("HalloStr");
				System.out.println(adresse1.getAdresse());
				
				adresse1.printAdresse();
				adresse2.printAdresse();
				
				// ab hier Point
				
				Point p1 = new Point(3,4);
				Point p2 = new Point(2,2); 
				Point p3 = new Point();
				
				// System.out.println(p1.y);	// Fehler wegen private
				System.out.println(p1.getX());
				System.out.println(p1.getY());
				
				p1.print();
				p2.print();
				p3.print();
				
				p1.move(-1, 1);
				p1.print();
				
				
			}

		}

		```

	=== "Adresse.java"
		```java
		package vorlesungen.vorl1127;

		public class Adresse
		{
			// Objektvariablen
			private String strasse;
			private int hausnummer;
			private int plz;
			private String wohnort;
			
			// Konstruktor
			public Adresse(String str, int hausnr, int postlz, String ort)
			{
				strasse = str;
				hausnummer = hausnr;
				plz = postlz;
				wohnort = ort;
			}
			
			// Objektmethoden
			public String getAdresse() 
			{
				return strasse + " " + hausnummer + " in " + plz + " " + wohnort;
			}
			
			public void printAdresse()
			{
				System.out.println(getAdresse());
			}
			
			public void strasseUmbennen(String neueStrasse)
			{
				strasse = neueStrasse;
			}
		}

		```

	=== "Point.java"
		```java
		package vorlesungen.vorl1127;

		public class Point
		{
			// Objektvariablen
			private int x;
			private int y;
			
			public Point(int newX, int newY)
			{
				x = newX;
				y = newY;
			}
			
			public Point()
			{
				x = 0;
				y = 0;
			}
			
			public int getX()
			{
				return x;
			}
			
			public int getY()
			{
				return y;
			}
			
			public void move(int deltaX, int deltaY)
			{
				x = x + deltaX;
				y = y + deltaY;
			}
			
			public void print()
			{
				System.out.println("[ x=" + x + ", y=" + y + " ]");
			}
		}

		```


??? question "Vorlesung 04.12.2023 - Klassen und Objekte (this)"
	=== "Programmklasse.java"
		```java
		package vorlesungen.vorl1204;

		public class Programmklasse
		{

			public static void main(String[] args)
			{
				Point p1 = new Point(3,4);
				p1.print();
				Point p2 = p1.move(2, 2);
				p1.print();
				p2.print();
				
				System.out.println("p1 links von p2 ? " + p1.isLeft(p2));
				System.out.println("p2 links von p1 ? " + p2.isLeft(p1));
				p1.isLeft(p1);
				p2.isLeft(p2);
				
				Point p3 = new Point(1,2);
				p3.print();
				System.out.println("p1 links von p3 ? " + p1.isLeft(p3));
				System.out.println("p3 links von p1 ? " + p3.isLeft(p1));
				
				System.out.println("p1 links von p2 UND p3 ? " + p1.isLeft(p2,p3));
				
				Circle c1 = new Circle(2.5);
				Circle c2 = new Circle();
				c1.print();
				c2.print();
				
				Circle c3 = c1;
				System.out.println("---------- c3 ----------- ");
				c3.print();
				
				c1.setRadius(5.0);
				
				System.out.println("---------- c3 ----------- ");
				c3.print();
				
				
				
				c1.diameter();
				System.out.println("c1 groesse als c2 ? " + c1.isBigger(c2));
				
				
			}

		}
		```

	=== "Point.java"
		```java
		package vorlesungen.vorl1204;

		public class Point
		{
			// Objektvariablen
			private int x;
			private int y;
			
			public Point(int x, int y)
			{
				this.x = x;
				this.y = y;
			}
			
			public Point()
			{
				this.x = 0;
				this.y = 0;
			}
			
			public int getX()
			{
				return this.x;
			}
			
			public int getY()
			{
				return this.y;
			}
			
			public Point move(int deltaX, int deltaY)
			{
				int xNew = this.x + deltaX;
				int yNew = this.y + deltaY;
				return new Point(xNew, yNew);
			}
			
			public void print()
			{
				System.out.println("[ x=" + this.x + ", y=" + this.y + " ]");
			}
			
			public boolean isLeft(Point other)
			{
				return (this.x < other.x);
			}
			
			
			public boolean isLeft(Point o1, Point o2)
			{
				return (this.x < o1.x && this.x < o2.x);
			}
		}

		```

	=== "Circle.java"
		```java
		package vorlesungen.vorl1204;

		public class Circle
		{
			private double radius;
			
			public Circle(double radius)
			{
				this.radius = radius;
			}
			
			public Circle()
			{
				this.radius = 1.0;
			}
			
			public double diameter()
			{
				return 2.0 * this.radius;
			}
			
			public double circumference()
			{
				return Math.PI * this.diameter();
			}
			
			public double area()
			{
				return Math.PI * this.radius * this.radius;
			}
			
			public boolean isSmaller(Circle other)
			{
				return this.radius < other.radius;
			}
				
			public boolean isBigger(Circle other)
			{
				return other.isSmaller(this);
			}
			
			public void setRadius(double radius)
			{
				this.radius = radius;
			}
			
			public void print()
			{
				System.out.printf("%-15s : %6.2f %n", "Radius", this.radius);
				System.out.printf("%-15s : %6.2f %n", "Durchmesser", this.diameter());
				System.out.printf("%-15s : %6.2f %n", "Umfang", this.circumference());
				System.out.printf("%-15s : %6.2f %n", "Flaecheninhalt", this.area());
				System.out.println();
			}
		}

		```


??? question "Vorlesung 11.12.2023 - Vererbung"
	=== "Programmklasse.java"
		```java
		package vorlesungen.vorl1211;

		import vorlesungen.vorl1127.Adresse;	// bei Ihnen evtl. woanders

		public class Programmklasse
		{

			public static void main(String[] args)
			{
				
				System.out.printf("%n%n----------- Objekte in Objekten ---------------%n%n");

				Adresse wilhelminenhof = new Adresse("Wilhelminenhofstr.", 75, 12459, "Berlin");
				Adresse treskowallee = new Adresse("Treskowallee", 8, 10318, "Berlin");
				
				Person max = new Person("Max", "Maxim", wilhelminenhof);
				Person maria = new Person("Maria", "Mariam", treskowallee);
				
				
				Adresse maxAdresse = max.getAdresse();	// Aufruf von getAdresse() aus Person
				maxAdresse.printAdresse();
				max.getAdresse().printAdresse();		// Aufruf von getAdresse() aus Person
				
				System.out.println(max.getAdresse().getAdresse());
				//System.out.println(max.getAdresse());
				
				maria.getAdresse().printAdresse();
				
				max.print();
				maria.print();
				
				treskowallee.strasseUmbenennen("Neue Strasse");
				maria.print();
				
				System.out.printf("%n%n----------- Verebung ---------------%n%n");
				
				Viereck v1 = new Viereck(10,15,20,25);
				v1.print();
				// System.out.println(v1.flaecheninhalt());	// fuer Viereck nicht definiert
				
				Rechteck r1 = new Rechteck(25, 35);
				r1.print();
				System.out.println(r1.umfang());
				System.out.println(r1.a);  // leider wegen protected
				System.out.println(r1.flaecheninhalt());

			}

		}
		```

	=== "Person.java"
		```java
		package vorlesungen.vorl1211;

		import vorlesungen.vorl1127.Adresse;	// bei Ihnen evtl. woanders

		public class Person
		{
			private String vorname;
			private String nachname;
			private Adresse adresse;
			
			public Person(String vorname, String nachname, Adresse adresse)
			{
				this.vorname = vorname;
				this.nachname = nachname;
				this.adresse = adresse;
			}
			
			public Adresse getAdresse()
			{
				return this.adresse;
			}
			
			public void print()
			{
				System.out.println(this.vorname + " " + this.nachname);
				System.out.println(this.adresse.getAdresse());  // Aufruf von getAdresse() aus Adresse
			}
		}

		```

	=== "Viereck.java"
		```java
		package vorlesungen.vorl1211;

		public class Viereck
		{
			// Objektvariablen
			// 4 Seiten des Vierecks
			protected int a;
			protected int b;
			protected int c;
			protected int d;
			
			// Konstruktor
			public Viereck(int a, int b, int c, int d)
			{
				this.a = a;
				this.b = b;
				this.c = c;
				this.d = d;
			}
			
			// Objektmethoden
			public int umfang()
			{
				return this.a + this.b + this.c + this.d;
			}
			
			public String toString()
			{
				String s = String.format("Seiten : a = %2d, b = %2d, c = %d, d = %d%n", this.a, this.b, this.c, this.d); 
				s =    s + String.format("Umfang : %3d%n", this.umfang());
				return s;
			}
			
			public void print()
			{
				System.out.println(this.toString());
			}

		}

		```

	=== "Rechteck.java"
		```java
		package vorlesungen.vorl1211;

		public class Rechteck extends Viereck
		{
			public Rechteck(int laenge, int breite)
			{
				super(laenge, breite, laenge, breite);	// Aufruf des Konstruktors von Viereck
			}
			
			public int flaecheninhalt()
			{
				return this.a * this.b;
			}
			
			@Override
			public String toString()
			{
				String s = String.format("Seiten         : a = %2d, b = %2d, c = %d, d = %d%n", this.a, this.b, this.c, this.d); 
				s =    s + String.format("Umfang         : %3d%n", this.umfang());
				s =    s + String.format("Flaecheninhalt : %3d%n", this.flaecheninhalt());
				return s;
			}
		}

		```


??? question "Vorlesung 18.12.2023 - Object und Arrays Einführung"
	=== "Programmklasse.java"
		```java
		package vorlesungen.vorl1218;

		public class Programmklasse
		{
			public static int computeSum(int[] numbersArray)
			{
				int sum = 0;
				for(int index = 0; index < numbersArray.length; index++)
				{
					sum = sum + numbersArray[index];
				}
				
				return sum;
			}

			public static void main(String[] args)
			{
				
				System.out.printf("%n%n----------- Verebung ---------------%n%n");
				
				Viereck v1 = new Viereck(15, 20, 25, 30);
				System.out.println(v1.umfang());
				//System.out.println(v1.flaecheninhalt());
				v1.print();
				
				Rechteck r1 = new Rechteck(20, 30);
				System.out.println(r1.umfang());
				System.out.println(r1.flaecheninhalt());
				r1.print();
				
				Quadrat q1 = new Quadrat(35);
				System.out.println(q1.umfang());
				System.out.println(q1.flaecheninhalt());
				q1.print();

				System.out.printf("%n%n----------- Object ---------------%n%n");
				
				Viereck v2 = new Quadrat(26);	// Compilertyp von v2 ist Viereck
				v2.print();
				if(v2 instanceof Object) {
					System.out.println("v2 vom Typ Object");	// Laufzeittypen
				}
				if(v2 instanceof Viereck) {
					System.out.println("v2 vom Typ Viereck");	// Laufzeittypen
				}
				if(v2 instanceof Rechteck) {
					System.out.println("v2 vom Typ Rechteck");	// Laufzeittypen
				}
				if(v2 instanceof Quadrat) {
					System.out.println("v2 vom Typ Quadrat");	// Laufzeittypen
				}
				// v2.flaecheninhalt();
				
				Viereck v3 = new Viereck(10,11,12,13);	// Compilertyp von v3 ist Viereck
				v3.print();
				if(v3 instanceof Object) {
					System.out.println("v3 vom Typ Object");
				}
				if(v3 instanceof Viereck) {
					System.out.println("v3 vom Typ Viereck");
				}
				if(v3 instanceof Rechteck) {
					System.out.println("v3 vom Typ Rechteck");
				} else {
					System.out.println("v3 ist NICHT vom Typ Rechteck");
				}
				if(v3 instanceof Quadrat) {
					System.out.println("v3 vom Typ Quadrat");
				} else {
					System.out.println("v3 ist NICHT vom Typ Quadrat");
				}
				
				Rechteck r2 = new Rechteck(12, 12);
				Object r3 = new Quadrat(12);
				
				//Quadrat q3 = new Viereck(1,2,3,4);
				//int i1 = 5.5;
				double d1 = 5;
				Viereck v4 = new Quadrat(5);
				
				System.out.println(r2.toString());
				//r2.print();
				System.out.println(r3.toString());
				
				System.out.println(r2);


				System.out.printf("%n%n----------- Arrays ---------------%n%n");
				
				Viereck[] viereckArray = new Viereck[10];	// 10 Referenzvariablen vom Typ Viereck
				viereckArray[0] = new Viereck(1,2,3,4);
				viereckArray[1] = new Rechteck(3,7);
				viereckArray[2] = new Quadrat(5);
				viereckArray[3] = new Viereck(3,5,8,9);
				viereckArray[4] = new Viereck(1,2,3,4);
				viereckArray[5] = new Rechteck(3,7);
				viereckArray[6] = new Quadrat(4);
				viereckArray[7] = new Viereck(13,5,18,9);		
				viereckArray[8] = new Quadrat(15);
				viereckArray[9] = new Viereck(2,5,7,9);	
				
				int kleinsterUmfang = viereckArray[0].umfang();
				for(int index = 0; index < 10; index++)
				{
					if(viereckArray[index].umfang() < kleinsterUmfang)
					{
						kleinsterUmfang = viereckArray[index].umfang();
					}
				}
				System.out.println("kleinster Umfang: " + kleinsterUmfang);
				
				viereckArray[0].print();
				viereckArray[1].print();
				viereckArray[2].print();
				System.out.println("Laenge des Arrays : " + viereckArray.length);
				
				int[] quadratzahlen = new int[1000];
				for(int index = 0; index < quadratzahlen.length; index++)
				{
					quadratzahlen[index] = (index * index);
				}
				
				//zahlen.length = 11;
				
				// 0 1 4 9 16 25 36 49 64 81
				// 0 1 2 3 4  5  6  7  8  9
				
				System.out.println(quadratzahlen[8]);
				
				for(int index = 0; index < quadratzahlen.length; index++)
				{
					System.out.printf("%3d x %3d = %7d%n", index, index, quadratzahlen[index]);
				}
				
				System.out.println("Summe = " + computeSum(quadratzahlen));
				
			}

		}
		```

	=== "Viereck.java"
		```java
		package vorlesungen.vorl1218;

		public class Viereck
		{
			// Objektvariablen
			// 4 Seiten des Vierecks
			protected int a;
			protected int b;
			protected int c;
			protected int d;
			
			// Konstruktor
			public Viereck(int a, int b, int c, int d)
			{
				this.a = a;
				this.b = b;
				this.c = c;
				this.d = d;
			}
			
			// Objektmethoden
			public int umfang()
			{
				return this.a + this.b + this.c + this.d;
			}
			
			public String toString()
			{
				String s = String.format("Seiten : a = %2d, b = %2d, c = %d, d = %d%n", this.a, this.b, this.c, this.d); 
				s =    s + String.format("Umfang : %3d%n", this.umfang());
				return s;
			}
			
			public void print()
			{
				System.out.println(this.toString());
			}

		}

		```

	=== "Rechteck.java"
		```java
		package vorlesungen.vorl1218;

		public class Rechteck extends Viereck
		{
			public Rechteck(int laenge, int breite)
			{
				super(laenge, breite, laenge, breite);	// Aufruf des Konstruktors von Viereck
			}
			
			public int flaecheninhalt()
			{
				return this.a * this.b;
			}
			
			@Override
			public String toString()
			{
				String s = String.format("Seiten         : laenge = %2d, breite = %2d%n", this.a, this.b); 
				s =    s + String.format("Umfang         : %3d%n", this.umfang());
				s =    s + String.format("Flaecheninhalt : %3d%n", this.flaecheninhalt());
				return s;
			}
		}

		```

	=== "Quadrat.java"
		```java
		package vorlesungen.vorl1218;

		public class Quadrat extends Rechteck
		{
			public Quadrat(int seite)
			{
				super(seite, seite);	// Aufruf des Konstruktors von Rechteck
			}
			
			@Override
			public String toString()
			{
				String s = String.format("Seiten         : seitenlaenge = %2d%n", this.a); 
				s =    s + String.format("Umfang         : %3d%n", this.umfang());
				s =    s + String.format("Flaecheninhalt : %3d%n", this.flaecheninhalt());
				return s;
			}
		}
		```


??? info "Vorlesung 18.12.2023 - Object und Arrays Einführung - Video"
	<iframe src="https://mediathek.htw-berlin.de/media/embed?key=ae1d054e69342c0575510926be120af3&width=720&height=405&autoplay=false&controls=true&autolightsoff=false&loop=false&chapters=false&playlist=false&related=false&responsive=false&t=0&loadonclick=true&thumb=true" data-src="https://mediathek.htw-berlin.de/media/embed?key=ae1d054e69342c0575510926be120af3&width=720&height=405&autoplay=false&controls=true&autolightsoff=false&loop=false&chapters=false&playlist=false&related=false&responsive=false&t=0&loadonclick=true" class="" width="720" height="405" title="Prog1_Object_und_Arrays" frameborder="0" allowfullscreen="allowfullscreen" allowtransparency="true" scrolling="no" aria-label="media embed code" style=""></iframe>



??? question "Vorlesung 2.1.2024 - Algorithmen über Arrays"
	```java
	package vorlesungen.vorl0102;

	import java.util.Random;

	public class Vorlesung0102
	{
		
		public static void doSomething(int a)
		{
			a = 2;
		}
		
		public static void doSomething(int[] a)
		{
			System.out.println(a[0]);
			//a[0] = 2;
		}

		public static int[] createAndFillArray(int length)
		{
			int[] a = new int[length];
			
			Random r = new Random();
			
			for(int index = 0; index < a.length; index++)
			{
				a[index] = r.nextInt(6)+1;
			}
			
			return a;
		}
		
		public static void print(int[] a)
		{
			System.out.print("[ ");
			for(int index = 0; index < a.length; index++)
			{
				System.out.print(a[index]);
				if(index < a.length-1)
				{
					System.out.print(", ");
				}
			}
			System.out.println(" ]");
		}
		
		public static boolean contains(int[] a, int value)
		{
			for (int index = 0; index < a.length; index++) 
			{
				if(a[index] == value)
				{
					return true;
				}
			}
			return false;
		}
		
		public static int[] insert(int[] a, int newValue)
		{
			int[] newArray = new int[a.length + 1];
			
			for (int index = 0; index < a.length; index++) 
			{
				newArray[index] = a[index];
			}
			newArray[a.length] = newValue;
			
			return newArray;
		}
		
		public static int[] concat(int[] a, int[] b)
		{
			int[] newArray = new int[a.length + b.length];
			
			for (int index = 0; index < a.length; index++) 
			{
				newArray[index] = a[index];	
			}
			
			for (int index = 0; index < b.length; index++) 
			{
				newArray[index + a.length] = b[index];
			}
			
			return newArray;
		}
		
		public static int nrOfOccurences(int[] a, int value)
		{
			int counter = 0;
			for (int index = 0; index < a.length; index++) 
			{
				if(a[index] == value)
				{
					counter++;
				}
			}
			return counter;
		}
		
		public static int[] filter(int[] a, int value)
		{
			int[] newArray = new int[a.length - nrOfOccurences(a,value)];
			
			int indexNewArray = 0;
			for (int indexA = 0; indexA < a.length; indexA++) 
			{
				if(a[indexA] != value)
				{
					newArray[indexNewArray] = a[indexA];
					indexNewArray++;
				}
			}
			
			return newArray;
		}
		
		public static void main(String[] args)
		{
			int a = 1;
			System.out.println("a = " + a);		// 1
			doSomething(a);
			System.out.println("a = " + a);		// 1
			
			//int[] b = { 1 };
			int[] b;	// b ist null  --> b == null ist true
			b = new int[1];
			b[0] = 1;
			System.out.println("b[0] = " + b[0]);	// 1
			doSomething(b);
			//b = null; // fuehrt zu NullPointerException
			System.out.println("b[0] = " + b[0]);	// 2
			
			int[] c = createAndFillArray(11);
			print(c);
			
			int[] d = insert(c, 12);
			print(d);
			
			int[] e = concat(d,c);
			print(e);
			
			int[] f = filter(e, 5);
			print(f);
		}

	}
	```

??? info "Vorlesung 2.1.2024 - Algorithmen über Arrays - Video"
	<iframe src="https://mediathek.htw-berlin.de/media/embed?key=08795afcedcc01d5d509a47578f795b4&width=720&height=405&autoplay=false&controls=true&autolightsoff=false&loop=false&chapters=false&playlist=false&related=false&responsive=false&t=0&loadonclick=true&thumb=true" data-src="https://mediathek.htw-berlin.de/media/embed?key=08795afcedcc01d5d509a47578f795b4&width=720&height=405&autoplay=false&controls=true&autolightsoff=false&loop=false&chapters=false&playlist=false&related=false&responsive=false&t=0&loadonclick=true" class="" width="720" height="405" title="Prog1_Arrays_Algorithmen" frameborder="0" allowfullscreen="allowfullscreen" allowtransparency="true" scrolling="no" aria-label="media embed code" style=""></iframe>



??? question "Vorlesung 8.1.2024 - Sortieren von Arrays"
	```java
	package vorlesungen.vorl0108;

	import java.util.Random;

	public class Vorlesung0108
	{
		
		public static int[] createAndFillArray(int length)
		{
			int[] intArray = new int[length];
			final int NR_OF_DIFFERENT_RANDOM_NUMBERS = 10;
			
			Random r = new Random();
			for(int index=0; index<intArray.length; index++)
			{
				intArray[index] = r.nextInt(NR_OF_DIFFERENT_RANDOM_NUMBERS);
			}
			return intArray;
		}
		
		public static int[] bubblesort(int[] original)
		{
			// zunaechst Kopie von original
			int[] copy = new int[original.length];
			for (int index = 0; index < copy.length; index++) 
			{
				copy[index] = original[index];
			}
			
			//boolean sorted = false;
			// Kopie sortieren
			for (int bubble = 0; bubble < copy.length && !isSorted(copy); bubble++) 
			{
				System.out.print(bubble + " : ");
				print(copy);
				//sorted = true;
				for (int index = 0; index < copy.length-1 - bubble; index++) 
				{
					if(copy[index]>copy[index+1])
					{
						int tmp = copy[index];
						copy[index] = copy[index+1];
						copy[index+1] = tmp;
						//sorted = false;
					}
					System.out.print("  : ");
					print(copy);
				}

			}
			
			// sortierte Kopie zurueckgeben
			return copy;
		}
		
		public static boolean isSorted(int[] a)
		{
			for (int index = 0; index < a.length-1; index++) 
			{
				if(a[index] > a[index+1])
				{
					return false;
				}
			}
			return true;
		}
		
		public static int[] createAndFillArrayNoDoublets(int length)
		{
			int[] intArray = new int[length];
			print(intArray);
			final int NR_OF_DIFFERENT_RANDOM_NUMBERS = 11;
			
			Random r = new Random();
			for(int index=0; index<intArray.length; index++)
			{
				int newValue = r.nextInt(NR_OF_DIFFERENT_RANDOM_NUMBERS);
				while(contains(intArray, newValue))
				{
					newValue = r.nextInt(NR_OF_DIFFERENT_RANDOM_NUMBERS);
					System.out.print(". ");
				}
				intArray[index] = newValue;
				System.out.println(newValue);
			}
			return intArray;
		}
		
		public static void print(int[] arr)
		{
			final int BIGGEST_INDEX = arr.length-1;
			String s = "[ ";
			for (int index = 0; index < arr.length; index++) 
			{
				s += arr[index];
				if(index < BIGGEST_INDEX)
				{
					s += ", ";
				}
			}
			s += " ]";
			System.out.println(s);
		}
		
		public static boolean contains(int[] arr, int value)
		{
			for (int index = 0; index < arr.length; index++) 
			{
				if(arr[index] == value)
				{
					return true;
				}
			}
			return false;
		}


		public static void main(String[] args)
		{
			int[] a = createAndFillArray(10);
			print(a);
			
			int[] b = createAndFillArray(5);
			print(b);
			
			print(createAndFillArray(8));
			System.out.println(contains(createAndFillArray(8), 6));
			
			print(b);
			b = createAndFillArray(8);
			print(b);

			int[] c = createAndFillArrayNoDoublets(10);
			print(c);
			
			int[] sorted = bubblesort(c);
			print(sorted);
			print(c);
		}
	}
	```


??? question "Vorlesung 15.01.2024 - Power"
	=== "Vorlesung0115.java"
		```java
		package vorlesungen.vorl0115;

		public class Vorlesung0115
		{

		    public static void main(String[] args)
		    {
		    	Power p1 = new Power(3,4);
		    	p1.print();
		    	System.out.println(p1.toString() + " = " + p1.getValue());
		    	
		    	Power p2 = new Power(-3,4);
		    	System.out.println(p2.toString() + " = " + p2.getValue());
		    	
		    	Power p3 = new Power(3,0);
		    	System.out.println(p3.toString() + " = " + p3.getValue());
		    	
		    	Power p4 = new Power(3,-4);
		    	System.out.println(p4.toString() + " = " + p4.getValue());
		    	
		    	Power p5 = new Power(-3,-4);
		    	System.out.println(p5.toString() + " = " + p5.getValue());
		    	
		    	/*
		    	Power p6 = new Power(-2,7);
		    	System.out.println(p6.getValue());
		    	
		    	Power p7 = new Power(2,-1);
		    	System.out.println(p7.getValue());
		    	
		    	Power p8 = new Power(2,-2);
		    	System.out.println(p8.getValue());
		    	
		    	Power p9 = new Power(2,-3);
		    	System.out.println(p9.getValue());
		    	*/
		    	
		    	PowerOfTwo po1 = new PowerOfTwo(4);
		    	po1.print();
		    	po1.printBinary();
		    	
		    	PowerOfTwo po2 = new PowerOfTwo(-4);
		    	po2.print();
		    	po2.printBinary();
		    	
		    	PowerOfTwo po3 = new PowerOfTwo(0);
		    	po3.print();
		    	po3.printBinary();
		    	
		    	System.out.printf("%n%n----------- PowerArray ----------%n%n");
		    	PowerArray pa1 = new PowerArray(7);
		    	pa1.fillArray();
		    	pa1.print();
		    	double[] values = pa1.createArrayOfValues();
		    	for (int index = 0; index < values.length; index++) 
		    	{
					System.out.println(values[index]);
				}
		    	pa1.sort();
		    	pa1.print();
		    }
		}
		```

	=== "Power.java"
		```java
		package vorlesungen.vorl0115;

		public class Power
		{
			private int base;
			private int exp;
			
			public int getBase()
			{
				return this.base;
			}
			
			public int getExp()
			{
				return this.exp;
			}
			
			public Power(int base, int exp)
			{
				this.base = base;
				this.exp = exp;
			}
			
			public double getValue()
			{
				double result = 1.0;
				if(this.exp >= 0)
				{
					for(int i = 0; i < this.exp; i++)
					{
						result = result * this.base;
					}
				} 
				else
				{
					for(int i = 0; i > this.exp; i--)
					{
						result = result * this.base;
					}
					result = 1.0/result;
				}
				return result;
			}
			
			@Override
			public String toString()
			{
				return "(" + this.base + "," + this.exp + ")";
			}
			
			public void print()
			{
				System.out.println(this.toString());
			}
		}
		```

	=== "PowerOfTwo.java"
		```java
		package vorlesungen.vorl0115;

		public class PowerOfTwo extends Power
		{
			public PowerOfTwo(int exp)
			{
				super(2, exp);
			}
			
			public void printBinary()
			{
				if(this.getExp() >= 0)
				{
					//System.out.print("1");
					String s = "1";
					for(int i = 0; i < this.getExp(); i++)
					{
						//System.out.print(" 0");
						s += " 0";
					}
					System.out.println(s);
				}
				else
				{
					System.out.println("Zahl ist kleiner als 1.");
				}
			}
		}
		```

	=== "PowerArray.java"
		```java
		package vorlesungen.vorl0115;

		import java.util.Random;

		public class PowerArray
		{
			private Power[] p;
			
			PowerArray(int length)
			{
				this.p = new Power[length];
			}
			
			public void fillArray()
			{
				Random r = new Random();
				final int BOUND = 5;
				for (int index = 0; index < this.p.length; index++) 
				{
					int base = r.nextInt(BOUND) + 1;
					int exp = r.nextInt(BOUND) + 1;
					while(base > exp)
					{
						base = r.nextInt(BOUND) + 1;
						exp = r.nextInt(BOUND) + 1;
					}
					this.p[index] = new Power(base, exp);
				}
			}
			
			public double[] createArrayOfValues()
			{
				double[] values = new double[this.p.length];
				for (int index = 0; index < values.length; index++) 
				{
					values[index] = this.p[index].getValue();
				}
				return values;
			}
			
			public int getIndexExponent(int exponent)
			{
				final int NOT_FOUND = -1;
				for (int index = 0; index < this.p.length; index++) 
				{
					if(this.p[index].getExp() == exponent)
					{
						return index;
					}
				}
				return NOT_FOUND;
			}
			
			@Override
			public String toString()
			{
				String s = "[ ";
				
				for (int index = 0; index < this.p.length; index++) 
				{
					s += this.p[index].toString();
					if(index < this.p.length-1)
					{
						s += ", ";
					}
				}
				
				s += " ]";
				return s;
			}
			
			public void print()
			{
				System.out.println(this.toString());
			}
			
			public void sort()
			{
				for(int bubble=0; bubble < this.p.length - 1; bubble++)
				{
					for(int index = 0; index < this.p.length -1 - bubble; index++)
					{
						if((this.p[index].getValue() > this.p[index+1].getValue()) || 
							(this.p[index].getValue() == this.p[index+1].getValue() && 
							 this.p[index].getExp() > this.p[index+1].getExp()))
						{
							// beide tauschen
							Power tmp = this.p[index];
							this.p[index] = this.p[index+1];
							this.p[index+1] = tmp;
						}
					}
				}
			}
		}

		```


??? info "Vorlesung 22.1.2024 - Klausurvorbereitung - Video"
	<iframe src="https://mediathek.htw-berlin.de/media/embed?key=a73c521e1e3afa823fef8b29e47f2fff&width=720&height=405&autoplay=false&controls=true&autolightsoff=false&loop=false&chapters=false&playlist=false&related=false&responsive=false&t=0&loadonclick=true&thumb=true" data-src="https://mediathek.htw-berlin.de/media/embed?key=a73c521e1e3afa823fef8b29e47f2fff&width=720&height=405&autoplay=false&controls=true&autolightsoff=false&loop=false&chapters=false&playlist=false&related=false&responsive=false&t=0&loadonclick=true" class="" width="720" height="405" title="Prog1_Klausurvorbereitung1" frameborder="0" allowfullscreen="allowfullscreen" allowtransparency="true" scrolling="no" aria-label="media embed code" style=""></iframe>

