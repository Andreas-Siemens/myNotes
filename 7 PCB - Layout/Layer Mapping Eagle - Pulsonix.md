Hier ein typisches Beispiel für ein Layer-Mapping:

| **Eagle Layer** | **Funktion**                       | **Pulsonix Layer** (Standard)    |
| --------------- | ---------------------------------- | -------------------------------- |
| 1 Top           | Leiterbahn oben                    | Signal Top (Copper Top)          |
| 16 Bottom       | Leiterbahn unten                   | Signal Bottom (Copper Bottom)    |
| 2..15           | Interne Signal-Lagen (falls 4L/6L) | Signal Inner1 … InnerN           |
| 17 Pads         | Durchkontaktierte Pads             | Pads (Pad Master)                |
| 18 Vias         | Vias                               | Vias                             |
| 19 Unrouted     | Luftlinien                         | Connections (Unrouted Nets)      |
| 20 Dimension    | Platinenkontur                     | Board Outline                    |
| 21 tPlace       | Bauteilumriss oben (Silkscreen)    | Silkscreen Top                   |
| 22 bPlace       | Bauteilumriss unten (Silkscreen)   | Silkscreen Bottom                |
| 23 tOrigins     | Referenzpunkte Oben                | Assembly Top (Optional)          |
| 24 bOrigins     | Referenzpunkte Unten               | Assembly Bottom (Optional)       |
| 25 tNames       | Bauteilnamen oben                  | Silkscreen Text Top              |
| 26 bNames       | Bauteilnamen unten                 | Silkscreen Text Bottom           |
| 27 tValues      | Bauteilwerte oben                  | Assembly Text Top (oder Doku)    |
| 28 bValues      | Bauteilwerte unten                 | Assembly Text Bottom (oder Doku) |
| 29 tStop        | Lötstoppmaske oben                 | Solder Mask Top                  |
| 30 bStop        | Lötstoppmaske unten                | Solder Mask Bottom               |
| 31 tCream       | Pastenmaske oben                   | Paste Mask Top                   |
| 32 bCream       | Pastenmaske unten                  | Paste Mask Bottom                |
| 33 tFinish      | Oberfläche oben (selten genutzt)   | Finish Top (falls benötigt)      |
| 34 bFinish      | Oberfläche unten (selten genutzt)  | Finish Bottom                    |
| 35 tGlue        | Klebepunkte oben                   | Glue Top                         |
| 36 bGlue        | Klebepunkte unten                  | Glue Bottom                      |
| 37 tTest        | Testpunkte oben                    | Test Top                         |
| 38 bTest        | Testpunkte unten                   | Test Bottom                      |
| 39 tKeepout     | Keepout oben                       | Keepout Top                      |
| 40 bKeepout     | Keepout unten                      | Keepout Bottom                   |
| 41 tRestrict    | Routing-Sperre oben                | Route Restrict Top               |
| 42 bRestrict    | Routing-Sperre unten               | Route Restrict Bottom            |
| 43 vRestrict    | Via-Sperre                         | Via Restrict                     |
| 44 Drills       | Bohrungen                          | Drill Holes                      |
| 45 Holes        | Nichtplattierte Bohrungen          | Mechanical Drill                 |
| 46 Milling      | Fräskontur                         | Mechanical Milling               |
| 47 Measures     | Bemaßung                           | Mechanical Dimension             |

## IPC-2221/2222

Die **IPC-2221/2222 (Generic Standards for Printed Boards)** und **IPC-2581 (Datenformat)** definieren, wie Lagen und deren Bezeichnungen standardisiert sind. Auch Fertiger erwarten üblicherweise diese Terminologie.

**IPC-Standard Layer-Bezeichnungen (gängige Praxis):**

### **Kupferlagen (Conductive Layers)**

- **Top Layer** → oberste Kupferlage
- **Bottom Layer** → unterste Kupferlage    
- **Inner Layer 1, Inner Layer 2, …** → Innenlagen, durchnummeriert von außen nach innen    

### **Lötstopplack (Solder Mask Layers)**

- **Top Solder Mask** → Lötstopplack oben    
- **Bottom Solder Mask** → Lötstopplack unten    

