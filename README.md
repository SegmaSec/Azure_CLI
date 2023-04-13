<img align="right" height="290" width="250" alt="" src="https://raw.githubusercontent.com/Its-Sn1p3r/Azure_CLI/master/azure.png" />
# Administration Azure CLI Bash:

## Grouppe de Ressource:
```bash
$az group create --name $name_resource --location $location
```

## Virtual Machine:
```bash
$az vm create --resource-group $name_resource --image $name_image --name $My_VM --admin-username $name_user --generate-ssh-keys --public-ip-sku Standard
```

## Subnet:
```bash
$az network vnet subnet create --resource-group $My_resource --vnet-name $My_Vnet --name $My_Subnet --address-prefix 10.0.2.0/24
```
## Network (Vnet):
```bash
$az network vnet create --resource-group $My_resource --name $myvnet --address-prefix 10.0.0.0/16 --subnet-name $My_Subnet --subnet-prefix 10.0.1.0/24
```

## Network Groupe Security:
```bash
$az network nsg create --resource-group $My_Resource --name $My_NSG
```

## Public IP:
```bash
$az network public-ip create --resource-group $My_resource --name $My_Public_IP
```
