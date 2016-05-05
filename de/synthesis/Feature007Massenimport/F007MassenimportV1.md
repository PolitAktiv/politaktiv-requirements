## Anforderungen Massenimport Version1

### Basis
Generelle Anmerkung mje:
* Validierung fehlt als Thema noch - wo werden die Daten validiert - und wie sehr sollen sie validiert werden?
* Muss der Import / Export per Portlet realisiert sein? Währe nicht eine einfache REST Schnittstelle mit einem kleinen Komandozeilen Tool viel billiger?


{% include "git+https://github.com/PolitAktiv/politaktiv-requirements.git/de/requirements/req0150.md" %}

Anmerkung mje:
* Wir haben 4 Files - wie benennen wir die denn?


{% include "git+https://github.com/PolitAktiv/politaktiv-requirements.git/de/requirements/req0151.md" %}

Anmerkung mje:
* Ich fürchte, der Tipp ist eine Anforderung - sonst müssts ja nicht umgesetzt werden.
* Portlet ausführen, betreten usw geht nicht. Wir könnten einen Wizzard-Flow starten und beenden.
* Verhindern, dass der Benutzer paralell anderes macht geht auch nicht.


{% include "git+https://github.com/PolitAktiv/politaktiv-requirements.git/de/requirements/req0152.md" %}

Anmerkung mje:
* "Jede Zeile ist ein Datensatz" geht nicht. Wir haben ja sicher Überschriften als Feldnamen.
* Müssen unterschiedliche Daten auch über ID verknüpft werden? 

{% include "git+https://github.com/PolitAktiv/politaktiv-requirements.git/de/requirements/req0153.md" %}

Anmerkung mje:
* Was hat es mit dem Probelauf auf sich?


### Steuerungsfelder
Damit das PA-Mimex-Portlet weiß, was es tun soll, benötigt es Steuerungsfelder.
{% include "git+https://github.com/PolitAktiv/politaktiv-requirements.git/de/requirements/req0154.md" %}

Anmerkung mje:
* Ein eigener, definierter Ordner ist für Import / Export sicher nützlich ...


{% include "git+https://github.com/PolitAktiv/politaktiv-requirements.git/de/requirements/req0157.md" %}

### Felder in den Files
{% include "git+https://github.com/PolitAktiv/politaktiv-requirements.git/de/requirements/req0155.md" %}
{% include "git+https://github.com/PolitAktiv/politaktiv-requirements.git/de/requirements/req0156.md" %}

Anmerkung mje:
* Ich fürchte das mit der Adition tut so nicht -1 + 1 = 0 ?. Warum nicht einfach für jede Steuerfunktion eine eigene Spalte mit (0|1) od (leer|x)?
 

{% include "git+https://github.com/PolitAktiv/politaktiv-requirements.git/de/requirements/req0158.md" %}

Anmerkung mje:
* Ist Security hier relevant (XSS) ?


{% include "git+https://github.com/PolitAktiv/politaktiv-requirements.git/de/requirements/req0159.md" %}
{% include "git+https://github.com/PolitAktiv/politaktiv-requirements.git/de/requirements/req0161.md" %} 

### Ergänzung im PA-AP
{% include "git+https://github.com/PolitAktiv/politaktiv-requirements.git/de/requirements/req0160.md" %} 

## Quelle
https://github.com/PolitAktiv/politaktiv-requirements/tree/master/de/domain/Feature007Massenimport/MassenimportDomainRequirements.md
