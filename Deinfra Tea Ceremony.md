# WARN!!!
Before you start, please Register Testnet User and Installation [Here](https://github.com/DaddyUnikii/Deinfra-Testnet)

#
<div align="center">

# Deinfra Tea Ceremony


<a href='https://thepower.io/'>
    <img width="700" height="350" src="https://user-images.githubusercontent.com/38981255/198820722-9f95bc3c-2963-4bda-8886-33c6ce89b13b.PNG"/>
</a>

<i>Simple Way to Join Deinfra Tea Ceremony</i>

# Reference

[Website ](https://thepower.io/)

[Official Docs](https://doc.thepower.io/docs/Maintain/testnet-start/)

[Telegram Group ](https://t.me/thepower_chat)

[BOT TELEGRAM REGISTER ](https://t.me/thepowerio_bot)

</div>

## Requirements

| Tool | Operation |
|----------|---------------------|
|[VPS](https://contabo.com/)-<b>M Size Recomemended</b>|Ubuntu 20 or higher|
|[Mobaxterm](https://mobaxterm.mobatek.net/download.html)|Terminal|

## First Step
1. Open your Terminal that connect to your VPS
2. Prepare some <b><i>Snack or Coffee</b></i> to enjoy your Code

# <p align="center">Lets Start</p>

## Preparing your VPS

```
sudo apt update
sudo apt upgrade
sudo apt install git
```

## 1. Opening Port
```
suoo ufw allow 22
sudo ufw allow 1080
sudo ufw allow 1443
sudo ufw allow 1800

```

## 2. Install Erlang 24.3

#### Ubuntu 22.04

```
apt install cmake clang gcc git curl libssl-dev build-essential automake autoconf libncurses5-dev elixir erlang
```
```
apt -y install erlang-base erlang-public-key erlang-ssl
```

#### Ubuntu 20.04
```
sudo apt update
sudo apt install curl wget gnupg apt-transport-https -y
```
```
curl -fsSL https://packages.erlang-solutions.com/ubuntu/erlang_solutions.asc | sudo gpg --dearmor -o /usr/share/keyrings/erlang.gpg
```

```
echo "deb [signed-by=/usr/share/keyrings/erlang.gpg] https://packages.erlang-solutions.com/ubuntu $(lsb_release -cs) contrib" | sudo tee /etc/apt/sources.list.d/erlang.list
```

```
sudo apt update
sudo apt install erlang
```

## 3. Install Dinfra Tea Ceremony
```
wget https://tea.thepower.io/teaclient
```
```
chmod +x teaclient
```

## 4. Start The Client

```
./teaclient -n nickname aaaaa.bbbbb
```

<b>Note 1:</b> replace `nickname` with your own nickname anything you want

<b>Note 2:</b> replace `aaaaa.bbbb` with your personal code. its refer to [Here](https://github.com/DaddyUnikii/Deinfra-Testnet)

## 5. Install Docker
```
sudo apt update && sudo apt upgrade -y
```
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
sudo apt update && sudo apt install docker-ce docker-ce-cli containerd.io -y
```

```
docker pull thepowerio/tpnode
```

```
docker run -d -p 44000:44000 --name tptest thepowerio/tpnode
```

## 6. Install SSL
```
cd ..
```
```
cd /opt
```
```
mkdir -p thepower/db/cert/
```
```
cd
apt-get install socat
curl https://get.acme.sh | sh -s email=youractiveemail
source ~/.bashrc
```
<b><i>Note: </b></i> replace `youractiveemail` with your own email

## <p align="center">Exit your VPS or Re-Login</p>

#### Next Step
```
source ~/.bashrc
```
```
acme.sh --server letsencrypt --issue --standalone  -d your_node.example.com
acme.sh --install-cert -d your_node.example.com \
--cert-file /opt/thepower/db/cert/your_node.example.com.crt \
--key-file /opt/thepower/db/cert/your_node.example.com.key \
--ca-file /opt/thepower/db/cert/your_node.example.com.crt.ca.crt
acme.sh --info -d your_node.example.com
```

<b><i>Note :</b></i> Replace `your_node.example.com` with your own link

> How to get `your_node.example.com` ?

> You can find `your_node.example.com` inside file `node.config`

> The File is look like this ![image](https://user-images.githubusercontent.com/97149134/205428326-5d705e52-2e37-4bcb-adfc-7d5453219f0d.png)

## 6. Run Docker

```
cd /opt/thepower
mkdir log
```
```
cd
cp node.config /opt/thepower/node.config
cp genesis.txt /opt/thepower/genesis.txt
```
```
cd /opt/thepower
docker run -d \
--name tpnode \
--restart unless-stopped \
--mount type=bind,source="$(pwd)"/db,target=/opt/thepower/db \
--mount type=bind,source="$(pwd)"/log,target=/opt/thepower/log \
--mount type=bind,source="$(pwd)"/node.config,target=/opt/thepower/node.config \
--mount type=bind,source="$(pwd)"/genesis.txt,target=/opt/thepower/genesis.txt \
-p 1800:1800 \
-p 1080:1080 \
-p 1443:1443 \
thepowerio/tpnode
```

## 7. Check your status
```
curl http://your_node.example.com:1080/api/node/status | jq
```

<b><i>Note :</b></i> Replace `your_node.example.com` with your own link


## 8. Enter your link to the bot

```
http://<your_node.example.com>:1800/api/node/status
```
<b><i>Note :</b></i> Replace `your_node.example.com` with your own link

#

# <p align='center'> Done </p>

## Feel Bored and Giving up ? Stop it!
```
docker stop tpnode
```
```
docker rm tpnode
```
```
docker rmi thepowerio/tpnode
```
