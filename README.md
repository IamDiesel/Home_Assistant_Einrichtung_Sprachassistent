## Home_Assistant_Einrichtung_Sprachassistent
Anleitung wie Rhasspy-Speech und Home-Assistant als digitaler Assistent genutzt werden kann
Sprachassistent Home Assistant

Text 2 Speech
•	Hierfür das rhasspy-speech add on direkt in home assistant installieren:
  <img width="772" height="153" alt="image" src="https://github.com/user-attachments/assets/0f66831e-188c-4001-8970-2fc76c32f84f" />

•	Nach der Installation unter Geräte die Integration einrichten
 <img width="945" height="255" alt="image" src="https://github.com/user-attachments/assets/07f08655-30cb-4249-9fd3-e15ff76fd933" />


•	Unter Einstellungen  Sprachassistenten: Konfiguration wie folgt

 <img width="457" height="746" alt="image" src="https://github.com/user-attachments/assets/6bbb1de0-d82c-4f4c-a9b2-5d4f81565acd" />

•	Unter Einstellungen  Sprachassistenten: Entitäten verfügbar machen: Entitäten, die über den Sprachassistenten gesteuert werden sollen müssen hier freigegeben werden. Es können zudem Alias Namen vergeben werden:

 <img width="945" height="236" alt="image" src="https://github.com/user-attachments/assets/b077fccb-5b1f-446c-ac97-f1a0fbd1f669" />


•	Add on konfigurieren: 
o	Unter Einstellungen  Addons  rhasspy-speech auf den Button „Benutzeroberfläche öffnen“ klicken. Dann „Edit senteces“

 <img width="945" height="192" alt="image" src="https://github.com/user-attachments/assets/b68f332b-9336-4162-8b65-6670e6a89f66" />

```
sentences:
  - in: "schalte {name} (an|aus)"
```

o	KI tranieren: Auf „Start training“ klicken

 <img width="538" height="196" alt="image" src="https://github.com/user-attachments/assets/8c666932-0661-4b98-9f3b-ef0888962291" />

•	Am Handy  Einstellungen  Standard App digitaler Asisstent: Home Assistant auswählen

 <img width="237" height="530" alt="image" src="https://github.com/user-attachments/assets/5f65c530-d24e-4a33-9e7f-7b73cb3d08fc" />


Jetzt kann per Sprachbefehl beispielsweise eine Kaffemaschine angeschaltet werden (dabei ist „Kaffe“ ein Alias:

Hinweis: Die HA Companion App wird vorausgesetzt.

 <img width="289" height="294" alt="image" src="https://github.com/user-attachments/assets/42956f6f-571e-4b8e-b80b-ede6acb827af" />


## Automatische Assistenten Umschaltung
Jetzt kann zwar dauerhaft per Sprachbefehl eine lokal laufende KI verwendet werden, allerdings entfällt für Anwendungen außerhalb der Smart Home Steuerung der digitale Assistent.

Da ich den Google-Assistenten nur nutze wenn ich unterwegs bin, habe ich eine Automation erstellt, welche, sobald abhängig davon ob ich mit dem Home-WLAN verbunden bin, den digitalen Assistenten umschaltet. Sprich Nicht-Zuhause=Google-Assistant, Zuhause=Home-Assistant

•	Automate auf dem Handy installieren: https://play.google.com/store/apps/details?id=com.llamalab.automate

 <img width="154" height="344" alt="image" src="https://github.com/user-attachments/assets/ee8fd19f-ed86-4f8a-9f71-2e91b94aac37" />

•	Automate öffnen, unter Settings Privileged service start method auf “Wireless debugging” stellen und den Anweisungen folgen (Es muss Wireless Debugging installiert und ein PIN eingegeben werden)

 <img width="515" height="573" alt="image" src="https://github.com/user-attachments/assets/a7dd870b-b81f-4a2b-a47e-e8ea5619ad9e" />

•	Unter Settings  Privileges folgende Rechte vergeben:

 <img width="232" height="1488" alt="image" src="https://github.com/user-attachments/assets/99b7a548-acc5-4c89-82dd-e052b091b3c8" />

•	Einen neuen Flow erstellen:

 <img width="351" height="784" alt="image" src="https://github.com/user-attachments/assets/459c1f70-c27d-4c8c-9310-923f509c39d8" />

o	Im Knoten „Wifi Network connected?” die WLAN SSID angeben und unter „Proceed“ „When changed“ auswählen und speichern
o	Im linken Shell CMD Knoten folgendes CMD eintragen: settings put secure assistant io.homeassistant.companion.android/.assist.AssistActivity
o	In den rechten beiden Shell CMD Knotend folgende CMDs eintragen: 
com.google.android.googlequicksearchbox/com.google.android.voiceinteraction.GsaVoiceInteractionService

•	Falls die CMDs falsch sind, können sie dem „Settings finder“ die entsprechenden Befehle gefunden werden. Hierfür einfach diese Routine ausführen und im Anschluss den digitalen Asisstenten in den Einstellungen von Home Assistant auf Google und wieder zurück ändern.