### **Bestückungsdruck (Silkscreen / Legend Layers)**

- **Top Silkscreen** oder **Top Legend** → Aufdruck oben    
- **Bottom Silkscreen** oder **Bottom Legend** → Aufdruck unten    

### **Lotpastenschablone (Solder Paste Layers)**

- **Top Paste Mask** → Pastendruck oben    
- **Bottom Paste Mask** → Pastendruck unten    

### **Mechanische/Umriss-Lagen (Mechanical / Outline Layers)**

- **Board Outline** → Umriss der Leiterplatte    
- **Mechanical 1, Mechanical 2, …** → für Fräsungen, Aussparungen, Dokumentationshinweise    

### **Bohr- und Fertigungsinformationen**

- **Drill Drawing** → Zeichnung mit Bohrsymbolen    
- **Drill Guide / NC Drill** → tatsächliche NC-Bohrdaten    
- **Plated Holes / Non-Plated Holes** → galvanisierte vs. nicht-galvanisierte Bohrungen    

### **Zusätzliche Funktionslagen nach IPC**

- **Assembly Top / Bottom** → Montagezeichnungen    
- **Courtyard** → Bauteilbegrenzungen nach IPC-7351    
- **Keepout** → Sperrflächen    
- **Fiducials** → Markierungen für Bestückungsautomaten


## 📑 Mapping-Tabelle: Pulsonix ↔ IPC ↔ Gerber-Ausgabe

Hier eine Übersicht, wie man die **Pulsonix-Layer-Namen** typischerweise den **IPC-Standardbezeichnungen** zuordnet und wie die **Gerber-Dateien** (oder ODB++ Layernamen) üblicherweise benannt werden:

| **Funktion**               | **Pulsonix Layername (üblich)** | **IPC-Standardname**   | **Gerber-Dateiname (Beispiel)** |
| -------------------------- | ------------------------------- | ---------------------- | ------------------------------- |
| **Oberseite Kupfer**       | Top Copper                      | Top Layer              | `TopCopper.GTL` oder `*.GTL`    |
| **Unterseite Kupfer**      | Bottom Copper                   | Bottom Layer           | `BottomCopper.GBL` oder `*.GBL` |
| **Innenlagen**             | Inner Layer 1, 2, …             | Inner Layer 1, 2, …    | `In1.Gx`, `In2.Gx`, …           |
| **Lötstopp oben**          | Top Solder Mask                 | Top Solder Mask        | `TopMask.GTS`                   |
| **Lötstopp unten**         | Bottom Solder Mask              | Bottom Solder Mask     | `BottomMask.GBS`                |
| **Bestückungsdruck oben**  | Top Silk Screen / Top Legend    | Top Silkscreen         | `TopSilk.GTO`                   |
| **Bestückungsdruck unten** | Bottom Silk Screen / Legend     | Bottom Silkscreen      | `BottomSilk.GBO`                |
| **Lotpaste oben**          | Top Paste                       | Top Paste Mask         | `TopPaste.GTP`                  |
| **Lotpaste unten**         | Bottom Paste                    | Bottom Paste Mask      | `BottomPaste.GBP`               |
| **Platinenkontur**         | Board Outline                   | Board Outline          | `Outline.GKO` oder `*.GML`      |
| **Fräsungen**              | Mechanical Layer (z. B. Mech1)  | Route/Mechanical Layer | `Route.GKO` oder `*.GML`        |
| **Bohrungen (NC-Drill)**   | Drill Data                      | NC Drill Data          | `Drill.TXT` oder `*.DRL`        |
| **Bauteilumriss**          | Courtyard                       | Courtyard (IPC-7351)   | ODB++ Layer / Gerber optional   |
| **Montagezeichnung oben**  | Assembly Top                    | Assembly Top           | ODB++ Layer / PDF               |
| **Montagezeichnung unten** | Assembly Bottom                 | Assembly Bottom        | ODB++ Layer / PDF               |
| **Keepout-Flächen**        | Keepout                         | Keepout                | ODB++ Layer / DRC               |
| **Fiducials**              | Fiducials                       | Fiducial Markers       | ODB++ Layer / Silkscreen        |






---
#Eagle #Pulsonix #PCB

