# **Azure Login**

In diesem Kapitel werden die Grundlagen zum automatisierten Azure Login erleutert und erklärt. Anhand praktischen Beispielen werden Sie die Grundanforderungen erlernen um ein REST API im Kapitel 02-VM erstellen zu können.

### **Lernziele**
Wenn Sie dieses Kapitel durchgearbeitet haben, kennen Sie die wichtigsten Parameter der Azure Plattform welche für die Automatisierung wichtig sind und können diese in einem REST API Client einbinden und Sie lernen die Authetifizuerung mittels dem Bearer Token kennen.

### **Inhaltsverzeichnis**
- [Azure ID's auslesen](#Azure-Plattform)
- [REST API Client](#REST-API-Client)
- [Bearer Token](#Bearer-Token)

# Azure ID's auslesen
>[&uarr; **_Zum Inhaltsverzeichnis_**](#Inhaltsverzeichnis)

Für was benötigen wir solche ID's?<br>

ID's werden benötigt, um dem erstelltem HTTP Request sein eindeutiges Ziel anzugeben. Solch ein Request kann zum Beispiel wie folgt aussehen:<br>

```
GET https://management.azure.com/subscriptions/5137de89-2b0d-4671-b576-0ed207322766/resourcegroups?api-version=2017-05-10
```

In diesem Beispiel wollen wir beispielsweise die Ressourcegruppen einer SubscriptionID herauslesen.<br>

---

Folgende ID's benötigen wir von Azure um weiterzufahren:

- tenantId
- subscriptionId
- clientId
- clientSecret
- resource &rarr; `https://management.azure.com/`

### **Azure Cloud Shell**
Gehen Sie auf Ihr Microsoft Azure Konto und öffnen Sie Cloud Shell.<br>

Geben Sie folgende Befehle ein:<br>
```
az account set --subscription "Ihr Subscription Name"
```

```
PS Azure:\> az account show
{
  "environmentName": "AzureCloud",
  "id": "5137de89-2b0d-4671-b576-0ed207322766",
  "isDefault": true,
  "name": "Kostenlose Testversion",
  "state": "Enabled",
  "tenantId": "f733fdc5-1255-4d8d-b793-2bc7aca0f214",
  "user": {
    "name": "mario.koller@edu.tbz.ch",
    "type": "user"
  }
}
```

```
PS Azure:\> az ad sp create-for-rbac -n "Selbststudienkurs"
Changing "Selbststudienkurs" to a valid URI of "http://Selbststudienkurs", which is the required format used for service principal names
Creating a role assignment under the scope of "/subscriptions/5137de89-2b0d-4671-b576-0ed207322766"
{
  "appId": "af038b9b-a0f2-49e5-8bf1-8a8fa74d4e69",
  "displayName": "Selbststudienkurs",
  "name": "http://Selbststudienkurs",
  "password": "62f888a1-8275-420d-818e-3aba5966dade",
  "tenant": "f733fdc5-1255-4d8d-b793-2bc7aca0f214"
}
```

Sie haben nun alle ID's welche Sie benötigen.<br>

**tenantId**<br>
*tenantid: f733fdc5-1255-4d8d-b793-2bc7aca0f214*<br>

**subscriptionId**<br>
*id: 5137de89-2b0d-4671-b576-0ed207322766*<br>

**clientId**<br>
*appId: af038b9b-a0f2-49e5-8bf1-8a8fa74d4e69*<br>

**clientSecret**<br>
*appId: 62f888a1-8275-420d-818e-3aba5966dade*<br>

# REST API Client
>[&uarr; **_Zum Inhaltsverzeichnis_**](#Inhaltsverzeichnis)

Um ein REST API absetzen zu können, benötigt man unter Windows ein REST API Client.<br>

Meine bisherigen Erfahrungen habe ich mit Postman gemacht, daher wird dies hier aufgezeigt.<br>
Postman kann direkt ab folgendem [Link](https://app.getpostman.com/run-collection/41b9fa3b957c297f283d#?env%5BAzure%20REST%5D=W3siZW5hYmxlZCI6dHJ1ZSwia2V5IjoidGVuYW50SWQiLCJ2YWx1ZSI6IiIsInR5cGUiOiJ0ZXh0In0seyJlbmFibGVkIjp0cnVlLCJrZXkiOiJjbGllbnRJZCIsInZhbHVlIjoiIiwidHlwZSI6InRleHQifSx7ImVuYWJsZWQiOnRydWUsImtleSI6ImNsaWVudFNlY3JldCIsInZhbHVlIjoiIiwidHlwZSI6InRleHQifSx7ImVuYWJsZWQiOnRydWUsImtleSI6InJlc291cmNlIiwidmFsdWUiOiJodHRwczovL21hbmFnZW1lbnQuYXp1cmUuY29tLyIsInR5cGUiOiJ0ZXh0In0seyJlbmFibGVkIjp0cnVlLCJrZXkiOiJzdWJzY3JpcHRpb25JZCIsInZhbHVlIjoiIiwidHlwZSI6InRleHQifV0=) installiert werden.<br>

Sie können aber gerne einen anderen Client verwenden.

### **Postman konfigurieren**

Wenn Postman installiert ist, muss dieser noch konfiguriert werden, mit den Angaben welche Sie vorhin von Azure ausgelesen haben.

1. Erstellen Sie im linken Teil des GUI eine neue Collection
2. Geben Sie Ihr einen passenden Namen und konfigurieren Sie die Variablen<br>
![Postman Collection](../Bilder/Postman_Collection.png)

# Bearer Token
>[&uarr; **_Zum Inhaltsverzeichnis_**](#Inhaltsverzeichnis)

Die Trägerauthentifizierung (auch als Tokenauthentifizierung bezeichnet) ist ein HTTP-Authentifizierungsschema, das Sicherheitstoken umfasst, die als Träger-Token bezeichnet werden. Der Name "Trägerauthentifizierung" kann als "*Zugriff auf den Träger dieses Tokens gewähren*" verstanden werden. Der Trägertoken ist eine kryptische Zeichenfolge, die normalerweise vom Server als Antwort auf eine Anmeldeanforderung generiert wird. Der Client muss diesen Token im Authorization-Header senden, wenn er Anforderungen an geschützte Ressourcen sendet.<br>

Folgende Grafik sollte dies besser veranschaulichen können.<br>

![Bearer Token](../Bilder/VA_Grafik_Bearer_Token.png)

