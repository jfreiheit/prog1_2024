# Clean Code

!!! quote "Robert C. Martin"
    *"Any fool can write code that a computer can understand. Good programmers write code that humans can understand."*

Wenn Sie ein Programm schreiben, ist Ihr erstes Ziel, dass es korrekt läuft. Aber das allein reicht nicht: Code wird nach dem Schreiben viel häufiger **gelesen** als geschrieben – von Ihnen selbst in drei Monaten, von Kommilitonen, von Kolleginnen und Kollegen, von Prüfenden. Unter *Clean Code* versteht man Programmcode, der nicht nur funktioniert, sondern auch **klar, verständlich und pflegbar** ist.

Der Begriff wurde vor allem durch das Buch *Clean Code* von [Robert C. Martin](https://de.wikipedia.org/wiki/Robert_Cecil_Martin) geprägt. Die Prinzipien darin sind heute ein zentraler Bestandteil professioneller Softwareentwicklung.

!!! info "Warum Clean Code von Anfang an?"
    Schlechte Gewohnheiten beim Programmieren sind schwer wieder loszuwerden. Wer von Anfang an auf verständlichen Code achtet, spart sich später viel Zeit – beim Debuggen, beim Erweitern und beim Zusammenarbeiten.

---

## Bezeichner

Ein **Bezeichner** ist jeder Name, den Sie selbst vergeben: für Variablen, Methoden, Klassen, Konstanten und Pakete. Gute Bezeichner sind der wichtigste Beitrag zu lesbarem Code.

### Allgemeine Regeln

- **Variablen und Parameter** → Substantive, die den Inhalt beschreiben
- **Methoden** → Verben oder Verb-Substantiv-Kombinationen
- **Klassen** → Substantive im Singular
- **Konstanten** → `GROSSBUCHSTABEN_MIT_UNTERSTRICH`
- **Pakete** → komplett in Kleinbuchstaben

### Länge ist eine Tugend

Ein häufiger Anfängerfehler ist, Bezeichner zu kurz zu wählen. Es gibt keinen Grund für Kürze – moderne IDEs ergänzen Namen automatisch. Ein langer, sprechender Name ist fast immer besser als ein kurzer, kryptischer.

=== "schlecht"
    ```java linenums="1"
    int n;
    double x;
    boolean flag;
    String s;

    void calc(int a, int b) { ... }
    ```

=== "besser"
    ```java linenums="1"
    int studentCount;
    double averageGrade;
    boolean isEnrolled;
    String firstName;

    void calculateSum(int firstSummand, int secondSummand) { ... }
    ```

### Booleans wie Fragen formulieren

Booleans drücken einen Wahrheitswert aus. Wenn ihr Name wie eine Ja/Nein-Frage klingt, ist der Code besonders lesbar:

=== "schlecht"
    ```java
    boolean active;
    boolean data;
    boolean check;
    ```

=== "besser"
    ```java
    boolean isActive;
    boolean hasData;
    boolean isPrimeNumber;
    ```

### Laufvariablen in Schleifen

Die klassischen Bezeichner `i`, `j`, `k` in `for`-Schleifen sind zwar weit verbreitet, aber oft irreführend. Sprechende Namen machen den Code sofort verständlicher:

=== "schlecht"
    ```java linenums="1"
    for(int i = 0; i < matrix.length; i++) {
        for(int j = 0; j < matrix[i].length; j++) {
            System.out.print(matrix[i][j] + " ");
        }
    }
    ```

=== "besser"
    ```java linenums="1"
    for(int row = 0; row < matrix.length; row++) {
        for(int col = 0; col < matrix[row].length; col++) {
            System.out.print(matrix[row][col] + " ");
        }
    }
    ```

### Kein Typ im Bezeichner

Früher war es üblich, den Typ in den Variablennamen zu kodieren (*Ungarische Notation*, z.B. `strName`, `iCount`). Das ist heute überholt – der Typ ist in Java bereits in der Deklaration sichtbar.

=== "schlecht"
    ```java
    String strName;
    int iCount;
    boolean bIsValid;
    ```

=== "besser"
    ```java
    String name;
    int count;
    boolean isValid;
    ```

!!! question "Übung Bezeichner"
    Welche der folgenden Bezeichner sind gut gewählt, welche nicht? Begründen Sie und benennen Sie die schlechten um:
    `d`, `numberOfPassedStudents`, `temp2`, `calculateCircleArea`, `FLAG`, `x1`, `isLeapYear`, `data`

---

## Magic Numbers vermeiden

Als *Magic Numbers* bezeichnet man numerische (oder andere) Werte, die direkt im Code stehen, ohne zu erklären, was sie bedeuten. Sie machen Code schwer lesbar und fehleranfällig – wenn sich der Wert ändert, muss man ihn an jeder Stelle suchen und ersetzen.

=== "schlecht"
    ```java linenums="1"
    if(age >= 18) {
        System.out.println("Volljährig");
    }

    double tax = price * 0.19;

    if(password.length() < 8) {
        System.out.println("Passwort zu kurz");
    }
    ```

=== "besser"
    ```java linenums="1"
    final int LEGAL_AGE        = 18;
    final double VAT_RATE      = 0.19;
    final int MIN_PASSWORD_LEN = 8;

    if(age >= LEGAL_AGE) {
        System.out.println("Volljährig");
    }

    double tax = price * VAT_RATE;

    if(password.length() < MIN_PASSWORD_LEN) {
        System.out.println("Passwort zu kurz");
    }
    ```

Konstanten werden in Java mit dem Schlüsselwort `final` deklariert. In Klassen werden sie oft zusätzlich als `static` deklariert, damit sie zur Klasse gehören und nicht zu einem bestimmten Objekt.

!!! info "Gilt auch für Strings"
    Magic Numbers sind nicht nur Zahlen. Auch hart kodierte Texte, die mehrfach verwendet werden, sollten als Konstanten definiert werden:
    ```java
    // schlecht
    System.out.println("Fehler: Eingabe ungültig");
    logger.log("Fehler: Eingabe ungültig");

    // besser
    final String ERROR_INVALID_INPUT = "Fehler: Eingabe ungültig";
    System.out.println(ERROR_INVALID_INPUT);
    logger.log(ERROR_INVALID_INPUT);
    ```

---

## Kommentare

Es klingt kontraintuitiv, aber: **zu viele Kommentare können Code schlechter lesbar machen.** Ein Kommentar, der nur wiederholt, was der Code ohnehin sagt, ist Lärm. Schlimmer noch: Kommentare veralten, werden vergessen zu aktualisieren und enthalten dann falsche Informationen.

### Kommentare, die man nicht braucht

=== "schlecht"
    ```java linenums="1"
    int counter = 0;   // Zähler auf null setzen

    // über das Array iterieren
    for(int index = 0; index < grades.length; index++) {
        // wenn Note bestanden
        if(grades[index] >= 4.0) {
            counter++;   // Zähler erhöhen
        }
    }
    // Ergebnis ausgeben
    System.out.println(counter);
    ```

=== "besser"
    ```java linenums="1"
    int passedCount = 0;

    for(double grade : grades) {
        if(isPassing(grade)) {
            passedCount++;
        }
    }
    System.out.println(passedCount);
    ```

Der "bessere" Code braucht keine einzige Kommentarzeile – die Bezeichner und die ausgelagerte Methode `isPassing()` machen ihn selbsterklärend.

### Wann sind Kommentare sinnvoll?

Kommentare sind dann wertvoll, wenn sie das **Warum** erklären – also den Hintergrund, den man dem Code nicht ansehen kann:

```java linenums="1"
// Division durch 2 statt durch pi, da die Formel für Halbkreise gilt
double area = radius * radius / 2;

// Wir prüfen explizit auf null, weil die Datenbank manchmal leere Einträge liefert
if(result == null) {
    return defaultValue;
}
```

### Was immer sinnvoll ist: JavaDoc

Für öffentliche Methoden und Klassen sind [JavaDoc-Kommentare](javadoc.md) stets sinnvoll. Sie beschreiben den Zweck, die Parameter und den Rückgabewert – das ist Dokumentation, kein Lärm.

```java linenums="1"
/**
 * Berechnet den Notendurchschnitt aller übergebenen Noten.
 *
 * @param grades Array mit Noten (1.0 bis 5.0)
 * @return Durchschnittsnote, oder 0.0 wenn das Array leer ist
 */
public double calculateAverage(double[] grades) {
    ...
}
```

!!! question "Übung Kommentare"
    Lesen Sie folgenden Code und entscheiden Sie für jeden Kommentar: Sinnvoll behalten, oder besser entfernen/den Code stattdessen verbessern?
    ```java
    // Student-Klasse
    public class Student {

        // Name des Studenten
        String name;

        // Prüft ob bestanden
        // Gibt true zurück wenn Note kleiner gleich 4
        // gibt false zurück wenn Note größer 4
        boolean passed(double grade) {
            // Vergleich
            if(grade <= 4.0) {
                return true;   // bestanden
            } else {
                return false;  // nicht bestanden
            }
        }
    }
    ```

---

## Methoden

Methoden sind das wichtigste Werkzeug für sauberen Code. Die folgenden Prinzipien helfen dabei, Methoden gut zu gestalten.

### Eine Methode – eine Aufgabe (SRP)

Das *Single Responsibility Principle* gilt nicht nur für Klassen, sondern besonders deutlich für Methoden: **Eine Methode sollte genau eine Sache tun.** Wenn Sie eine Methode mit „und" beschreiben müssen, ist sie zu groß.

=== "schlecht"
    ```java linenums="1"
    // Diese Methode liest Eingabe, berechnet UND gibt aus – zu viel!
    void processAndPrintStudentResult(String name, double[] grades) {
        double sum = 0;
        for(double grade : grades) {
            sum += grade;
        }
        double average = sum / grades.length;

        System.out.println("Student: " + name);
        System.out.println("Durchschnitt: " + average);
        if(average <= 4.0) {
            System.out.println("Bestanden!");
        } else {
            System.out.println("Nicht bestanden.");
        }
    }
    ```

=== "besser"
    ```java linenums="1"
    double calculateAverage(double[] grades) {
        double sum = 0;
        for(double grade : grades) {
            sum += grade;
        }
        return sum / grades.length;
    }

    boolean isPassing(double average) {
        return average <= 4.0;
    }

    void printResult(String name, double average) {
        System.out.println("Student: " + name);
        System.out.println("Durchschnitt: " + average);
        System.out.println(isPassing(average) ? "Bestanden!" : "Nicht bestanden.");
    }
    ```

Drei kleine Methoden sind viel besser als eine große: jede ist einzeln testbar, wiederverwendbar und verständlich.

### DRY – Don't Repeat Yourself

*Don't Repeat Yourself* bedeutet: **Jede Information (jede Logik) sollte im Code genau einmal vorkommen.** Wenn Sie Code kopieren und einfügen, ist das fast immer ein Zeichen, dass Sie eine Methode brauchen.

=== "schlecht"
    ```java linenums="1"
    // Dreimal der gleiche Berechnungsblock, nur mit anderen Werten
    double price1 = 29.99;
    double tax1 = price1 * 0.19;
    System.out.println("Preis: " + price1 + ", MwSt: " + tax1);

    double price2 = 49.99;
    double tax2 = price2 * 0.19;
    System.out.println("Preis: " + price2 + ", MwSt: " + tax2);

    double price3 = 9.99;
    double tax3 = price3 * 0.19;
    System.out.println("Preis: " + price3 + ", MwSt: " + tax3);
    ```

=== "besser"
    ```java linenums="1"
    final double VAT_RATE = 0.19;

    void printPriceWithTax(double price) {
        double tax = price * VAT_RATE;
        System.out.println("Preis: " + price + ", MwSt: " + tax);
    }

    // Aufruf:
    printPriceWithTax(29.99);
    printPriceWithTax(49.99);
    printPriceWithTax(9.99);
    ```

!!! info "Warum DRY so wichtig ist"
    Angenommen, der Mehrwertsteuersatz ändert sich von 19% auf 21%. Im „schlechten" Beispiel müssen Sie die `0.19` an drei Stellen suchen und ändern – und könnten eine vergessen. Im „besseren" Beispiel ändern Sie eine einzige Zeile.

### Komplexe Bedingungen auslagern

Lange `if`-Bedingungen mit mehreren logischen Operatoren sind schwer zu lesen. Eine eigene Methode mit einem sprechenden Namen macht den Code sofort klarer:

=== "schlecht"
    ```java linenums="1"
    if(age >= 18 && hasValidID && !isBlacklisted && membershipYears >= 1) {
        grantAccess();
    }
    ```

=== "besser"
    ```java linenums="1"
    boolean isEligibleForAccess(int age, boolean hasValidID,
                                boolean isBlacklisted, int membershipYears) {
        return age >= LEGAL_AGE
            && hasValidID
            && !isBlacklisted
            && membershipYears >= MIN_MEMBERSHIP_YEARS;
    }

    if(isEligibleForAccess(age, hasValidID, isBlacklisted, membershipYears)) {
        grantAccess();
    }
    ```

### Parameterzahl begrenzen

Je mehr Parameter eine Methode hat, desto schwerer ist sie zu verstehen und aufzurufen. Als Faustregel gilt:

- **0–2 Parameter**: gut
- **3 Parameter**: akzeptabel, aber hinterfragen
- **4+ Parameter**: fast immer ein Zeichen, dass ein Objekt übergeben werden sollte

=== "schlecht"
    ```java
    void createStudent(String firstName, String lastName,
                       int age, String email, double gpa) { ... }
    ```

=== "besser"
    ```java
    // Die Daten gehören zusammen – ein Objekt ist sinnvoller
    void createStudent(Student student) { ... }
    ```

---

## Formatierung

Konsistente Formatierung macht Code schneller lesbar. In einem Team sollte sich jeder an dieselben Regeln halten. Die meisten IDEs (Eclipse, IntelliJ) können Code automatisch formatieren.

### Einrückung

Verwenden Sie **konsistent** entweder Leerzeichen oder Tabs – niemals beides gemischt. In Java ist 4 Leerzeichen pro Einrückungsebene der verbreitete Standard.

### Klammern

In Java ist der *K&R-Stil* üblich: Die öffnende geschweifte Klammer `{` steht am Ende der vorherigen Zeile, die schließende `}` auf einer eigenen Zeile:

```java linenums="1"
public void printHello() {
    System.out.println("Hallo!");
}
```

### Immer geschweifte Klammern bei `if`

Auch wenn eine `if`-Bedingung nur eine einzige Anweisung hat, sollten Sie immer `{}`-Blöcke verwenden. Das Weglassen hat schon zu ernsthaften Softwarefehlern geführt:

=== "gefährlich und falsch"
    ```java linenums="1"
    if(error)
        shutdown();  // Das sieht aus wie ein Block – ist aber keiner!
        return;      // Diese Zeile wird IMMER ausgeführt, egal ob error true ist
    ```

=== "sicher und richtig"
    ```java linenums="1"
    if(error) {
        shutdown();
        return;
    }
    ```

!!! info "Der Apple-SSL-Bug"
    2014 enthielt Apples SSL-Implementierung genau diesen Fehler: Ein versehentlich doppeltes `goto fail;` ohne Klammern führte dazu, dass Sicherheitszertifikate immer als gültig akzeptiert wurden. Mehr dazu im [Selektion-Kapitel](selektion.md#if-else).

### Leerzeilen und Zeilenlänge

- Trennen Sie logische Abschnitte innerhalb einer Methode durch eine Leerzeile.
- Halten Sie Zeilen auf ca. **80–120 Zeichen** – längere Zeilen müssen beim Lesen gescrollt werden.
- Halten Sie Methoden kurz: Eine Methode, die auf einen Bildschirm passt (ca. 20–30 Zeilen), ist leichter zu verstehen als eine, die über mehrere Seiten geht.

---

## SOLID Design-Prinzipien

Nachdem [Robert C. Martin](https://de.wikipedia.org/wiki/Robert_Cecil_Martin) Design-Prinzipien für die Softwareentwicklung zusammengetragen hatte, wurden diese unter dem Akronym **SOLID** zusammengefasst:

| Buchstabe | Prinzip | Kurzbeschreibung |
|-----------|---------|-----------------|
| **S** | Single Responsibility Principle | Eine Klasse hat genau einen Grund zur Änderung |
| **O** | Open/Closed Principle | Offen für Erweiterung, geschlossen für Änderung |
| **L** | Liskov Substitution Principle | Kindklassen müssen Elternklassen ersetzen können |
| **I** | Interface Segregation Principle | Keine Abhängigkeit von nicht verwendeten Methoden |
| **D** | Dependency Inversion Principle | Abhängigkeiten zeigen auf Abstraktionen |

### Single Responsibility Principle (SRP)

> *A class should have only one reason to change.* – Robert C. Martin

Eine Klasse soll genau **eine Verantwortung** haben. Wenn mehrere unabhängige Konzepte in einer Klasse vermischt werden, wird sie schwer zu verstehen, zu testen und zu ändern.

=== "schlecht"
    ```java linenums="1"
    // Diese Klasse ist für Studentendaten, Dateiexport UND E-Mail zuständig – zu viel!
    public class Student {
        String name;
        double[] grades;

        double calculateAverage() { ... }

        void saveToFile(String filename) {
            // Datei schreiben ...
        }

        void sendGradeEmail(String recipient) {
            // E-Mail versenden ...
        }
    }
    ```

=== "besser"
    ```java linenums="1"
    public class Student {
        String name;
        double[] grades;

        double calculateAverage() { ... }
    }

    public class StudentExporter {
        void saveToFile(Student student, String filename) { ... }
    }

    public class GradeNotifier {
        void sendGradeEmail(Student student, String recipient) { ... }
    }
    ```

Jetzt hat jede Klasse genau eine Aufgabe. Wenn sich das E-Mail-System ändert, muss nur `GradeNotifier` angepasst werden – `Student` und `StudentExporter` bleiben unberührt.

### Open/Closed Principle (OCP)

> *Software entities should be open for extension, but closed for modification.*

Eine Klasse soll so gestaltet sein, dass man ihr **neues Verhalten hinzufügen** kann (offen für Erweiterung), **ohne bestehenden Code zu ändern** (geschlossen für Modifikation). In Java erreicht man das häufig durch [Vererbung](vererbung.md).

=== "schlecht"
    ```java linenums="1"
    // Jede neue Form erfordert eine Änderung dieser Methode!
    double calculateArea(Object shape) {
        if(shape instanceof Rectangle) {
            Rectangle r = (Rectangle) shape;
            return r.width * r.height;
        } else if(shape instanceof Circle) {
            Circle c = (Circle) shape;
            return Math.PI * c.radius * c.radius;
        }
        // Beim Hinzufügen eines Dreiecks muss diese Methode geändert werden...
        return 0;
    }
    ```

=== "besser"
    ```java linenums="1"
    // Jede Form implementiert ihre eigene Berechnung – keine zentrale Änderung nötig
    public class Shape {
        double calculateArea() { return 0; }
    }

    public class Rectangle extends Shape {
        double width, height;
        double calculateArea() { return width * height; }
    }

    public class Circle extends Shape {
        double radius;
        double calculateArea() { return Math.PI * radius * radius; }
    }

    public class Triangle extends Shape {
        double base, height;
        double calculateArea() { return 0.5 * base * height; }
    }
    ```

Ein neues `Triangle` hinzuzufügen erfordert keine Änderung an vorhandenem Code.

### Liskov Substitution Principle (LSP)

> *If S is a subtype of T, then objects of type T may be replaced by objects of type S without altering the correctness of the program.*

Einfach gesagt: **Überall, wo ein Objekt der Elternklasse verwendet wird, muss auch ein Objekt der Kindklasse funktionieren** – ohne dass das Programm falsch läuft oder Ausnahmen geworfen werden müssen.

Ein klassisches Gegenbeispiel ist das Rechteck/Quadrat-Problem:

```java linenums="1"
public class Rectangle {
    protected double width;
    protected double height;

    public void setWidth(double width)   { this.width = width; }
    public void setHeight(double height) { this.height = height; }
    public double calculateArea()        { return width * height; }
}

// Verletzt LSP: Ein Quadrat muss width == height erzwingen,
// was die Semantik von setWidth/setHeight bricht.
public class Square extends Rectangle {
    public void setWidth(double side) {
        this.width  = side;
        this.height = side;  // erzwingt Gleichheit – unerwartet für Aufrufer von Rectangle!
    }
    public void setHeight(double side) {
        this.width  = side;
        this.height = side;
    }
}
```

Code, der `Rectangle` erwartet und `setWidth(5); setHeight(3);` aufruft, bekommt bei einem `Square` die Fläche `9` statt `15` – das Verhalten ist überraschend und verletzt LSP. Die Lösung: `Square` und `Rectangle` sollten nicht in einer Vererbungsbeziehung stehen, sondern beide von einer gemeinsamen Elternklasse `Shape` erben.

### Interface Segregation Principle (ISP) und Dependency Inversion Principle (DIP)

Diese beiden Prinzipien werden relevant, sobald Sie mit *Interfaces* (Java-Schnittstellen) und komplexeren Abhängigkeiten zwischen Klassen arbeiten. Sie werden diese Konzepte in **Programmieren 2** und **Software Engineering** vertiefen. Kurz zusammengefasst:

- **ISP**: Eine Klasse sollte nur die Methoden implementieren müssen, die sie auch wirklich nutzt. Statt eines großen „Alles-kann"-Interfaces lieber mehrere kleine, spezifische Interfaces.
- **DIP**: Klassen sollten von Abstraktionen (Interfaces, abstrakten Klassen) abhängen, nicht von konkreten Implementierungen. Das macht Code flexibler und leichter testbar.

---

## Übungen

??? note "Übung 1 – Bezeichner verbessern"
    Benennen Sie alle Bezeichner im folgenden Code so um, dass der Code ohne Kommentare verständlich ist. Entfernen Sie danach alle Kommentare.

    ```java linenums="1"
    // Methode zur Berechnung
    double m(double[] d) {
        double s = 0;       // Summe
        int c = 0;          // Zähler
        for(int i = 0; i < d.length; i++) {
            if(d[i] >= 0) { // nur positive Werte
                s += d[i];
                c++;
            }
        }
        if(c == 0) return 0; // kein Element vorhanden
        return s / c;        // Durchschnitt zurückgeben
    }
    ```

??? note "Übung 2 – Magic Numbers eliminieren"
    Welche Magic Numbers finden Sie im folgenden Code? Ersetzen Sie sie durch benannte Konstanten.

    ```java linenums="1"
    double calculateShippingCost(double weight, double distance) {
        if(weight > 30) {
            return -1;
        }
        double cost = weight * 0.5 + distance * 0.02;
        if(cost < 4.99) {
            cost = 4.99;
        }
        return cost;
    }

    boolean isValidPassword(String password) {
        return password.length() >= 8
            && password.length() <= 64;
    }
    ```

??? note "Übung 3 – Kommentare aufräumen"
    Entscheiden Sie für jeden Kommentar im folgenden Code: entfernen, behalten oder den Code so umschreiben, dass der Kommentar überflüssig wird?

    ```java linenums="1"
    public class BankAccount {

        double balance; // Kontostand

        // Einzahlen
        void deposit(double amount) {
            balance += amount; // zum Kontostand addieren
        }

        // Prüft ob Betrag abgehoben werden kann
        // Gibt true zurück wenn Betrag <= Kontostand
        boolean canWithdraw(double amount) {
            if(amount <= balance) { // Vergleich
                return true;
            }
            return false;
        }

        // Berechne Zinsen (1.5% pro Jahr, wird monatlich gutgeschrieben,
        // aber nur wenn Kontostand über 100 Euro, wegen interner Regelung vom 12.03.2019)
        void addMonthlyInterest() {
            if(balance > 100) {
                balance += balance * 0.015 / 12;
            }
        }
    }
    ```

??? note "Übung 4 – DRY und Methoden"
    Der folgende Code enthält Wiederholungen. Lagern Sie den gemeinsamen Code in eine oder mehrere Methoden aus.

    ```java linenums="1"
    public static void main(String[] args) {
        // Kreis mit Radius 5
        double radius1 = 5;
        double area1 = 3.14159 * radius1 * radius1;
        double perimeter1 = 2 * 3.14159 * radius1;
        System.out.println("Kreis 1: Fläche=" + area1 + ", Umfang=" + perimeter1);

        // Kreis mit Radius 3
        double radius2 = 3;
        double area2 = 3.14159 * radius2 * radius2;
        double perimeter2 = 2 * 3.14159 * radius2;
        System.out.println("Kreis 2: Fläche=" + area2 + ", Umfang=" + perimeter2);

        // Kreis mit Radius 7.5
        double radius3 = 7.5;
        double area3 = 3.14159 * radius3 * radius3;
        double perimeter3 = 2 * 3.14159 * radius3;
        System.out.println("Kreis 3: Fläche=" + area3 + ", Umfang=" + perimeter3);
    }
    ```

??? note "Übung 5 – Single Responsibility Principle"
    Die folgende Klasse `Library` verletzt das Single Responsibility Principle. Sie ist gleichzeitig für Bücherverwaltung, Ausleihe und Berichtserstellung zuständig.

    Identifizieren Sie die verschiedenen Verantwortlichkeiten und teilen Sie die Klasse in mindestens drei Klassen auf. Überlegen Sie, welche Methoden und Variablen zu welcher Klasse gehören.

    ```java linenums="1"
    public class Library {
        String[] books;
        String[] borrowedBy;   // wer hat welches Buch ausgeliehen
        int bookCount;

        void addBook(String title) { ... }
        void removeBook(String title) { ... }
        boolean isAvailable(String title) { ... }

        void borrowBook(String title, String member) { ... }
        void returnBook(String title) { ... }
        boolean hasBorrowed(String member, String title) { ... }

        void printInventoryReport() { ... }
        void printOverdueReport() { ... }
        String generateStatistics() { ... }
    }
    ```

!!! success "Zusammenfassung"
    Clean Code ist kein Luxus, sondern professionelles Handwerk. Die wichtigsten Prinzipien auf einen Blick:

    - **Bezeichner** sind lang, sprechend und ohne Abkürzungen
    - **Magic Numbers** werden durch benannte Konstanten ersetzt
    - **Kommentare** erklären das *Warum*, nicht das *Was*
    - **Methoden** tun genau eine Sache (SRP) und werden nicht kopiert (DRY)
    - **Formatierung** ist konsistent und macht Struktur sichtbar
    - **SOLID**-Prinzipien führen zu flexiblem, erweiterbarem Design
