# 1. Activer SNMP sur le routeur ou switch

Connectez-vous à votre équipement (Cisco, HP, etc.) en console ou SSH.
Entrez en mode configuration, puis tapez la commande suivante :

```bash
snmp-server community public RO
```

- **public** : C'est la communauté SNMP (léger mot de passe pour SNMPv2c).
- **RO** : Read-Only (lecture seule).

> SNMP est maintenant actif sur l'équipement.

---

# 2. Vérifications réseau

Avant d'ajouter l'équipement dans Zabbix :

- Vérifiez que le **port UDP 161** est **ouvert** entre Zabbix et l'équipement.
- Vérifiez que **Zabbix peut joindre** l'équipement (testez avec `ping`).
- Testez SNMP depuis Zabbix avec la commande suivante :

```bash
snmpwalk -v2c -c public IP_DU_ROUTEUR
```

- Si des données apparaissent, SNMP fonctionne correctement.

---

# 3. Ajouter l'équipement dans Zabbix

1. Connectez-vous à l'interface web de **Zabbix**.
2. Allez dans **Configuration** > **Hosts** > **Create host**.
3. Renseignez :
   - **Hostname** : Nom du routeur ou switch.
   - **Groups** : Exemple : "Network Devices".
   - **Interfaces** :
     - Cliquez sur **Add** > **SNMP interface**.
     - Renseignez l'**IP** de l'équipement.
4. Dans l'onglet **Templates** :
   - Cliquez sur **Link new templates**.
   - Sélectionnez **Template Net Network Generic SNMPv2**.

> Après quelques minutes, les données SNMP remonteront dans Zabbix.

---

# 4. Résultat attendu

- Supervision des interfaces (up/down).
- Trafic entrant/sortant par interface.
- Détection automatique des interfaces (LLD).

---
