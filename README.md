# Workshop: Jump'n'Run Spiel programmieren

## Los geht's! @showdialog

Willkommen! 🎮

In diesem Tutorial baust du ein eigenes Jump'n'Run-Spiel in Microsoft MakeCode Arcade. Du malst eine Spielfigur, baust zuerst einen einfachen Boden, lässt die Figur laufen, springen und schießen und ergänzt danach Gegner, Münzen, Herzen, eine Flagge und eine einfache Animation.

Wichtig für die Glühbirne: Die Bilder und Block-Beispiele in der Hilfe zeigen dir, **welchen Block du suchen musst**. Der grüne Rahmen `beim Start` kann in der Hilfe automatisch mit angezeigt werden. Das bedeutet **nicht**, dass du jedes Mal einen neuen `beim Start`-Block bauen sollst. Wenn im Schritt steht, dass etwas in `beim Start` gehört, ziehst du den neuen Block **unten in den vorhandenen `beim Start`-Block**.

Klicke auf **Weiter**, um zu starten.

## Schritt 1: Hintergrundfarbe einstellen

Gehe links in die Kategorie **Szene**. Ziehe den Block `||scene:setze Hintergrundfarbe auf||` in den vorhandenen Block `||loops:beim Start||`.

Wähle eine helle Farbe, zum Beispiel Blau. So sieht dein Spiel direkt nach einer Welt aus und nicht wie eine leere Fläche.

Erstelle keinen neuen `beim Start`-Block. Ziehe den Hintergrund-Block in den vorhandenen `beim Start`-Block.

```blocks
// @highlight
scene.setBackgroundColor(9)
```

## Schritt 2: Spielfigur malen oder aus der Galerie wählen

Gehe in die Kategorie **Sprites**. Ziehe den Block `||variables:setze mySprite auf Sprite vom Typ Player||` unter den Hintergrund-Block in `||loops:beim Start||`.

Klicke auf das kleine Bild im Block. Jetzt öffnet sich der Mal-Editor. Du kannst deine Spielfigur selbst malen oder über **Galerie** eine Figur auswählen.

So kann deine Spielfigur aussehen. Du kannst sie nachmalen oder komplett anders gestalten.

![Vorschlag Spielfigur](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/sprite.png)

Achte darauf, dass die Figur ungefähr 16 x 16 Pixel groß bleibt. Dann passt sie gut in die Tilemap.

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

## Schritt 3: Spielfigur nach links und rechts bewegen

Gehe in die Kategorie **Controller**. Ziehe den Block `||controller:bewege mySprite mit Knöpfen||` unter deine Spielfigur in `||loops:beim Start||`.

Klicke im Block auf das **Plus-Zeichen**. Erst danach siehst du die Felder für `vx` und `vy`.

Stelle ein:

- `vx = 100`
- `vy = 0`

`vx` ist die Geschwindigkeit nach links und rechts. `vy = 0` bedeutet: Die Figur soll nicht mit den Pfeiltasten nach oben und unten fliegen. Springen bauen wir später selbst.

Der Bewegungsblock gehört in den vorhandenen `beim Start`-Block, direkt unter die Spielfigur.

Klicke auf das **Plus-Zeichen**, damit du `vx` und `vy` einstellen kannst.

```blocks
let mySprite: Sprite = null
// @highlight
controller.moveSprite(mySprite, 100, 0)
```

## Schritt 4: Tilemap öffnen

Jetzt bauen wir den ersten Boden. Gehe in die Kategorie **Szene** und ziehe `||scene:setze Tilemap auf||` unter den Bewegungsblock in `||loops:beim Start||`.

Klicke auf das kleine Kachelbild im Block. Dadurch öffnet sich der **Tilemap-Editor**.

Eine Tilemap ist deine Spielwelt aus kleinen Quadraten. Diese Quadrate heißen **Kacheln**. Aus den Kacheln baust du Boden, Plattformen und später dein Level.

```blocks
// @highlight
tiles.setCurrentTilemap(tilemap`Level1`)
```

## Schritt 5: Tilemap-Größe einstellen

Im Tilemap-Editor stellst du zuerst die Größe ein.

Stelle ein:

- Breite: `50`
- Höhe: `15`

So wird dein Level breiter als der Bildschirm. Später folgt die Kamera deiner Spielfigur.

Hier siehst du, wo du Breite und Höhe findest:

![Hinweis Breite Höhe Tilemap einstellen](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/tilemap_breite_hoehe.png)

Die Zahl links ist die Breite. Die Zahl rechts ist die Höhe.

