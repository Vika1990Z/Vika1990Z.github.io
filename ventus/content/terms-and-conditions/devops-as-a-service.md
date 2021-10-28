---
title: Devops as a Service
weight: 10
---
___
Leistungsbeschreibung & zusätzliche Bedingungen DevOps-as-a-Service ist eine DevOps-Tool-Umgebung für eine container-basierte Software-Entwicklung. Der Kunde erhält über Ventus Cloud Console Zugriff auf nachfolgende DevOps-Funktionen.

Leistungsbeschreibung & zusätzliche Bedingungen DEVOPS-AS-A-SERVICE

*Stand: 25.11.2020*
*Version: 1*
___

## Funktionen

### DevOps-Funktionen

Die Ventus Cloud stellt dem Kunden nachfolgende DevOps-Funktionen innerhalb einer Tool-Umgebung bereit. Die Ventus Cloud ist frei, durch welche Software-Tools in welcher Version die DevOpsFunktionen realisiert werden. Folgend ist der aktuelle Stand von DevOps-Funktionen und Software-Tools dargestellt:

|DevOps-Funktion|Tools|
| :- | :- |
|Issue Tracking / Agile Boards|Hubspot Service Desk|
|Collaboration / Dokumentation|Confluence|
|Source Code Management|GitHub, BitBucket|
|Continuous Integration / Delivery|Jenkins, GitLab, Atlassian|
|Artifact Repository / Docker Registry|Ventus Cloud S3 Object Storage|
|Container Management|Kubernetes|

Die Ventus Cloud wird den Kunden über Änderungen der Software-Tools per E-Mail informieren.

### Katalogbereitstellung

Im Rahmen der DevOps-Funktion Container Management stellt die Ventus Cloud einen definierten Anwendungskatalog bestehend aus einem oder mehreren Docker Containern mit Konfigurationshilfen bereit.

Der Kunde kann die in den Containern enthaltenen Anwendungen in seiner Umgebung installieren und betreiben. Der jeweils aktuelle Inhalt des Katalogs kann über die DevOps-Funktion Container Management eingesehen werden.

Mit Nutzung der im Katalog bereitgestellten Anwendungen akzeptiert der Kunde die im Katalog angezeigten Nutzungsbedingungen der jeweiligen Softwarehersteller. Durch die Installation kommt eine separate Vereinbarung zwischen dem Nutzer und dem jeweiligen Softwarehersteller zu den jeweils hinterlegten Nutzungsbedingungen zustande.

{{% notice note %}}
Der Katalog wird durch die Ventus Cloud regelmässig angepasst. Dies bedeutet, dass bestehende Images aktualisiert werden oder entfallen können oder neue Images hinzugefügt werden können.
{{% /notice %}}

### Ventus Cloud Console und Nutzer-Management

Der Kunde erhält über Ventus Cloud Console Zugriff auf das zentrale Nutzer-Management und die einzelnen DevOps-Funktionen. Das zentrale Nutzer-Management bietet dem Kunden folgende Funktionen als Self-Service:

- Anlegen und Löschen von Projekten. Pro Kunde ist die Anzahl der Projekte unbeschränkt.
- Anlegen, Ändern und Löschen von Nutzer-Konten im Rahmen
- Passwortverwaltung
- Zuordnung von Nutzern zu Projekten
- Zuordnung von Nutzern zu Rollen/Gruppen in Projekten
  Die definierten Rollen können abgestuften Privilegien zur Nutzung und Konfiguration der Software-Tools haben

Durch das zentrale Nutzerverzeichnis können sich alle Nutzer mit ihrem Konto auf allen Tools mit dem gleichen Nutzername anmelden.

Nutzer-Namen sind in Form von E-Mail-Adressen der Nutzer anzulegen.

Aus dem gebuchten Nutzer-Paket ist ein Nutzer-Konto für die System-Administration und die Umsetzung von Service Requests durch den Service Desk reserviert.

### Architektur
{{% notice note %}}
Das folgende Bild zeigt eine schematische, beispielhafte Übersicht der Systemarchitektur, Anbindung der Ziel-Umgebungen und Zugriff durch die Nutzer.  
{{% /notice %}}

![](../../assets/images/terms/1.png?classes=border,shadow) 

### Technische Merkmale

