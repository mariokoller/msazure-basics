```
{
    "$schema": "http://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
    "contentVersion": "1.0.0.0",
    "parameters": {
        "name": {
            "type": "string"
        },
        "resourceGroup": {
            "type": "string"
        },
        "location": {
            "type": "string"
        },
        "addressPrefix": {
            "type": "string"
        },
        "subnetName": {
            "type": "string"
        },
        "subnetAddressPrefix": {
            "type": "string"
        },
        "enableDdosProtection": {
            "type": "bool"
        }
    },
    "resources": [
        {
            "apiVersion": "2019-04-01",
            "name": "[parameters('name')]",
            "type": "Microsoft.Network/virtualNetworks",
            "location": "[parameters('location')]",
            "properties": {
                "addressSpace": {
                    "addressPrefixes": [
                        "[parameters('addressPrefix')]"
                    ]
                },
                "subnets": [
                    {
                        "name": "[parameters('subnetName')]",
                        "properties": {
                            "addressPrefix": "[parameters('subnetAddressPrefix')]",
                            "addressPrefixes": []
                        }
                    }
                ],
                "enableDdosProtection": "[parameters('enableDdosProtection')]"
            }
        }
    ]
}
```