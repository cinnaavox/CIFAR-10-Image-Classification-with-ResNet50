# 🌟 CIFAR-10 Bildklassifikation mit ResNet50  
**Deep Learning · Computer Vision · Transfer Learning · TensorFlow**

---

## 🧭 Überblick

Dieses Repository enthält zwei vollständig ausgearbeitete Google-Colab-Notebooks, in denen ich den CIFAR-10-Datensatz mithilfe von **Transfer Learning** und **ResNet50** klassifiziere.

Das Projekt war Teil meiner Data-Analytics-Fortbildung und mein Ziel war es, einen **kompletten Computer-Vision-Workflow selbstständig** aufzubauen – ohne Schritt-für-Schritt-Anleitung.

Um das Verhalten des Modells besser zu verstehen, habe ich **zwei Varianten** erstellt:

### 🔹 Experiment A – 10.000 Trainingsbilder (Aufgabenstellung)  
Version, die ich präsentiere.  
Zeigt Overfitting sehr klar.

### 🔹 Experiment B – 50.000 Trainingsbilder (voller Datensatz)  
Ein Erweiterungsexperiment, das ich danach erstellt habe.  
Zeigt deutlich stabileres Lernen und bessere Generalisierung.

Beide Versionen liegen diesem Repository bei.

---

### 📂 Repository-Struktur

cifar10-resnet50/

- CV_Project_Final_Version.ipynb        -> Version mit 10.000 Bildern (Präsentation)
- CV_Project_Version_2_all_data.ipynb   -> Version mit allen 50.000 Trainingsbildern
- README.md

---

## 🎯 Projektziele

- CIFAR-10-Datensatz verstehen  
- Vollständige Bildklassifikations-Pipeline aufbauen  
- ResNet50 als Feature-Extractor nutzen  
- Eigenen Klassifikationskopf ergänzen  
- Zwei Trainingsphasen durchführen:
  - **Head-Only Training**
  - **Fine-Tuning**
- Generalisierung vs. Overfitting analysieren  
- Ergebnisse durch Plots und Beispiele visualisieren  
- Unterschiede zwischen kleinem und großem Datensatz verstehen  

---

# 📦 Der CIFAR-10 Datensatz

- 60.000 RGB-Bilder  
- 10 Klassen (z. B. airplane, dog, car, ship …)  
- Auflösung: **32 × 32 Pixel**  
- 50.000 Trainingsbilder  
- 10.000 Testbilder  

Die geringe Auflösung macht CIFAR-10 anspruchsvoll – perfekt, um zu beobachten, wie gut ein starkes, vortrainiertes Modell damit umgehen kann.

---

# 🧪 Experiment A – 10.000 Bilder (Aufgabe)

### **Workflow**
- Begrenzen auf 10k Trainingsbilder  
- Normalisierung (0–1)  
- One-Hot-Encoding der Labels  
- Laden von ResNet50 ohne Top-Layer  
- Eigenen Klassifikationskopf bauen:
  - GAP → Dense(256) → Dense(64) → Dense(10)  
- Phase 1 → nur Kopf trainieren  
- Phase 2 → ResNet50 auftauen und feinabstimmen  

---

### **Ergebnisse**

#### **Head-Training**
- Trainingsgenauigkeit: ~0,37  
- Testgenauigkeit: ~0,36  
- Stabile, parallele Kurven  
- Modell lernt etwas, aber bleibt limitiert  

#### **Fine-Tuning**
- Trainingsgenauigkeit: **bis 97 %**  
- Testgenauigkeit: **nur ~26,7 %**  
- Validation-Loss extrem hoch  
- → **klassisches Overfitting**

---

## 🧠 Learnings aus Experiment A

- 10k Bilder sind zu wenig für ein großes Modell wie ResNet50  
- Fine-Tuning ist extrem empfindlich gegenüber Datenmenge  
- Overfitting ist sowohl in Zahlen als auch in Plots sofort sichtbar  
- Vorhersagen bestätigen das Muster: manche Treffer, viele Fehler  

