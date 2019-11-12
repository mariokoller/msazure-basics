# 00-Grundlagen

Dieses Kapitel behandelt einerseits die Grundlagen zur Azure Plattform und zum REST API und dient des weiteren dazu, das man Ressourcen erstellt, welche zwingend für das Kapitel 01-Azure Login und 02-VM notwendig sind.

### **Lernziele**
Nach Abschluss des Kapitels 00-Grundlagen, kennen Sie den Aufbau der Azure Plattform, haben die ersten Ressourcen angelegt und Wissen was das REST API ist.

### **Inhaltsverzeichnis**
- [Azure Plattform](#Azure-Plattform)
- [Ressourcen erstellen](#Ressourcen-erstellen)
- [REST API](#REST-API)

# Azure Plattform

> [&uarr; *Zum Inhaltsverzeichnis*](#Inhaltsverzeichnis)

### **Übersicht**
Zuerst einmal eine kurze Übersicht über alle Ressourcen die wir auf der Hauptseite sehen.<br>

Menüpunkte                                                             | Beschreibung
-----------------------------------------------------------------------|-----------------------------------
![](../Bilder/Ressourcen_erstellen.png)<br>Ressourcen erstellen        | Dies ist eine Art eine neue Ressource in Ihrem Azure Konto zu erstellen, weitere Möglichkeiten finden Sie in jedem Menüpunkt wieder.
![](../Bilder/Home.png)<br>Home                                        | Diese dient zur Navigation, somit gelangen Sie wieder zur Hauptübersicht Ihres Azure Kontos.
![](../Bilder/Dashboard.png)<br>Dashboard                              | Dies dient rein zur Übersicht, Sie können ein Dashboard nach belieben ändern und erstellen.
![](../Bilder/Alle_Dienste.png)<br>Alle Dienste                        | Sie suchen einen Dienst, wissen aber nicht in welchem Untermenü dieser sein soll, hier werden Sie sicher fündig.
![](../Bilder/Alle_Ressourcen.png)<br>Alle Ressourcen                  | Dies ist eine Übersicht aller Ressourcen, welche Sie bereits erstellt haben.
![](../Bilder/Ressourcengruppen.png)<br>Ressourcengruppen              | Sie können Ihre Ressourcen in Ressourcengruppen aufteilen um somit eine bessere Übersicht zu haben.
![](../Bilder/App_Services.png)<br>App Services                        | Erstellung, Entwicklung, Bereitstellung und Verwaltung von Web-Apps, mobiler Apps und API-Apps.
![](../Bilder/Funktions_App.png)<br>Funktions-App                      | Erstellung, Entwicklung, Bereitstellung und Verwaltung von Services für Web-Apps, mobile Apps und API-Apps.
![](../Bilder/SQL_Datenbanken.png)<br>SQL_Datenbanken                  | Dieser Menüpunkt, dient zur Erstellung von SQL-Datenbanken.
![](../Bilder/Azure_Cosmos.png)<br>Azure Cosmos DB                     | Dient zur Erstellung einer global verteilten Datenbank und der Entwicklung von Apps mithilfe der API Ihrer Wahl.
![](../Bilder/Virtuelle_Computer.png)<br>Virtuelle Computer            | Dieser Menüpunkt, dient zur Erstellung von SQL-Datenbanken.
![](../Bilder/Lastenausgleich.png)<br>Lastenausgleichsmodule           | Mit dem Lastenausgleichsmodul von Azure, können Sie für Clouddienste und VM's hochverfügbare und skalierbare Anwendungen erstellen.
![](../Bilder/Speicherkonten.png)<br>Speicherkonten                    | Jede Ressource die Sie in Ihrem Azure Konto anlegen, benötigt im Hintergrund einen Speicher, dieser Speicher wird hier angelegt.
![](../Bilder/Virtuelle_Netzwerke.png)<br>Virtuelle Netzwerke          | Ein virtuelles Netzwerkk (VNET) ist der grundlegende Baustein für Ihr privates Netzwerk in Azure. Mit VNET können zahlreiche Arten von Azure-Ressourcen (beispielsweise virtuelle Azure-Computer) sicher untereinander sowie mit dem Internet und mit lokalen Netzwerken kommunizieren.
![](../Bilder/Azure_Active_Directory.png)<br>Azure Active Directory    | Azure Active Directory (AAD) dient dazu in Ihrer Azure Cloud ein Active Directory hochzuziehen, damit können wie Sie es wahrscheinlich schon kennen, User, Sicherheitsgruppen usw. erstellt werden.
![](../Bilder/Monitor.png)<br>Monitor                                  | Mit Azure Monitor können Sie die Leistung und Verfügbarkeit Ihrer Anwendungen maximieren und Probleme in Sekundenschnelle proaktiv erkennen.
![](../Bilder/Advisor.png)<br>Advisor                                  | Azure Advisor analysiert Ihre Konfigurationen und Ihre Nutzungstelemetriedaten und bietet personalisierte, handlungsorientierte Empfehlungen zum Optimieren Ihrer Azure-Ressourcen im Hinblick auf Hochverfügbarkeit, Sicherheit, Leistung und Kosten.
![](../Bilder/Security_Center.png)<br>Security Center                  | Microsoft nutzt eine Vielzahl physischer, infrastruktureller und operationaler Verfahren zum Schutz von Azure, diese können hier eingestellt werden.
![](../Bilder/Kostenverwaltung.png)<br>Kostenverwaltung und Abrechnung | Dient zur Übersicht Ihrer aktuellen Kosten und Abrechnungen.
![](../Bilder/Hilfe.png)<br>Hilfe und Support                          | Sie haben ein Problem in Ihrem Azure Konto oder wissen über etwas nicht Bescheid, dieser Menüpunkt sollte Ihnen behilflich sein.

# Ressourcen erstellen

> [&uarr; *Zum Inhaltsverzeichnis*](#Inhaltsverzeichnis)

Die folgenden zwei Ressourcen sind notwendig, um mit dem Folgekapiteln **01-Azure Login** und **02-VM erstellen** weiterzufahren.<br>
Die Vorlagen für die Automatisierung finden Sie immer am Ende eines Subkapitels. 

### **Ressourcengruppen**

Muss manuell erstellt werden, erst mittels dieser Ressourcengruppe lässt sich mittels REST API weitere Ressourcen ansteurn.

1. Klicken Sie auf Ressourcengruppen und danach auf Hinzufügen
2. Geben Sie der Ressourcengruppe einen **eindeutigen** Namen, dieser wird im Kapitel 01-Azure Login und 02-VM erstellen wieder benötigt.
3. Wählen Sie noch als Region (Europa) Europa, Westen aus.

> [**Vorlage für die Automatisierung**](../Vorlagen/Ressourcengruppe.md)

### **Virtuelles Netzwerk**

1. Klicken Sie auf Virtuelle Netzwerke und danach auf Hinzufügen
2. Geben Sie dem virtuellem Netzwerk einen **eindeutigen** Namen, dieser wiederrum wird auch im Kapitel 01-Azure Login und 02-VM erstellen benötigt.
3. Geben Sie unter Ressourcengruppe, die Gruppe an welche so vorhin erstellt haben.
4. Als Standort geben Sie ebenfalls (Europa) Europa, Westen an.
5. Alle anderen Einstellungen belassen wir auf Standard.

> [**Vorlage für die Automatisierung**](../Vorlagen/VNET.md)

# REST API
>[&uarr; *Zum Inhaltsverzeichnis*](#Inhaltsverzeichnis)

Was ist ein REST API?<br>

Um dies besser verstehen zu können, müssen die einzelnen Begriffe zuerst getrennt voneinander erklärt werden.

> **REST** &rarr; Representational State Transfer<br>

REST ist eine Programmierschnittstelle, welche vor allem für Webservices genutzt wird, der Schwerpunkt von REST liegt hauptsächlich auf der Maschine-zu-Maschine-Kommunikation. Dabei werden sogenannte HTTP Requests gesendet, um mögliche Ressourcen abzufragen, zu erstellen oder zu verändern.
<br>
HTTP Methoden   | Beschreibung
----------------|-----------------------------------------
*GET*           | fordert Daten vom Server an
*POST*          | übermittelt Daten an den Server
*PUT / PATCH*   | ändert bestehende Daten auf dem Server
*DELETE*        | löscht bestehnde Daten auf dem Server

> **API** &rarr; Application Programming Interface

API ist eine vereinbarte Methode zum Senden und Empfangen von Daten zwischen Computern. Wenn Sie zum Beispiel eine eigene Webseite haben und auf dieser Google Maps angezeigt haben möchten, müssen Sie Google auffordern Ihnen die Karte zur Verfügung zu stellen. Dies geschieht indem Sie eine von Google bereitgestellte API verwenden, die Ihnen mitteilt welche Webadresse Sie die Anforderungen zum Abrufen der Daten senden sollen. Dies muss dann in einer formalen Sprache geschehen um vom Google-Server eine Antwort zu erhalten.<br>
<br>
Folgende Grafik erleutert den Vorgang eines REST API besser:<br>
![Grafik REST API](../Bilder/VA_Grafik_REST API.png)

>Um solch ein REST API nutzen zu können benötigen Sie unter Windows zusätzliche Software.<br> Hierzu finden Sie unter folgendem [Link](https://www.slant.co/topics/7913/~rest-api-clients) einige Auswahlmöglichkeiten.