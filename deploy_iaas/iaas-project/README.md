


# 😜 PASSOS PARA O DEPLOY EM VM (IAAS):


## 1 - Fazer login na azure:

```bash
az login --use-device-code
```

## 2 - Criar variáveis para ajudar nos comandos (opcional):
```bash
$RG="gabriela-braga-rg"
$VM="gabriela-braga-vm"
$LOC="eastus"
```

## 3 - Criar um resource group:
```bash
az group create --name $RG --location $LOC
```


## 4 - Criar uma virtual machine:
```bash
az vm create --resource-group $RG --name $VM --image "Ubuntu2204" --size "Standard_B1s" --admin-username "gabriela-braga" --generate-ssh-keys
```

## 5 - Pegar o IP público da sua vm:
```bash
"publicIpAddress": "104.211.50.37",
```

## 6 - Liberar a porta 80 (http) da vm:
```bash
az vm open-port --resource-group $RG --name $VM --port 80
```

## 7 - Instalar o nginx na VM via bastion ou ssh(fora do senai):
```bash
sudo apt-get install nginx
```


## 8 - mover a pasta dist para a vm (comando dentro da dist): 
```bash
scp -r dist/* gabriela-braga@20.127.113.182:/tmp/
```