Diese Version eignet sich perfekt, um **Generalisation vs. Memorisation** zu demonstrieren.

---

# 🧪 Experiment B – 50.000 Bilder (voller Datensatz)

Nachdem Experiment A abgeschlossen war, habe ich das Notebook neu aufgebaut – dieses Mal mit **allen 50.000 Trainingsbildern**.

### **Workflow**
Gleiche Architektur, gleiche Hyperparameter.  
Nur die Datenmenge wurde erhöht.

---

### **Ergebnisse**
- **Testaccuracy: 66,30 %**  
- deutlich stabilere Trainingskurven  
- viel weniger Overfitting  
- bessere, nachvollziehbarere Vorhersagen  

---

## 🧠 Learnings aus Experiment B

- Datenmenge ist einer der stärksten Einflussfaktoren im Deep Learning  
- Fine-Tuning funktioniert deutlich besser mit mehr Daten  
- ResNet50 wird stabiler, je mehr Beispiele es sieht  
- Auch mit 32px-Bildern ist gute Performance möglich  
- Der Unterschied zwischen 10k und 50k ist **dramatisch – und extrem lehrreich**  

---

# 🔍 Vergleich: 10k vs. 50k

| Faktor | 10.000 Bilder | 50.000 Bilder |
|--------|----------------|----------------|
| Datenmenge | reduziert | vollständig |
| Trainingsverhalten | instabil | harmonisch |
| Testaccuracy | ~26,7 % | ~66,3 % |
| Overfitting | stark | deutlich geringer |
| Vorhersagen | wechselhaft | deutlich zuverlässiger |

👉 Der Vergleich zeigt sehr klar, warum **Datenquantität** bei Deep Learning entscheidend ist.

---

# 🔧 Technischer Workflow (beide Versionen)

1. CIFAR-10 laden  
2. Normalisieren  
3. Labels One-Hot-Encoden  
4. ResNet50 laden (ohne Top-Layer)  
5. Klassifikationskopf bauen  
6. Head-Training  
7. Fine-Tuning  
8. Test-Evaluation  
9. Lernkurven visualisieren  
10. Vorhersagen anzeigen  
11. Zweites Experiment mit 50k Bildern durchführen  

---

# 💡 Was ich aus dem Projekt gelernt habe

- Wie Transfer Learning praktisch funktioniert  
- Warum das Einfrieren des Basismodells wichtig ist  
- Wie stark die Datenmenge die Generalisierung beeinflusst  
- Wie man Overfitting erkennt und interpretiert  
- Wie CNNs visuelle Muster verarbeiten  
- Warum Trainingsaccuracy allein nicht aussagekräftig ist  
- Wie Architektur, Lernrate und Datenmenge zusammen wirken  

Dieses Projekt hat mein Verständnis für Deep Learning und Computer Vision massiv vertieft.

---

# 🚀 Nächste Schritte

- Data Augmentation  
- L2-Regularisierung & Dropout  
- Teilweises Auftauen einzelner ResNet-Schichten  
- Alternatives Modell (EfficientNet, MobileNet) testen  
- Längeres Fine-Tuning auf GPU/TPU  
- Mixed Precision Training  

---

📄 Notebook (10.000 Bilder – Präsentationsversion):
👉 [Hier klicken](https://colab.research.google.com/drive/1LtZH3GiPX27fzAkld4mNZo2LKuOTeZGW?usp=sharing)

📄 Notebook (50.000 Bilder – vollständiger Datensatz):
👉 [Hier klicken](https://colab.research.google.com/drive/1FQVA2m7Zo43ApRV2ry36I7CTq9AWDsnS?usp=sharing)

---

# 📫 Kontakt

Wenn du Feedback hast oder über Deep Learning sprechen möchtest – jederzeit gerne!
