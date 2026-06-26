# Workshop: Jump'n'Run Spiel programmieren

## Los geht's! @showdialog

Willkommen! 🎮

In diesem Tutorial programmierst du dein eigenes Jump'n'Run-Spiel in Microsoft MakeCode Arcade.

Du baust dein Spiel Schritt für Schritt auf: zuerst Hintergrund und Spielfigur, dann Boden und Schwerkraft, danach Springen, Kamera, Punkte, Schießen, Gegner, Münzen, Herzen, Flagge und am Ende eine einfache Laufanimation.

Wichtig: Wenn du in einem Schritt eine **Glühbirne** siehst, kannst du darauf klicken. Dort findest du zusätzliche Hilfe mit Bildern.

Klicke auf **Weiter**, um zu starten.

## Schritt 1: Editor

Im Blöcke-Editor findest du links Kategorien wie **Szene**, **Sprites**, **Controller**, **Spiel**, **Info**, **Logik** und **Variablen**. Aus diesen Kategorien ziehst du die Blöcke in die Arbeitsfläche. Schau dir gerne zuerst alle Blöcke an, um sie später einfacher zu finden.

## Schritt 2: Der Startbereich

Auf der Arbeitsfläche gibt es den grünen Block `||loops:beim Start||`.

Alles, was in diesen Block kommt, passiert direkt beim Start des Spiels. Wir füllen diesen nach und nach von oben nach unten.

Wichtig: Erstelle keinen zweiten `beim Start`-Block. Wenn ein Schritt sagt, dass ein Block in `beim Start` gehört, ziehst du ihn unten in den zuletzt eingefügten Block

```blocks
// Alles im Block "beim Start" passiert beim Start des Spiels.
```

## Schritt 3: Hintergrundfarbe einstellen

Zuerst bekommt dein Spiel einen Himmel.

Gehe links in die Kategorie **Szene**. Ziehe den Block `||scene:setze Hintergrundfarbe auf||` in den vorhandenen Block `||loops:beim Start||`.

Klicke auf die Farbe und wähle ein helles Blau oder eine andere helle Farbe.

Tipp in der Glühbirne!

```blocks
// @highlight
scene.setBackgroundColor(9)
```

## Schritt 4: Spielfigur erstellen

Jetzt kommt dein Held ins Spiel.

Gehe in die Kategorie **Sprites**. Ziehe den Block `||sprites:setze mySprite auf Sprite vom Typ Player||` unter die Hintergrundfarbe in `||loops:beim Start||`.

Klicke auf das kleine Bild im Block. Jetzt öffnet sich der Mal-Editor.

Du hast zwei Möglichkeiten: Du kannst deine eigene Spielfigur malen oder über **Galerie** eine Figur auswählen. In der Glühbirne findest du einen Designvorschlag.

Tipp in der Glühbirne!

![Vorschlag Spielfigur](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/sprite.png)


```blocks
// @highlight
let mySprite = sprites.create(img`
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . 1 1 . . . 1 1 . . . . . .
    . . . 1 1 . . . 3 1 . . . . . .
    . . . . 1 1 1 1 1 3 . . . . . .
    . . . 1 1 f 1 1 f 1 1 . . . . .
    . . . 5 1 1 1 4 1 1 5 . . . . .
    . . . 1 1 1 1 1 1 1 1 . . . . .
    . . . . 1 1 1 1 1 1 . . . . . .
    . . . 3 3 3 3 3 3 3 3 . . . . .
    . . 1 3 3 3 3 3 3 3 3 1 . . . .
    . . . 3 3 3 3 3 3 3 3 . . . . .
    . . . 3 3 3 3 3 3 3 3 . . . . .
    . . . 3 3 3 3 3 3 3 3 . . . . .
    . . 1 1 . . . . . . 1 1 . . . .
`, SpriteKind.Player)
```

## Schritt 5: Spielfigur nach links und rechts bewegen

Jetzt soll sich deine Figur bewegen können.

Gehe in die Kategorie **Controller**. Ziehe den Block `||controller:bewege mySprite mit Knöpfen||` unter deine Spielfigur in `||loops:beim Start||`.

Klicke auf das kleine **Plus-Zeichen** am Block. Erst danach kannst du `vx` und `vy` einstellen.

Stelle ein:

- `vx = 100`
- `vy = 0`

`vx` ist die Geschwindigkeit nach links und rechts. `vy = 0` bedeutet: Die Pfeiltasten sollen die Figur nicht nach oben oder unten bewegen. Springen bauen wir später mit der A-Taste ein.

```blocks
let mySprite: Sprite = null
// @highlight
controller.moveSprite(mySprite, 100, 0)
```

