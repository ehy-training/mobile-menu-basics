# Mobil-Menü Grundlagen
In wenigen Schritten zum funktionierenden Mobil-Menü. 

Hier der Link zur Seite unter GitHub Pages: https://ehy-training.github.io/mobile-menu-basics/

Hier geht's zum dazugehörigen YouTube Video: https://youtu.be/6wnMtCkJHlg

---

## Schritt 1

### Allgemeiner Aufbau
Der Code besteht aus:
- Einem Header mit dem Titel der Seite.
- Einem Hauptnavigationsmenü, das aus einer Liste von Links besteht.
- Abschnitten (`section-01`, `section-02`, `section-03`), die den Inhalt der Seite bereitstellen.
- Einem Footer mit einer Lizenzinformation.

### CSS für das Layout und die Navigation

#### Allgemeine CSS-Eigenschaften:
- Header und Navigation: Es wird ein `padding-top` von 55px für den Header, die Navigation und die Abschnitte verwendet. Das stellt sicher, dass diese Elemente unterhalb des festen Burger-Icons angezeigt werden.
- Navigationslinks: Die Links in der Navigation sind standardmäßig ohne Unterstreichung formatiert. Die Farbe ist weiß, und beim Hover wird sie orange hervorgehoben.

#### Navigation für Mobilgeräte:
- Verstecktes Menü auf Mobilgeräten:
  - Das `nav.main-nav`-Element ist standardmäßig auf `display: none` gesetzt. Es wird nur dann sichtbar gemacht, wenn das Burger-Icon geklickt wird (das soll später per JavaScript geschehen).
  - Die Position des Menüs ist `fixed`, sodass es immer oben im Viewport bleibt und den restlichen Inhalt überlagert. Dies wird nützlich sein, um das Menü als Overlay für mobile Geräte anzuzeigen.
  - Die Links im Menü haben eine große Schriftgröße (`font-size: 1.5em`) und belegen die volle Breite des Bildschirms, was das Layout für mobile Geräte gut lesbar und zugänglich macht.

#### Burger-Icon:
- CSS für das Burger-Icon:
  - Das Burger-Icon besteht aus drei `div`-Elementen, die jeweils eine weiße, horizontale Linie darstellen. Die Linien sind durch einen kleinen Abstand getrennt und haben abgerundete Ecken (`border-radius: 4px`).
  - Das Icon ist fixed positioniert und bleibt daher immer sichtbar, auch wenn man nach unten scrollt. Es wird zentriert am oberen Rand der Seite angezeigt und ist nur für mobile Geräte sichtbar.

#### Desktop-Ansicht:
- Media Query für Bildschirme ab 580px:
  - In der Desktopansicht (ab 580px) wird das Menü `nav.main-nav` auf `display: block` gesetzt, was das Menü immer sichtbar macht und die Hamburger-Navigation überflüssig macht.
  - Die Links im Menü werden horizontal mit Flexbox angeordnet (`display: flex`), sodass sie sich im verfügbaren Raum gleichmäßig verteilen.
  - Das Burger-Icon wird in dieser Ansicht über `display: none` ausgeblendet.

### Abschnitte und Inhalt
Die Abschnitte sind einfach strukturiert und enthalten jeweils einen Titel (`h2`) und mehrere Absätze mit Platzhaltertexten. Die Struktur dieser Abschnitte ist für die Navigation durch das Menü wichtig, da die Links im Menü auf die verschiedenen Abschnitte verweisen.

### JavaScript (Platzhalter)
Das `<script>`-Tag enthält derzeit keine aktive Funktionalität. Hier können wir später die JavaScript-Logik implementieren, um das Menü zu öffnen und zu schließen, wenn das Burger-Icon angeklickt wird.

### Footer
Der Footer ist ein einfacher Container mit einem Copyright-Hinweis und einem (noch nicht korrekt verlinkten) Hinweis auf die GNU General Public License.

