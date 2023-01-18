# Criação de servidor FTP e acesso SSH

- **Tópicos**

  - 1. [Download do FTP](#instalação-dos-programas)
    - 2. [Configuração do FTP](#configuração-do-ftp)
### Instalação dos programas

  ```
  sudo apt install vsftpd
  sudo apt install openssh-server
  ```
## Configuração do FTP
  - ### Criação de um falso terminal

    Caso alguém tente acessar o servidor FTP por meio do SSH, será criado uma shell falsa
    ```
      sudo nano /etc/shells
    ```
    Coloque `/bin/false` abaixo das outras opções."
  - ### Criando um novo usuário 

    ```
    sudo mkdir -p /home/ftp/{nome_do_usuário} 
    sudo useradd {nome_do_usuário}  -d /home/ftp/{nome_do_usuário}/ -s /bin/false
    ```
  - ### Criando senha para o usuário
    ```
    sudo passwd {nome_do_usuário} 
    ```
  - ### Dando permissão total ao usuário para manipular a própria pasta
    ```
    sudo chown {nome_do_usuário} /home/ftp/{nome_do_usuário} 
    ```
  - ### Reiniciando o servidor FTP
    ```
    sudo /etc/init.d/vsftpd restart
    ```
## Inicializando o SSH
  - ### Start
    ```
    ssh-keygen -A   
    service ssh start
    ```
  - ### Logando
    ```
    ssh {nome_do_usuário}@{ip_da_máquina}
    ```
    > **Exemplo:** ssh ruan@192.168.0.10