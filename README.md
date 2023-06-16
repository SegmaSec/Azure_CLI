<img align="right" height="100" width="90" alt="" src="https://raw.githubusercontent.com/Its-Sn1p3r/Azure_CLI/master/azure.png" />

# Administration Azure CLI Bash:

### Cree group de resource :
+ az group create --name MyRg --location EASTUS

### Cree network :
+ az network vnet create --name MyVnet --adress-prefix 10..0.0.23/24 --resource-group  MyRg

### Cree Subent:
+ az network vnet subnet create --name MySubnet --resource-group MyRg --adress-prefix 10.0.0.20/24 --vnet-name MyVnet

### Cree Carte Reseau:
+ az network nic --name MyCarte --subnet-name MySubnet --adress-prefix 10.0.0.12/24

### Cree Public IP:
+ az network public-ip create --name MyIP --allocation-methode Dynamic/Static

### Cree Group Securite Reseau:
+ az network nsg create --name MyNSG --location EASTUS

### Cree Machine Virtuel:
+ az vm create --name MyVM --nics Mycarte --subnet-name MySubnet --vnet-name MyVnet --image Ubuntu --admin-username Sky --admin-password cloud123

### Cree Rules NSG:
+ az network nsg rule create --resource-group MyRG --nsg-name MyNSG --name MyRules --priority 100 --source-address-prefixes 0.0.0.0/24 --destination-port-ranges 22 --access allow --protocol tcp

### Cree Application Securite Group:
+ az network asg create --name MyASG --resource-group MyRG --location EASTUS

### Cree peering entre Vnet1 et Vnet2:
+ az network vnet peering create \
--name <peering_name> \
--resource-group resource-group \
--vnet-name VNet1 \
--remote-vnet VNet2-ID \
--allow-vnet-access

+ az network vnet peering create \
--name peering_name \
--resource-group resource-group \
--vnet-name VNet2 \
--remote-vnet VNet1-ID \
--allow-vnet-access 

### Install serveur web:
+ az vm run-command invoke -g MyRG -n MyVM --command-id RunShellScript --scripts "sudo apt update && sudo apt install -y nginx"

### Cree Compte Stockage :
+ az storage account create --name $storageAccountName --resource-group $resourceGroupName --location $location --sku $sku --kind $kind

### Exécuter la commande suivante pour générer l’image :  
+ docker build --tag appsvc-tutorial-custom-image .  

### Vérifier que la build fonctionne en exécutant le conteneur Docker localement :  
docker run -it -p 8000:8000 appsvc-tutorial-custom-image

### Azure (Azure Container Registry) :  
+ az acr create --name registry-name --resource-group myResourceGroup --sku Basic --admin-enabled true  

### Exécutez la commande az acr show afin de récupérer les informations d’identification pour le registre : 

+ az acr credential show --resource-group myResourceGroup --name registry-name  
La sortie JSON de cette commande fournit deux mots de passe, ainsi que le nom d’utilisateur du registre. 

### Utiliser la commande docker login pour vous connecter au registre de conteneurs :  
+ docker login registry-name.azurecr.io --username registry-username

### Une fois la connexion établie, étiqueter votre image Docker locale dans le registre :  
docker tag appsvc-tutorial-custom-image registry-name.azurecr.io/appsvc-tutorial-custom-image:latest  

###  Utiliser la commande docker push pour envoyer (push) l’image vers le registre :  
docker push registry-name.azurecr.io/appsvc-tutorial-custom-image:lates

### Créer un plan App Service à l’aide de la commande az appservice plan create:  
• az appservice plan create --name myAppServicePlan --resource-group myResourceGroup --is-linux

### Créer l’application web à l’aide de la commande az webapp create :  
• az webapp create --resource-group myResourceGroup --plan myAppServicePlan --name app-name --deployment-container-image-name registry-name.azurecr.io/appsvc-tutorial-custom-image:latest

### Ouvrez le port 80 pour le trafic:
+ az vm open-port --port 80 -g MyRg -n MyVM

### Cree Group Machine Virtuel:
+ az vmss create -g MyRg -n MyVM --image ubuntu --upgrade-policy automatic --admin-username Sky --generate-ssh-keys --data-disk-sizes-gb 64 128 --instance-count 3

### Attach disk a Groupe Identique:
+ az vmss disk attach -g MyRg -n MyScalSet --size-gb 128


## Network Groupe Security:
```bash
$az network nsg create --resource-group $My_Resource --name $My_NSG
```

## Public IP:
```bash
$az network public-ip create --resource-group $My_resource --name $My_Public_IP
```