## Schritt 6: Testen: Kann die Figur laufen?

Klicke auf den Play-Knopf im Simulator.

Teste kurz:

- Bewegt sich die Figur nach links?
- Bewegt sich die Figur nach rechts?
- Bleibt sie ruhig, wenn du oben oder unten drückst?

Wenn die Figur nach oben oder unten läuft, prüfe den Bewegungsblock: `vy` muss auf `0` stehen.

## Schritt 7: Tilemap-Block einfügen

Jetzt bekommt dein Spiel einen Boden.

Gehe in die Kategorie **Szene** und ziehe den Block `||scene:setze Tilemap auf||` unter den Bewegungsblock in `||loops:beim Start||`.

Klicke auf das kleine Kachelbild im Block. Dadurch öffnet sich der **Tilemap-Editor**.

Eine Tilemap ist deine Spielwelt aus kleinen Quadraten. Diese Quadrate heißen **Kacheln**. Aus Kacheln baust du Boden, Plattformen und später dein gesamtes Level.

```blocks
// @highlight
tiles.setCurrentTilemap(tilemap`Level1`)
```

## Schritt 8: Tilemap-Größe einstellen

Im Tilemap-Editor stellst du zuerst die Größe deiner Karte ein.

Stelle ein:

- Breite: `50`
- Höhe: `15`

Die Welt ist damit breiter als der Bildschirm. Keine Sorge: Später folgt die Kamera deiner Spielfigur, damit du trotzdem alles sehen kannst.

Tipp in der Glühbirne: Das Bild zeigt dir, wo du Breite und Höhe findest.

![Hinweis Breite und Höhe Tilemap einstellen](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/tilemap_breite_hoehe.png)

Die Zahl links ist die Breite. Die Zahl rechts ist die Höhe.

## Schritt 9: Erstmal nur den Boden malen

Male jetzt noch keine ganze Welt. Für den Anfang reicht ein einfacher Boden, damit die Figur nicht dauerhaft herunterfällt.

Wähle eine Boden-Kachel, zum Beispiel Gras oder Erde. Male unten im Tilemap-Editor eine durchgehende Bodenfläche.

![Vorschlag Boden-Kacheln](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/tilemap_boden_kacheln.png)

Der erste Boden muss nicht schön sein. Er muss nur dafür sorgen, dass du gleich Schwerkraft testen kannst.

## Schritt 10: Boden direkt als Wand markieren

Das ist der wichtigste Tilemap-Schritt.

Der Boden sieht jetzt zwar wie Boden aus, aber die Figur würde ohne Wand-Markierung trotzdem hindurchfallen. Deshalb muss jede Boden-Kachel als **Wand** markiert werden.

Aktiviere zuerst **Wände anzeigen**. Danach wählst du das **Wand-Werkzeug** und markierst die Boden-Kacheln als Wand.

![Funktion Wände anzeigen](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/waende_anzeigen.png)

![Hinweis Wände Zeichnen Tool](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/waende_zeichnen_tool.png)

Merke dir: Boden muss **gemalt** und zusätzlich als **Wand** markiert sein. Erst dann kann die Spielfigur darauf stehen.

## Schritt 11: Tilemap speichern

Wenn dein erster Boden fertig ist, klicke im Tilemap-Editor auf **Fertig** oder schließe den Editor.

```blocks
tiles.setCurrentTilemap(tilemap`Level1`)
```

## Schritt 12: Schwerkraft einschalten

Jetzt soll die Figur nach unten fallen und auf dem Boden stehen bleiben. Dafür bekommt sie eine **Beschleunigung nach unten**.

Gehe links in die Kategorie **Sprites**. Suche dort den Block, der so aussieht:

`setze mySprite x auf 0`

Der Block kann am Anfang auch eine andere Eigenschaft anzeigen, zum Beispiel `x`, `y`, `vx`, `vy` etc.. Diese Eigenschaft kann man über das Dropdown-Menü ändern.

Ziehe diesen Block in den vorhandenen `||loops:beim Start||`-Block, unter deine bisherigen Start-Blöcke. Erstelle keinen neuen `||loops:beim Start||`-Block.

Klicke im Block auf das Dropdown-Menü und wähle dort:

`ay (Beschleunigung y)`

Stelle danach den Zahlenwert auf:

`350`

Dann sieht der Block so aus:

`setze mySprite ay (Beschleunigung y) auf 350`

`ay` ist die Schwerkraft in unserem Spiel. Eine positive Zahl zieht die Figur nach unten.

```blocks
let mySprite: Sprite = null
// @highlight
mySprite.ay = 350
```

## Schritt 13: Spielfigur an den Start setzen

