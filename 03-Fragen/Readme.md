# Fragen

**1. Was ist Cloud Computing?**
<details><summary>Antwort</summary><p>
Cloud Computing beinhaltet Technologien und Geschäftsmodelle um IT Ressourcen dynamisch zur Verfügung zu stellen und ihre Nutzung nach flexiblen Bezahlmodellen abzurechnen. Anstelle IT Ressourcen, beispielsweise Server oder Anwendungen, in unternehmenseigenen Rechenzentren zu betreiben, sind diese bedarfsorientiert und flexibel in Form eines dienstleistungsbasierten Geschäftsmodells über das Internet oder ein Intranet verfügbar.
</p></details>

---

**2. Was ist REST API?**
<details><summary>Antwort</summary><p>
REST API steht für "Representational State Transfer" und "Application Programming Interface". Sie macht den Austausch von Informationen möglich, wenn diese sich auf unterschiedlichen Systemen befinden. Im Zeitalter von Desktop-PCs und mobilen Geräten wie Tablets oder Smartphones trifft man oft auf solche unterschiedlichen Systeme, die den Einsatz von REST API notwendig machen. Man spricht bei REST API auch von der Maschine-Maschine-Kommunikation, da die verschiedenen Systeme und Geräte zusammengebracht werden und gewissermaßen die „gleiche Sprache“ sprechen. Dank REST API ist es möglich, Informationen und Aufgaben auf verschiedene Server zu verteilen und mit Hilfe eines HTTP Requests anzufordern. Der HTTP Request setzt sich aus dem Endpoint und den entsprechenden Parametern zusammen.
</p></details>

---
**3. Für was sind folgende HTTP Methoden?**

HTTP Methoden GET
<details><summary>Antwort</summary><p>
GET &rarr; Fordert Daten vom Server an
</p></details>

HTTP Methoden POST
<details><summary>Antwort</summary><p>
POST &rarr; Übermittelt Daten an den Server
</p></details>

HTTP Methoden PUT / PATCH
<details><summary>Antwort</summary><p>
PUT / PATCH &rarr; Ändert bestehende Daten auf dem Server
</p></details>

HTTP Methoden DELETE
<details><summary>Antwort</summary><p>
DELETE &rarr; Löscht bestehende Daten auf dem Server
</p></details>

---

**4. Was ist der Unterschied zwischen Tenant und Subscription?**
<details><summary>Antwort</summary><p>
Azure-Tenant ist ein Verzeichnis, Subscription ist ein Abonement oder Ordner. Ein Verzeichnis kann immer mehrer Ordner haben, aber ein Ordner kann nicht mehrere Verzeichnissse haben.
</p></details>

---

**5. Für was wird ein Bearer Token benötigt?**
<details><summary>Antwort</summary><p>
Ein Bearer Token wird im Authorization-Header von REST benötigt um Anforderungen an geschützte Ressourcen senden zu können. Ohne diesen Authorization-Header weiss die gegenüberliegende Ressource ansonsten nicht wer eine Anforderung senden möchte, daher ist der Bearer Token ein HTTP-Authentifizierungsschema.
</p></details>

---

**6. Was wird mit folgendem GET Request abgefragt?**<br>`GET https://management.azure.com/subscriptions/5137de89-2b0d-4671-b576-0ed207322766/resourcegroups?api-version=2017-05-10`
<details><summary>Antwort</summary><p>
Die Resourcegruppen der SubscriptionId 5137de89-2b0d-4671-b576-0ed207322766
</p></details>