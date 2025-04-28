# 1. Installer Zabbix agent2 sur Debian

Installez Zabbix agent2 :

```bash
sudo apt install zabbix-agent2
```

---

# 2. Configurer Zabbix agent2

Éditez le fichier de configuration principal :

```bash
sudo nano /etc/zabbix/zabbix_agent2.conf
```

Modifiez ou vérifiez les lignes suivantes :

```bash
Server=IP_DU_SERVEUR_ZABBIX
ServerActive=IP_DU_SERVEUR_ZABBIX
Hostname=NomDeLaMachine
```

Sauvegardez et quittez.

Redémarrez et activez l'agent :

```bash
sudo systemctl restart zabbix-agent2
sudo systemctl enable zabbix-agent2
```

Vérifiez que le service tourne correctement :

```bash
sudo systemctl status zabbix-agent2
```

---

# 3. Ajouter la machine dans Zabbix

1. Connectez-vous à l'interface web de Zabbix.
2. Allez dans **Configuration** > **Hosts** > **Create host**.
3. Remplissez :
   - **Hostname** : Nom de la machine Debian.
   - **Groups** : Exemple : "Linux Servers".
   - **Interfaces** :
     - Type : **Agent**.
     - IP : IP de la machine Debian.
4. Dans **Templates** :
   - Liez le template : **Template OS Linux by Zabbix agent**.

> Après quelques minutes, les données apparaîtront dans Zabbix.
