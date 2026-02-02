# TREINAMENTO-UNIC-CASS

# Pré-requisitos-UNIC-CASS
Este repositorio é extraído com atualizações do site da UNIC-CASS, é apresentada a ferramenta para se conseguir gerar um layout através de uma imagem docker.

# Isabelle Mendes
-------------------------
1. Instalação da WSL e distribuição Ubuntu
No PowerShell do Windows, instale o Ubuntu 24.04 na WSL 2:
```bash
 wsl --install -d Ubuntu-24.04
```
Durante a instalação, será solicitado criar nome de usuário e senha no Linux.

Para abrir o Ubuntu diretamente no home do usuário:
```bash
wsl ~ -d Ubuntu-24.04
```
2. Preparação

Atualize sua distribuição Linux se você acabou de instalá-la executando o seguinte comando:
```bash
sudo apt-get update -q && sudo apt-get upgrade -q -y
```
Neste guia, vamos usar gedit como o editor padrão porque é fácil de usar. Se o seu sistema ainda não o tiver, você pode instalá-lo usando o seguinte comando:
```bash
sudo apt-get install gedit python3-pip -y
```
3.  Instalar e iniciar o serviço Docker

Instale o docker seguindo as instruções aqui: https://docs.docker.com/engine/install/ubuntu/

Este é o comando para instalar o Docker no Ubuntu 24.04:

```bash
sudo apt-get install ca-certificates curl gnupg -q -y
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
echo   "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update -q
sudo apt-get install -q -y docker-ce docker-ce-cli containerd.io  docker-buildx-plugin docker-compose-plugin

```
4. Iniciar o serviço de docker

Se você usa um sistema Linux real ou um sistema WSL Linux com Systemd suportado, você pode iniciar o docker executando estes comandos:

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

5. Adicionar usuário ao grupo docker

Você também precisará adicionar seu usuário ao grupo docker para que você tenha permissão para puxar a imagem docker como usuários normais:
```bash
sudo gpasswd -a $USER docker

```
Para que o comando acima entre em vigor, você tem que sair:

```bash
exit
```
Depois disso, você pode abrir um novo shell e continuar para prosseguir com as configurações necessárias.
# Design de sinal misto analógico usando imagem docker 

1. Instalar e iniciar o serviço Docker

 ```bash
sudo apt-get install ca-certificates curl gnupg -q -y
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
echo   "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update -q
sudo apt-get install -q -y docker-ce docker-ce-cli containerd.io  docker-buildx-plugin docker-compose-plugin
```
2. Iniciar o serviço de docker
Se você usa um sistema Linux real ou um sistema WSL Linux com Systemd suportado, você pode iniciar o docker executando este comando:
 ```bash
sudo systemctl start docker
sudo systemctl enable docker
```
3. Adicionar usuário ao grupo docker

Você também precisará adicionar seu usuário ao grupo docker para que você tenha permissão para puxar a imagem docker como usuários normais:
 ```bash
sudo gpasswd -a $USER docker
```
Para que o comando acima entre em vigor, você tem que sair:
 ```bash
exit
```
# Baixe os arquivos de origem do docker e inicie a imagem do UNIC-CASS Docker 
1. Clone o repositório:

Abra o terminal e execute o seguinte comando para clonar o repositório para sua máquina local:
 ```bash
git clone https://github.com/unic-cass/uniccass-icdesign-tools.git
```
2. Navegue até o diretório do repositório:

Altere para o diretório criado clonando o repositório:

 ```bash
cd uniccass-icdesign-tools/
```
3. Iniciar a imagem do docker executando faça começar:

Executar o make startcomando para iniciar o processo definido no Makefile:
 ```bash
make start
```
# Execute o design de exemplo 
1. Execute o xschem dentro da imagem do docker

 ```bash
xschem
```

2. Abra o "IHP testcases" no xschem

Para abrir o "IHP testcasesexemplo", clique em "IHP testcases" e "NGSPICE + XYCE" pressione o "e".
<img width="919" height="671" alt="image" src="https://github.com/user-attachments/assets/45ef2d89-dc92-486d-b06f-02fac259f104" />
Os circuitos de testes para o "IHP testcases" aparecerão no esquema da janela.
<img width="926" height="674" alt="image" src="https://github.com/user-attachments/assets/1be46c7d-97ea-4494-b30f-f0d72f460afd" />

3. Abrir o esquemático "DC lv_nmos" no xschem

Para abrir o esquemático "DC lv_nmos", clique em "DC lv_nmos" sobre a categoria "DC" e pressione o "e". O circuito de teste para "DC lv_nmos" aparecerá na janela do esquema.
<img width="892" height="646" alt="image" src="https://github.com/user-attachments/assets/99210b4d-2ce6-4a7e-a680-4d9e4f1a4994" />

4.  Execute a simulação
Para executar a simulação usando ngspice, segure a tecla "Ctrl" e clique sobre o seta a rotulação "SimulateNGSPICE". Então a simulação aparecerá a tela.
<img width="913" height="585" alt="image" src="https://github.com/user-attachments/assets/1a8616fa-a372-47cf-b1d7-001954b0671a" />
5. Atualizar resultados de simulação na janela do Xschem

Para exibir a forma de onda na janela do esquema, segure o a tecla "CTRL"  e clique na seta rotulada "load waves"  dai a forma de onda será apresentada.
<img width="896" height="667" alt="image" src="https://github.com/user-attachments/assets/9f206c8b-8998-4e64-a031-afef9439f302" />

6. Volta para o esquema anterior.

Para voltar ao nível anterior, você pode pressionar "Ctrl + e".

# Referência
1. 2024 IEEE CASS
2. https://learn.microsoft.com/pt-br/windows/wsl/install