Jetzt legen wir fest, wo die Figur am Anfang auf dem Bildschirm erscheint.

Gehe in die Kategorie **Sprites**. Ziehe den Block `||sprites:setze Position von mySprite auf x y||` in `||loops:beim Start||`.

Stelle ein:

- `x = 20`
- `y = 100`

Damit startet die Figur links unten im Level.

```blocks
let mySprite: Sprite = null
// @highlight
mySprite.setPosition(20, 100)
```

## Schritt 14: Testen: Boden und Schwerkraft

Starte das Spiel kurz mit dem Play-Knopf.

Prüfe:

- Fällt die Figur nach unten?
- Bleibt sie auf dem Boden stehen?
- Kannst du nach links und rechts laufen?

Wenn die Figur durch den Boden fällt, ist fast immer die Wand-Markierung das Problem. Öffne die Tilemap nochmal und markiere den Boden als Wand.

## Schritt 15: A-Taste vorbereiten

Jetzt bauen wir den Sprung.

Gehe in die Kategorie **Controller**. Ziehe den Block `||controller:wenn A Knopf gedrückt||` frei auf die Arbeitsfläche.

Dieser Block kommt **nicht** in `||loops:beim Start||`. Er ist ein eigener Ereignis-Block. Er wird immer dann ausgeführt, wenn die A-Taste gedrückt wird.

```blocks
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
})
```

## Schritt 16: Nur springen, wenn die Figur am Boden ist

In den A-Block kommt eine Bedingung.

Die Figur darf nur springen, wenn `vy = 0` ist. Das bedeutet: Sie bewegt sich gerade nicht nach oben oder unten.

Wenn die Bedingung stimmt, setzen wir `vy` auf `-220`. Eine negative y-Geschwindigkeit bewegt die Figur nach oben.

```blocks
let mySprite: Sprite = null
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    if (mySprite.vy == 0) {
        mySprite.vy = -220
    }
})
```

## Schritt 17: Testen: Springen mit A

Starte das Spiel und drücke die A-Taste.

Prüfe:

- Springt die Figur nach oben?
- Fällt sie danach wieder auf den Boden?
- Kann sie unendlich oft in der Luft springen? Die zuvor programmierte Schwerkraft sollte das verhindern.

## Schritt 18: Spielfigur darf den Bildschirm verlassen

Unser Level wird später breiter als der sichtbare Bildschirm.

Gehe in die Kategorie **Sprites**. Ziehe den Block `||sprites:setze mySprite bleibe auf dem Display auf||` in `||loops:beim Start||`.

Stelle den Wert auf **AUS**. Dadurch darf die Figur nach rechts weiterlaufen, auch wenn der Bildschirmrand erreicht ist.

```blocks
let mySprite: Sprite = null
// @highlight
mySprite.setStayInScreen(false)
```

## Schritt 19: Kamera folgt der Spielfigur

Damit man die Figur immer sieht, soll die Kamera ihr folgen.

Gehe in die Kategorie **Szene**. Ziehe den Block `||scene:Kamera folgt Sprite||` in `||loops:beim Start||`.

Wähle `mySprite` aus. Dann bewegt sich der Bildausschnitt mit deiner Figur mit.

```blocks
let mySprite: Sprite = null
// @highlight
scene.cameraFollowSprite(mySprite)
```

## Schritt 20: Leben und Punkte einstellen

Gehe in die Kategorie **Info**.

Ziehe zwei Blöcke in `||loops:beim Start||`:

1. `||info:setze Anzahl Leben auf||` mit dem Wert `3`
2. `||info:setze Punktzahl auf||` mit dem Wert `0`

So startet jedes Spiel mit 3 Leben und 0 Punkten.

```blocks
// @highlight
info.setLife(3)
// @highlight
info.setScore(0)
```

## Schritt 21: B-Taste vorbereiten

Jetzt kommt der coole Teil: Die Figur soll schießen können.

Gehe in die Kategorie **Controller**. Ziehe den Block `||controller:wenn B Knopf gedrückt||` frei auf die Arbeitsfläche.

Dieser Block kommt **nicht** in `||loops:beim Start||`. Er wird ausgeführt, wenn die B-Taste gedrückt wird.

```blocks
controller.B.onEvent(ControllerButtonEvent.Pressed, function () {
})
```

## Schritt 22: Projektil malen und abschießen

Gehe in die Kategorie **Sprites**. Ziehe in den B-Block den Block `||sprites:setze projectile auf Projektil von mySprite||`.

Klicke auf das Bild und male ein kleines Feuer-Projektil. 

Stelle ein:

- `vx = 150`
- `vy = 0`

