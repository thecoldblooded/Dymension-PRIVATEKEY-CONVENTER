# Dymension PRIVKEY CONVERT

# SONUNA KADAR OKUYUN

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

# Dym'ye aktarıyoruz. (Oluşturduğunuz şifreyi girin.)

```
dymd keys import wallet $HOME/new_pk.json --keyring-backend test
```

# En son Kontrol Ediyoruz.

```
dymd keys list --keyring-backend test
```

# 5. Bundan Sonraki İşlemleri Mainnet Gelince Yapacağız.

Tokenleri Yeni Dymnension Walletimize Aktaracağız. Sakın Hemen Borsaya Atmaya Çalışmayın, Keplrdan Yeni Cüzdan Oluşunca Oraya Küçük Miktar Atarak Deneyebilirsiniz.


# 6. ÖZELLİKLE SÖYLÜYORUM GERİ KALAN İŞLEMLERİ MAİNNET BAŞLAYINCA YAPACAĞIZ.

Dym'leri yeni adrese gönderiyoruz.
Kaç Adet Tokeniniz Varsa Sonuna 18tane 0 girerek göndereceğiz. Mesela 1tane ise 1000000000000000000adym Aşağıya yazdım "tokenadediburası" kısmına yazacağız.

"$NEW_ADDRESS" Kısmına Yeni dymension Cüzdanınızı gireceksiniz.

"dymension-xxx_x" Burası chain ismi, Mainnet gelince öğreneceğiz.




```
dymd tx bank send wallet $NEW_ADDRESS tokenadediburasıadym --keyring-backend test --node https://rpc-dymension.mzonder.com:443 --chain-id dymension_1100-1 --gas-prices 20000000000adym --gas 200000
```







