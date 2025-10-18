🧩 1. Tokenisierung — Wörter in Zahlen

Das Modell kann keine Wörter verstehen, nur Zahlen.
Darum wird dein Satz

„Ist die Erde rund?“
zuerst in kleine Bausteine zerlegt (Tokens),
z. B.: ["Ist", "die", "Erde", "rund", "?"].

Jedes dieser Tokens bekommt eine feste ID aus einem riesigen Wörterbuch (z. B. 50 000 Einträge).
Beispiel:
„Erde“ = 9321, „rund“ = 10107.

So wird Sprache zu Daten.

🧮 2. Embeddings — Wörter bekommen Bedeutung

Jetzt werden diese IDs in Vektoren umgewandelt — lange Zahlenreihen, die die Bedeutung eines Wortes im Raum darstellen.
Das nennt man Embedding.

Ähnliche Wörter haben ähnliche Vektoren.

„Erde“, „Planet“, „Welt“ liegen nahe beieinander.

„rund“ liegt nahe bei „kugelförmig“ oder „kreisförmig“.

Damit kennt das Modell also Bedeutungen und Zusammenhänge, nicht nur Buchstaben.

📍 3. Positionsinformationen — Reihenfolge merken

Ein Transformer weiß an sich nicht, in welcher Reihenfolge Wörter stehen.
Darum bekommt jedes Wort zusätzlich einen Positionsvektor, z. B.:

Wort → „Anfang des Satzes“

Wort → „am Ende, evtl. Fragezeichen“

Diese werden einfach zu den Embeddings addiert.
So weiß das Modell:

„Erde“ kommt vor „rund“, also ist das Subjekt, nicht das Adjektiv.

🧠 4. Self-Attention — Wörter schauen sich gegenseitig an

Das ist der wichtigste Schritt.
Hier passiert das eigentliche „Verstehen“.

🧭 Idee:

Jedes Wort schaut auf alle anderen Wörter und fragt:

„Wie wichtig bist du für mich in diesem Satz?“

„Erde“ achtet stark auf „rund“.

„Ist“ achtet auf „Erde“ (Subjekt).

„?“ achtet auf „Ist“ (weil es eine Frage ist).

Das nennt man Aufmerksamkeit (Attention).
Daraus entsteht eine Gewichtungsmatrix, die sagt:

„Wort A beeinflusst Wort B zu x %.“

Das ist wie ein soziales Netzwerk der Wörter:

Manche Verbindungen sind stark („Erde“ ↔ „rund“),

andere schwach („die“ ↔ „?“).

Ergebnis:
Jedes Wort bekommt eine neue, kontextabhängige Bedeutung —
also nicht nur, was es ist, sondern wie es im Satz gemeint ist.

⚙️ 5. Feed-Forward Layer — Bedeutung verdichten

Nachdem alle Wörter sich gegenseitig „verstanden“ haben,
wird jedes Wort durch ein kleines neuronales Netz geschickt,
das die Information verdichtet und neu kombiniert.

Man kann es sich vorstellen wie:

„Ich fasse das, was ich über mich und meine Nachbarn gelernt habe, zusammen.“

Das sorgt dafür, dass abstraktere Zusammenhänge entstehen:

„Erde rund“ → physikalische Eigenschaft

„Ist ... ?“ → Frageform

→ das Ganze = Faktabfrage.

🔁 6. Viele Schichten — Denken in Ebenen

GPT hat viele (bei GPT-5 über 100) solcher Schichten,
und jede Schicht denkt „tiefer“ als die vorige.

Schicht Erkennt
1–3 Grammatik, Wortbeziehungen
4–10 Satzstruktur, Bedeutung
11–50 Logische Beziehungen, Weltwissen
51–100+ Abstrakte Konzepte, Argumentation, Faktwissen

Man kann sich das vorstellen wie:
Erst erkennt das Modell Wörter, dann Sätze, dann Ideen, dann Wissen.

🔮 7. Ausgabe — Vorhersage des nächsten Wortes

Nach der letzten Schicht hat das Modell für jedes Wort eine kontextreiche „Verständnisrepräsentation“.
Das letzte Token („?“) dient als Signal:

„Bitte sag mir, was jetzt am wahrscheinlichsten als Antwort kommt.“

Das Modell berechnet für jedes mögliche Wort im Vokabular (z. B. 50 000 Wörter) eine Wahrscheinlichkeit:

Wort Wahrscheinlichkeit
Ja 0.92
Nein 0.05
Vielleicht 0.03

Das wahrscheinlichste Token („Ja“) wird ausgegeben,
und so entsteht die Antwort:

„Ja, die Erde ist rund.“

⚡️ 8. Das Ganze passiert in Millisekunden

All das — Tokenisierung, Embeddings, Attention, Feed-Forward, Wahrscheinlichkeitsberechnung —
läuft auf vielen GPUs parallel ab,
innerhalb von Millisekunden pro Token.

🧭 Kurz zusammengefasst:
Schritt Funktion Was passiert inhaltlich
Tokenisierung Wörter → IDs Sprache wird zu Zahlen
Embedding IDs → Bedeutungen Jedes Wort bekommt einen Sinn im Zahlenraum
Position Reihenfolge Satzstruktur bleibt erhalten
Self-Attention Wörter reden miteinander Kontext entsteht
Feed-Forward Verarbeitung Informationen werden abstrahiert
Viele Schichten Mehrstufiges Denken Vom Satz zur Bedeutung
Softmax-Output Antwortberechnung Wahrscheinlichstes nächstes Wort
Ergebnis Ausgabe „Ja, die Erde ist rund.“

Möchtest du, dass ich diesen Ablauf jetzt noch algorithmisch beschreibe —
also Schritt-für-Schritt in Pseudocode, wie GPT das intern „ausführt“?