1. Die Tool-Umgebung wird pro Kunde in einer logisch isolierten Mandanten auf dedizierten virtuellen Servern und IP-Subnetzen realisiert.
1. Nutzer greifen verschlüsselt per SSL/TLS über das Internet auf die Software-Tools zu.
1. Der Kunde kann durch die Verwendung DevOps-Funktionen Docker-Container mit seinen Applikationen erstellen. Diese können mit der DevOps-Funktion für das Container Management in die kundeneigene Ziel-Umgebung eingespielt werden (Deployment).
1. DevOps-as-a-Service unterstützt nur Ziel-Umgebungen, die mit dem Software-Tool der DevOps-Funktion für Container Management kompatibel sind (insb. Betriebssystem und Docker-Version) und ausgehende Verbindungen in das Internet aufbauen können.

Weiterhin kann der Kunde feste public IP-Adressen bestellen. Die festen IP-Adressen ermöglichen es Verbindungen in die Zielumgebung des Kunden mit einer bekannten IP-Adresse aufzubauen.

-----
## LEISTUNGEN DER VENTUS CLOUD

#### Bereitstellung

Die Ventus Cloud legt die Tool-Umgebung und ein Nutzer-Konto mit Administrator-Rolle an. Hiernach versendet die Ventus Cloud eine E-Mail an den Kunden mit Zugangsdaten und der URL zur Ventus Cloud Console, sowie Kontaktinformationen für den Service Desk (Ready-for-Service E-Mail). Mit Versendung der Ready-for-Service E-Mail, spätestens mit Nutzungsbeginn, ist die Bereitstellung der Leistung abgeschlossen.

#### Betrieb

**Ort der Leistungserbringung**  

Die Ventus Cloud stellt die Leistungen aus Rechenzentren in Österreich, Schweiz und Deutschland bereit. Die Ventus Cloud erbringt die Support- und Betriebsleistungen in der Europäischen Union und der Schweiz.

#### Betriebszeiten

1. **Betriebszeit**  
   Die Betriebszeit ist Montag bis Sonntag 0:00 Uhr bis 24:00 Uhr. Innerhalb der Betriebszeit kann die Leistung genutzt werden.
1. **Betreute Betriebszeit (AOT):**  
   Die betreute Betriebszeit ist Montag bis Freitag, jeweils 8:00 Uhr bis 18:00 Uhr (MEZ/MESZ), ausser an schweizer Während der betreuten Betriebszeit erbringt die Ventus Cloud Betriebs- und Supportleistungen.

### Betriebs- und Supportleistungen

#### Bereitstellung Service Desk

