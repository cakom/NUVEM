
##  Criar grupo de recurso

``` bash
az group create --name gabriela-braga-iaas-rg --location centralus
```

## 2 -Criar a máquina virtual no recurso

``` bash
az vm create --name gabriela-braga-iaas-vm --resource-group gabriela-braga-iaas-rg --image Ubuntu2204 --admin-username gabriela-braga --generate-ssh-keys --public-ip-sku Standard --size Standard_B1s
 ```

 ## 3 - Copiar o IP público
 ``` json
  "publicIpAddress": "104.43.244.138"
 ```

 ## 4 - Liberar porta 80 da VM
 ``` bash
 az vm open-port --port 80 --resource-group gabriela-braga-iaas-rg --name gabriela-braga-iaas-vm
 ```

 ## 5.1 - Transferir os arquivos do projeto para a VM
 (digitar no nível da pasta a ser transferida - senai bloqueia)
 ``` bash
 scp -r \dist\* gabriela-braga@104.43.244.138:/tmp/
 ```

 ## 6 - Conecte-se na VM
 
 ``` bash
 sudo apt update
 ```
  ``` bash
 sudo apt install nginx
 ```