## Schritt 6: Erstmal nur den Boden malen

Male jetzt noch keine komplizierte Welt. Für den Anfang reicht ein einfacher Boden, damit deine Spielfigur nicht ins Leere fällt.

Wähle eine Boden-Kachel aus dem Bereich **Forest**. Male unten eine durchgehende Bodenfläche. Du kannst erstmal nur den unteren Bereich füllen.

Hier siehst du passende Boden-Kacheln. Nimm für den Anfang eine gut erkennbare Gras- oder Erdkachel.

![Vorschlag Boden Kacheln](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/tilemap_boden_kacheln.png)

Wichtig: Du musst noch keine vollständige Welt malen. Erstmal reicht ein einfacher Boden.

## Schritt 7: Boden direkt als Wand markieren

Der Boden sieht jetzt zwar aus wie Boden, aber die Spielfigur kann noch hindurchfallen. Deshalb musst du die Boden-Kacheln als **Wand** markieren.

Aktiviere im Tilemap-Editor zuerst **Wände anzeigen**. Danach wählst du das **Wand-Werkzeug** und markierst die Boden-Kacheln als Wand.

Aktiviere zuerst **Wände anzeigen**:

![Funktion Wände anzeigen](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/waende_anzeigen.png)

Dann wählst du das Wand-Werkzeug:

![Hinweis Wände Zeichnen Tool](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/waende_zeichnen_tool.png)

Eine Kachel mit Wand ist fest. Die Spielfigur kann nicht hindurchfallen.

Wenn du fertig bist, schließe den Tilemap-Editor mit **Fertig**.

## Schritt 8: Schwerkraft einstellen

Jetzt bekommt die Spielfigur Schwerkraft.

Gehe in die Kategorie **Sprites**. Suche den Block, mit dem man eine Eigenschaft eines Sprites setzt. Im Dropdown-Menü steht vielleicht zuerst `x`, `y`, `vx` oder etwas anderes.

Wähle im Dropdown-Menü **ay (Beschleunigung y)** aus und stelle den Wert auf `350`.

`ay` ist die Beschleunigung nach unten. Dadurch fällt die Figur wie in einem Jump'n'Run-Spiel.

Wichtig: Du musst im Dropdown-Menü wirklich **ay / Beschleunigung y** auswählen. Nicht `y`, nicht `vy`.

- `y` ist die Position.
- `vy` ist die aktuelle Geschwindigkeit nach oben oder unten.
- `ay` ist die Schwerkraft/Beschleunigung.

```blocks
let mySprite: Sprite = null
// @highlight
mySprite.ay = 350
```

## Schritt 9: Spielfigur an den Start setzen

Die Spielfigur soll links im Level starten.

Gehe in die Kategorie **Sprites** und ziehe den Block `||sprites:setze Position von mySprite auf x y||` in `||loops:beim Start||`.

Stelle ein:

- `x = 20`
- `y = 100`

```blocks
let mySprite: Sprite = null
// @highlight
mySprite.setPosition(20, 100)
```

## Schritt 10: Teste Boden, Bewegung und Schwerkraft

Drücke auf **Play**.

Prüfe:

- Siehst du den Hintergrund?
- Siehst du deine Spielfigur?
- Kannst du links und rechts laufen?
- Fällt die Figur nach unten?
- Bleibt sie auf dem Boden stehen?

Wenn die Figur durch den Boden fällt, hast du die Boden-Kacheln noch nicht als Wand markiert.

## Schritt 11: Springen mit der A-Taste vorbereiten

Jetzt soll die Spielfigur springen.

Gehe in die Kategorie **Controller**. Ziehe den Block `||controller:wenn A Knopf gedrückt||` frei auf die Arbeitsfläche. Dieser Block kommt **nicht** in `||loops:beim Start||`.

```blocks
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
})
```

## Schritt 12: Nur springen, wenn die Figur am Boden ist

In den A-Block kommt eine Bedingung.

Die Figur darf nur springen, wenn `vy = 0` ist. Das bedeutet: Sie bewegt sich gerade nicht nach oben oder unten und steht auf dem Boden.

Wenn das stimmt, setzen wir `vy` auf `-220`. Eine negative y-Geschwindigkeit bewegt die Figur nach oben.

```blocks
let mySprite: Sprite = null
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    if (mySprite.vy == 0) {
        mySprite.vy = -220
    }
})
```

## Schritt 13: Teste den Sprung

Drücke auf **Play** und teste:

