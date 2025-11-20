🌟 CIFAR-10 Image Classification with ResNet50

Deep Learning · Computer Vision · Transfer Learning · TensorFlow

🧭 Über dieses Projekt

Dieses Repository enthält zwei vollständige Google-Colab-Notebooks, in denen ich den CIFAR-10-Datensatz mit Hilfe von Transfer Learning und ResNet50 klassifiziere.
Das Projekt war Teil meines Data-Analytics-Programms und hatte das Ziel, zum ersten Mal einen eigenständigen Computer-Vision-Workflow aufzubauen – ohne Schritt-für-Schritt-Anleitung.

Ich habe bewusst zwei Experimente durchgeführt:

Experiment A – 10.000 Trainingsbilder
(gemäß Aufgabenstellung, für die Live-Präsentation)
→ zeigt Overfitting sehr klar

Experiment B – 50.000 Trainingsbilder
(erweiterte Version zur Vertiefung)
→ deutlich stabilere Performance, realistischere Ergebnisse

Beide Notebooks sind im Repository enthalten.

📂 Repository-Inhalte
📁 cifar10-resnet50/
│
├── notebook_10k.ipynb      # Projekt gemäß Aufgabenstellung (Präsentation)
├── notebook_50k.ipynb      # Erweiterte Version mit allen Trainingsdaten
└── README.md

🎯 Zielsetzung

CIFAR-10 verstehen und vorbereiten

komplette Bildverarbeitungspipeline aufbauen

vortrainiertes ResNet50 nutzen (Transfer Learning)

eigenen Klassifikationskopf erstellen

zweistufiges Training umsetzen

Phase 1: nur Kopf

Phase 2: Fine-Tuning

Generalisierung & Overfitting nachvollziehbar erklären

Ergebnisse visualisieren (Accuracy/Loss + Beispielvorhersagen)

Unterschiede zwischen kleinem und großem Datensatz analysieren

📦 Der Datensatz: CIFAR-10

60.000 RGB-Bilder

10 Klassen (airplane, automobile, bird, cat, deer, dog, frog, horse, ship, truck)

32×32 Pixel (sehr geringe Auflösung)

50k Train / 10k Test

Die niedrige Auflösung macht die Aufgabe überraschend anspruchsvoll und zeigt klar, wie wichtig gute Feature-Extractor sind.

🧪 Experiment A – 10.000 Trainingsbilder (Aufgabenstellung)
Vorgehen

Trainingsdaten auf 10.000 begrenzt

One-Hot-Encoding der Labels

Normalisierung der Bilder

ResNet50 (ImageNet-Weights) ohne Top-Layer

eigener Kopf: GAP → Dense(256) → Dense(64) → Dense(10)

Phase 1: Kopf trainieren

Phase 2: ResNet auftauen + Fine-Tuning mit kleiner Lernrate

Ergebnisse

Head-Training (Phase 1)

Train Accuracy: ~0.37

Test Accuracy: ~0.36

stabile, parallele Kurven

Fine-Tuning (Phase 2)

Train Accuracy: bis 97 %

Test Accuracy: ~26.7 %

Validierungs-Loss sehr hoch

→ klares Overfitting

Erkenntnisse aus Experiment A

10.000 Bilder sind für ein Modell wie ResNet50 sehr wenig

Fine-Tuning funktioniert nur, wenn genug Daten vorhanden sind

die Trainingskurven zeigen genau das typische Verhalten von Overfitting

Beispielvorhersagen erklären das Muster perfekt: einige richtige Treffer, doppelt so viele falsche Zuordnungen

das Setup ist ideal, um das Thema Generalisation vs. Memorization zu verstehen

🧪 Experiment B – 50.000 Trainingsbilder (Erweiterung)

Nach dem Pflichtprojekt habe ich dasselbe Setup erneut durchgeführt – diesmal mit allen 50.000 Trainingsbildern.

Vorgehen

identische Datenvorbereitung

gleicher Kopf

identische Hyperparameter

nur mehr Trainingsdaten

Ergebnisse

Test Accuracy: 66.30 %

Training stabil und harmonisch

wesentlich bessere Generalisierung

deutlich weniger Overfitting

Fehlklassifikationen traten nur bei wirklich ähnlichen Klassen auf

Erkenntnisse aus Experiment B

Datenmenge ist ein zentraler Faktor für Deep Learning

Fine-Tuning wird erst dann effektiv, wenn das Modell genug Beispiele hat

ResNet50 kann auch kleine Bilder gut verarbeiten – aber es braucht Masse

das Modell lernt robuste Muster, sobald genügend Varianz vorhanden ist

🔍 Vergleich: 10k vs. 50k
Faktor	10k	50k
Trainingsdaten	begrenzt	komplett
Verhalten	starkes Overfitting	stabil
Test Accuracy	~26.7 %	~66.3 %
Kurven	divergierend	harmonisch
Vorhersagen	viele Fehler	deutlich besser

👉 Der Unterschied ist ein perfektes Beispiel dafür, wie sehr Daten Qualität und Stabilität beeinflussen.

🔧 Mein technisches Vorgehen

CIFAR-10 laden

Bilder normalisieren

Labels via One-Hot-Encoding vorbereiten

ResNet50 laden (ImageNet, ohne Kopf)

eigenen Klassifikationskopf bauen

Phase 1: Kopf trainieren

Phase 2: komplettes Modell finetunen

Evaluation via Accuracy, Loss, Plots

Beispielvorhersagen visualisieren

zweites Experiment zum Vergleich durchführen

💡 Was ich gelernt habe

Wie man Transfer Learning sinnvoll einsetzt

Warum man Modelle zuerst einfriert

Warum Fine-Tuning extrem empfindlich auf die Datenmenge reagiert

wie Overfitting aussieht – nicht nur als Zahl, sondern optisch

dass Generalisierung die wichtigste Metrik ist

wie Architektur, Lernrate und Daten zusammenarbeiten

Das Projekt hat mein Verständnis für CNNs und Deep Learning enorm vertieft.

🚀 Nächste Schritte / Verbesserungsmöglichkeiten

Data Augmentation (Flip, Crop, Noise, Farbe)

Dropout & L2-Regularisierung

längeres Training auf GPU/TPU

nur obere ResNet-Schichten finetunen

experimentieren mit EfficientNet oder MobileNet

Mixed Precision Training

📫 Kontakt

Bei Fragen, Feedback oder Interesse am Projekt – ich freue mich über Austausch!