`vx = 150` bedeutet: Das Projektil fliegt nach rechts. `vy = 0` bedeutet: Es fliegt nicht nach oben oder unten. Wir wollen einen geraden Schuss.

Danach spielst du einen Ton ab.

```blocks
let mySprite: Sprite = null
let projectile: Sprite = null
controller.B.onEvent(ControllerButtonEvent.Pressed, function () {
    projectile = sprites.createProjectileFromSprite(img`
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . 2 . . . 2 2 2 4 4 . . . .
        . . . . . . 2 2 2 2 2 4 5 . . .
        . . . 2 2 2 2 2 2 4 2 4 4 2 . .
        . . 2 . . 2 2 2 2 2 2 2 2 5 . .
        . 2 . 2 . 2 2 2 4 2 5 4 2 . . .
        . . 2 . . 2 2 2 2 2 4 4 2 2 . .
        . . 2 . 2 . 2 2 2 2 2 2 5 . . .
        . . . . . . . . 2 . 2 . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
    `, mySprite, 150, 0)
    music.baDing.play()
})
```

## Schritt 23: Testen: Schießen mit B

Starte das Spiel und drücke die B-Taste.

Prüfe:

- Erscheint ein Projektil bei deiner Figur?
- Fliegt es nach rechts?
- Kommt ein Ton?

Wenn das Projektil nach oben oder unten fliegt, prüfe `vy = 0`.

## Schritt 24: Eigene Sprite-Arten vorbereiten

Für Münzen, Herzen und die Flagge brauchen wir eigene Sprite-Arten.

**Player**, **Enemy** und **Projectile** gibt es schon. **Coin**, **Heart** und **Flag** legst du einmalig neu an.

So geht das:

1. Öffne bei einem Sprite-Block das Dropdown-Menü, in dem zum Beispiel `Player` steht.
2. Wähle **Hinzufügen** oder **Add a new kind**.
3. Schreibe den Namen genau so: `Coin`, `Heart` oder `Flag`.

Groß- und Kleinschreibung ist wichtig. `Coin` und `coin` sind nicht dasselbe. Vermeide ä, ü, ö.

```typescript
namespace SpriteKind {
    export const Coin = SpriteKind.create()
    export const Heart = SpriteKind.create()
    export const Flag = SpriteKind.create()
}
```

## Schritt 25: Level erweitern: erst wenig, dann mehr

Jetzt kannst du deine Tilemap erweitern.

Standard für den Workshop: Male erstmal nur **1 bis 2 Plattformen** über dem Boden und markiere jede Plattform wieder als **Wand**. Teste danach direkt.

Wenn du schon schneller bist, kannst du die vollständige Welt ungefähr nach dieser Vorlage malen.

![Vorschlag vollständige Tilemap](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/tilemap_vollstaendig.png)

So sieht dieselbe Welt aus, wenn die Wände angezeigt werden:

![Vorschlag vollständige Tilemap mit Wänden](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/tilemap_vollstaendig_mit_waenden.png)

Wichtig bleibt immer: Plattformen müssen nicht nur gemalt werden. Sie müssen auch als Wand markiert werden.

## Schritt 26: Funktion für Gegner erstellen

Jetzt bauen wir einen Helfer-Block für Gegner.

Gehe links auf **Fortgeschritten**. Öffne **Funktionen** und klicke auf **Funktion erstellen**.

Nenne die Funktion genau:

`platziereGegner`

Füge zwei Parameter hinzu:

- `x` als Zahl
- `y` als Zahl

Eine Funktion ist wie ein Rezept. Du erstellst sie einmal und kannst sie später mehrfach benutzen.

```blocks
function platziereGegner (x: number, y: number) {
}
```

## Schritt 27: Gegner malen und bewegen

In die Funktion `platziereGegner` kommt ein Sprite vom Typ `Enemy`.

Male einen Gegner. Danach stellst du ein:

- Position: `x`, `y`
- `ay = 350`
- `vx = 30`
- `pralle gegen Wand = EIN`

Der Gegner bekommt also auch Schwerkraft, läuft automatisch los und prallt an Wänden ab.

![Vorschlag Enemy](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/enemy.png)

```blocks
let e: Sprite = null
function platziereGegner (x: number, y: number) {
    e = sprites.create(img`
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . . . . . . . . . . . . . .
        . . . 5 5 . . . 5 5 . . . . . .
        . . 5 f 2 5 . 5 f 2 5 . . . . .
        . . . 5 5 . . . 5 5 . . . . . .
        . . 5 5 5 5 5 5 5 5 5 5 . . . .
        . 5 2 5 5 5 5 5 5 5 5 2 5 . . .
        . 5 2 2 5 5 5 5 5 5 2 2 5 . . .
        . . 5 5 5 f f f 5 5 5 5 . . . .
        . . . 5 f 5 5 5 f 5 5 . . . . .
        . . . 5 5 5 5 5 5 5 5 . . . . .
        . . . 5 5 5 5 5 5 5 5 . . . . .
        . . 5 5 . . . . . . 5 5 . . . .
        . . . . . . . . . . . . . . . .
    `, SpriteKind.Enemy)
    e.setPosition(x, y)
    e.ay = 350
    e.vx = 30
    e.setBounceOnWall(true)
}
```

