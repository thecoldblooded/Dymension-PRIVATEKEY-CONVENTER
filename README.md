# Dymension-PRIVATEKEY-Converter

# 1. Install roller binaries

```
cd $HOME
```

```
curl -L https://dymensionxyz.github.io/roller/install.sh | bash
```

# install GO
cd $HOME
ver="1.21.3"
wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz"
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz"
rm "go$ver.linux-amd64.tar.gz"
echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> $HOME/.bash_profile
source $HOME/.bash_profile

cd $HOME
git clone https://github.com/alphab-ai/pk_convert
cd pk_convert

go build -o pk_convert ./main.go

## 3. Convert privatekey

### convert your saved hub_sequencer privatekey to correct format (json file)


# set var
HUB_SEQUENCER_PK="your_privatekey"
PASSWORD="12345678"                  # any password

cd $HOME/pk_convert

./pk_convert -pk $HUB_SEQUENCER_PK -password $PASSWORD >> $HOME/new_pk.json


import created json to dymd


# import to dymd (enter you password from above)
dymd keys import wallet $HOME/new_pk.json --keyring-backend test

# check your wallet imported correctly
dymd keys list --keyring-backend test


