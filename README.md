# Merhaba arkadaşlar, Nubit için kurulum rehberidir. NOT : Kurmak için [Buradan](https://www.points.nubit.org/#/?invite=RCr4G) kayıt olmanız ve 2000 Puan toplayıp "Gaz kuponu" almanız gerekiyor.
# Puan toplamak için işlem yaptığınız BTC cüzdanları ile giriş yapmanız ve referans olarak kişi eklemeniz gerekiyor ki puan toplayabilesiniz.

# Website : [Buradan](https://www.nubit.org)
# Explorer : [Buradan](https://www.explorer.nubit.org/#/)
# Doc : [Buradan](https://docs.nubit.org/developer-guides/introduction)

# 1. Gereksinimler
Sorunsuz kurulum için cihazınızın aşağıdaki minimum özellikleri karşıladığından emin olun:
```
Metric	Minimum Requirements
CPU	Single Core
Memory	512 MB
Disk	30 GB
Bandwidth	Upload/Download 100 KB/s
```

# BURADAN BAŞLIYORUZ ARKADAŞLAR.

# Sunucu güncelleme : 
```
sudo apt update -y && sudo apt upgrade -y
```

# Github'dan verileri klonluyoruz : 
```
git clone https://github.com/RiemaLabs/modular-indexer-light
```

# Go kurulumu yapıyoruz :
```
cd $HOME
VER="1.22.0"
wget "https://golang.org/dl/go$VER.linux-amd64.tar.gz"
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf "go$VER.linux-amd64.tar.gz"
rm "go$VER.linux-amd64.tar.gz"
[ ! -f ~/.bash_profile ] && touch ~/.bash_profile
echo "export PATH=$PATH:/usr/local/go/bin:~/go/bin" >> ~/.bash_profile
source $HOME/.bash_profile
[ ! -d ~/go/bin ] && mkdir -p ~/go/bin
```

# Kuruluma devam :
```
go mod tidy
```

# Yapılandırma ayarları :
```
cp config.example.json config.json
```

# Burada config içine girip bilgileri eklemelisiniz hemen aşşağıda belirttim yaptıktan sonra CTRL X ardından Y yapıp kaydetip çıkıyoruz.
```
nano config.example.json
```

# Örnek aşağıdaki gibi olmalı düzenleyin ilgili yerleri : 

```
 "verification": {
    "bitcoinRPC": "Quicknode BTC ağı ya da bunu ( https://bitcoin-mainnet-archive.allthatnode.com ) genel BTC ağı. Mainet olmalı girmelisiniz.",
    "metaProtocol": "brc-20",
    "minimalCheckpoint": 1
  },
  "report": {
    "name": "Burada kendinize bir isim belirleyin",
    "network": "Pre-Alpha Testnet",
    "namespaceID": "",
    "gasCoupon": "Gaz kuponu buraya girilmeli",
    "timeout": 15000  
```
  
# Üst tarafı yaptıktan sonra burada config içine girip aynı yukardaki gibi yaptıktan sonra CTRL X ardından Y yapıp kaydetip çıkıyoruz.
```
nano config.json
```

# Burada sürekli arka planda çalışacağı için aşağıdaki kodu girip Screen açıyoruz. Screene arkaplanda bırakmak için CTRL A - D yapıp çıkıyoruz. NOT :  Tekrar girmek için " Screen -r Nubit " yazarsanız screene tekrar girersiniz.
```
Screen -S Nubit
```

# Şimdi geldik başlatmaya aşağıdakileri sırayla giriyoruz : 
```
cd modular-indexer-light
go build
./modular-indexer-light
```

# Kurulum bu kadar.


