# NeoSoft Connect 5000 – Home Assistant Integration

![Dashboard-Preview](dashboard.png)

Dieses Projekt bindet eine **SYR NeoSoft Connect 5000**-Enthärtungsanlage vollumfänglich in Home Assistant ein:

| Funktion | Beschreibung |
|----------|--------------|
| **REST-Paket** `neosoft_connect.yaml` | holt alle Betriebsdaten (Flow, Druck, Temperatur, Volumen, Härte-Werte, Salz-/Reserve-Level, Regeneration, Wartung) direkt vom Steuerkopf <br>`http://<IP>:5333/neosoft/get/*` |
| **Template-Sensoren** | • Gesamtvolumen *m³* <br>• Restreichweite Reserve-Flasche 1 (Tage) <br>• Timestamp der letzten Regeneration F1 |
| **Utility-Meter** | Tages- & Monats-Verbrauch (Liter & m³) |
| **REST-Command** | manueller Regenerations-Trigger |
| **Lovelace-Dashboard** | 2-Spalten-Grid mit: <br>• Live-Übersicht aller Sensoren <br>• Gauges (Druck, Durchfluss, Roh/Weichwasser) <br>• 24 h-Min/Max-Statistik für Leitungsdruck <br>• Verlauf Gesamtvolumen <br>• Button „Regeneration starten“ |

---

## Voraussetzungen

* SYR NeoSoft Connect 5000 mit aktivierter Lokalschnittstelle (Port **5333**)
* Sie müssen die IP-Adresse noch in den YAML hinzufügen die ihre SYR Neosoft hat.
* Home Assistant ≥ 2023.9 (wegen *statistics-graph*-Card)
* Ordner-Struktur  