Die Ventus Cloud stellt benannten Nutzern des Kunden einen [Service Desk](https://share.hsforms.com/1L4qNGjNUSpGqJDMl3SN8Yg4wnqg?__hstc=242763933.13b00a3271ac607f313707b3c27f9c1a.1606133566041.1635345485486.1635410062714.240&__hssc=242763933.10.1635410062714&__hsfp=2187346942) als zentralen Kommunikationspunkt bereit. Der Service Desk erbringt folgende Leistungen:

- Annahme und Bearbeitung von Störungsmeldungen des Kunden
- Erkennung von Alarmen im Monitoring und deren Bearbeitung
- Information des Kunden über Störungen an die benannte E-Mail-Adresse (Standard) bzw. über die benannte Telefonnummer (**Urgent**)
- Annahme und Bearbeitung von Service-Requests des Kunden
- Information des Kunden über Wartungsarbeiten
- Early-Life-Support
  Bis zu 4 Wochen nach Bereitstellung der Leistung unterstützt die Ventus Cloud den Kunden bei Fragen zur Benutzung der Tool-Umgebung.

{{% notice note %}}
Der Kunde kann den Service Desk per ChatBot oder [E-Mail](mailto:support@ventus.ag) kontaktieren. Die Kontaktdaten des Service Desk werden zusammen mit der Ready-for-Service-E-Mail kommuniziert. Die Kommunikation durch den Kunden mit dem Service Desk erfolgt grundsätzlich in englischer Sprache. Eine Kommunikation auf Deutsch ist, soweit verfügbar, möglich.
{{% /notice %}}

#### Störungsbearbeitung

Störungen werden durch die Ventus Cloud entsprechend ihrer Kritikalität bearbeitet. Dabei klassifiziert die Ventus Cloud Störungsmeldungen wie folgt:

|**Urgent**|Ein oder mehrere DevOps-Funktionen oder das zentrale Nutzer-Management sind nicht erreichbar bzw. vollständig nicht nutzbar.|
| :- | :- |
|**Standard**|Einzelne DevOps-Funktionen sind nur eingeschränkt oder mit verminderter Leistung nutzbar, oder der Grund der Störung liegt in der Verantwortung des Kunden.|


Die Ventus Cloud informiert den Kunden über den Status der Störungsbearbeitung. Sofern die Ventus Cloud Supportverträge für einzelne Software-Tools abgeschlossen hat, bindet die Ventus Cloud den Hersteller-Support in die Störungsbearbeitung ein.

Die Ventus Cloud ist berechtigt, Störungen durch einen Workaround zu beheben.

{{% notice warning %}}
Ist die Ursache einer Störung die Auslastung oder Überlastung der Kapazitäten des Kunden (z.B. Disk-Kapazität, vCPU/ vRAM überlastet), informiert die Ventus Cloud den Kunden. Der Kunde ist in diesem Fall verpflichtet, durch eine Mindernutzung (z.B. Last verringern, Daten löschen) oder, sofern technisch möglich, eine kostenpflichtige Erweiterung der Kapazitäten die Ursache dieser Störung zu beheben.
{{% /notice %}}

#### Patch Management

Die Ventus Cloud installiert nach eigenem Ermessen für die von der Ventus Cloud bereitgestellten Leistungen im Rahmen der Wartungsarbeiten durch Hersteller bereitgestellte Patches bzw. Minor Updates.

#### Housekeeping

Die Ventus Cloud bereinigt die durch die Leistungserbringung der Ventus Cloud generierten Logfiles und temporären Dateien, um die genutzten Ressourcen des Kunden zu reduzieren.

#### Monitoring

Die Ventus Cloud überwacht die bereitgestellten Services und die zugrunde liegende Infrastruktur, um Störungen der vereinbarten Leistung proaktiv zu erkennen und Alarme zu generieren.

#### Backup

Die Ventus Cloud führt ein tägliches Backup der Server der Tool-Umgebung durch, um diese im Desaster-Fall wiederherstellen zu können. Das Backup dient nicht der Wiederherstellung einzelner Daten des Kunden. Das Backup wird automatisiert ausserhalb der betreuten Betriebszeit durchgeführt. Während des Backups kann es zu kurzen Unterbrechungen oder Beeinträchtigungen der Services kommen.

#### Service Requests

Der Service Desk der Ventus Cloud führt auf Anfrage des Kunden Unterstützungsleistungen und Änderungen an der bereitgestellten technischen Konfiguration der Tool-Umgebung durch:

1. Kapazitätsanpassungen
1. Konfigurationsanpassungen
1. Unterstützung bei konkreten fachlichen Fragestellungen zur Nutzung der DevOps-Funktionen
1. Unterstützung bei Datensicherung

Die Ventus Cloud ist berechtigt einen Service Request abzulehnen, wenn dieser die Leistungserbringung der Ventus Cloud negativ beeinflussen kann.

Die bei der Ventus Cloud entstehenden Aufwände zur Umsetzung von Service Requests werden gemäss aktueller Preisliste berechnet.

### Wartungsarbeiten

Die Ventus Cloud führt regelmässig Wartungsarbeiten durch. Sollten diese Wartungsarbeiten zu Unterbrechungen der Leistung führen, wird die Ventus Cloud den Kunden vorab informieren. Die Ventus Cloud ist hierbei bestrebt, Beeinträchtigungen durch Wartungsarbeiten möglichst gering zu halten. Wartungsarbeiten gelten nicht als Ausfallzeiten und bleiben daher bei der Berechnung der Verfügbarkeit unberücksichtigt.

{{% notice note %}}
Im Falle von Notfall-Wartungsarbeiten erfolgt eine Information der Kunden ggf. nachträglich.
{{% /notice %}}

### Leistungsübergabepunkt

Die Verantwortung der Ventus Cloud endet am Leistungsübergabepunkt. Leistungsübergabepunkt der Ventus Cloud ist jeweils die Web-Anwendung der in der Tool-Umgebung laufenden einzelnen Software-Tools und die Ventus Cloud Console am Eintrittspunkt des Rechenzentrums in das Internet.

### Service Qualität

Die nachfolgende Verfügbarkeit bezieht sich ausschliesslich auf die betreuten Betriebszeiten der jeweiligen DevOps-Funktion. Ausserhalb der betreuten Betriebszeit gilt für die Leistung keine Mindestverfügbarkeit aus beim Nutzungspaket - Enterprise. Die Ventus Cloud ist jedoch bemüht Einschränkungen der Leistung gering zu halten.

**Verfügbarkeit**:  
Die Verfügbarkeit pro DevOps-Funktion beträgt 99,0% je Kalendermonat am Leistungsübergabepunkt und wird wie folgt berechnet:

|Summe Minuten betreute Betriebszeit– Summe Ausfallminuten|x 100 %|
| :- | :- |
|Summe Minuten betreute Betriebszeit||
Summe Minuten betreute Betriebszeit – Gesamte Anzahl der Minuten innerhalb der betreuten Betriebszeit (AOT) eines Monats

Summe Ausfallminuten – Anzahl der Minuten eines Kalendermonats, in der die betrachtete DevOps-Funktion nicht verfügbar war, abzüglich der ausgeschlossenen Ereignisse (Excused Events). Als Kriterium dienen die Ergebnisse des Monitorings am Leistungsübergabepunkt. Die Ventus Cloud stellt dem Kunden die erreichte Verfügbarkeit über https://uptime.ventuscloud.eu zu Verfügung.

>**Excused Events:**
>
>Ausfallzeiten auf Grund eines der nachfolgenden Ereignisse bleiben bei der Berechnung der Verfügbarkeit unberücksichtigt:
>- Ausfälle aufgrund von Wartungsarbeiten
>- Störungen, Ausfälle und Probleme, die auf den Kunden, seine Mitarbeiter oder Vertreter zurückzuführen sind, insbesondere Ausfälle auf Grund einer Überschreitung der zur Verfügung gestellten Kapazitäten
>- Angriffe Dritter, z.B. durch (D)DoS Attacken, Hacking, Spamming
>
>Gefährdung oder Störung für Leistungen Dritter.  
>Die Ventus Cloud ist berechtigt, die Leistung für den Kunden ohne vorherige Benachrichtigung, bis zur Behebung einer Gefährdung oder Störung für Leistungen Dritter oder die Infrastruktur der Ventus Cloud, zu deaktivieren.

**Störungsbearbeitung:**

Für die Störungsklasse Urgent beträgt die Reaktionszeit innerhalb der betreuten Betriebszeit 1h. Die Reaktionszeit stellt die Zeitspanne von Meldung oder Auftreten der Störung bis zur ersten Bestätigung des aktuellen Status an den Kunden dar.

#### Nutzungsrechte, Lizenzen

Soweit für die Leistungserbringung erforderlich erhält der Kunde für die Laufzeit des Vertrags ein einfaches Nutzungsrecht an den nachfolgend aufgeführten Software-Tools der benannten Hersteller.

Durch die Nutzung der DevOps-Funktionen akzeptiert der Kunde die nachfolgend aufgeführten Nutzungsbedingungen der Hersteller der zur Realisierung der jeweiligen DevOps-Funktion eingesetzten Software-Tools. Hierdurch kommt eine Vereinbarung zwischen dem Kunden und dem jeweiligen Software-Hersteller zustande.

- Jenkins (Continuous Integration / Delivery): https://jenkins.io/license/

#### Einseitige Leistungsänderungen

Die Ventus Cloud behält sich einseitige Leistungsänderungen und Entgeltreduzierungen zu Gunsten des Kunden vor. Der Kunde erklärt sich mit diesen Anpassungen einverstanden.

In Abweichung zu dem vereinbarten Schriftformerfordernis wird die Ventus Cloud den Kunden über diese Anpassungen durch Übersendung aktualisierter Versionen der bestehenden Vertragsunterlagen per E-Mail informieren, welche die bestehenden Unterlagen ersetzen.

#### Optionale Leistungen

Die nachfolgend beschriebenen optionalen Leistungen werden bei gesonderter Beauftragung gegen zusätzliche Vergütung durch die Ventus Cloud erbracht. Auf Anfrage wird die Ventus Cloud dem Kunden ein Angebot unterbreiten, sowie detaillierte Beschreibungen zu den nachfolgenden Leistungen zur Verfügung stellen.

#### Erweiterte Betriebsleistung

Die Ventus Cloud stellt folgende erweiterte Betriebsleistungen zur Verfügung:

- Die Betriebsleistungen Service Desk, Störungsbearbeitung und Monitoring werden auch ausserhalb der betreuten Betriebszeit, also Montag bis Sonntag 0:00 bis 24:00 (MEZ/MESZ) erbracht.
- Die Formel zur Berechnung der Verfügbarkeit wird dementsprechend auf die erweiterte Betriebsleistung angepasst.
- Wartungsarbeiten werden regelmässig nicht Montag bis Freitag 8:00 bis 18:00 durchgeführt.

### Try & Buy

Die Ventus Cloud stellt dem Kunden zwecks Test seiner Anforderungen an die Leistung das Developer Nutzerpaket für zwölf Monate als Try-and-Buy-Option bereit. Für die Try-and-Buy-Option gelten folgende Bestimmungen:

- Die Try-and-Buy-Option endet zwölf Monaten nach Ihrer Bereitstellung. Bis dahin ist die Leistung nach zwei Monaten jederzeit mit einer Frist von einem Monat zum Monatsende kündbar.
- Wird die Try-and-Buy-Option nicht bis zu Ihrem Ende gekündigt, wird das Developer-Nutzerpaket zu den regulären Bedingungen (insbesondere Laufzeit und Kündigung und Preise) fortgeführt.
- Der Kunde kann während der Try-and-Buy-Option jederzeit ein höherwertiges Nutzerpaket beauftragen. Mit Bereitstellung des höherwertigen Nutzerpaketes endet die Try-and-BuyOption. Für das höherwertige Nutzerpaket gelten die regulären Bestimmungen.

### Consulting-Paket

Die Ventus Cloud bietet für DevOps-as-a-Service folgende Beratungsleistungen an, die über die Beantwortung einzelner konkreter fachlicher Fragestellungen hinausgehen:

- Erläuterung der Tools und deren Interaktion
- Benutzung und Konfiguration der Tools
- Lösung von Integrationsfragen
- Migrations-Support
- Schulungen
- Workshops

### Individuelle Nutzerpakete

Die Ventus Cloud stellt dem Kunden auf[ Anfrage](mailto:support@ventus.ag) auf seine Bedürfnisse zugeschnittene Nutzerpakete bereit.

-----
## MITWIRKUNGSLEISTUNGEN DES KUNDEN
Der Kunde verpflichtet sich, alle Leistungen, die zur ordnungsgemässen Leistungserbringung erforderlich sind, insbesondere jedoch nachfolgende Leistungen unentgeltlich, rechtzeitig und in erforderlichem Umfang zu erbringen.

### Allgemeine Mitwirkungsleistungen

1. Der Kunde hat alle für die Erbringung der Leistung erforderlichen und geeigneten Nutzungsrechte und kompatible Softwarelizenzen (einschliesslich Updates oder Upgrades) beizustellen, soweit diese nicht durch die Ventus Cloud auf Grund einer schriftlichen Vereinbarung beizustellen sind.
1. Der Kunde erklärt sich mit dem unverschlüsselten Schriftwechsel per E-Mail einverstanden und wird stets aktuelle E-Mail-Adressen hinterlegen. Dem Kunden ist bekannt, dass für die Leistungserbringung wesentliche Informationen, wie Zugangsdaten, Informationen zu Änderungen der Leistungen und der rechtlichen Bedingungen, Passwortrücksetzung, sowie Rechnungen ausschliesslich per Mail versendet werden.
1. Der Kunde prüft eigenverantwortlich, ob die von ihm im Zusammenhang mit der Nutzung der Leistung an die Ventus Cloud übermittelten Daten personenbezogene Daten darstellen und die Verarbeitung dieser personenbezogenen Daten zulässig ist. Sofern der Kunde personenbezogene Daten verarbeiten lassen möchte, wird dieser eine Vereinbarung über die Verarbeitung personenbezogener Daten nach dem Data Processing Agreement (DPA) der Ventus Cloud abschliessen, welches die Ventus Cloud dem Kunden auf Anfrage zur Verfügung stellt.
1. Der Kunde ist verpflichtet, seine Daten in anwendungsadäquaten Intervallen in geeigneter Form zu sichern, damit diese mit vertretbarem Aufwand wiederhergestellt werden können. Eine Datensicherung zur Wiederherstellung von Kunden-Daten durch die Ventus Cloud findet nicht statt.
1. Der Kunde prüft eigenverantwortlich alle für Ihn im Zusammenhang mit der Nutzung der Leistung relevanten und anwendbaren rechtlichen Vorschriften, Gesetze, Verordnungen und branchenspezifischen Bestimmungen und stellt deren Einhaltung sicher. Dazu zählen insbesondere auch die Einhaltung von Geheimhaltungsverpflichtungen, die z.B. aus einer beruflichen Tätigkeit herrühren.
1. Der Kunde stellt sicher, dass die Leistungen nicht missbräuchlich genutzt werden.
1. Der Kunde ist verpflichtet, einen qualifizierten und entscheidungsbefugten Ansprechpartner zu benennen und dessen Erreichbarkeit/Vertretung sicherzustellen.
1. Der Kunde stellt die Erbringung erforderlicher Mitwirkungsleistungen durch seine Vertragspartner oder sonst dem Kunden zuzurechnende Dritte sicher.
1. Der Kunde ist verpflichtet Passwörter und Zugangsdaten geheim zu halten, nur an berechtigte Dritte weiterzugeben, bzw. diese vor unberechtigtem Zugriff zu schützen und soweit erforderlich zu ändern. Der Kunde wird die Ventus Cloud unverzüglich bei Anhaltspunkten der Kenntnisnahme durch unberechtigte Dritte informieren. Des Weiteren ist es untersagt, dass ein persönliches Nutzer-Konto von mehreren Personen genutzt wird.
1. Der Kunde stellt sicher, dass er keine Inhalte nutzen, auf dem vertragsgegenständlichen Speicherplatz speichern oder sonst zugänglich machen wird, die Schadsoftware enthalten und/oder deren Bereitstellung, Veröffentlichung, Übertragung oder Nutzung gegen geltendes Recht oder Rechte Dritter verstösst, dies gilt insbesondere für ehrverletzende, volksverhetzende oder rechtsradikale Inhalte. Dem Kunden ist es untersagt, Leistungen für den Versand von Massen-E-Mails (SPAM) zu nutzen.
1. Der Kunde stellt sicher, dass durch seine Nutzung der Leistung keine Gefährdung oder Störung Dritter oder der Infrastruktur der Ventus Cloud ausgeht. Im Falle einer solchen Gefährdung oder Störung (z.B. auf Grund einer DDoS-Attacke) ist die Ventus Cloud ohne vorherige Benachrichtigung des Kunden berechtigt, die betroffene Leistung bis zur Behebung der Gefährdung oder Störung zu deaktivieren. Die hierdurch entstehenden Ausfallzeiten bleiben bei der Berechnung der Verfügbarkeit unberücksichtigt. Die Ventus Cloud wird den Kunden informieren.
1. Der Kunde versichert, dass alle Angaben wahrheitsgemäss sind. Besteht der Verdacht, dass der Kunde dieser Verpflichtung nicht vollständig nachgekommen ist oder dass der Kunde Opfer eines Angriffs Dritter wurde, ist die Ventus Cloud berechtigt, die Leistungen des Kunden auf dessen Kosten zu reduzieren bzw. zu sperren. Der Kunde bleibt in diesem Fall verpflichtet, die vereinbarten Entgelte zu zahlen. Die hierdurch entstehenden Ausfallzeiten bleiben bei der Berechnung der Verfügbarkeit unberücksichtigt. Die Ventus Cloud wird den Kunden informieren.
1. Der Kunde wird die Ventus Cloud unverzüglich schriftlich informieren, wenn er eine Mitwirkungsleistung nicht wie vereinbart erbringen kann.
1. Der Kunde stellt der Ventus Cloud alle erforderlichen Informationen zur Verfügung und stellt sicher, dass seine Angaben inhaltlich richtig und stets aktuell sind.
1. Die Ventus Cloud empfiehlt zur Nutzung die Browser Google Chrome und Mozilla Firefox in jeweils aktueller Version. Der Microsoft Internet Explorer wird nicht unterstützt.
1. Die Leistungen werden dem Kunden innerhalb Ventus Cloud Console Der Kunde ist daher insbesondere für die Konfiguration, Kapazitätsmanagement und die sonstige Bedienung des Service selbst verantwortlich.

### Mitwirkungsleistungen im Rahmen des Betriebs

1. Der Kunde ist verpflichtet sich auf Anforderung gegenüber dem Service Desk der Ventus Cloud zu authentifizieren.
1. Der Kunde ist verpflichtet, Störungen oder Beeinträchtigungen der Leistungen unverzüglich mit einer nachvollziehbaren Schilderung der Fehlersymptome anzuzeigen.
1. Der Kunde ist verpflichtet bei der Behebung einer Störung zu unterstützen. Insbesondere führt der Kunde vor einer Störungsmeldung soweit möglich eine Selbstprüfung durch, um auszuschliessen, dass die Störungsursache in seinem Verantwortungsbereich liegt.
1. Der Kunde ist verpflichtet, soweit erforderlich bei der Planung und Durchführung von Wartungsarbeiten zu unterstützen.
1. Der Kunde führt ein Kapazitätsmanagement der Tool-Umgebung durch, so dass die zur Verfügung gestellten Kapazitäten nicht vollständig ausgelastet oder überlastet werden.
1. Zur durchgängigen Nutzung der DevOps-Funktionen stellt der Kunde sicher, dass Software Entwicklung, Build-Prozesse und Deployments der Kunden-Applikationen auf Basis von Docker-Containern erfolgen.
1. Der Kunde bindet die Ziel-Umgebungen für das Deployment der erstellten Container in das Tool für Container Management selbständig ein. Die Verantwortung für die Ziel-Umgebung und das Deployment der erstellten Container in die Ziel-Umgebungen verbleibt vollständig beim Kunden und ist kein Bestandteil der Leistung der Ventus Cloud. Ebenso liegt die Verantwortung für die über die Tool-Umgebung erstellten Container inkl. der enthaltenen Software und Daten vollständig beim Kunden.

### Mitwirkungsleistungen bei Beendigung der Leistung

Der Kunde muss selbständig – vor Beendigung des Vertrags – alle von ihm benötigten Daten in der Tool-Umgebung durch Nutzung von Funktionen und Schnittstellen der Tools herunterladen und eigenverantwortlich sichern.

-----

## MINDESTÜBERLASSUNGSZEIT/BEENDIGUNG

### Mindestlaufzeit und Kündigung

Ein Nutzerpaket hat eine Mindestlaufzeit von 12 Monaten ab Bereitstellung der Leistung. Die Leistung kann unter Einhaltung einer Frist von drei (3) Monaten erstmalig zum Ablauf der Mindestlaufzeit gekündigt werden. Anderenfalls verlängert sich diese automatisch um zwölf (12) Monate und kann dann mit einer Frist von drei (3) Monaten zum Ende des jeweiligen Verlängerungszeitraums gekündigt werden.

### Änderung der Paketgrösse

Der Wechsel in ein grösseres Nutzer-Paket ist während und nach Ende der Mindestlaufzeit mit einer Frist von 2 Wochen zum Monatsende möglich. In diesem Falle beginnt die Mindestlaufzeit von 12 Monaten zum Zeitpunkt der Bereitstellung der Änderung erneut. Der Wechsel in ein kleineres Nutzer-Paket ist erst nach Ende der Mindestvertragslaufzeit mit einer Frist von 2 Wochen zum Monatsende möglich.

### Beendigung

Alle Preise verstehen sich zzgl. der zum Zeitpunkt der Lieferung und Leistung geltenden Steuern und Abgaben. Bei untermonatlicher Bereitstellung wird anteilig gemäss der Anzahl der Tage des jeweiligen Kalendermonats abgerechnet.

### Nutzer Pakete und Preise

Die Vergütung erfolgt gemäss nachfolgender Preisliste für die einzelnen Nutzer-Pakete:

|** |**Developer**|**Business**|**Enterprise**|
| :- | :- | :- | :- |
|**Reaktionszeit**|Best effort|8h zu Bürozeiten|3h, 24/7|
|**Durchschnittl. Wiederherstellungszeit**|Best effort|8h zu Bürozeiten|3h, 24/7|
|**Garantierte Verfügbarkeit des Services** |Best effort|99,5%|99,9%|
|**Erwartete Verfügbarkeit des Services** |99,5%|99,9%|99,95%|
|**Backup**|-|1x täglich|Mind. 1x täglich, nach Absprache|
|**Installations-Consulting**|-|Best effort|inkl.|
|**Laufende Kapazitätsplanung**|-|Best effort|inkl.|
|**Tuning**|-|-|inkl.|
|**Wartungsfenster**|1x wöchentlich|1x wöchentlich|Nach Absprache|
|**Anwendungsfälle**|<p>Prototyping, Developers,</p><p>Staging</p>|Normale produktive Verwendung, auch empfohlen für Systeme von Build- und Test-Pipelines|Geschäftskritische Verwendung, z.B. Webshops, Reservierungssysteme, ERP|
|**Kosten pro vRAM**|**CHF 9,- / 8,35 €**|**CHF 19,- / 17,60 €**|**CHF 29,- / 26,80 €**|

{{% notice note %}}
Auf [Anfrage](mailto:support@ventus.ag) bietet die Ventus Cloud auch grössere Nutzerpakete an.
{{% /notice %}}

### Preise für zusätzliche Betriebsleistungen

Zusätzliche Betriebsleistungen werden wie folgt zusätzlich berechnet:

|Option|Preis|
| :- | :- |
|Bearbeitungsaufwand für Störungsmeldungen des Kunden, die in seinem Verantwortungsbereich liegen|<p>CHF 30,- / 28,- € je angefangene 15 Minuten</p><p> </p>|
|Bearbeitungsaufwand zur Umsetzung von Service Requests des Kunden|<p>CHF 30,- / 28,- € je angefangene 15 Minuten</p><p> </p>|
-----

## NUTZERPAKET VERGLEICH

|<p>Managed Services</p><p> </p><p> </p>|<p>CHF Preis/</p><p>per 1GB vRAM</p>|8|16|32|64|128|256|RAM|
| :- | :- | :- | :- | :- | :- | :- | :- | :- |
|VM/Cluster Price| |51.3|98.4|192.7|385.5|770.9|1342.7| |
|**Developer Managed\***|9|**123.3**|**242.4**|**480.7**|**961.5**|**1922.9**|**3646.7**| |
|**Business Managed\***|19|**203.3**|**402.4**|**800.7**|**1601.5**|**3202.9**|**6206.7**| |
|**Enterprise Managed\***|29|**283.3**|**562.4**|**1120.7**|**2241.5**|**4482.9**|**8766.7**| |

*Managed Preise beinhalten VM o. Cluster Ressourcenpreise

-----

## GLOSSAR/ ABKÜRZUNGSVERZEICHNIS

|API|Application Programming Interface – Programmierschnittstelle einer Software|
| :- | :- |
|AOT|Attended Operation Time (betreute Betriebszeiten)|
|Container|Technik zur Isolierung von Anwendungen mit Container-Virtualisierung. Wird in diesem Dokument synonym für Container-Images (Speicherabbild eines Containers) und die aktive Laufzeitinstanz verwendet.|
|Deployment|Übertragung erzeugter Docker-Container bzw. deren Images in eine ZielUmgebung zum Zwecke der Ausführung|
|DevOps|Kunstwort aus „Development“ und „Operations“, definiert Methoden zur Verbesserung von Softwareentwicklung und -betrieb|
|<p>Release Upgrades</p><p> </p>|Upgrade auf eine neue Software Version, die über ein Minor Update oder Patch hinausgeht. Geht häufig mit Änderungen der Schnittstellen und Funktionen einher.|
|SSL|Secure Sockets Layer - Verschlüsselungsprotokoll zur sicheren Datenübertragung im Internet|
|URL|Uniform Resource Locator – Lesbare Adresse einer Webseite|
|vCPU|Virtuelle CPU (Central Processing Unit) eines virtuellen Servers|
|Virtual Machines|Logisch isolierte Umgebung in einer Cloud über dedizierte virtuelle Server, Subnetze und IP-Adressen|
|vRAM|Virtueller RAM (Random Access Memory) eines virtuellen Servers|



