# NeoSoft Connect 5000 – Home Assistant Integration

![Dashboard-Preview](SYR_Neosoft_5000.png)

Dieses Projekt bindet eine **SYR NeoSoft Connect 5000**-Enthärtungsanlage vollumfänglich in Home Assistant ein.

| Funktion | Beschreibung |
|----------|--------------|
| **REST-Paket** `neosoft_connect.yaml` | Bereitstellung aller Betriebsdaten (Flow, Druck, Temperatur, Volumen, Härte-Werte, Salz-/Reserve-Level, Regeneration, Wartung, Flaschenkapazität, WIFI, LAN etc.) direkt von der Steuerung via <br>`http://<IP>:5333/neosoft/get/*` |
| **Template-Sensoren** | • Gesamtvolumen *m³* <br>• Restkapazität in Litern *l* Reserve-Flasche 1,0 (Tage) <br>• Timestamp der letzten Regeneration F1 |
| **Utility-Meter** | Tages- & Monats-Verbrauch (Liter & m³) |
| **REST-Command** | Manueller Regenerations-Trigger   ** Mehr Ausführungsbefehler wurden bewust weggelassen | 
| **Lovelace-Dashboard** | 2-Spalten-Layout mit: <br>• Live-Übersicht vieler Sensoren <br>• Balken/Gauges (Druck, Salz, Reserve) <br>• Statistik (7 Tage) <br>• Netzwerkstatus (WLAN/LAN) <br>• Systeminfos (Firmware/Serial) <br>• Button „Regeneration starten“ |

---

## Voraussetzungen

- **SYR NeoSoft Connect 5000** mit aktivierter **Lokalschnittstelle** (Port **5333**)
- **IP-Adresse** der Anlage muss in den YAML-Dateien eingetragen bzw. geändert werden (`<IP>` ersetzen)
- **Home Assistant ≥ 2023.9** (u. a. wegen moderner Dashboard-/Statistik-Funktionen)
- Passende **Ordnerstruktur** in deinem HA-Config-Verzeichnis (siehe unten)

---

## HACS / Frontend-Erweiterungen (für die Visualisierung)

Diese HACS-Frontend-Cards werden im bereitgestellten Dashboard-YAML **verwendet** und sind daher erforderlich über HACS etc. zu Installieren sonst funktioniert es nicht:

- **Mushroom Cards** (für `custom:mushroom-title-card`, `custom:mushroom-template-card`, `custom:mushroom-entity-card`)
- **card-mod** (für `card_mod: style: | ...` CSS-Styling)
- **bar-card** (für `custom:bar-card` Balkenanzeigen)
- **ApexCharts Card** (für `custom:apexcharts-card` Statistik/Charts)

> Hinweis: Standardkarten wie `grid`, `vertical-stack`, `conditional`, `markdown`, `heading` sind **Home Assistant Core** (kein HACS nötig).

---

## Ordner-Struktur

Beispiel (empfohlen):

```text
config/
  integrations/
    neosoft_connect.yaml
  lovelace/
    neosoft_dashboard.yaml
