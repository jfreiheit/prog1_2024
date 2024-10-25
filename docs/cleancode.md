# Clean Code

#### Sinnvoller Umgang mit Kommentaren

Wirklich sinnvoll sind nur JavaDoc-Kommentare. Andere Kommentare sollten, wenn überhaupt, sehr sparsam verwendet werden. 

Erläutern Sie nicht  

- die Bedeutung einer Variablen bei der Deklaration. Das sollte durch den Namen klar sein. 
- die Bedeutung einer Bedingung. Spendieren Sie besser eine eigene Methode für diese Bedingung und geben Sie dieser Methode einen entsprechenden Namen. 
- die Bedeutung einer `for`-Schleife. Geben Sie stattdessen der Laufvariablen einen entsprechenden Namen. 
- die Bedeutung von *magic numbers*. Deklarieren Sie stattdessen Konstanten mit sprechenden Namen. 
- die Bedeutung verschachtelter Schleifen. Lagern Sie innere Schleifen besser in eigene Methoden aus und geben Sie den Methoden sprechende Namen. 

Generell wird häufig versucht, "schlechte" Programmierung durch Kommentare zu "verbessern". Ein Problem bei Kommentaren besteht darin, dass sie ebenfalls geändert werden müssen, wenn der Code geändert wird. Außerdem können Kommentare einfach falsche Informationen enthalten, nämlich dann, wenn darin Gedanken formuliert sind, die gar nicht bis zu Ende gedacht wurden. 

#### Bezeichner

- Variablennamen sollten nicht den Typ der Variable enthalten. Das ist unnötig. 
- Klassennamen sollten Substantive sein.
- Methodennamen sollten Verben enthalten.
- Ein typischer Fehler bei Bezeichnern ist, sie zu kurz zu wählen. Dafür gibt es keinen Grund! `calculateMeanValueOfAges()` ist besser als `calc`. Typisch ist es auch, Laufvariablen in `for`-Schleifen die Bezeichner `i` und `j` usw. geben. Besser sind sprechende Namen, wie z.B. `row` und `column`. 

#### Methoden

- Methoden sollten genau eine Funktion ausführen. 
- Komplexere Bedingungen (mit logischen Operatoren verknüpfte Ausdrücke) sollten in eigene Methoden ausgelagert werden, um ihnen einen sprechenden Namen zu geben.
- Die Parameter sollten zu den Methoden passen, z.B. ist `write(String)` verständlich, aber `write(boolean` nicht. 
- Methoden sollten so (kurz und knapp) geschrieben werden, dass sie wiederverwendet werden können. 
- Daten sollten möglichst nicht "hartcodiert" sein, z.B.: 

=== "schlecht"
	```java
	String getCapital(String country) {
		String capital = switch(country) {
			case "Italien" -> "Rom"; 
			case "Portugal" -> "Lissabon";
			case "Spanien" -> "Madrid";
			default -> "";
		};
		return capital;
	}
	```


=== "besser"
	```java
	Map<String, String> capitals = Map.ofEntries(
		entry("Italien","Rom"),
		entry("Portugal","Lissabon"),
		entry("Spanien", "Madrid")
	);
	
	String getCapital(String country) {
		String capital = "";
		capital = this.capitals.get(country);
		return capital;
	}
	```

### SOLID Design Prinzipien

Nachdem [Robert C. Martin](https://de.wikipedia.org/wiki/Robert_Cecil_Martin) Design-Prinzipien für die Softwareentwicklung zusammengetragen hatte ([Clean Code Literatur](https://portal.dnb.de/opac.htm?method=simpleSearch&query=114440964)), wurden diese unter dem Akronym SOLID zusammengefasst. SOLID steht für die Prinzipien:

- <b>S</b>ingle Responsibility Principle (RSP)
- <b>O</b>pen Closed Principle
- <b>L</b>iskov Substitution Principle (LSP)
- <b>I</b>nterface Segregation Principle
- <b>D</b>ependency Inversion Principle

#### Single Responsibility Principle

Diese Prinzip wird heute auch häufiger für Methoden verwendet, es bezieht sich aber auf Klassen. Im Original hat Robert C. Marting dieses Prinzip so erklärt: 

>> A class should have only one reason to change

Man kann es sich auch so merken, dass man in einer Klasse alle die Eigenschaften definieren soll, die aus einem Grund geändert werden können. Eigenschaften, die aus anderen Gründen geändert werden können, sollten in anderen Klassen definiert werden. 

Ein typischer Fall für die Missachtung des SRP besteht z.B. darin, wenn ein Spiel programmiert wird und in derselben Klasse auch die GUI für dieses Spiel. Generell sollte stets die Datenverwaltung (*Model*) von den Interaktionen (*Controller*) und der Darstellung (*View*) getrennt werden. Dafür hat sich z.B. das *Design-Pattern* *Model-View-Controller* etabliert. 