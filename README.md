# Dymension-PRIVATEKEY-Converter

# 1. Dymension, ikili Dosyalarını Yükleyin.

```
cd $HOME
```

```
curl -L https://dymensionxyz.github.io/roller/install.sh | bash
```

# 2. GO'yu Yüklüyoruz.

```
cd $HOME
```

```
ver="1.21.3"
wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz"
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz"
rm "go$ver.linux-amd64.tar.gz"
echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> $HOME/.bash_profile
source $HOME/.bash_profile
```

# 3. Conventeri Yüklüyoruz.

```
cd $HOME
```

```
git clone https://github.com/alphab-ai/pk_convert
```
Klasöre Giriyoruz.

```
cd pk_convert
```

Conventeri Çalıştırıyoruz.

```
go build -o pk_convert ./main.go
```

## 3. Private Keyi Convert Edicez.

### hub_sequencer private keyini (json file)' dönüştüreceğiz.

```
HUB_SEQUENCER_PK="PRİVATEKEYİNİZİGİRİN"
PASSWORD="ŞİFRENİZİGİRİN"
```            

```
cd $HOME/pk_convert
```

```
./pk_convert -pk $HUB_SEQUENCER_PK -password $PASSWORD >> $HOME/new_pk.json
```

# 4. Oluşan Json'u Dymensiona Entegre Ediyoruz.

# import to dymd (enter you password from above)
dymd keys import wallet $HOME/new_pk.json --keyring-backend test

# check your wallet imported correctly
dymd keys list --keyring-backend test


