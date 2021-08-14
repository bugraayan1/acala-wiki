---
açıklama: Burada bir düğüm kurma rehberi ve Acala'ya katılmanın yolları var.
---

# Mandala Test Ağı Bakımcıları Kılavuzu

### Tam Düğüm

Mandala Test Ağı, yalnızca işlevleri ve "patlayıcı" deneyleri test etmek için risksiz ve değersiz bir oyun alanıdır. Ağ değeri veya ödül yoktur. Bununla birlikte, bir düğümü çalıştırıp ağa katılabilirsiniz, bunu denemek, Karura Network \(Kusama'ya ağ değeriyle katılacak\) ve Acala Mainnet'e hazırlanmak için ya da sadece aşk için.

#### Tam Düğüm Çalıştırın \(Mandala\)

**Docker'ı kullanma**

Docker'ı Linux ile kurun:
`wget -qO- https://get.docker.com/ | ş'

Docker yüklediyseniz, koddan derlemeye gerek kalmadan düğümünüzü başlatmak için kullanabilirsiniz. İşte komut

```text
docker run -d --restart=always -p 30333:30333 -p 9933:9933 -p 9944:9944 -v node-data:/acala/data acala/acala-node:latest --chain mandala --base-path=/acala/data/01-001 --ws-port 9944 --rpc-port 9933 --port 30333 --ws-external --rpc-external --ws-max-connections 1000 --rpc-cors=all --unsafe-ws-external --unsafe-rpc-external --pruning=archive --name "Name of Telemetry" 
```