- Mit links und rechts läuft die Figur.
- Mit **A** springt die Figur.
- Die Figur kann nicht unendlich oft in der Luft springen.

Wenn die Figur nicht springt, prüfe:

- Steht im A-Block wirklich `vy = -220`?
- Prüfst du vorher `mySprite vy = 0`?
- Ist der Boden als Wand markiert?

## Schritt 14: Display verlassen und Kamera folgen

Unser Level ist breiter als der Bildschirm. Deshalb darf die Figur den Bildschirm verlassen und die Kamera soll ihr folgen.

Ziehe in `||loops:beim Start||` diese zwei Blöcke untereinander ein:

1. `||sprites:setze mySprite bleibe auf dem Display auf AUS||`
2. `||scene:Kamera folgt Sprite mySprite||`

```blocks
let mySprite: Sprite = null
mySprite.setStayInScreen(false)
scene.cameraFollowSprite(mySprite)
```

## Schritt 15: Leben und Punkte einstellen

Gehe in die Kategorie **Info**. Ziehe zwei Blöcke in `||loops:beim Start||`:

- `||info:setze Anzahl Leben auf 3||`
- `||info:setze Punktzahl auf 0||`

So startet das Spiel mit 3 Leben und 0 Punkten.

```blocks
// @highlight
info.setLife(3)
// @highlight
info.setScore(0)
```

## Schritt 16: Projektil mit der B-Taste vorbereiten

Jetzt wird es spannender: Die Spielfigur soll schießen können.

Gehe in die Kategorie **Controller** und ziehe `||controller:wenn B Knopf gedrückt||` frei auf die Arbeitsfläche. Dieser Block kommt nicht in `||loops:beim Start||`.

```blocks
controller.B.onEvent(ControllerButtonEvent.Pressed, function () {
})
```

## Schritt 17: Projektil malen und abschießen

Gehe in die Kategorie **Sprites**. Ziehe in den B-Block den Block `||sprites:setze projectile auf Projektil von mySprite||`.

Klicke auf das Bild und male ein kleines Feuer-Projektil. Stelle ein:

- `vx = 150`
- `vy = 0`

Danach spiele einen Ton ab.

So kann dein Projektil aussehen: klein, schnell und gut sichtbar.

Du kannst ein eigenes Projektil malen. Wichtig ist nur: Es sollte nicht zu groß sein.

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

## Schritt 18: Teste das Schießen

Drücke auf **Play**.

Prüfe:

- Mit links und rechts läuft die Figur.
- Mit **A** springt sie.
- Mit **B** schießt sie nach rechts.

Wenn das Projektil nicht fliegt, prüfe `vx = 150` und `vy = 0`.

## Schritt 19: Level optional erweitern

Jetzt kannst du dein Level größer machen.

Standard für den Workshop: Male erstmal **1 bis 2 Plattformen** über dem Boden und markiere sie ebenfalls als Wand.

Wer schneller ist, darf die vollständige Welt nach der Vorlage malen.

So kann die vollständige Tilemap ohne Wandanzeige aussehen:

![Vorschlag vollständige Tilemap](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/tilemap_vollstaendig.png)

So sieht dieselbe Tilemap aus, wenn Wände angezeigt werden:

![Vorschlag vollständige Tilemap mit Wänden](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/tilemap_vollstaendig_mit_waenden.png)

Für den Anfang musst du nicht alles nachbauen. 1 bis 2 Plattformen reichen.

Teste danach wieder kurz, ob die Figur auf den Plattformen stehen kann. Wenn sie durchfällt, fehlt die Wand-Markierung.

## Schritt 20: Gegner-Funktion erstellen

Jetzt bauen wir Gegner. Damit wir später mehrere Gegner einfach platzieren können, erstellen wir eine Funktion.

Gehe zu **Fortgeschritten** → **Funktionen** → **Funktion erstellen**.

Name:

`platziereGegner`

Füge zwei Parameter hinzu:

- `x` als Zahl
- `y` als Zahl

Eine Funktion ist ein eigener Helfer-Block. Du baust ihn einmal und kannst ihn später mehrfach benutzen.

```blocks
function platziereGegner (x: number, y: number) {
}
```

## Schritt 21: Gegner malen und bewegen

In die Funktion `platziereGegner` kommt ein Sprite vom Typ `Enemy`.

Male einen Gegner. Danach stellst du ein:

- Position: `x`, `y`
- `ay = 350`
- `vx = 30`
- `pralle gegen Wand = EIN`

So kann dein Gegner aussehen:

![Vorschlag Enemy](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/enemy.png)

