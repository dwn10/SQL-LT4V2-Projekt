# Mini-CRUD-App | Formular zur Datenverwaltung:

`>> IMG + VIDEO <<`
<img align="left" width="30" height="30" alt="GIF" src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExZXRjd3h3enpkOGx3amV4YmN3Y3NoZXU2emVsYnhnb2FhazkwaWJrZSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/WFmjWifrj9DJ50YaXj/giphy.gif" />


<a href="https://www.instagram.com/p/C4SdRNxrtPl/"><img src="https://media.discordapp.net/attachments/1214730549969813504/1215142862778269749/18.JPG?ex=65fbacfa&is=65e937fa&hm=c17600d3ed6e21abdd34ab82cb81fee527f8169e1eae01cfc8fcb481f68ab454&=&format=webp&width=1439&height=579" style="height: 100%; width:100%;"/></a>

Mit der Anwendung können Benutzer Datensätze in einer Tabelle erstellen, bearbeiten und löschen die Tabelle im PDF-Format generieren.

### Nachfolgend präsentieren wir eine Zusammenfassung und Funktionalitäten des Codes:

## 1. Benutzerobjekt:
Ein leeres `Benutzerobjekt` wird definiert, um die Informationen des aktuellen Benutzers (ID, Name, E-Mail, Position) zu speichern.

## 2. Zustandsvariablen:
`isValid:` Gibt an, ob die Formularfelder korrekt ausgefüllt wurden (true) oder nicht (false).
`isEditing:` Gibt an, ob ein bestehender Benutzer bearbeitet wird (true) oder ein neuer erstellt wird (false).

## 3. Benutzeraktionsfunktion:
- Es wird aktiviert, wenn das Formular gesendet wird (das Ereignis „preventDefault“ verhindert die manuelle Steuerung).
- Rufen Sie die Funktion `„validateFields“` auf, um zu überprüfen, ob die Felder ausgefüllt sind.
- Wenn die Felder gültig sind:
  - Wenn es nicht bearbeitet wird `(!isEditing)`, rufen Sie die Funktion addUser auf, um einen neuen Benutzer zu erstellen.
  - Wenn es bearbeitet wird `(isEditing)`, rufen Sie die Funktion `editUser` auf, um den aktuellen Benutzer zu aktualisieren.
- Bereinigen Sie das Benutzerobjekt und die Formularfelder mit den Funktionen `cleanObj` und `cleanFields.`

## 4. addUser-Funktion:
- Erzeugt eine eindeutige Kennung für den Benutzer basierend auf der aktuellen Uhrzeit.
- Ruft die Werte der Formularfelder (Name, E-Mail, Position) ab.
- Erstellen Sie eine neue Zeile `(tr)` in der Tabelle.
- Erstellen Sie Zellen für ID, Name, E-Mail und Titel und fügen Sie sie der Zeile hinzu.
- Erstellen Sie die Schaltflächen „Bearbeiten“ und „Löschen“ für die Zeile:
- Die Schaltfläche „Bearbeiten“ ändert den Status in `isEditing`, kopiert die Benutzerdaten in die Formularfelder und aktualisiert den Schaltflächentext.
- Die Schaltfläche „Löschen“ löscht die Zeile aus der Tabelle.
- Fügen Sie die Zeile zur Tabelle hinzu.

## 5. editUser-Funktion:
- Ruft die Tabellenzeile ab, die dem aktuellen Benutzer anhand seiner ID entspricht.
- Aktualisiert den Inhalt der Zeilenzellen mit den Werten der Formularfelder.
- Ändern Sie den Text und die Klassen der Schaltfläche „Bearbeiten“, um die Erstellung eines neuen Benutzers widerzuspiegeln.

## 6. cleanObj- und cleanFields-Funktionen:
- Sie löschen das `Benutzerobjekt` bzw. die Formularfelder.

## 7. validateFields-Funktion:
- Überprüfen Sie, ob die Formularfelder leer sind.
- Wenn ein Feld leer ist, wird eine Warnung angezeigt und `isValid` auf „false“ gesetzt.
- Wenn alle Felder ausgefüllt sind, setzen Sie `isValid` auf true.

## 8. Funktion zum Generieren von PDFs:
- Wird ausgelöst, wenn auf eine Schaltfläche geklickt wird (das Ereignis `„preventDefault“` verhindert dies zur manuellen Steuerung).
- Prüft, ob die Tabelle Daten enthält. Wenn es leer ist, wird eine Warnung angezeigt und die Funktion beendet.
- Rufen Sie die Funktion `traverseTable` auf, um den Tabellentext abzurufen.
- Erstellen Sie ein PDF-Dokument mit der jsPDF-Bibliothek.
- Fügt den Tabellentext zum `PDF` hinzu und speichert ihn unter dem Namen `„myDoc.pdf“`.

## 9. TraverseTable-Funktion:
- Durchläuft die Zeilen und Spalten der Tabelle, um eine Textzeichenfolge zu erstellen, die den Inhalt der Tabelle darstellt.
- Der Text enthält Tags zum Formatieren der `Ausgabe im PDF`.