## Schritt 28: Einen Gegner platzieren

Jetzt benutzt du deine Funktion.

Gehe zu **Funktionen** und ziehe den Block `||functions:Aufruf platziereGegner||` in `||loops:beim Start||`.

Trage zum Test ein:

- `x = 128`
- `y = 96`

```blocks
platziereGegner(128, 96)
```

Wenn du später weitere Gegner möchtest, setzt du denselben Funktionsaufruf nochmal darunter und änderst nur die Positionen.

## Schritt 29: Gegner mit Projektil besiegen

Jetzt soll ein Schuss einen Gegner zerstören.

Ziehe einen neuen Overlap-Block heraus:

`Projectile` überlappt `Enemy`.

Wenn ein Schuss einen Gegner trifft:

- Gegner verschwindet mit Feuer-Effekt.
- Schuss verschwindet.
- Punktzahl steigt um 2.
- Ein Ton wird abgespielt.

```blocks
sprites.onOverlap(SpriteKind.Projectile, SpriteKind.Enemy, function (sprite, otherSprite) {
    otherSprite.destroy(effects.fire, 300)
    sprite.destroy()
    info.changeScoreBy(2)
    music.zapped.play()
})
```

## Schritt 30: Gegner von oben besiegen

Jetzt soll die Figur Gegner auch von oben besiegen können.

Ziehe einen neuen Overlap-Block heraus:

`Player` überlappt `Enemy`.

Dann prüfen wir mit einer Bedingung: Kommt die Spielfigur wirklich von oben? Wenn ja, wird der Gegner besiegt. Wenn sie den Gegner von der Seite berührt, verliert sie ein Leben.

```blocks
let mySprite: Sprite = null
sprites.onOverlap(SpriteKind.Player, SpriteKind.Enemy, function (sprite, otherSprite) {
    if (sprite.vy > 0 && sprite.bottom < otherSprite.top + 8) {
        otherSprite.destroy(effects.smiles, 300)
        sprite.vy = -120
        info.changeScoreBy(2)
        music.zapped.play()
    } else {
        sprite.startEffect(effects.fire, 500)
        info.changeLifeBy(-1)
        sprite.vx = -80
        pause(300)
        sprite.vx = mySprite.vx
    }
})
```

## Schritt 31: Testen: Gegner

Starte das Spiel und teste:

- Läuft der Gegner auf dem Boden?
- Prallt er an Wänden oder Plattformen ab?
- Kannst du ihn mit B abschießen?
- Kannst du ihn von oben besiegen?
- Verlierst du ein Leben, wenn du ihn von der Seite berührst?

Wenn der Gegner herunterfällt, fehlt unter ihm Boden oder die Plattform ist keine Wand.

## Schritt 32: Münzen mit einer Funktion erstellen

Jetzt kommen Sammelobjekte.

Erstelle eine neue Funktion mit dem Namen:

`platziereMuenze`

Füge zwei Parameter hinzu:

- `x` als Zahl
- `y` als Zahl

In diese Funktion kommt ein Sprite vom Typ `Coin`. Die Münze bekommt außerdem **Geist durch Wände = EIN**, damit sie nicht herunterfällt oder an Wänden hängen bleibt.

![Vorschlag Münze](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/muenze.png)

```blocks
let coin: Sprite = null
function platziereMuenze (x: number, y: number) {
    coin = sprites.create(img`
        . . . 5 5 5 5 . . .
        . . 5 4 4 4 4 5 . .
        . 5 4 4 5 4 4 4 5 .
        5 4 4 5 4 4 4 4 4 5
        5 4 4 4 4 4 4 4 4 5
        5 4 4 4 4 4 5 4 4 5
        5 4 4 4 4 4 4 4 4 5
        . 5 4 4 4 4 4 4 5 .
        . . 5 4 4 4 4 5 . .
        . . . 5 5 5 5 . . .
    `, SpriteKind.Coin)
    coin.setPosition(x, y)
    coin.setFlag(SpriteFlag.GhostThroughWalls, true)
}
```

## Schritt 33: Münze einsammeln

Ziehe einen neuen Overlap-Block heraus:

`Player` überlappt `Coin`.

Wenn die Spielfigur eine Münze berührt, verschwindet die Münze, die Punktzahl steigt um 1 und ein Ton wird abgespielt.

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Coin, function (sprite, otherSprite) {
    otherSprite.destroy(effects.smiles, 200)
    info.changeScoreBy(1)
    music.powerUp.play()
})
```

## Schritt 34: Münzen platzieren

Gehe zu **Funktionen** und ziehe den Block `||functions:Aufruf platziereMuenze||` in `||loops:beim Start||`.

Trage eine Position ein, zum Beispiel:

```blocks
platziereMuenze(112, 96)
```

Du kannst so viele Münzen platzieren, wie du möchtest. Dafür setzt du den Block `Aufruf platziereMuenze` mehrmals untereinander und änderst jedes Mal `x` und `y`.

Beispielpositionen aus dem fertigen Spiel:

```blocks
platziereMuenze(112, 96)
platziereMuenze(144, 96)
platziereMuenze(240, 80)
platziereMuenze(272, 80)
platziereMuenze(384, 96)
platziereMuenze(416, 96)
platziereMuenze(512, 64)
platziereMuenze(544, 64)
platziereMuenze(640, 96)
platziereMuenze(672, 96)
```

## Schritt 35: Herzen mit einer Funktion erstellen

Herzen geben deiner Figur Leben zurück.

Erstelle eine neue Funktion mit dem Namen:

`platziereHerz`

Füge zwei Parameter hinzu:

- `x` als Zahl
- `y` als Zahl

In diese Funktion kommt ein Sprite vom Typ `Heart`. Auch das Herz bekommt **Geist durch Wände = EIN**, damit es an seiner Position bleibt.

![Vorschlag Herz](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/herz.png)

```blocks
let heart: Sprite = null
function platziereHerz (x: number, y: number) {
    heart = sprites.create(img`
        . f . . . . f .
        f 2 f . . f 2 f
        f 2 2 f f 2 2 f
        f 2 2 2 2 2 2 f
        . f 2 2 2 2 f .
        . . f 2 2 f . .
        . . . f 2 f . .
        . . . . f . . .
    `, SpriteKind.Heart)
    heart.setPosition(x, y)
    heart.setFlag(SpriteFlag.GhostThroughWalls, true)
}
```

## Schritt 36: Herz einsammeln

Ziehe einen neuen Overlap-Block heraus:

`Player` überlappt `Heart`.

Wenn die Spielfigur weniger als 3 Leben hat, bekommt sie ein Leben dazu. Wenn sie schon 3 Leben hat, verschwindet das Herz trotzdem.

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Heart, function (sprite, otherSprite) {
    if (info.life() < 3) {
        otherSprite.destroy(effects.hearts, 200)
        info.changeLifeBy(1)
        music.powerUp.play()
    } else {
        otherSprite.destroy(effects.hearts, 200)
    }
})
```

## Schritt 37: Herzen platzieren

Ziehe den Block `||functions:Aufruf platziereHerz||` in `||loops:beim Start||`.

Trage eine Position ein, zum Beispiel:

```blocks
platziereHerz(256, 80)
```

Du kannst mehrere Herzen einbauen, indem du den Block mehrfach untereinander setzt und jedes Mal andere Positionen einträgst.

Beispielpositionen aus dem fertigen Spiel:

```blocks
platziereHerz(256, 80)
platziereHerz(528, 64)
platziereHerz(656, 96)
```

## Schritt 38: Weitere Gegner platzieren

Du kannst auch mehrere Gegner einbauen.

Dafür setzt du den Block `Aufruf platziereGegner` mehrfach untereinander und änderst die Positionen.

Beispielpositionen aus dem fertigen Spiel:

```blocks
platziereGegner(128, 96)
platziereGegner(400, 96)
platziereGegner(656, 96)
```

## Schritt 39: Ziel-Flagge erstellen

Am Ende des Levels braucht dein Spiel ein Ziel.

Gehe zu **Sprites** und erstelle einen Sprite vom Typ `Flag`. Falls `Flag` noch nicht existiert, lege diese Sprite-Art über das Dropdown-Menü neu an.

Male eine kleine Flagge. Setze die Position auf:

- `x = 768`
- `y = 80`

Setze außerdem **Geist durch Wände = EIN**, damit die Flagge nicht herunterfällt oder an Kacheln hängen bleibt.

![Vorschlag Flagge](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/flagge.png)