Der Gegner bekommt auch Schwerkraft und läuft automatisch nach links und rechts.

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

## Schritt 22: Einen Gegner platzieren und testen

Ziehe aus **Funktionen** den Block `||functions:Aufruf platziereGegner||` in `||loops:beim Start||`.

Setze für den ersten Test:

- `x = 128`
- `y = 96`

```blocks
platziereGegner(128, 96)
```

Wenn du später mehrere Gegner möchtest, ziehst du denselben Funktionsaufruf mehrmals untereinander in `beim Start` und änderst nur die Positionen.

Für die vollständige Version kannst du diese Positionen nutzen:

```blocks
platziereGegner(128, 96)
platziereGegner(400, 96)
platziereGegner(656, 96)
```

Teste kurz, ob der Gegner erscheint und auf dem Boden läuft.

## Schritt 23: Gegner mit Projektil besiegen

Jetzt soll ein Schuss den Gegner zerstören.

Gehe in die Kategorie **Sprites** und ziehe einen Overlap-Block heraus:

`Projectile` überlappt `Enemy`.

Wenn ein Projektil einen Gegner trifft:

- Gegner verschwindet mit Feuer-Effekt.
- Projektil verschwindet.
- Punktzahl steigt um 2.
- Ton wird abgespielt.

```blocks
sprites.onOverlap(SpriteKind.Projectile, SpriteKind.Enemy, function (sprite, otherSprite) {
    otherSprite.destroy(effects.fire, 300)
    sprite.destroy()
    info.changeScoreBy(2)
    music.zapped.play()
})
```

## Schritt 24: Gegner von oben besiegen oder Leben verlieren

Jetzt soll die Spielfigur Gegner auch von oben besiegen können.

Ziehe einen Overlap-Block heraus:

`Player` überlappt `Enemy`.

Dann prüfen wir:

- Fällt die Spielfigur gerade nach unten?
- Ist sie knapp über dem Gegner?

Wenn ja, wird der Gegner besiegt. Wenn nicht, verliert die Spielfigur ein Leben.

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

## Schritt 25: Münzen vorbereiten

Jetzt kommen Münzen. Dafür brauchst du eine neue Sprite-Art.

Wenn du bei einem Sprite-Block das Feld **Player** oder **Enemy** siehst, klicke auf den kleinen Pfeil. Wähle **Hinzufügen** oder **Add a new kind** und schreibe genau:

`Coin`

Groß- und Kleinschreibung ist wichtig.

```typescript
namespace SpriteKind {
    export const Coin = SpriteKind.create()
}
```

## Schritt 26: Münz-Funktion erstellen

Erstelle eine neue Funktion:

Name:

`platziereMuenze`

Parameter:

- `x` als Zahl
- `y` als Zahl

In dieser Funktion erstellen wir eine Münze, setzen sie an die Position `x`, `y` und schalten **Geist durch Wände** ein. Dadurch bleibt die Münze dort, wo wir sie platzieren.

So kann deine Münze aussehen:

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

## Schritt 27: Eine Münze platzieren und einsammeln

Ziehe einmal den Funktionsaufruf `platziereMuenze` in `||loops:beim Start||`.

Setze zum Test:

- `x = 112`
- `y = 96`

Dann baust du den Overlap:

`Player` überlappt `Coin`.

Wenn die Spielfigur die Münze berührt, verschwindet sie und die Punktzahl steigt um 1.

```blocks
platziereMuenze(112, 96)

sprites.onOverlap(SpriteKind.Player, SpriteKind.Coin, function (sprite, otherSprite) {
    otherSprite.destroy(effects.smiles, 200)
    info.changeScoreBy(1)
    music.powerUp.play()
})
```

Du musst Münzen nicht jedes Mal neu programmieren.

Wenn du mehr Münzen möchtest, ziehst du den Block `Aufruf platziereMuenze` mehrmals untereinander in `beim Start` und trägst verschiedene Positionen ein.

Für die vollständige Version kannst du später diese Positionen nutzen:

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

## Schritt 28: Herzen vorbereiten

Jetzt kommen Herzen. Herzen geben Leben zurück.

Lege eine neue Sprite-Art an und nenne sie genau:

`Heart`

```typescript
namespace SpriteKind {
    export const Heart = SpriteKind.create()
}
```

## Schritt 29: Herz-Funktion erstellen

Erstelle eine neue Funktion:

Name:

`platziereHerz`

Parameter:

- `x` als Zahl
- `y` als Zahl

So kann dein Herz aussehen:

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

