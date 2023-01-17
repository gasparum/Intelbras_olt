**🏗️ Em construção 🏗️**

# Acesso de informações da OLT Intelbras 8820G

Os scripts deste repositório são para *estudo* de acesso remoto através do pacote [Netmiko](https://pypi.org/project/netmiko/).

A ideia geral é fazer um pequeno parser da CLI do equipamento e automatizar backup das OLTs em sua rede do modelo 8820i


## Dependências
- [DotEnv](https://pypi.org/project/python-dotenv/) >= 0.17.0
- [Netmiko](https://pypi.org/project/netmiko/) >= 3.3.3
- [Python](https://www.python.org/) >= 3.7

## Setup do *virtualenv*

1. Clone o repo e entre na pasta 
```
https://github.com/gasparum/Intelbras_olt.git
cd intelbras_olt
```
2. instalar, criar e ativar o pacote virtualenv

2.1 Ubuntu, Debian, Mint
```
sudo apt update
sudo apt install -y python3-pip python3-venv
python3 -m venv venv
```
2.2 Fedora
```
sudo dnf install -y python3-virtualenv
python3 -m virtualenv venv
```
2.3
```
source venv/bin/actvate
```

## Instale as dependências

Com o virtualenv ativo, instale as dependências:
```
pip install -r requirements.txt
```

## Adicionando OLTs para Backup

As credenciais devem ser colocadas no arquivo 'lista_olt', devicename, usuário, senha e o ip do dispositivo. Por exemplo:
```
nano $PWD/lista_olt
```
```
olt01,172.31.0.2,admin,senha
fim,fim,fim,fim
```
## Configurando IP do servidor TFTP
Dentro do arquivo script_backup_olt procurar por tftp ao lado vai estar um IP alterar para o seu 
```
nano $PWD/script_backup_olt
```
```
command = f'backup network tftp 172.21.0.227 filename '+devicename+'-'+str(data)+'.cfg'
```

## Rodando o script
Os scripts script_backup_olt.py
```sh
python script_backup_olt.py

Ao término da execução do script, será enviado os arquivos de backup para o IP do servidor FTP
