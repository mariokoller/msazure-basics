# VM erstellen

Dieses Kapitel dient als Anleitung wie man eine virtuelle Maschine (Windows Server 2016) automatisiert zur Verfügung stellen kann, es werden alle Lernziele welche in den Kapiteln 00-01 gelernt wurden nun angewendet.

### **Lernziele**
Sie können nach Abschluss dieses Kapitels den Bodyinhalt eines REST Requests nach belieben verändern und wissen wie man ein JSON-File in ein Request einbinden kann. Sie lernen die Automatisierung anhand eines praktischen Beispieles, noch besser kennen.

### **Inhaltsverzeichnis**
- [VM Template](#VM-Template)
- [REST Request erstellen](#REST-Request-erstellen)

# VM Template
> [&uarr; *Zum Inhaltsverzeichnis*](#Inhaltsverzeichnis)

Sie sind nun mit der Thematik Automatisierung ein wenig vertrauter, daher wird ein Template für die Erstellung einer virtuellen Maschine einmal auseinandergenommen und analysiert.

**Zum ersten Teil:**

```
"location": "westeurope",
  "properties": {
    "hardwareProfile": {
      "vmSize": "Standard_DS1_v2"
```
Als Location müssen Sie, wenn Sie bereits immer West Europa angegeben haben, auch hier wieder westeurope auswählen, da es ansonsten zu Fehlern kommt. Was Sie hier auch noch anpassen können ist die vmSize, es gibt von Azure gewisse Standards die Sie auswählen können, eine Übersicht dazu finden Sie auf dieser [Webseite](https://docs.microsoft.com/de-de/azure/virtual-machines/windows/sizes-general).<br>

Ich habe mich für "Standard_DS1_v2" entschieden, da Sie mit der Kostenlosen Testversion nur 200$ zur Verfügung haben.

**Zum zweiten Teil dieses Templates:**
```
    "storageProfile": {
      "imageReference": {
        "sku": "2016-Datacenter",
        "publisher": "MicrosoftWindowsServer",
        "version": "latest",
        "offer": "WindowsServer"
```
In diesem Abschnitt wurde das Image ausgewählt, welches gerolloutet werden soll.<br>
Mit folgendem [Link](https://docs.microsoft.com/en-us/rest/api/compute/virtualmachineimages/list), können Sie eine Übersicht aller Images erstellen welche in Azure vorhanden sind, nutzen Sie dafür den REST API WebClient von Microsoft. 

**Dritter Teil:**
```
"osDisk": {
        "caching": "ReadWrite",
        "createOption": "FromImage",
        "name": "VMdisk"
      },
      "dataDisks": [
        {
          "diskSizeGB": 1023,
          "createOption": "Empty",
          "lun": 0
        },
        {
          "diskSizeGB": 1023,
          "createOption": "Empty",
          "lun": 1
```
Folgender Abschnitt zeigt im oberen Teil `name: VMdisk`, die Disk auf welcher die zwei LUN's erstellt wurden mit je 1023 GB Speicher. Der Name wie auch die Diskgrösse kann nach belieben geändert werden.

**Vierter und letzter Teil**
```
    "osProfile": {
      "adminUsername": "mario",
      "computerName": "NeuerWin2016Srv",
      "adminPassword": "DasistmeinPasswort$"
    },
    "networkProfile": {
      "networkInterfaces": [
        {
          "id": "/subscriptions/5137de89-2b0d-4671-b576-0ed207322766/resourceGroups/storagemsazurebasics/providers/Microsoft.Network/networkInterfaces/networkazurebasics",
          "properties": {
            "primary": true
```
Im letzten Abschnitt wird ein Admin-User und das dazugehörige Passwort, wie auch der Computername definiert.<br>
Die &rarr; *SubscriptionId* welche im Kapitel 00-Grundlagen sowie die erstellten Ressourcen müssen hier angegeben werden, diese sind die &rarr; *Ressourcengruppen* und das &rarr; *Virtuelle Netzwerk*.
<br>

> **Den Link zum kompletten Template finden Sie [**hier**](../Vorlagen/VM_Template.md).**

# REST Request erstellen
> [&uarr; *Zum Inhaltsverzeichnis*](#Inhaltsverzeichnis)

Mittels einem PUT Request erstellen Sie nun die virtuelle Maschine.<br>
Dieser kann wie folgt aussehen:<br>
```
PUT https://management.azure.com/subscriptions/{{subscriptionId}}/resourceGroups/storagemsazurebasics/providers/Microsoft.Compute/virtualMachines/NeuerWin2016Srv?api-version=2019-03-01
```
Wichtig ist vor allem, dass im Header folgende Angaben mitgegeben werden.<br>

Key               | Value
------------------|-----------------------------------------
Content-Type      | `application/json`
Authorization     | `Bearer {{bearertoken}}`

Dann muss das im Subkapitel erstellte Template im Body einefügt werden und der Request kann ausgeführt werden.<br>

> **Der POST Request vom Kapitel 01-Azure Login muss zuerst ausgeführt werden, da der Bearer Token nur 1 Stunde gültig ist.**