## Schritt 30: Ein Herz platzieren und einsammeln

Ziehe einmal den Funktionsaufruf `platziereHerz` in `||loops:beim Start||`.

Setze zum Test:

- `x = 256`
- `y = 80`

Dann baust du den Overlap:

`Player` überlappt `Heart`.

Wenn die Spielfigur weniger als 3 Leben hat, bekommt sie 1 Leben dazu. Wenn sie schon 3 Leben hat, verschwindet das Herz trotzdem.

```blocks
platziereHerz(256, 80)

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

Wenn du mehr Herzen möchtest, ziehst du `Aufruf platziereHerz` mehrmals untereinander in `beim Start` und gibst verschiedene Positionen ein.

Für die vollständige Version kannst du später diese Positionen nutzen:

```blocks
platziereHerz(256, 80)
platziereHerz(528, 64)
platziereHerz(656, 96)
```

## Schritt 31: Ziel-Flagge vorbereiten

Am Ende braucht dein Level ein Ziel.

Lege eine neue Sprite-Art an und nenne sie genau:

`Flag`

```typescript
namespace SpriteKind {
    export const Flag = SpriteKind.create()
}
```

## Schritt 32: Flagge erstellen und platzieren

Gehe zu **Sprites** und erstelle einen Sprite vom Typ `Flag`.

Male eine kleine Flagge und setze sie weit rechts am Ende des Levels.

Stelle ein:

- `x = 768`
- `y = 80`
- `Geist durch Wände = EIN`

So kann deine Flagge aussehen:

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

## Schritt 33: Spiel gewinnen

Ziehe einen Overlap-Block heraus:

`Player` überlappt `Flag`.

Wenn die Spielfigur die Flagge berührt:

- Konfetti erscheint.
- Ein Ton wird abgespielt.
- Das Spiel ist gewonnen.

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Flag, function (sprite, otherSprite) {
    otherSprite.startEffect(effects.confetti, 1000)
    music.powerUp.play()
    game.gameOver(true)
})
```

## Schritt 34: Laufbilder für die Animation erstellen

Jetzt bekommt die Spielfigur eine einfache Laufanimation.

Erstelle drei Variablen:

- `frame1`
- `frame2`
- `frame3`

Diese drei Bilder kommen in den vorhandenen `beim Start`-Block. `frame1` und `frame2` sind Laufbilder. `frame3` ist das Stand- und Sprungbild.

So können die drei Bilder aussehen:

![Vorschlag Frame1](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/frame1.png)

![Vorschlag Frame2](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/frame2.png)

![Vorschlag Frame3](https://raw.githubusercontent.com/Layla-Abdelwahab-th-ab-de/MakeCode-Arcade-Bilder/main/docs/static/jumpnrun/frame3.png)

Male die Bilder ähnlich wie deine Spielfigur. Bei `frame1` und `frame2` änderst du nur die Beine etwas.

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

## Schritt 35: A-Block mit Sprungbild ergänzen

Jetzt kannst du deinen A-Block noch verbessern.

Wenn die Figur springt, soll sie das Bild `frame3` bekommen.

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

## Schritt 36: Game Over beim Herunterfallen

Gehe in die Kategorie **Spiel** und ziehe `||game:wenn Spielupdate||` frei auf die Arbeitsfläche.

Wenn die Spielfigur zu tief fällt, ist das Spiel verloren.

Wir prüfen:

`mySprite y > 230`

```blocks
let mySprite: Sprite = null
game.onUpdate(function () {
    if (mySprite.y > 230) {
        game.gameOver(false)
    }
})
```

## Schritt 37: Laufanimation einbauen

In denselben `||game:wenn Spielupdate||`-Block kommt jetzt die Animation.

Wenn die Figur nach rechts läuft, wechseln `frame1` und `frame2`. Wenn sie nach links läuft, wechseln wir die Reihenfolge. Wenn sie steht und auf dem Boden ist, bekommt sie `frame3`.

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

## Schritt 38: Alles testen

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

## Schritt 39: Häufige Fehler beheben

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

## Geschafft! @showdialog

Super gemacht! 🎮

Du hast ein eigenes Jump'n'Run-Spiel gebaut: mit Hintergrund, Spielfigur, Tilemap, Wänden, Schwerkraft, Sprung, Kamera, Punkten, Leben, Projektil, Gegnern, Münzen, Herzen, Flagge, Animation und Game Over.

Jetzt kannst du dein Level verschönern, mehr Plattformen bauen oder eigene Figuren und Gegenstände malen.
