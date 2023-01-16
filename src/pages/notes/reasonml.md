---
layout: ../../layouts/MarkdownPostLayout.astro
title: 'Eine Geschmacksrichtung zur Typensicherheit in JavaScript Apps'
date: "2019-12-18"
description: ""
---

# Eine Geschmacksrichtung zur Typensicherheit in JavaScript Apps

Eine kleine und von mir persönlich angefertigte Zusammenfassung des Talks von Sophia Brandt https://sophiabrandt.com in der Dortmunder https://softwerkskammer.org Loaction der Softwarkskammer.

Sophia sprach über das Thema ReasenML https://reasonml.github.io/ eine wie man so will,
Geschmacksrichtung für die Typensicherhet in JavaScript Applikationen.

Vorweg Reason ist keine neue Programmiersparache, sondern eine andere Syntax die wiederum auf der sehr alten und robusten OCaml Sprache, die den in den 1990 Jahren entwickelt worden ist, aufbaut.
Reason hat die gleichen Wurzeln wie React und viele Prototypen wurden im Hause facebook auf Basis dieser Sprache entwickelt und vorangeführt.
Unter der Haube wird der geschriebene Reason Code mithilfe von BuckleScript und OCaml/Reason in lesbares JavaScript kompiliert.

Die Sprache JavaScript ist in ihrem Ursprung nicht typen sicher. Sie gilt als dynamisch typisierte Sprache.
Wir kennen alle das Szenario, wenn wir versuchen auf etwas zu klicken und die Fehlerausgabe `undefined is not a function` bekommen.
Das liegt daran, dass wird versuchen Code auszuführen

Typensicherheit schützt uns vor diesen Fehlern.
Der Datentyp muss gemäß seiner Definition verwendet werden aonsten tritt ein Typenfehler auf und das Programm wirft einen Fehler.

Möchte man jedoch in JavaScript die Vorteile der Typensicherheit nutzen, so kann man auf eine vielzahl von "Geschmacksrichtungen"/Typensets zurückgreifen. Einige Beispiele sind TypeScript, PureScript oder Elm.

Die Syntax von Reason ist angelehnt an die von JavaScript/React, sodass man sich schnell heimisch fühlt. Zudem bietet OCaml einige wesentlichen Vorteile gegenüber plain JS, sodass robustere Frontend Apps entwickelt werden können. Einige Vorteile sind: 100% Code Coverage, der compiler macht transpiler wie babel, eslint oder prettifier überflüssig, da dies von Haus aus mitgeliefert werden. Und es ist sehr gut verträglich mit dem JS Ökosystem.

Um euch selbst ein Bild von der Syntax zu machen, hier ein paar Code Beispiele.

Die Slides zum Vortrag findet Ihr unter https://sophiabrandt.github.io/write-type-safe-react-applications-with-reason/slides.html#1

Links:
https://blog.logrocket.com/what-makes-reasonml-so-great-c2c2fc215ccb/

```javascript
type option('a) = None | Some('a)
//Eine Variable kann nicht mehr undefined sein

//Varianten typen machen es möglich eine Art state zu definieren
type payload =
  | BadResult(int)
  | GoodResult(string)
  | NoResult;

```