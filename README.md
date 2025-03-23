# 📌 Zabbix Server 7.2 Ubuntu 24.04 Kurulum Playbook'u  

## 🔧 Neler Yapıyor?  
✔️ Gerekli bağımlılıkları yüklüyor.  
✔️ PostgreSQL ve Python-PostgreSQL bağımlılığını kuruyor.  
✔️ Zabbix deposunu ekleyip gerekli paketleri kuruyor.  
✔️ Zabbix veritabanını oluşturuyor ve yapılandırıyor.  
✔️ Servisleri başlatıyor ve otomatik açılmalarını sağlıyor.  

### 1️⃣ Ansible'ın yüklü olduğundan emin olun  
```sh
ansible --version
```
### 2️⃣ Hedef makineleri yapılandırın
Envanter dosyanızda (inventory) Zabbix sunucusunun IP adresini ekleyin:
```sh
[zabbix]
zabbix-server ansible_host=192.168.233.160 ansible_user=root
```

### 3️⃣ Playbook'u çalıştırın
```sh
ansible-playbook -i inventory zabbix_server_setup.yml
```

### 4️⃣ Nginx'i yapılandırın

Altaki dizine girin 

```sh
sudo nano /etc/zabbix/nginx.conf
```
Aşağıdaki gibi düzeltin dosyayı

```sh
listen 80;
server_name example.com;
```
Burada `example.com` yerine zabbix sunucusun ip adresini yaz kaydet ve çık.

Daha sonra nginxi yeniden başlat:
```sh
sudo systemctl restart nginx
```

### 5️⃣ Zabbix Web Arayüzüne erişin
Kurulum tamamlandıktan sonra tarayıcıdan aşağıdaki adresi açın:
```sh
http://<sunucu_ip_adresi>

```

Varsayılan giriş bilgileri:

- Kullanıcı adı: Admin

- Şifre: zabbix

  
