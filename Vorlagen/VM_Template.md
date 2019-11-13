```
{
  "location": "westeurope",
  "properties": {
    "hardwareProfile": {
      "vmSize": "Standard_DS1_v2"
    },
    "storageProfile": {
      "imageReference": {
        "sku": "2016-Datacenter",
        "publisher": "MicrosoftWindowsServer",
        "version": "latest",
        "offer": "WindowsServer"
      },
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
        }
      ]
    },
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
          }
        }
      ]
    }
  }
}
```