```blocks
let flag = sprites.create(img`
    . 2 2 2 2 2 2 2 . .
    . 2 5 5 5 5 5 2 . .
    . 2 5 2 2 2 5 2 . .
    . 2 5 2 5 2 5 2 . .
    . 2 5 2 2 2 5 2 . .
    . 2 5 5 5 5 5 2 . .
    . 2 2 2 2 2 2 2 . .
    . 2 . . . . . . . .
    . 2 . . . . . . . .
    . 2 . . . . . . . .
    . 2 . . . . . . . .
    . 2 . . . . . . . .
    . 2 . . . . . . . .
    . 2 . . . . . . . .
    . 2 . . . . . . . .
    . . . . . . . . . .
`, SpriteKind.Flag)
flag.setPosition(768, 80)
flag.setFlag(SpriteFlag.GhostThroughWalls, true)
```

## Schritt 40: Spiel gewinnen

Ziehe einen neuen Overlap-Block heraus:

`Player` überlappt `Flag`.

Wenn die Spielfigur die Flagge berührt, gibt es Konfetti, ein Ton wird abgespielt und das Spiel ist gewonnen.

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Flag, function (sprite, otherSprite) {
    otherSprite.startEffect(effects.confetti, 1000)
    music.powerUp.play()
    game.gameOver(true)
})
```

## Schritt 41: Laufbilder vorbereiten

Jetzt bekommt die Spielfigur eine einfache Laufanimation.

Erstelle drei Variablen:

- `frame1`
- `frame2`
- `frame3`

`frame1` und `frame2` sind Laufbilder. `frame3` ist das Stand- und Sprungbild.

Eine Variable ist hier wie eine kleine Schublade mit Namen. In den drei Variablen speichern wir verschiedene Bilder deiner Figur.

![Vorschlag Frame1](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/frame1.png)

![Vorschlag Frame2](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/frame2.png)

![Vorschlag Frame3](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/frame3.png)

Male die Bilder ähnlich wie deine Spielfigur. Bei `frame1` und `frame2` änderst du vor allem die Beine.

```blocks
let frame1 = img`
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . 1 1 . . . 1 1 . . . . . .
    . . . 1 1 . . . 3 1 . . . . . .
    . . . . 1 1 1 1 1 3 . . . . . .
    . . . 1 1 f 1 1 f 1 1 . . . . .
    . . . 5 1 1 1 4 1 1 5 . . . . .
    . . . 1 1 1 1 1 1 1 1 . . . . .
    . . . . 1 1 1 1 1 1 . . . . . .
    . . . 3 3 3 3 3 3 3 3 . . . . .
    . . 1 3 3 3 3 3 3 3 3 1 . . . .
    . . . 3 3 3 3 3 3 3 3 . . . . .
    . . . 3 3 3 . 3 3 3 3 . . . . .
    . . . 3 . . . 3 3 3 3 . . . . .
    . . 1 . . . . . . . 1 1 . . . .
`
let frame2 = img`
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . 1 1 . . . 1 1 . . . . . .
    . . . 1 1 . . . 3 1 . . . . . .
    . . . . 1 1 1 1 1 3 . . . . . .
    . . . 1 1 f 1 1 f 1 1 . . . . .
    . . . 5 1 1 1 4 1 1 5 . . . . .
    . . . 1 1 1 1 1 1 1 1 . . . . .
    . . . . 1 1 1 1 1 1 . . . . . .
    . . . 3 3 3 3 3 3 3 3 . . . . .
    . . 1 3 3 3 3 3 3 3 3 1 . . . .
    . . . 3 3 3 3 3 3 3 3 . . . . .
    . . . 3 3 3 3 . 3 3 3 . . . . .
    . . . 3 3 3 3 . . . 3 . . . . .
    . . 1 1 . . . . . . . 1 . . . .
`
let frame3 = img`
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . 1 1 . . . 1 1 . . . . . .
    . . . 1 1 . . . 3 1 . . . . . .
    . . . . 1 1 1 1 1 3 . . . . . .
    . . . 1 1 f 1 1 f 1 1 . . . . .
    . . . 5 1 1 1 4 1 1 5 . . . . .
    . . . 1 1 1 1 1 1 1 1 . . . . .
    . . . . 1 1 1 1 1 1 . . . . . .
    . . . 3 3 3 3 3 3 3 3 . . . . .
    . . 1 3 3 3 3 3 3 3 3 1 . . . .
    . . . 3 3 3 3 3 3 3 3 . . . . .
    . . . 3 3 3 3 3 3 3 3 . . . . .
    . . . . 1 1 . . 1 1 . . . . . .
    . . . . 1 1 . . 1 1 . . . . . .
`
```

## Schritt 42: A-Sprungbild ergänzen

Im A-Block kannst du zusätzlich das Bild auf `frame3` setzen.

Dann sieht die Figur beim Springen sauber aus.

Füge im vorhandenen A-Block unter `vy = -220` den Block hinzu:

`||sprites:setze mySprite Bild auf frame3||`

```blocks
let mySprite: Sprite = null
let frame3: Image = null
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    if (mySprite.vy == 0) {
        mySprite.vy = -220
        mySprite.setImage(frame3)
    }
})
```

## Schritt 43: Spielupdate vorbereiten

Gehe in die Kategorie **Spiel** und ziehe den Block `||game:wenn Spielupdate||` frei auf die Arbeitsfläche.

Dieser Block wird immer wieder ausgeführt, solange das Spiel läuft. Deshalb eignet er sich für Dinge, die ständig geprüft werden müssen.

```blocks
game.onUpdate(function () {
})
```

## Schritt 44: Herunterfallen bedeutet Game Over

In den `||game:wenn Spielupdate||`-Block kommt zuerst diese Abfrage:

Wenn die y-Position der Figur größer als `230` ist, ist sie aus dem Level gefallen. Dann ist das Spiel verloren.

```blocks
let mySprite: Sprite = null
game.onUpdate(function () {
    if (mySprite.y > 230) {
        game.gameOver(false)
    }
})
```

## Schritt 45: Laufanimation nach rechts und links

Jetzt ergänzen wir im selben `||game:wenn Spielupdate||`-Block die Laufanimation.

Wenn `vx > 10` ist, läuft die Figur nach rechts. Wenn `vx < -10` ist, läuft sie nach links. Dabei wechseln wir zwischen `frame1` und `frame2`. Wenn sie steht und auf dem Boden ist, bekommt sie `frame3`.

```blocks
let mySprite: Sprite = null
let frame1: Image = null
let frame2: Image = null
let frame3: Image = null
game.onUpdate(function () {
    if (mySprite.y > 230) {
        game.gameOver(false)
    }
    if (mySprite.vx > 10) {
        if (game.runtime() % 300 < 150) {
            mySprite.setImage(frame1)
        } else {
            mySprite.setImage(frame2)
        }
    } else if (mySprite.vx < -10) {
        if (game.runtime() % 300 < 150) {
            mySprite.setImage(frame2)
        } else {
            mySprite.setImage(frame1)
        }
    } else if (mySprite.vy == 0) {
        mySprite.setImage(frame3)
    }
})
```

## Schritt 46: Alles testen

Starte dein Spiel und teste in dieser Reihenfolge:

- Hintergrund ist sichtbar.
- Spielfigur erscheint.
- Spielfigur läuft mit links und rechts.
- Boden ist fest und die Figur fällt nicht hindurch.
- Spielfigur springt mit **A**.
- Kamera folgt der Figur.
- Spielfigur schießt mit **B**.
- Gegner erscheinen und laufen.
- Gegner können mit Schuss besiegt werden.
- Gegner können von oben besiegt werden.
- Berührung von der Seite kostet Leben.
- Münzen geben Punkte.
- Herzen geben Leben zurück.
- Die Flagge beendet das Spiel mit Gewinn.
- Wenn die Figur herunterfällt, ist das Spiel verloren.

## Schritt 47: Häufige Fehler beheben

Wenn etwas nicht funktioniert, prüfe diese Punkte:

- Figur fällt durch den Boden: Boden-Kacheln sind nicht als Wand markiert.
- Figur bewegt sich nach oben/unten mit Pfeiltasten: Beim Bewegungsblock muss `vy = 0` stehen.
- Figur springt nicht: Im A-Block muss `vy = -220` stehen.
- Schwerkraft fehlt: Bei der Sprite-Eigenschaft muss `ay = 350` stehen.
- Kamera folgt nicht: `Kamera folgt Sprite mySprite` fehlt.
- Münzen oder Herzen fallen herunter: `Geist durch Wände = EIN` fehlt.
- Gegner bleiben stehen: `vx = 30` fehlt oder `pralle gegen Wand = EIN` fehlt.
- Schüsse treffen Gegner nicht: Overlap muss `Projectile` mit `Enemy` sein.
- Spiel endet nicht beim Fallen: Im Spielupdate muss `mySprite y > 230` stehen.

## Schritt 48: Fertig! @showdialog

Super gemacht! 🎮

Du hast ein eigenes Jump'n'Run-Spiel gebaut: mit Hintergrund, Spielfigur, Tilemap, Wänden, Schwerkraft, Sprung, Kamera, Punkten, Leben, Projektil, Gegnern, Münzen, Herzen, Flagge, Animation und Game Over.

Jetzt kannst du dein Level verschönern, mehr Plattformen bauen oder eigene Figuren und Gegenstände malen.