### 6. Fehlende JavaScript-Funktionalität
Da die JavaScript-Funktionalität zur Steuerung des Menüs noch fehlt, wird das Menü derzeit nicht sichtbar, wenn das Burger-Icon auf mobilen Geräten geklickt wird. Das werden wir als nächsten Schritt implementieren.

---

### Zusammenfassung der Analyse:
- Aktueller Zustand: Das Menü ist für mobile Geräte ausgeblendet und das Burger-Icon ist sichtbar. Auf größeren Bildschirmen wird das Menü standardmäßig als horizontale Navigation angezeigt.
- Fehlende Funktionalität: Die JavaScript-Logik, um das Menü bei einem Klick auf das Burger-Icon zu öffnen und zu schließen, fehlt noch.
- Layout und Design: Das Design ist gut strukturiert, und die responsive Navigation wird korrekt über Media Queries gesteuert.

### Nächster Schritt:
Hinzufügen der JavaScript Funktionalität

---

## Schritt 2

Der JavaScript-Code steuert das Verhalten des Menüs auf mobilen Geräten und passt sich an unterschiedliche Bildschirmgrößen an. Folgende Funktionen werden implementiert:

- **Event-Listener für das Burger-Icon**: 
  Der Code überwacht das **Burger-Icon** und reagiert auf Klicks. Der `click`-Event-Listener auf dem `burger-icon`-Element führt eine Funktion aus, die das Menü öffnet oder schließt, jedoch nur, wenn der Viewport kleiner als 580px ist. Dies wird durch die Überprüfung `if (window.innerWidth <= 580)` gesteuert. 
  - Wenn das Menü geschlossen ist (`display: none`), wird es geöffnet (`display: block`).
  - Zusätzlich wird bei jedem Öffnen des Menüs das `padding-top` auf **55px** gesetzt und die Links innerhalb des Menüs (`nav.main-nav a`) erhalten `display: inline-block`, um die Darstellung zu verbessern.

- **Event-Listener für Links im Menü (Mobilansicht)**:
  Der Code fügt jedem **Link** im Menü (`nav.main-nav a`) einen `click`-Event-Listener hinzu, der das Menü wieder schließt, wenn ein Link angeklickt wird, aber nur in der Mobilansicht. Dies wird durch die Bedingung `if (window.innerWidth <= 580)` gesteuert, die sicherstellt, dass diese Funktion nur auf kleinen Bildschirmen ausgeführt wird. Auf größeren Bildschirmen (über 580px) bleibt das Menü immer sichtbar.

- **Resize-Event zur Anpassung an Bildschirmgrößen**:
  Ein `resize`-Event-Listener sorgt dafür, dass das Menü korrekt auf Bildschirmgrößenänderungen reagiert. Wenn der Viewport größer als 580px wird, setzt der Code sicher, dass das Menü immer sichtbar ist (`display: block`), auch wenn es vorher durch das JavaScript ausgeblendet wurde. Zusätzlich wird in diesem Fall das `padding-top` auf **0.3em** gesetzt, um die gewünschte Darstellung im Desktop-Modus zu gewährleisten. Wenn der Viewport kleiner als 580px ist, wird das Menü wieder ausgeblendet, bis es durch das Burger-Icon geöffnet wird.

**Zusammenfassung der wichtigsten JavaScript-Komponenten**:
1. **`burger-icon` Click-Event**: Öffnet und schließt das Menü in der Mobilansicht.
2. **`nav.main-nav a` Click-Event**: Schließt das Menü automatisch, wenn ein Link angeklickt wird (nur in der Mobilansicht).
3. **`resize`-Event**: Stellt sicher, dass das Menü bei Viewports über 580px immer sichtbar ist und das korrekte `padding-top` verwendet wird.

Dieser JavaScript-Code sorgt dafür, dass das Menü in der Mobilansicht ein- und ausgeblendet wird, während es in der Desktopansicht immer sichtbar und korrekt positioniert ist.
