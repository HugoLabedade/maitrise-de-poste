# TP1
## Self-footprinting
### Host OS

Quelques informations sur le nom de la machine et l'OS : 
```
PS C:\Users\hugol> Get-ComputerInfo -Property "*name*"

WindowsProductName : Windows 10 Pro
BiosName           : V1.01
CsDNSHostName      : LAPTOP-094TMCHO
CsName             : LAPTOP-094TMCHO
CsUserName         : LAPTOP-094TMCHO\hugol
OsName             : Microsoft Windows 10 Professionnel
```

Informations sur le processeur : 
```
PS C:\Users\hugol> Get-ComputerInfo -Property "*proc*"

CsNumberOfLogicalProcessors : 8
CsNumberOfProcessors        : 1
CsProcessors                : {Intel(R) Core(TM) i5-8265U CPU @ 1.60GHz}
OsMaxNumberOfProcesses      : 4294967295
OsMaxProcessMemorySize      : 137438953344
OsNumberOfProcesses         : 295

PS C:\Users\hugol> Get-ComputerInfo -Property "*arch*"

OsArchitecture
--------------
64 bits
```

De l'information sur la RAM : 
```
C:\Users\hugol>wmic memorychip get devicelocator, manufacturer, typedetail, capacity, speed, memorytype
Capacity    DeviceLocator   Manufacturer  MemoryType  Speed  TypeDetail
4294967296  ChannelA-DIMM0  SK Hynix      0           2667   128
4294967296  ChannelB-DIMM0  SK Hynix      0           2667   128

puis grace a la commande "systeminfo"

Mémoire physique totale:                    8 048 Mo
Mémoire physique disponible:                1 709 Mo
Mémoire virtuelle : taille maximale:        17 753 Mo
Mémoire virtuelle : disponible:             3 495 Mo
Mémoire virtuelle : en cours d’utilisation: 14 258 Mo
```

### Devices

Toutes les infos sur le cpu : 
```
PS C:\Users\hugol> Get-ComputerInfo -Property "*proc*"

CsNumberOfLogicalProcessors : 8
CsNumberOfProcessors        : 1
CsProcessors                : {Intel(R) Core(TM) i5-8265U CPU @ 1.60GHz}
OsMaxNumberOfProcesses      : 4294967295
OsMaxProcessMemorySize      : 137438953344
OsNumberOfProcesses         : 295
```

Explication du nom du cpu :
    - i5 est le "brand modifier" qui signale différentes features
    - Le premier chiffre, en l'occurence "8" signifie la 8eme génération de processeur
    - Les 3 derniers chiffres correspondent à une nomenclature faite par le fabricant pour identifier leur produit
    - La lettre U correspond à une très basse consommation 


Voila toutes les partitions de mon disque dur : 
```
DISKPART> list partition

  N° partition   Type              Taille   Décalage
  -------------  ----------------  -------  --------
  Partition 1    Système            100 M   1024 K
  Partition 2    Réservé             16 M    101 M
  Partition 3    Principale         475 G    117 M
  Partition 4    Récupération      1024 M    475 G
```

### Network

Toutes les informations des cartes réseau en utilisant la commande systeminfo : 
```
Carte(s) réseau:                            9 carte(s) réseau installée(s).
                                            [01]: VMware Virtual Ethernet Adapter for VMnet1
                                                  Nom de la connexion : VMware Network Adapter VMnet1
                                                  DHCP activé :         Non
                                                  Adresse(s) IP
                                                  [01]: 192.168.169.1
                                                  [02]: fe80::9845:6ae6:9f4f:8991
                                            [02]: VMware Virtual Ethernet Adapter for VMnet8
                                                  Nom de la connexion : VMware Network Adapter VMnet8
                                                  DHCP activé :         Non
                                                  Adresse(s) IP
                                                  [01]: 192.168.177.1
                                                  [02]: fe80::90c2:3c8c:ebd5:a9b6
                                            [03]: Intel(R) Wireless-AC 9560 160MHz
                                                  Nom de la connexion : Wi-Fi                                                                                             DHCP activé :         Oui                                                                                               Serveur DHCP :        192.168.1.254                                                                                     Adresse(s) IP                                                                                                           [01]: 192.168.1.75
                                                  [02]: fe80::5428:f516:35b1:966e
                                            [04]: Bluetooth Device (Personal Area Network)
                                                  Nom de la connexion : Connexion réseau Bluetooth
                                                  État :                Support déconnecté
                                            [05]: VirtualBox Host-Only Ethernet Adapter
                                                  Nom de la connexion : VirtualBox Host-Only Network
                                                  DHCP activé :         Non
                                                  Adresse(s) IP
                                                  [01]: 192.168.1.150
                                                  [02]: fe80::7996:8b98:5793:e477
                                            [06]: VirtualBox Host-Only Ethernet Adapter
                                                  Nom de la connexion : VirtualBox Host-Only Network #4
                                                  DHCP activé :         Non
                                                  Adresse(s) IP
                                                  [01]: 192.168.126.1
                                                  [02]: fe80::e4ec:928f:9d81:da4
                                            [07]: VirtualBox Host-Only Ethernet Adapter
                                                  Nom de la connexion : VirtualBox Host-Only Network #2
                                                  DHCP activé :         Non
                                                  Adresse(s) IP
                                                  [01]: 10.3.2.1
                                                  [02]: fe80::4546:b5c0:cfa3:99af
                                            [08]: VirtualBox Host-Only Ethernet Adapter
                                                  Nom de la connexion : VirtualBox Host-Only Network #3
                                                  DHCP activé :         Non
                                                  Adresse(s) IP
                                                  [01]: 169.254.185.17
                                                  [02]: fe80::90bf:f0ae:3c80:b911
                                            [09]: TAP-Windows Adapter V9
                                                  Nom de la connexion : Connexion au réseau local
                                                  État :                Support déconnecté
Configuration requise pour Hyper-V:         Extensions de mode du moniteur d’ordinateur virtuel : Oui
                                            Virtualisation activée dans le microprogramme : Oui
                                            Traduction d’adresse de second niveau : Oui
                                            Prévention de l’exécution des données disponible : Oui
```
Les cartes virtualbox et vmware servent pour ces logiciels pour créer des réseaux "host-only"
La carte [3] correspond à la carte wifi
La carte [4] correspond à la carte Bluetooth à laquelle nos appareils se connectent
La carte [9] correspond à un pilote réseau qui permet au VPN de se connecter à ses serveurs

Liste de tous les ports TCP et UDP en utilisation :
```
PS C:\WINDOWS\system32> netstat -abo

Connexions actives

  Proto  Adresse locale         Adresse distante       État
  TCP    0.0.0.0:80             LAPTOP-094TMCHO:0      LISTENING       4
 Impossible d’obtenir les informations de propriétaire
  TCP    0.0.0.0:135            LAPTOP-094TMCHO:0      LISTENING       908
  RpcSs
 [svchost.exe]
  TCP    0.0.0.0:443            LAPTOP-094TMCHO:0      LISTENING       10416
 [httpd.exe]
  TCP    0.0.0.0:445            LAPTOP-094TMCHO:0      LISTENING       4
 Impossible d’obtenir les informations de propriétaire
  TCP    0.0.0.0:902            LAPTOP-094TMCHO:0      LISTENING       5708
 [vmware-authd.exe]
  TCP    0.0.0.0:912            LAPTOP-094TMCHO:0      LISTENING       5708
 [vmware-authd.exe]
  TCP    0.0.0.0:3306           LAPTOP-094TMCHO:0      LISTENING       5044
 [mysqld.exe]
  TCP    0.0.0.0:5040           LAPTOP-094TMCHO:0      LISTENING       11140
  CDPSvc
 [svchost.exe]
  TCP    0.0.0.0:5357           LAPTOP-094TMCHO:0      LISTENING       4
 Impossible d’obtenir les informations de propriétaire
  TCP    0.0.0.0:7680           LAPTOP-094TMCHO:0      LISTENING       14956
 Impossible d’obtenir les informations de propriétaire
  TCP    0.0.0.0:8080           LAPTOP-094TMCHO:0      LISTENING       10416
 [httpd.exe]
  TCP    0.0.0.0:8866           LAPTOP-094TMCHO:0      LISTENING       8552
 [AgSvc.exe]
  TCP    0.0.0.0:21092          LAPTOP-094TMCHO:0      LISTENING       8552
 [AgSvc.exe]
  TCP    0.0.0.0:33060          LAPTOP-094TMCHO:0      LISTENING       5044
 [mysqld.exe]
  TCP    0.0.0.0:49664          LAPTOP-094TMCHO:0      LISTENING       768
 [lsass.exe]
  TCP    0.0.0.0:49665          LAPTOP-094TMCHO:0      LISTENING       684
 Impossible d’obtenir les informations de propriétaire
  TCP    0.0.0.0:49666          LAPTOP-094TMCHO:0      LISTENING       2120
  EventLog
 [svchost.exe]
  TCP    0.0.0.0:49667          LAPTOP-094TMCHO:0      LISTENING       2808
  Schedule
 [svchost.exe]
  TCP    0.0.0.0:49668          LAPTOP-094TMCHO:0      LISTENING       3168
  SessionEnv
 [svchost.exe]
  TCP    0.0.0.0:49669          LAPTOP-094TMCHO:0      LISTENING       4236
 [spoolsv.exe]
  TCP    0.0.0.0:49677          LAPTOP-094TMCHO:0      LISTENING       736
 Impossible d’obtenir les informations de propriétaire
  TCP    10.3.2.1:139           LAPTOP-094TMCHO:0      LISTENING       4
 Impossible d’obtenir les informations de propriétaire
  TCP    127.0.0.1:1120         LAPTOP-094TMCHO:0      LISTENING       24972
 [Agent.exe]
  TCP    127.0.0.1:1120         LAPTOP-094TMCHO:3211   TIME_WAIT       0
  TCP    127.0.0.1:1120         LAPTOP-094TMCHO:3216   TIME_WAIT       0
  TCP    127.0.0.1:1120         LAPTOP-094TMCHO:3221   TIME_WAIT       0
  TCP    127.0.0.1:1120         LAPTOP-094TMCHO:3222   TIME_WAIT       0
  TCP    127.0.0.1:1120         LAPTOP-094TMCHO:3223   TIME_WAIT       0
  TCP    127.0.0.1:1120         LAPTOP-094TMCHO:3225   TIME_WAIT       0
  TCP    127.0.0.1:1120         LAPTOP-094TMCHO:3229   TIME_WAIT       0
  TCP    127.0.0.1:1120         LAPTOP-094TMCHO:3231   TIME_WAIT       0
  TCP    127.0.0.1:1120         LAPTOP-094TMCHO:3235   TIME_WAIT       0
  TCP    127.0.0.1:1120         LAPTOP-094TMCHO:3240   TIME_WAIT       0
  TCP    127.0.0.1:1434         LAPTOP-094TMCHO:0      LISTENING       5472
 [sqlservr.exe]
  TCP    127.0.0.1:3210         LAPTOP-094TMCHO:49350  TIME_WAIT       0
  TCP    127.0.0.1:3212         LAPTOP-094TMCHO:49350  TIME_WAIT       0
  TCP    127.0.0.1:3220         LAPTOP-094TMCHO:49350  TIME_WAIT       0
  TCP    127.0.0.1:3224         LAPTOP-094TMCHO:49350  TIME_WAIT       0
  TCP    127.0.0.1:3226         LAPTOP-094TMCHO:49350  TIME_WAIT       0
  TCP    127.0.0.1:3227         LAPTOP-094TMCHO:49350  TIME_WAIT       0
  TCP    127.0.0.1:3228         LAPTOP-094TMCHO:49350  TIME_WAIT       0
  TCP    127.0.0.1:3230         LAPTOP-094TMCHO:49350  TIME_WAIT       0
  TCP    127.0.0.1:3232         LAPTOP-094TMCHO:49350  TIME_WAIT       0
  TCP    127.0.0.1:3233         LAPTOP-094TMCHO:49350  TIME_WAIT       0
  TCP    127.0.0.1:3234         LAPTOP-094TMCHO:49350  TIME_WAIT       0
  TCP    127.0.0.1:3239         LAPTOP-094TMCHO:49350  TIME_WAIT       0
  TCP    127.0.0.1:3241         LAPTOP-094TMCHO:49350  TIME_WAIT       0
  TCP    127.0.0.1:3242         LAPTOP-094TMCHO:49350  TIME_WAIT       0
  TCP    127.0.0.1:5721         LAPTOP-094TMCHO:5722   TIME_WAIT       0
  TCP    127.0.0.1:5939         LAPTOP-094TMCHO:0      LISTENING       5164
 [TeamViewer_Service.exe]
  TCP    127.0.0.1:6463         LAPTOP-094TMCHO:0      LISTENING       16276
 [Discord.exe]
  TCP    127.0.0.1:28385        LAPTOP-094TMCHO:0      LISTENING       4
 Impossible d’obtenir les informations de propriétaire
  TCP    127.0.0.1:49350        LAPTOP-094TMCHO:0      LISTENING       26248
 [esrv_svc.exe]
  TCP    127.0.0.1:49351        LAPTOP-094TMCHO:0      LISTENING       13616
 [esrv.exe]
  TCP    127.0.0.1:49671        LAPTOP-094TMCHO:49672  ESTABLISHED     5044
 [mysqld.exe]
  TCP    127.0.0.1:49672        LAPTOP-094TMCHO:49671  ESTABLISHED     5044
 [mysqld.exe]
  TCP    127.0.0.1:64498        LAPTOP-094TMCHO:0      LISTENING       7548
 [Code.exe]
  TCP    169.254.185.17:139     LAPTOP-094TMCHO:0      LISTENING       4
 Impossible d’obtenir les informations de propriétaire
  TCP    192.168.1.75:139       LAPTOP-094TMCHO:0      LISTENING       4
 Impossible d’obtenir les informations de propriétaire
  TCP    192.168.1.75:2545      40.67.251.132:https    ESTABLISHED     5300
  WpnService
 [svchost.exe]
  TCP    192.168.1.75:2930      ec2-52-2-221-12:https  ESTABLISHED     17364
 [chrome.exe]
  TCP    192.168.1.75:3124      24.105.29.76:https     CLOSE_WAIT      24972
 [System]
  TCP    192.168.1.75:3189      ec2-34-247-150-224:https  ESTABLISHED     17364
 [chrome.exe]
  TCP    192.168.1.75:3197      BouygtelTV-271011819710905:8008  ESTABLISHED     17364
 [chrome.exe]
  TCP    192.168.1.75:3198      wo-in-f188:5228        ESTABLISHED     17364
 [chrome.exe]
  TCP    192.168.1.75:3199      ec2-54-194-216-197:https  ESTABLISHED     17364
 [chrome.exe]
  TCP    192.168.1.75:3200      ec2-54-194-216-197:https  ESTABLISHED     17364
 [chrome.exe]
  TCP    192.168.1.75:3201      ec2-54-194-216-197:https  ESTABLISHED     17364
 [chrome.exe]
  TCP    192.168.1.75:3236      53:https               ESTABLISHED     15412
 [Discord.exe]
  TCP    192.168.1.75:3237      162.159.134.233:https  ESTABLISHED     15412
 [Discord.exe]
  TCP    192.168.1.75:3238      47:https               TIME_WAIT       0
  TCP    192.168.1.75:21179     cds4:1119              LAST_ACK        22764
 [System]
  TCP    192.168.1.75:21180     cds4:1119              LAST_ACK        22764
 [System]
  TCP    192.168.1.75:63023     162.159.134.234:https  ESTABLISHED     15412
 [Discord.exe]
  TCP    192.168.1.75:63496     162.159.138.234:https  ESTABLISHED     15412
 [Discord.exe]
  TCP    192.168.1.75:64522     52.236.190.14:https    ESTABLISHED     14048
 [vsls-agent.exe]
  TCP    192.168.1.150:139      LAPTOP-094TMCHO:0      LISTENING       4
 Impossible d’obtenir les informations de propriétaire
  TCP    192.168.126.1:139      LAPTOP-094TMCHO:0      LISTENING       4
 Impossible d’obtenir les informations de propriétaire
  TCP    192.168.169.1:139      LAPTOP-094TMCHO:0      LISTENING       4
 Impossible d’obtenir les informations de propriétaire
  TCP    192.168.177.1:139      LAPTOP-094TMCHO:0      LISTENING       4
 Impossible d’obtenir les informations de propriétaire
  TCP    [::]:80                LAPTOP-094TMCHO:0      LISTENING       4
 Impossible d’obtenir les informations de propriétaire
  TCP    [::]:135               LAPTOP-094TMCHO:0      LISTENING       908
  RpcSs
 [svchost.exe]
  TCP    [::]:443               LAPTOP-094TMCHO:0      LISTENING       10416
 [httpd.exe]
  TCP    [::]:445               LAPTOP-094TMCHO:0      LISTENING       4
 Impossible d’obtenir les informations de propriétaire
  TCP    [::]:3306              LAPTOP-094TMCHO:0      LISTENING       5044
 [mysqld.exe]
  TCP    [::]:5357              LAPTOP-094TMCHO:0      LISTENING       4
 Impossible d’obtenir les informations de propriétaire
  TCP    [::]:7680              LAPTOP-094TMCHO:0      LISTENING       14956
 Impossible d’obtenir les informations de propriétaire
  TCP    [::]:8080              LAPTOP-094TMCHO:0      LISTENING       10416
 [httpd.exe]
  TCP    [::]:21092             LAPTOP-094TMCHO:0      LISTENING       8552
 [AgSvc.exe]
  TCP    [::]:33060             LAPTOP-094TMCHO:0      LISTENING       5044
 [mysqld.exe]
  TCP    [::]:49664             LAPTOP-094TMCHO:0      LISTENING       768
 [lsass.exe]
  TCP    [::]:49665             LAPTOP-094TMCHO:0      LISTENING       684
 Impossible d’obtenir les informations de propriétaire
  TCP    [::]:49666             LAPTOP-094TMCHO:0      LISTENING       2120
  EventLog
 [svchost.exe]
  TCP    [::]:49667             LAPTOP-094TMCHO:0      LISTENING       2808
  Schedule
 [svchost.exe]
  TCP    [::]:49668             LAPTOP-094TMCHO:0      LISTENING       3168
  SessionEnv
 [svchost.exe]
  TCP    [::]:49669             LAPTOP-094TMCHO:0      LISTENING       4236
 [spoolsv.exe]
  TCP    [::]:49677             LAPTOP-094TMCHO:0      LISTENING       736
 Impossible d’obtenir les informations de propriétaire
  TCP    [::1]:1434             LAPTOP-094TMCHO:0      LISTENING       5472
 [sqlservr.exe]
  TCP    [::1]:49834            LAPTOP-094TMCHO:0      LISTENING       2768
 [jhi_service.exe]
  UDP    0.0.0.0:500            *:*                                    4944
  IKEEXT
 [svchost.exe]
  UDP    0.0.0.0:1900           *:*                                    26248
 [esrv_svc.exe]
  UDP    0.0.0.0:3702           *:*                                    2560
 [dashost.exe]
  UDP    0.0.0.0:3702           *:*                                    4784
  FDResPub
 [svchost.exe]
  UDP    0.0.0.0:3702           *:*                                    4784
  FDResPub
 [svchost.exe]
  UDP    0.0.0.0:3702           *:*                                    2560
 [dashost.exe]
  UDP    0.0.0.0:4500           *:*                                    4944
  IKEEXT
 [svchost.exe]
  UDP    0.0.0.0:5050           *:*                                    11140
  CDPSvc
 [svchost.exe]
  UDP    0.0.0.0:5353           *:*                                    17016
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17016
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17016
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17016
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17016
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17016
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17364
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17364
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17016
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17364
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17364
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17364
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17364
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17364
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17364
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17016
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17016
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17016
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17016
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    2988
  Dnscache
 [svchost.exe]
  UDP    0.0.0.0:5353           *:*                                    17016
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17016
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17364
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17364
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17364
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17364
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17364
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17364
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*                                    17016
 [chrome.exe]
  UDP    0.0.0.0:5355           *:*                                    2988
  Dnscache
 [svchost.exe]
  UDP    0.0.0.0:21091          *:*                                    8552
 [AgSvc.exe]
  UDP    0.0.0.0:49490          *:*                                    2560
 [dashost.exe]
  UDP    0.0.0.0:58467          *:*                                    16276
 [Discord.exe]
  UDP    0.0.0.0:58818          *:*                                    4784
  FDResPub
 [svchost.exe]
  UDP    0.0.0.0:58820          *:*                                    5164
 [TeamViewer_Service.exe]
  UDP    0.0.0.0:64265          *:*                                    9320
 [SkypeApp.exe]
  UDP    10.3.2.1:137           *:*                                    4
 Impossible d’obtenir les informations de propriétaire
  UDP    10.3.2.1:138           *:*                                    4
 Impossible d’obtenir les informations de propriétaire
  UDP    10.3.2.1:1900          *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    10.3.2.1:2177          *:*                                    21436
  QWAVE
 [svchost.exe]
  UDP    10.3.2.1:5353          *:*                                    5164
 [TeamViewer_Service.exe]
  UDP    10.3.2.1:57279         *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    127.0.0.1:1900         *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    127.0.0.1:49536        *:*                                    5684
  iphlpsvc
 [svchost.exe]
  UDP    127.0.0.1:57284        *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    169.254.185.17:137     *:*                                    4
 Impossible d’obtenir les informations de propriétaire
  UDP    169.254.185.17:138     *:*                                    4
 Impossible d’obtenir les informations de propriétaire
  UDP    169.254.185.17:1900    *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    169.254.185.17:2177    *:*                                    21436
  QWAVE
 [svchost.exe]
  UDP    169.254.185.17:5353    *:*                                    5164
 [TeamViewer_Service.exe]
  UDP    169.254.185.17:57280   *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    192.168.1.75:137       *:*                                    4
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.1.75:138       *:*                                    4
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.1.75:1900      *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    192.168.1.75:2177      *:*                                    21436
  QWAVE
 [svchost.exe]
  UDP    192.168.1.75:5353      *:*                                    5164
 [TeamViewer_Service.exe]
  UDP    192.168.1.75:57283     *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    192.168.1.150:137      *:*                                    4
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.1.150:138      *:*                                    4
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.1.150:1900     *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    192.168.1.150:2177     *:*                                    21436
  QWAVE
 [svchost.exe]
  UDP    192.168.1.150:5353     *:*                                    5164
 [TeamViewer_Service.exe]
  UDP    192.168.1.150:57277    *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    192.168.126.1:137      *:*                                    4
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.126.1:138      *:*                                    4
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.126.1:1900     *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    192.168.126.1:2177     *:*                                    21436
  QWAVE
 [svchost.exe]
  UDP    192.168.126.1:5353     *:*                                    5164
 [TeamViewer_Service.exe]
  UDP    192.168.126.1:57278    *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    192.168.169.1:137      *:*                                    4
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.169.1:138      *:*                                    4
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.169.1:1900     *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    192.168.169.1:2177     *:*                                    21436
  QWAVE
 [svchost.exe]
  UDP    192.168.169.1:5353     *:*                                    5164
 [TeamViewer_Service.exe]
  UDP    192.168.169.1:57281    *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    192.168.177.1:137      *:*                                    4
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.177.1:138      *:*                                    4
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.177.1:1900     *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    192.168.177.1:2177     *:*                                    21436
  QWAVE
 [svchost.exe]
  UDP    192.168.177.1:5353     *:*                                    5164
 [TeamViewer_Service.exe]
  UDP    192.168.177.1:57282    *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    [::]:500               *:*                                    4944
  IKEEXT
 [svchost.exe]
  UDP    [::]:3702              *:*                                    4784
  FDResPub
 [svchost.exe]
  UDP    [::]:3702              *:*                                    2560
 [dashost.exe]
  UDP    [::]:3702              *:*                                    4784
  FDResPub
 [svchost.exe]
  UDP    [::]:3702              *:*                                    2560
 [dashost.exe]
  UDP    [::]:4500              *:*                                    4944
  IKEEXT
 [svchost.exe]
  UDP    [::]:5353              *:*                                    17364
 [chrome.exe]
  UDP    [::]:5353              *:*                                    17364
 [chrome.exe]
  UDP    [::]:5353              *:*                                    17364
 [chrome.exe]
  UDP    [::]:5353              *:*                                    17016
 [chrome.exe]
  UDP    [::]:5353              *:*                                    17364
 [chrome.exe]
  UDP    [::]:5353              *:*                                    17016
 [chrome.exe]
  UDP    [::]:5353              *:*                                    17016
 [chrome.exe]
  UDP    [::]:5353              *:*                                    17016
 [chrome.exe]
  UDP    [::]:5353              *:*                                    17016
 [chrome.exe]
  UDP    [::]:5353              *:*                                    17016
 [chrome.exe]
  UDP    [::]:5353              *:*                                    17364
 [chrome.exe]
  UDP    [::]:5353              *:*                                    17364
 [chrome.exe]
  UDP    [::]:5353              *:*                                    2988
  Dnscache
 [svchost.exe]
  UDP    [::]:5353              *:*                                    17364
 [chrome.exe]
  UDP    [::]:5353              *:*                                    17016
 [chrome.exe]
  UDP    [::]:5355              *:*                                    2988
  Dnscache
 [svchost.exe]
  UDP    [::]:49491             *:*                                    2560
 [dashost.exe]
  UDP    [::]:58819             *:*                                    4784
  FDResPub
 [svchost.exe]
  UDP    [::]:58821             *:*                                    5164
 [TeamViewer_Service.exe]
  UDP    [::]:64265             *:*                                    9320
 [SkypeApp.exe]
  UDP    [::1]:1900             *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    [::1]:57276            *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::4546:b5c0:cfa3:99af%8]:1900  *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::4546:b5c0:cfa3:99af%8]:2177  *:*                                    21436
  QWAVE
 [svchost.exe]
  UDP    [fe80::4546:b5c0:cfa3:99af%8]:57271  *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::5428:f516:35b1:966e%20]:546  *:*                                    2588
  Dhcp
 [svchost.exe]
  UDP    [fe80::5428:f516:35b1:966e%20]:1900  *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::5428:f516:35b1:966e%20]:2177  *:*                                    21436
  QWAVE
 [svchost.exe]
  UDP    [fe80::5428:f516:35b1:966e%20]:57275  *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::7996:8b98:5793:e477%3]:1900  *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::7996:8b98:5793:e477%3]:2177  *:*                                    21436
  QWAVE
 [svchost.exe]
  UDP    [fe80::7996:8b98:5793:e477%3]:57269  *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::90bf:f0ae:3c80:b911%12]:1900  *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::90bf:f0ae:3c80:b911%12]:2177  *:*                                    21436
  QWAVE
 [svchost.exe]
  UDP    [fe80::90bf:f0ae:3c80:b911%12]:5353  *:*                                    5164
 [TeamViewer_Service.exe]
  UDP    [fe80::90bf:f0ae:3c80:b911%12]:57272  *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::90c2:3c8c:ebd5:a9b6%19]:1900  *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::90c2:3c8c:ebd5:a9b6%19]:2177  *:*                                    21436
  QWAVE
 [svchost.exe]
  UDP    [fe80::90c2:3c8c:ebd5:a9b6%19]:57274  *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::9845:6ae6:9f4f:8991%7]:1900  *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::9845:6ae6:9f4f:8991%7]:2177  *:*                                    21436
  QWAVE
 [svchost.exe]
  UDP    [fe80::9845:6ae6:9f4f:8991%7]:57273  *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::e4ec:928f:9d81:da4%10]:1900  *:*                                    3528
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::e4ec:928f:9d81:da4%10]:2177  *:*                                    21436
  QWAVE
 [svchost.exe]
  UDP    [fe80::e4ec:928f:9d81:da4%10]:57270  *:*                                    3528
  SSDPSRV
 [svchost.exe]
```

Le processurs svchost est un processus de Windows qui sert d'hôte pour les autres processus et dont le fonctionnement repose sur des librairies dynamiques. Il y en a beaucoup car il en existe autant qu'il existe de processus qui l'utilisent.

Le processus httpd est le processus Apache pour les serveurs web

Le processus agsvc est un processus acer "Acer Office Manager Agent"

Le processus vmware-authd "VMware Authorization Service" est l'autorisation que j'ai donné a vmware pour pouvoir lancer des vm

Le processus mysqld appartient au logixiel xampp et est lié au serveur Apache

Le processus lsass est un executable necessaire pour le bon fonctionnement de windows et assure l'identification des utilisateurs

Le processus Agent est aussi connu comme un agent d'installation de pilotes

Le processur esrv_svc est un processus intel qui gere les rapports d'utilisation d'energie


### Users

Voici tous les utilisateurs sur mon pc :
```
PS C:\WINDOWS\system32> net user                                                                                        
comptes d’utilisateurs de \\LAPTOP-094TMCHO

-------------------------------------------------------------------------------
Administrateur           DefaultAccount           hugol
Invité                   WDAGUtilityAccount       YNOV01
YNOV02                   YNOV03                   YNOV04
YNOV05                   YNOV06                   YNOV07
YNOV08                   YNOV09                   YNOV10
YNOV11                   YNOV12                   YNOV13
YNOV14                   YNOV15                   YNOV16
YNOV17                   YNOV18                   YNOV19
YNOV20
La commande s’est terminée correctement.
```

C'est moi qui ai tous les droits sur mon pc :) :
```
PS C:\WINDOWS\system32> net user hugol                                                                                  Nom d’utilisateur                              hugol
Nom complet                                    hugo labedade
Commentaire
Commentaires utilisateur
Code du pays ou de la région                   000 (Valeur par défaut du système)
Compte : actif                                 Oui
Le compte expire                               Jamais

Mot de passe : dernier changmt.                ‎09/‎09/‎2019 18:55:48
Le mot de passe expire                         Jamais
Le mot de passe modifiable                     ‎09/‎09/‎2019 18:55:48
Mot de passe exigé                             Oui
L’utilisateur peut changer de mot de passe     Oui

Stations autorisées                            Tout
Script d’ouverture de session
Profil d’utilisateur
Répertoire de base
Dernier accès                                  Jamais

Heures d’accès autorisé                        Tout

Appartient aux groupes locaux                  *Administrateurs
                                               *HelpLibraryUpdaters
                                               *Utilisateurs
                                               *Utilisateurs du journ
Appartient aux groupes globaux                 *Aucun
La commande s’est terminée correctement.
```

Voice la liste de tous les processus en cours sur mon pc :
```
PS C:\WINDOWS\system32> tasklist                                                                                        
Nom de l’image                 PID Nom de la sessio Numéro de s Utilisation
========================= ======== ================ =========== ============
System Idle Process              0 Services                   0         8 Ko
System                           4 Services                   0       608 Ko
Registry                       120 Services                   0    31 652 Ko
smss.exe                       460 Services                   0       224 Ko
csrss.exe                      592 Services                   0     1 912 Ko
wininit.exe                    684 Services                   0       616 Ko
services.exe                   736 Services                   0     8 588 Ko
csrss.exe                      760 Console                    1     2 680 Ko
lsass.exe                      768 Services                   0    13 808 Ko
winlogon.exe                   856 Console                    1     4 412 Ko
svchost.exe                    984 Services                   0     1 004 Ko
WUDFHost.exe                  1008 Services                   0     5 396 Ko
svchost.exe                     88 Services                   0    28 132 Ko
fontdrvhost.exe                484 Services                   0       152 Ko
fontdrvhost.exe                476 Console                    1     2 484 Ko
svchost.exe                    908 Services                   0    15 660 Ko
svchost.exe                   1056 Services                   0     4 760 Ko
dwm.exe                       1212 Console                    1    39 004 Ko
svchost.exe                   1308 Services                   0     3 824 Ko
svchost.exe                   1332 Services                   0     1 860 Ko
svchost.exe                   1344 Services                   0     3 876 Ko
svchost.exe                   1384 Services                   0     4 056 Ko
svchost.exe                   1504 Services                   0     4 288 Ko
svchost.exe                   1516 Services                   0     4 276 Ko
WUDFHost.exe                  1636 Services                   0     2 056 Ko
svchost.exe                   1692 Services                   0     2 356 Ko
svchost.exe                   1732 Services                   0     3 264 Ko
svchost.exe                   1740 Services                   0     1 388 Ko
svchost.exe                   1860 Services                   0    11 004 Ko
svchost.exe                   1892 Services                   0     4 144 Ko
svchost.exe                   1968 Services                   0     4 920 Ko
svchost.exe                   1980 Services                   0     2 988 Ko
igfxCUIService.exe            1188 Services                   0     1 972 Ko
svchost.exe                   2096 Services                   0     1 764 Ko
svchost.exe                   2120 Services                   0    10 176 Ko
svchost.exe                   2220 Services                   0     9 172 Ko
svchost.exe                   2228 Services                   0     5 148 Ko
svchost.exe                   2268 Services                   0     5 292 Ko
svchost.exe                   2288 Services                   0     1 608 Ko
svchost.exe                   2328 Services                   0    12 832 Ko
dasHost.exe                   2560 Services                   0    10 116 Ko
svchost.exe                   2580 Services                   0     3 576 Ko
svchost.exe                   2588 Services                   0     3 952 Ko
svchost.exe                   2596 Services                   0     3 244 Ko
Memory Compression            2648 Services                   0   462 428 Ko
svchost.exe                   2808 Services                   0     7 496 Ko
svchost.exe                   2824 Services                   0     3 152 Ko
svchost.exe                   2980 Services                   0     8 908 Ko
svchost.exe                   2988 Services                   0     5 584 Ko
svchost.exe                   2524 Services                   0     2 452 Ko
svchost.exe                   3100 Services                   0     5 788 Ko
svchost.exe                   3168 Services                   0     2 364 Ko
svchost.exe                   3528 Services                   0     3 656 Ko
svchost.exe                   3780 Services                   0     9 208 Ko
EgisTicketService.exe         3880 Services                   0     3 264 Ko
svchost.exe                   3980 Services                   0     2 360 Ko
svchost.exe                   3988 Services                   0     4 624 Ko
svchost.exe                   3276 Services                   0     8 612 Ko
svchost.exe                   3468 Services                   0     8 228 Ko
svchost.exe                   4168 Services                   0     5 528 Ko
spoolsv.exe                   4236 Services                   0     4 880 Ko
wlanext.exe                   4244 Services                   0     2 584 Ko
conhost.exe                   4260 Services                   0       840 Ko
svchost.exe                   4356 Services                   0    14 248 Ko
Intel_PIE_Service.exe         4480 Services                   0     2 332 Ko
svchost.exe                   4524 Services                   0     1 944 Ko
svchost.exe                   4708 Services                   0     1 236 Ko
svchost.exe                   4852 Services                   0       992 Ko
svchost.exe                   4864 Services                   0    21 488 Ko
ACCSvc.exe                    4872 Services                   0     5 064 Ko
IntelCpHDCPSvc.exe            4880 Services                   0     1 456 Ko
DSAService.exe                4888 Services                   0     6 220 Ko
svchost.exe                   4904 Services                   0    47 356 Ko
ibtsiva.exe                   4912 Services                   0     1 600 Ko
openvpnserv.exe               4928 Services                   0     1 216 Ko
svchost.exe                   4936 Services                   0    11 028 Ko
svchost.exe                   4944 Services                   0     2 896 Ko
esif_uf.exe                   4968 Services                   0     1 316 Ko
svchost.exe                   4980 Services                   0    14 352 Ko
RstMwService.exe              5008 Services                   0     1 416 Ko
IntelAudioService.exe         5020 Services                   0     7 392 Ko
svchost.exe                   5028 Services                   0       900 Ko
RtkAudUService64.exe          5048 Services                   0     3 312 Ko
svchost.exe                   5056 Services                   0     3 652 Ko
sqlwriter.exe                 5064 Services                   0     1 936 Ko
mysqld.exe                    4288 Services                   0     1 780 Ko
SurSvc.exe                    4264 Services                   0    12 732 Ko
svchost.exe                   5148 Services                   0     3 340 Ko
TeamViewer_Service.exe        5164 Services                   0     5 372 Ko
svchost.exe                   5184 Services                   0     1 372 Ko
vmnetdhcp.exe                 5196 Services                   0     1 188 Ko
vmnat.exe                     5292 Services                   0     3 164 Ko
svchost.exe                   5300 Services                   0    12 464 Ko
MsMpEng.exe                   5312 Services                   0   183 220 Ko
sqlceip.exe                   5352 Services                   0    17 228 Ko
ReportingServicesService.     5360 Services                   0    46 560 Ko
sqlservr.exe                  5460 Services                   0    76 560 Ko
sqlservr.exe                  5472 Services                   0    53 088 Ko
sqlceip.exe                   5484 Services                   0    17 512 Ko
svchost.exe                   5608 Services                   0     1 828 Ko
svchost.exe                   5684 Services                   0     7 400 Ko
vmware-usbarbitrator64.ex     5692 Services                   0     3 364 Ko
vmware-authd.exe              5708 Services                   0     5 160 Ko
mysqld.exe                    5044 Services                   0    11 604 Ko
conhost.exe                   6200 Services                   0       764 Ko
IntelCpHeciSvc.exe            6276 Services                   0     1 384 Ko
WmiPrvSE.exe                  6708 Services                   0    16 576 Ko
WmiPrvSE.exe                  7116 Services                   0    18 524 Ko
svchost.exe                   6076 Services                   0     4 084 Ko
svchost.exe                   6628 Services                   0     3 608 Ko
Microsoft.ReportingServic     7592 Services                   0     5 712 Ko
conhost.exe                   7612 Services                   0       800 Ko
fdlauncher.exe                8424 Services                   0     1 120 Ko
Launchpad.exe                 8456 Services                   0     4 120 Ko
fdhost.exe                    8484 Services                   0     1 160 Ko
conhost.exe                   8492 Services                   0       612 Ko
svchost.exe                   8540 Services                   0    10 388 Ko
svchost.exe                   5080 Services                   0     1 260 Ko
svchost.exe                   4784 Services                   0     4 868 Ko
svchost.exe                   9508 Services                   0    35 512 Ko
dllhost.exe                   9868 Services                   0     4 272 Ko
NisSrv.exe                   10168 Services                   0     5 544 Ko
DSAUpdateService.exe          9564 Services                   0     5 220 Ko
DSATray.exe                   9972 Console                    1    37 244 Ko
sihost.exe                   10352 Console                    1    20 176 Ko
svchost.exe                  10376 Console                    1    17 704 Ko
svchost.exe                  10388 Console                    1     2 588 Ko
PresentationFontCache.exe    10448 Services                   0     2 068 Ko
svchost.exe                  10460 Console                    1    27 772 Ko
svchost.exe                  10596 Services                   0    11 224 Ko
taskhostw.exe                10632 Console                    1    12 204 Ko
svchost.exe                  10744 Services                   0     1 736 Ko
ctfmon.exe                   10844 Console                    1     7 596 Ko
igfxEM.exe                   11064 Console                    1     7 312 Ko
explorer.exe                 11100 Console                    1   117 108 Ko
svchost.exe                  11140 Services                   0    10 564 Ko
svchost.exe                  11384 Services                   0     7 664 Ko
svchost.exe                  11600 Console                    1    13 868 Ko
svchost.exe                  11736 Console                    1    10 656 Ko
svchost.exe                  11972 Services                   0     2 672 Ko
svchost.exe                  12044 Services                   0     2 828 Ko
StartMenuExperienceHost.e    12244 Console                    1    33 952 Ko
RuntimeBroker.exe            11336 Console                    1     4 744 Ko
SearchUI.exe                 12472 Console                    1    64 872 Ko
RuntimeBroker.exe            12596 Console                    1    36 140 Ko
GoogleCrashHandler.exe        1444 Services                   0       616 Ko
GoogleCrashHandler64.exe     13508 Services                   0        96 Ko
smartscreen.exe              13916 Console                    1    19 200 Ko
QASvc.exe                     2112 Services                   0     4 704 Ko
QAAgent.exe                  13152 Console                    1     2 952 Ko
QAAdminAgent.exe              9696 Console                    1     7 448 Ko
igfxext.exe                   1432 Console                    1     2 360 Ko
unsecapp.exe                 14292 Console                    1     2 672 Ko
QALockHandler.exe            12180 Console                    1     2 804 Ko
unsecapp.exe                  9996 Console                    1     2 636 Ko
ApplicationFrameHost.exe      2360 Console                    1    23 764 Ko
WinStore.App.exe              2400 Console                    1       196 Ko
RuntimeBroker.exe            13716 Console                    1     3 364 Ko
svchost.exe                   5228 Services                   0     7 928 Ko
svchost.exe                   1664 Services                   0     5 208 Ko
svchost.exe                  10900 Services                   0     4 772 Ko
AgSvc.exe                     8552 Services                   0     8 520 Ko
IAStorDataMgrSvc.exe         11532 Services                   0     8 276 Ko
jhi_service.exe               2768 Services                   0     1 168 Ko
LMS.exe                       9056 Services                   0     2 500 Ko
SgrmBroker.exe               10544 Services                   0     4 404 Ko
svchost.exe                  10480 Services                   0     4 020 Ko
AgStdAlo.exe                  2484 Console                    1       628 Ko
ePowerButton_NB.exe          11212 Console                    1     1 944 Ko
ACCStd.exe                    2764 Console                    1     7 300 Ko
conhost.exe                  13116 Services                   0     1 316 Ko
esrv.exe                     13616 Console                    1     8 892 Ko
UBTService.exe                4400 Services                   0    16 396 Ko
svchost.exe                   1176 Services                   0     4 952 Ko
SettingSyncHost.exe          14364 Console                    1     4 824 Ko
SkypeApp.exe                  9320 Console                    1    31 780 Ko
RemindersServer.exe          14548 Console                    1     7 552 Ko
SkypeBackgroundHost.exe      15048 Console                    1     2 076 Ko
RuntimeBroker.exe            12984 Console                    1    10 228 Ko
svchost.exe                  12408 Services                   0    12 564 Ko
SecurityHealthSystray.exe    12980 Console                    1     1 804 Ko
SecurityHealthService.exe    13236 Services                   0     7 200 Ko
RtkAudUService64.exe         14632 Console                    1     6 400 Ko
Discord.exe                   2744 Console                    1    52 480 Ko
Discord.exe                  15364 Console                    1    94 604 Ko
Discord.exe                  15412 Console                    1    18 804 Ko
Discord.exe                  16104 Console                    1     2 160 Ko
Discord.exe                  16276 Console                    1   533 984 Ko
CCXProcess.exe               16400 Console                    1        80 Ko
node.exe                     16420 Console                    1     9 008 Ko
conhost.exe                  16428 Console                    1       740 Ko
svchost.exe                  16672 Services                   0     5 144 Ko
EgisTSR.exe                  16772 Console                    1    15 724 Ko
chrome.exe                   17016 Console                    1   260 432 Ko
chrome.exe                   17044 Console                    1     1 884 Ko
chrome.exe                   17128 Console                    1     1 364 Ko
AdobeIPCBroker.exe           17164 Console                    1     1 828 Ko
chrome.exe                   17356 Console                    1   245 948 Ko
chrome.exe                   17364 Console                    1    48 824 Ko
Discord.exe                  16436 Console                    1     7 416 Ko
chrome.exe                   16632 Console                    1    41 768 Ko
chrome.exe                   15632 Console                    1     7 548 Ko
chrome.exe                   17440 Console                    1    18 864 Ko
chrome.exe                   17448 Console                    1   121 076 Ko
chrome.exe                   17912 Console                    1     8 248 Ko
IAStorIcon.exe               17632 Console                    1     4 500 Ko
taskhostw.exe                18964 Console                    1     7 992 Ko
WindowsInternal.Composabl     5508 Console                    1    10 196 Ko
RuntimeBroker.exe            14544 Console                    1     1 132 Ko
dllhost.exe                  12252 Console                    1     5 092 Ko
chrome.exe                   11944 Console                    1     3 940 Ko
CompPkgSrv.exe               13288 Console                    1     4 036 Ko
RuntimeBroker.exe            16876 Console                    1    19 856 Ko
ShellExperienceHost.exe       7156 Console                    1       212 Ko
RuntimeBroker.exe            18292 Console                    1     2 260 Ko
svchost.exe                  20956 Services                   0     2 088 Ko
OfficeClickToRun.exe          8528 Services                   0    34 164 Ko
AppVShNotify.exe             18828 Services                   0       792 Ko
AppVShNotify.exe              3928 Console                    1       796 Ko
SearchIndexer.exe             6912 Services                   0    38 028 Ko
svchost.exe                  19216 Services                   0     1 632 Ko
svchost.exe                  21436 Services                   0     2 824 Ko
svchost.exe                  21036 Services                   0     1 648 Ko
rundll32.exe                 15432 Console                    1     2 272 Ko
LockApp.exe                   6240 Console                    1    17 100 Ko
RuntimeBroker.exe            13380 Console                    1    17 836 Ko
Microsoft.Photos.exe          1436 Console                    1       700 Ko
RuntimeBroker.exe             9640 Console                    1    14 516 Ko
Video.UI.exe                 19656 Console                    1       408 Ko
RuntimeBroker.exe            10328 Console                    1     2 952 Ko
dllhost.exe                  10148 Console                    1     5 540 Ko
svchost.exe                  21004 Console                    1     1 368 Ko
SecurityHealthHost.exe       10280 Console                    1     1 540 Ko
YourPhone.exe                19228 Console                    1     2 584 Ko
RuntimeBroker.exe            19028 Console                    1    10 564 Ko
conhost.exe                  22712 Console                    1       972 Ko
vsls-agent.exe               23236 Console                    1     3 216 Ko
conhost.exe                  19900 Console                    1     1 220 Ko
svchost.exe                  23612 Services                   0     2 904 Ko
svchost.exe                  25120 Services                   0     3 580 Ko
chrome.exe                   18368 Console                    1   261 424 Ko
chrome.exe                   14476 Console                    1    58 232 Ko
chrome.exe                   19352 Console                    1    10 696 Ko
svchost.exe                  14956 Services                   0     9 924 Ko
chrome.exe                    1716 Console                    1    84 596 Ko
svchost.exe                   8120 Services                   0     2 664 Ko
httpd.exe                    10416 Console                    1     1 824 Ko
conhost.exe                  18744 Console                    1     1 836 Ko
httpd.exe                    17028 Console                    1     1 516 Ko
chrome.exe                   26868 Console                    1    30 296 Ko
svchost.exe                   9408 Services                   0     1 092 Ko
chrome.exe                   20236 Console                    1    41 148 Ko
AppMonitorPlugIn.exe          4116 Console                    1    12 288 Ko
esrv_svc.exe                 26248 Services                   0    24 612 Ko
audiodg.exe                  11508 Services                   0    15 972 Ko
WUDFHost.exe                   356 Services                   0     4 088 Ko
chrome.exe                   30852 Console                    1    67 456 Ko
svchost.exe                  31184 Services                   0     3 664 Ko
WUDFHost.exe                 15100 Services                   0     4 352 Ko
chrome.exe                    1132 Console                    1   187 408 Ko
chrome.exe                   26936 Console                    1    76 256 Ko
Code.exe                      7884 Console                    1    76 220 Ko
Code.exe                     27152 Console                    1    95 680 Ko
Code.exe                     18212 Console                    1    20 008 Ko
Code.exe                     29284 Console                    1   168 396 Ko
Code.exe                     25020 Console                    1     8 932 Ko
Code.exe                      7548 Console                    1    68 480 Ko
Code.exe                     23504 Console                    1    56 252 Ko
conhost.exe                  29812 Console                    1     4 176 Ko
vsls-agent.exe               14048 Console                    1    27 500 Ko
vds.exe                      29952 Services                   0     8 548 Ko
powershell.exe               28656 Console                    1    57 160 Ko
conhost.exe                   3476 Console                    1    14 796 Ko
EgisTSR.exe                  30268 Console                    1        60 Ko
SystemSettings.exe           19388 Console                    1     7 236 Ko
SearchProtocolHost.exe       19536 Services                   0    12 048 Ko
SearchFilterHost.exe         22860 Services                   0     6 196 Ko
SearchProtocolHost.exe       25620 Console                    1     7 760 Ko
backgroundTaskHost.exe        1704 Console                    1    30 092 Ko
svchost.exe                  28112 Services                   0    12 376 Ko
chrome.exe                   26164 Console                    1    72 932 Ko
chrome.exe                    4620 Console                    1    42 504 Ko
chrome.exe                   27892 Console                    1    22 168 Ko
tasklist.exe                 14132 Console                    1     8 356 Ko
```

Le processus System est simplement Windows, et sans, windows ne pourrait juste pas fonctionner.

Le processus vds.exe est un fichier executable qui assure le fonctionnement des disques durs.

Le processus smss.exe est exécuté dès le processus de démarrage de windows. Durant cette phase, il lance autochk.exe pour vérifier le ou les différents systèmes de fichiers, puis après cette vérification, il crée les variables d'environnement et démarre certains processus indispensable au fonctionnement de windows tel que la gestion de la mémoire ou encore le mode noyau du sous-système Win32.

Le processus wininit.exe est un lanceur d'application en arrière-plan. Il est responsable du processus d'initialisation Windows.

Le processus services.exe gère le démarrage et l'arrêt des services Windows mais aussi la création et la suppression de ces derniers.

## Scripting



## Gestion de softs

Pour le téléchargement sur internet, le gestionnaire de paquet permet de vérifier l'intégrité d'un fichier avant de la télécharger

J'ai installé chocolatey sur mon pc et j'ai listé tous les packages sur mon PC : 
```
PS C:\WINDOWS\system32> choco list
Chocolatey v0.10.15
azshell 0.2.2 [Approved] Downloads cached for licensed users
tusk.portable 0.23.0 [Approved]
corsixth 0.63 [Approved]
playlist-creator 3.6.2 [Approved] - Possibly broken
moonlight.install 1.0.0 [Approved]
playlist-creator.portable 3.6.2 [Approved] Downloads cached for licensed users - Possibly broken for FOSS users (due to original download location changes by vendor)
playlist-creator.install 3.6.2 [Approved] Downloads cached for licensed users - Possibly broken for FOSS users (due to original download location changes by vendor)
corsixth.portable 0.63 [Approved]
k-meleon.portable 75.1 [Approved]
k-meleon.install 75.1 [Approved]
k-meleon 75.1 [Approved]
moonlight.portable 1.0.0 [Approved]
brutaldoom-scythe2 2.0.0 [Approved] Downloads cached for licensed users
brutaldoom-dtwid 1.1.1 [Approved] Downloads cached for licensed users
brutaldoom-goingdown 1.0.0 [Approved] Downloads cached for licensed users
brutaldoom-d2reload 1.0.0 [Approved] Downloads cached for licensed users
3dduke-shareware 1.3.0 [Approved] Downloads cached for licensed users
opentyrian 2.1.0 [Approved] Downloads cached for licensed users
infinitex.portable 0.9.16 [Approved]
infinitex 0.9.16 [Approved]
infinitex.install 0.9.16 [Approved]
doom-sigil 1.1.0 [Approved] Downloads cached for licensed users
spaceradar 5.1.0 [Approved] Downloads cached for licensed users
dotmemory-unit 3.0.20171219.105559 [Approved]
keepass-kpentrytemplates 1.8.0.20190608 [Approved]
speedcrunch.portable 0.12 [Approved]
nats-server 2.0.0.20190610 [Approved] Downloads cached for licensed users
pluralsight-transcripter 1.0.0 [Approved] Downloads cached for licensed users
ukinternationalkeyboard 2.0.0 [Approved] Downloads cached for licensed users
klatexformula 4.0.0 [Approved]
boot-no-hyperv 0.1.0 [Approved]
classyshark 8.2 [Approved]
KB2519277 1.0.0 [Approved] Downloads cached for licensed users
dexed 0.9.4 [Approved]
rss-builder 2.1.8 [Approved] Downloads cached for licensed users
qaac 2.68 [Approved] Downloads cached for licensed users
avinaptic 2011.12.18 [Approved]
splint.portable 3.1.2 [Approved]
splint.install 3.1.2 [Approved]
splint 3.1.2 [Approved]
mcr-r2015b 9.0 [Approved] Downloads cached for licensed users
q10.portable 1.2.21 [Approved]
aerozoom 4.0.0.7 [Approved]
fluxfonts 2.0 [Approved]
windows-sandbox 0.0.1 [Approved]
dissenter-browser 0.66.99 [Approved] Downloads cached for licensed users
altcopy 1.0.7 [Approved] Downloads cached for licensed users
gsubs 1.0.2 [Approved]
quollwriter 2.6.14 [Approved]
brutaldoom-kamasutra 03.09.05 [Approved] Downloads cached for licensed users
click-monitor-ddc 7.0 [Approved] Downloads cached for licensed users
buddybackup 2.0.2.400 [Approved] Downloads cached for licensed users
prometheus-grok-exporter 0.2.8 [Approved] Downloads cached for licensed users
cica 5.0.1.20190723 [Approved] Downloads cached for licensed users
librefox-firefox 2.1 [Approved]
vscode-cortex-debug 0.3.1 [Approved]
cronical 1.3 [Approved]
little-fighter-2 2.0 [Approved] Downloads cached for licensed users
jcliff 2.12.3 [Approved]
mcr-r2019a 9.6.0.1150989 [Approved] Downloads cached for licensed users
wop 1.6 [Approved] Downloads cached for licensed users
keyferret.install 2.6 [Approved]
keyferret.portable 2.6 [Approved]
keyferret 2.6 [Approved]
sql-multi-select 4.3.0.142 [Approved] Downloads cached for licensed users - Possibly broken for FOSS users (due to original download location changes by vendor)
tabula 1.2.1 [Approved]
watchexec 1.10.3 [Approved] Downloads cached for licensed users
acronis-vdi 1.1.2141.20190805 [Approved] Downloads cached for licensed users
disable-logon-blur 1.0.0 [Approved]
zephyr-ide 1.14.0 [Approved]
acronis-drive-monitor 1.0.566 [Approved] Downloads cached for licensed users
startup-organizer 2.9.324 [Approved] Downloads cached for licensed users
evga-eleet 1.10.4 [Approved] Downloads cached for licensed users
hyperx-ngenuity 5.2.8.0 [Approved] Downloads cached for licensed users
gpac 0.8.0.20190812 [Approved] Downloads cached for licensed users
briss 2.0 [Approved]
huggle 3.4.9 [Approved] Downloads cached for licensed users
adoptopenjdk12 12.0.2.10 [Approved] Downloads cached for licensed users
tcpipmanager.portable 4.1.1 [Approved]
tcpipmanager.install 4.1.1 [Approved]
leagueoflegendseuw 1.0.0.0 [Approved] Downloads cached for licensed users - Possibly broken for FOSS users (due to original download location changes by vendor)
tcpipmanager 4.1.1 [Approved]
orangec 6.0.42.1 [Approved]
jpdftweak 1.1 [Approved]
nip2 8.7.0 [Approved]
paraview 5.6.1 [Approved] Downloads cached for licensed users
prometheus-sql-exporter 0.5 [Approved] Downloads cached for licensed users
sdcard-formatter 5.0.1 [Approved] Downloads cached for licensed users
iecv 1.79 [Approved]
dotmemory-console 2019.2.1 [Approved]
90 packages found.
```

La meme chose en faisant la commande : choco list -v : 
```
acronis-vdi 1.1.2141.20190805 [Approved] Downloads cached for licensed users
 Title: Acronis Virtual Disk Driver | Published: 05/08/2019
 Package approved by Pauby on août 13 2019 17:22:31.
 Package testing status: Passing on août 05 2019 19:25:05.
 Number of Downloads: 135 | Downloads for this version: 95
 Package url
 Chocolatey Package Source: https://github.com/chtof/chocolatey-packages/tree/master/manual/acronis-vdi
 Package Checksum: '7QwXRigEkkD9lGtifp0hrNj5lh4rhDar4jfij13z29okhtbVCZ4CVYeCO2wBYc+z/E9lyNxYCT7bYT4L1mrhAw==' (SHA512)
 Tags: acronis-vdi acronis virtual disk driver
 Software Site: https://kb.acronis.com/content/38937
 Software License: n/a
 Mailing List: https://forum.acronis.com/
 Issues: https://kb.acronis.com/
 Summary: Solves an issue to install True Image 2013 successfully on a 2 TB+ drive.
 Description: Solves an issue to install True Image 2013 successfully on a 2 TB+ drive.
  See. https://kb.acronis.com/content/38937

disable-logon-blur 1.0.0 [Approved]
 Title: Disable Windows 10 Logon Blur | Published: 05/08/2019
 Package approved by flcdrg on août 17 2019 00:12:04.
 Package testing status: Passing on août 05 2019 20:50:17.
 Number of Downloads: 146 | Downloads for this version: 146
 Package url
 Chocolatey Package Source: https://github.com/pauby/chocopackages/tree/master/manual/disable-logon-blur
 Package Checksum: 'dY0ZkoP3m9YmUjiZuRMRm5qIdp4S4MMmnBTu3Y/rD561ly4+TwNK3dCDgKJww478KWx3S2V3VdEM6cl87RpIDA==' (SHA512)
 Tags: windows windows10 logon admin
 Software Site: https://github.com/pauby/chocopackages/tree/master/manual/disable-logon-blur
 Software License: n/a
 Documentation: https://github.com/pauby/ChocoPackages/blob/master/manual/disable-logon-blur/README.md
 Summary: Remove the background blur on the logon screen of Windows 10 1903+.
 Description: Starting with Windows 10 1903 the logon screen background wallpaper is blurred. This package removes this feature to keep it in line with previous version and un-blurs the background.

  Requirements:

  * Windows 10 1903 (currently) - only previous version this should have no effect;
  * Administrator rights - this allows the registry entries to be updated and will fail without it;

zephyr-ide 1.14.0 [Approved]
 Title: zephyr-ide (Install) | Published: 20/10/2019
 Package approved by flcdrg on oct. 20 2019 09:36:13.
 Package testing status: Exempted on oct. 20 2019 07:43:24.
 Number of Downloads: 142 | Downloads for this version: 142
 Package url
 Chocolatey Package Source: https://github.com/n3rd4i/zephyr-ide
 Package Checksum: 'aeNlisUAZNx7Kn4Mf8WvNGRC7FxkwqcmML8v4W8bCTJwteJvL3MSTwinACnZNWp5pO7NaK5I0Hk6dR5LgWHfrA==' (SHA512)
 Tags: zephyr-ide zephyr ide development embedded
 Software Site: https://www.zephyrproject.org/
 Software License: https://github.com/zephyrproject-rtos/zephyr/blob/master/LICENSE
 Software Source: https://github.com/zephyrproject-rtos/zephyr
 Documentation: https://docs.zephyrproject.org/latest/index.html
 Issues: https://github.com/zephyrproject-rtos/zephyr/issues
 Summary: Zephyr based IDE from multiple components
 Description: ## Ready-to-start Windows IDE for developing with Zephyr platform
  This package is a set of tools needed for a Windows user to start developing applications with [Zephyr Project](https://www.zephyrproject.org/).
  Using [VSCode](http://aka.ms/vscode) as main IDE with the source for the Zephyr Project together with GNU ARM toolchain.

  ### Components:
  * [VSCode](http://aka.ms/vscode) based IDE (w/ ext. cpptools, cortex-debug)
  * [GNU Arm Embedded Toolchain](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm)
  * [CMake](https://cmake.org/) open-source system that manages the build process.
  * [nRF Command Line Tools](https://www.nordicsemi.com/Software-and-Tools/Development-Tools/nRF-Command-Line-Tools)
  * [J-Link Software and Documentation pack for Windows](https://www.segger.com/downloads/jlink/JLink_Windows.exe)
  * [OpenOCD](http://openocd.org/), the Open On-Chip Debugger
  * [pyOCD](https://github.com/mbedmicro/pyOCD) is an open source Python package for programming and debugging Arm Cortex-M microcontrollers
 Release Notes: https://github.com/n3rd4i/zephyr-ide/blob/master/ReadMe.md

acronis-drive-monitor 1.0.566 [Approved] Downloads cached for licensed users
 Title: Acronis Drive Monitor | Published: 10/08/2019
 Package approved by flcdrg on août 17 2019 02:19:40.
 Package testing status: Passing on août 10 2019 15:05:55.
 Number of Downloads: 183 | Downloads for this version: 183
 Package url
 Chocolatey Package Source: https://github.com/chtof/chocolatey-packages/tree/master/manual/acronis-drive-monitor
 Package Checksum: 'nR+XUi98v09sLVMS0MaGTcPXyCLPfbCg5eNSKs0Hxuv5eix69q5nofwHfvA33zGFDPhYZJMQNVmkSIZ9EI/uDA==' (SHA512)
 Tags: acronis-drive-monitor acronis drive monitor disk
 Software Site: https://kb.acronis.com/content/58078
 Software License: n/a
 Documentation: http://www.acronis.com/en-us/download/docs/adm/userguide/
 Mailing List: https://forum.acronis.com/
 Issues: https://kb.acronis.com/
 Summary: Acronis Drive Monitor is a free, downloadable software application developed by Acronis to monitor server, workstation and PC hard disk drives.
 Description: Acronis Drive Monitor is a free, downloadable software application developed by Acronis to monitor server, workstation and PC hard disk drives.

  ## Features
  - Automatically checks for disk problems
  Works on any Windows PC, workstation or server.
  - Weekly status reports
  Shows the electromechanical health of all your drives in one report.
  - Monitors Event logs
  Flags events that may indicate that data is in danger so you can back it up.
  - Can support RAID drives too
  Scripting allows you to monitor RAID controllers not using S.M.A.R.T. monitoring technology. An Acronis forum acts as a clearinghouse for users to share scripts.
  - Three kinds of support
  Acronis forum, Acronis knowledge base with dozens of articles and built-in help are available for this easy-to-use software application.
  - Receive alerts immediately
  Sends an email and displays a message on the Windows taskbar when it uncovers a disk-related problem.

  ![screenshot](https://cdn.jsdelivr.net/gh/chtof/chocolatey-packages/manual/acronis-drive-monitor/screenshot.png)

startup-organizer 2.9.324 [Approved] Downloads cached for licensed users
 Title: Startup Organizer | Published: 10/08/2019
 Package approved by flcdrg on août 17 2019 06:18:31.
 Package testing status: Passing on août 10 2019 17:21:18.
 Number of Downloads: 97 | Downloads for this version: 97
 Package url
 Chocolatey Package Source: https://github.com/chtof/chocolatey-packages/tree/master/automatic/startup-organizer
 Package Checksum: 'LCBj80rk7ZcR4UwiUlELcRni7VwYoXVE+MguHOQFwx9q3ia+GhJDC6EYzruEdegvtELhp2VpgMYptOZGJMEolw==' (SHA512)
 Tags: startup-organizer startup organizer trial
 Software Site: https://metaproducts.com/products/startup-organizer
 Software License: https://metaproducts.com/products/startup-organizer
 Mailing List: https://metaproducts.com/forum/startup-organizer
 Issues: https://metaproducts.com/forum/startup-organizer
 Summary: Startup Organizer was developed to provide quick access to all of the programs that are automatically started when you turn on or logon to your computer.
 Description: Startup Organizer is a Windows 95/98/ME/NT/2000/XP/2003/Vista/7 program that was developed to provide quick access to all of the programs that are automatically started when you turn on or logon to your computer.

  Using Startup Organizer, you can inspect, edit, print and/or temporarily disable such programs and make backup configurations.

  You may significantly reduce the time required for your system startup by disabling programs that you don`t need all the time.

  With RunOnceEx, Services and AutoRunDLL technology support, StartUp Organizer provides you with the most complete control on all methods to start programs automatically.

  The **Controlled Startup** feature allows you to skip certain programs during startup if you hold the **[Shift]** key while Windows is logging on.

  The new version allows you to choose the key for the Controlled Startup feature. It is also possible now to prompt for a confirmation of whether to start all or each program in the Controlled Startup.

  **StartUp Guard** detects non-standard ways to run applications when Windows starts and issues recommendations when it encounters suspicious programs.

  Users of Windows NT 4.0/2000/XP/2003/Vista/2008 can benefit from the new ability to work with **other users startup configurations**. StartUp Organizer displays other users among your standard Registry, Controlled Startup and Start menu items. You can view programs of other users, edit them, add new ones and drag programs to them.

  You can even **add programs to multiple users** with just a few clicks!

  You can also define the **order** in which to run your programs and even set a **delay** when running them consecutively.

  ![screenshot](https://cdn.jsdelivr.net/gh/chtof/chocolatey-packages/automatic/startup-organizer/screenshot.png)
 Release Notes: https://metaproducts.com/news

evga-eleet 1.10.4 [Approved] Downloads cached for licensed users
 Title: EVGA E-LEET Tuning Utility | Published: 13/08/2019
 Package approved by Pauby on août 20 2019 16:33:45.
 Package testing status: Passing on août 13 2019 17:30:10.
 Number of Downloads: 134 | Downloads for this version: 123
 Package url
 Chocolatey Package Source: https://github.com/chtof/chocolatey-packages/tree/master/manual/evga-eleet
 Package Checksum: 'KCY7hMDdBbuZ+u9wkUEIDOuz/LPkv/RiPsUIQgTkN2wCJ6YyZ4aX7YXd70+r7MoVISRt7Ypepp2Zq2l2x7Dlgg==' (SHA512)
 Tags: evga-eleet ecga e-leet advanced motherboard tuning
 Software Site: https://www.evga.com/eleet/
 Software License: https://www.evga.com/legal/terms/
 Mailing List: http://www.evga.com/forums/tt.aspx?forumid=22
 Summary: Free EVGA E-LEETX advanced motherboard tuning.
 Description: EVGA now gives you more with the EVGA E-LEET Tuning Utility. This utility allows you to easily set your motherboard QPI and system Voltages from within Windows to get your system running at the highest level of performance possible. EVGA E-LEET also includes a validation feature, allowing you to save a CPU screenshot and generates a unique URL, also a Brink OC feature that automatically saves a screenshot with every clockspeed increase.

  Increase your voltage to maximize your overclock, or lower your voltage to decrease the operating temperatures.

  **CPU**
  Familiar and clean interface.

  **Memory**
  View memory frequency, timings and memory amount.

  **Monitoring**
  Monitor system vitals.

  **Overclocking**
  Overclock on the fly, from within Windows!

  **Voltages**
  Adjust system voltages in realtime.

  **Options**
  Setup profiles and assign hotkeys.

  ## Features
  - Real-time monitoring of CPU, Memory and QPI frequencies
  - Real-time monitoring of vital voltages such as: CPU VCore, DRAM Voltage, +12v, etc.
  - Real-time monitoring of each individual core, north bridge and voltages regulator temperatures
  - Real-time adjustments of QPI Base Clocks, CPU Multiplier and PCIe Bus Frequencies

  ## System Requirements
  - Windows XP, Vista, 7, 8 32/64, 10 32/64
  - EVGA Z390, X299, Z370, H370, B360, Z270, Z170, X99, Z87, X79, X58, P67/Z68, P55* or H57/H55* Motherboards
    * P55V and H55V Motherboards not supported

  ![screenshot](https://cdn.jsdelivr.net/gh/chtof/chocolatey-packages/manual/evga-eleet/screenshot.png)

hyperx-ngenuity 5.2.8.0 [Approved] Downloads cached for licensed users
 Title: HyperX NGenuity Software | Published: 09/08/2019
 Package approved by flcdrg on août 17 2019 02:10:37.
 Package testing status: Passing on août 09 2019 22:08:42.
 Number of Downloads: 638 | Downloads for this version: 638
 Package url
 Chocolatey Package Source: https://github.com/JMarquezine/chocolatey-hyperxngenuity
 Package Checksum: '8InS1KLwz2J+4ASCJgfsph1lDpM02D8HS2d6WT48MKxeI76Db2RQacWG+aMqtlh5DbJ4XHflI3ZC2KTUQTB4yA==' (SHA512)
 Tags: hyperxngenuity ngenuity hyperx
 Software Site: https://www.hyperxgaming.com/us/ngenuity
 Software License: https://www.kingston.com/company/privacy
 Documentation: https://media.kingston.com/support/downloads/Ngenuity_Gaming_Software_Manual.pdf
 Issues: https://www.kingston.com/support
 Summary: HyperX NGenuity is powerful, easy-to-use software that will allow you to personalize your HyperX products.
 Description: HyperX NGenuity is powerful, easy-to-use software that will allow you to personalize your HyperX products.
  Set button bindings, program and store macros, assign colors to individual keys on your keyboard,
  or set up colors for zones or keys, adjust your audio and monitor battery life;
  HyperX NGenuity gives you as much control as you want.
  HyperX NGenuity also comes with a library of presets for the hottest games, so you can quickly choose one to install, 
  and jump straight into the action.
  Be on the lookout for NGenuity support for new features and future compatible HyperX peripherals.
  [See compatible products](https://www.hyperxgaming.com/us/ngenuity#product-gallery-related)

gpac 0.8.0.20190812 [Approved] Downloads cached for licensed users
 Title: GPAC | Published: 12/08/2019
 Package approved by Pauby on août 20 2019 10:38:27.
 Package testing status: Passing on août 12 2019 15:00:58.
 Number of Downloads: 331 | Downloads for this version: 221
 Package url
 Chocolatey Package Source: https://github.com/facorread/GPAC-Chocolatey
 Package Checksum: '2aZv2nQKF5UNg6rawPrPQvkCKKThZFkQQcYQi2n8cZylrVWlW549GGeeNMvlCqeL+/KG8U5ljUvxuLab5tKPXA==' (SHA512)
 Tags: library foss cross-platform multimedia audio video mp3 dvd avi media player
 Software Site: https://gpac.wp.imt.fr/
 Software License: https://raw.githubusercontent.com/gpac/gpac/master/COPYING
 Software Source: https://github.com/gpac/gpac
 Documentation: https://gpac.wp.imt.fr/mp4box/mp4box-documentation/
 Issues: https://github.com/gpac/gpac/issues
 Summary: MPEG-4 Systems Framework, SDK, and command line tools
 Description: MPEG-4 systems framework, SDK, and command line tools (MP4Box, MP4Client, MP42TS, MP42AVI, DashCast). GPAC stands for  GPAC Project on Advanced Content.
 Release Notes: https://raw.githubusercontent.com/gpac/gpac/master/Changelog

briss 2.0 [Approved]
 Title: Briss | Published: 10/08/2019
 Package approved by flcdrg on août 17 2019 02:15:18.
 Package testing status: Passing on août 10 2019 11:10:17.
 Number of Downloads: 144 | Downloads for this version: 144
 Package url
 Chocolatey Package Source: https://github.com/chtof/chocolatey-packages/tree/master/automatic/briss
 Package Checksum: 'wIle/vumYikcXg8vm8SU79903ODWjLB08pP7X+JuRuTQ7wNcp5maA5AtsneW3UmM6L7NxpnCtE/oUNJAUgS+mA==' (SHA512)
 Tags: briss mass PDF crop
 Software Site: https://github.com/mbaeuerle/Briss-2.0
 Software License: https://raw.githubusercontent.com/mbaeuerle/Briss-2.0/master/LICENSE.txt
 Software Source: https://github.com/mbaeuerle/Briss-2.0
 Documentation: https://github.com/mbaeuerle/Briss-2.0#commandline
 Issues: https://github.com/mbaeuerle/Briss-2.0/issues
 Summary: Briss 2.0 is intended to be a GUI Update for the Briss PDF cropping tool.
 Description: Briss 2.0 is intended to be a GUI Update for the Briss PDF cropping tool.

  Briss 2.0 is based on Briss 0.9 which is located at sourceforge: http://sourceforge.net/projects/briss/

  ### Things that are done by now
  - Small refinements on gui which improve the workflow
  - Better file chooser than provided by swing
  - Added support for drag and drop

  ## Screenshots
  Startscreen with drag and drop support:

  ![screenshot](https://cdn.jsdelivr.net/gh/chtof/chocolatey-packages/manual/briss/screenshot1.png)

  Cropping view:

  ![screenshot](https://cdn.jsdelivr.net/gh/chtof/chocolatey-packages/manual/briss/screenshot2.png)
 Release Notes: https://github.com/mbaeuerle/Briss-2.0/releases

huggle 3.4.9 [Approved] Downloads cached for licensed users
 Title: Huggle | Published: 11/08/2019
 Package approved by flcdrg on août 17 2019 06:23:13.
 Package testing status: Passing on août 11 2019 11:02:58.
 Number of Downloads: 84 | Downloads for this version: 74
 Package url
 Chocolatey Package Source: https://github.com/chtof/chocolatey-packages/tree/master/automatic/huggle
 Package Checksum: 'Z0H4S6WQphH2dfOdR2ZEaDGr6e9CVW5tXQovtxskZYV8lPwRYIR0oE1eRWMfAe4pkMzDjdLJcZnM2WJjuCt5+Q==' (SHA512)
 Tags: huggle wikimedia diff browser
 Software Site: https://en.wikipedia.org/wiki/Wikipedia:Huggle
 Software License: https://raw.githubusercontent.com/huggle/huggle3-qt-lx/master/LICENSE
 Software Source: https://github.com/huggle/huggle3-qt-lx
 Documentation: https://www.mediawiki.org/wiki/Manual:Huggle
 Issues: https://phabricator.wikimedia.org/tag/huggle/
 Summary: Huggle is an anti-vandalism tool for use on MediaWiki based projects.
 Description: **Huggle** is a diff browser intended for dealing with vandalism and other unconstructive edits on Wikimedia projects, written in C++ using the Qt framework. It was originally developed in .NET Framework by [Gurch](https://en.wikipedia.org/wiki/User:Gurch), who is no longer active on this project. Anyone can download Huggle, but rollback permission is required to use the program without restrictions on the English Wikipedia.

  The principal idea of Huggle as an anti-vandalism tool is to make it possible for Wikipedia to stay as open and free as possible (allowing everyone to edit without any restrictions), while keeping it clean of any vandalism.

  While Huggle can load and review edits made to Wikipedia in real time, it also helps users identify unconstructive edits and allows them to be reverted quickly. Various mechanisms are used to draw conclusions as to whether an edit is constructive or not. It uses a semi-distributed model where edits are retrieved using a provider (this can be anything that is capable of distributing a stream of edit information, such as the Wikipedia API or IRC recent changes feed), pre-parsed and analyzed. This information is then shared with other anti-vandalism tools, such as [ClueBot NG](https://en.wikipedia.org/wiki/User:ClueBot_NG). Huggle also uses a number of self-learning mechanisms, including a global white-list (users that are considered trusted) and user-badness scores that are stored locally on the client's computer.

  Before using Huggle, it is recommended that users read the [privacy statement](https://en.wikipedia.org/wiki/Wikipedia:Huggle/Privacy), which contains information about how Huggle stores and manages data. Support and development chat is available on [#huggle](https://webchat.freenode.net/?channels=#huggle). Also, please use it with caution and verify every edit you make.

  ![screenshot](https://cdn.jsdelivr.net/gh/chtof/chocolatey-packages/automatic/huggle/screenshot.png)
 Release Notes: https://github.com/huggle/huggle3-qt-lx/releases

adoptopenjdk12 12.0.2.10 [Approved] Downloads cached for licensed users
 Title: AdoptOpenJDK 12 | Published: 13/08/2019
 Package approved by Pauby on août 20 2019 16:52:31.
 Package testing status: Passing on août 13 2019 18:00:15.
 Number of Downloads: 303 | Downloads for this version: 303
 Package url
 Chocolatey Package Source: https://github.com/johanjanssen/ChocolateyPackages/tree/master/AdoptOpenJDK
 Package Checksum: 'fUP0FzDV/a+IaIT400/Tn/5tANPO2I/WgxkbZWF1NEU2kkOciDYzbTvkRZ1C5NPSejRUnuQy2l08PtJUnoN//w==' (SHA512)
 Tags: openjdk java jvm
 Software Site: https://adoptopenjdk.net/
 Software License: https://github.com/AdoptOpenJDK/openjdk-jdk12u/blob/master/LICENSE
 Summary: AdoptOpenJDK provides prebuilt OpenJDK build binaries. This one uses Hotspot.
 Description: AdoptOpenJDK provides prebuilt OpenJDK build binaries. This one uses Hotspot.

tcpipmanager.portable 4.1.1 [Approved]
 Title: TCP/IP Manager (Portable) | Published: 10/08/2019
 Package approved by flcdrg on août 17 2019 02:17:36.
 Package testing status: Passing on août 10 2019 11:45:22.
 Number of Downloads: 71 | Downloads for this version: 71
 Package url
 Chocolatey Package Source: https://github.com/chtof/chocolatey-packages/tree/master/manual/tcpipmanager.portable
 Package Checksum: 'tHN/MaYV//0mvHy2gKSzK9T86imDmGA04BYbyKkHGoxp3dK++Qa3yGy+q60hIwaFEau/fn1JSwzUb/cMTtWAdw==' (SHA512)
 Tags: tcpipmanager.portable tcp ipnetwork configuration manager
 Software Site: https://tcpipmanager.sourceforge.io/
 Software License: https://www.gnu.org/licenses/gpl-3.0.txt
 Software Source: https://sourceforge.net/p/tcpipmanager/code/HEAD/tree
 Issues: https://sourceforge.net/p/tcpipmanager/bugs
 Summary: TCP/IP Manager is designed to help computer users keep track of their network configuration in different locations.
 Description: TCP/IP Manager is designed to help computer users keep track of their network configuration in different locations. At home or at work, changing network settings is now just one click away!

  ## Features
  - Save your network settings in an unlimited number of profiles
  - Support for switching TCP/IP settings (including multiple IP/Gateway/DNS servers)
  - Support for switching proxy settings, computer and workgroup names
  - Support for MAC spoofing
  - Easy switching between profiles (with tray icon and hotkeys)
  - Generate batch files from network profiles
  - Import current system settings
  - Very fast and easy to use interface
  - Run at Windows startup
  - WebUpdate (complete with news) and statistics modules
  - Installer and standalone (7z) versions for both 32-bit and 64-bit platforms

  ![screenshot](https://cdn.jsdelivr.net/gh/chtof/chocolatey-packages/manaual/tcpipmanager.portable/screenshot.png)
 Release Notes: https://sourceforge.net/p/tcpipmanager/news

tcpipmanager.install 4.1.1 [Approved]
 Title: TCP/IP Manager (Install) | Published: 10/08/2019
 Package approved by flcdrg on août 17 2019 02:17:53.
 Package testing status: Passing on août 10 2019 11:45:22.
 Number of Downloads: 151 | Downloads for this version: 151
 Package url
 Chocolatey Package Source: https://github.com/chtof/chocolatey-packages/tree/master/manual/tcpipmanager.install
 Package Checksum: 'VkvIxp4z3AsHnsc5ib0CR4fhkDGO8SuMzA6ccAMR8CmtaTn+7KgOpOQmNmqDdOkWKej1xY9Rxk7uEkLo8Fq5cg==' (SHA512)
 Tags: tcpipmanager.install tcp ipnetwork configuration manager
 Software Site: https://tcpipmanager.sourceforge.io/
 Software License: https://www.gnu.org/licenses/gpl-3.0.txt
 Software Source: https://sourceforge.net/p/tcpipmanager/code/HEAD/tree
 Issues: https://sourceforge.net/p/tcpipmanager/bugs
 Summary: TCP/IP Manager is designed to help computer users keep track of their network configuration in different locations.
 Description: TCP/IP Manager is designed to help computer users keep track of their network configuration in different locations. At home or at work, changing network settings is now just one click away!

  ## Features
  - Save your network settings in an unlimited number of profiles
  - Support for switching TCP/IP settings (including multiple IP/Gateway/DNS servers)
  - Support for switching proxy settings, computer and workgroup names
  - Support for MAC spoofing
  - Easy switching between profiles (with tray icon and hotkeys)
  - Generate batch files from network profiles
  - Import current system settings
  - Very fast and easy to use interface
  - Run at Windows startup
  - WebUpdate (complete with news) and statistics modules
  - Installer and standalone (7z) versions for both 32-bit and 64-bit platforms

  ![screenshot](https://cdn.jsdelivr.net/gh/chtof/chocolatey-packages/manual/tcpipmanager.install/screenshot.png)
 Release Notes: https://sourceforge.net/p/tcpipmanager/news

leagueoflegendseuw 1.0.0.0 [Approved] Downloads cached for licensed users - Possibly broken for FOSS users (due to original download location changes by vendor)
 Title: League Of Legends EUW | Published: 26/08/2019
 Package approved by gep13 on août 27 2019 06:42:53.
 Package testing status: Failing on août 26 2019 16:20:41.
 Number of Downloads: 314 | Downloads for this version: 314
 Package url
 Chocolatey Package Source: n/a
 Package Checksum: '6jkufpjoeTVbI1gdglTAGgmnS9vZY/VNAmetZra7EfkxTPuAsU9rQPbVYfEZlgsFPl0u/CY2RAaQA0TCeldRMA==' (SHA512)
 Tags: leagueoflegends euw leagueoflegendseuw lol league riot riotgames
 Software Site: https://signup.euw.leagueoflegends.com/en/signup/index
 Software License: https://euw.leagueoflegends.com/en/legal/termsofuse
 Documentation: https://euw.leagueoflegends.com/en/game-info/
 Issues: https://github.com/hurbeana/leagueoflegendseuw/issues
 Summary: EUW (Europe West) Installer for League of Legends from Riot Games.
 Description: League of Legends is a fast-paced, competitive online game that blends the speed and intensity of an RTS with RPG elements. Two teams of powerful champions, each with a unique design and playstyle, battle head-to-head across multiple battlefields and game modes. With an ever-expanding roster of champions, frequent updates and a thriving tournament scene, League of Legends offers endless replayability for players of every skill level. This installer is for the Europe West Region.

tcpipmanager 4.1.1 [Approved]
 Title: TCP/IP Manager | Published: 10/08/2019
 Package approved by flcdrg on août 17 2019 02:18:07.
 Package testing status: Passing on août 10 2019 11:45:21.
 Number of Downloads: 117 | Downloads for this version: 117
 Package url
 Chocolatey Package Source: https://github.com/chtof/chocolatey-packages/tree/master/manual/tcpipmanager
 Package Checksum: '/y4g1xeR+ZHwT6vugBu/MBpOXOHD3H+R2JHnXpn9ADSS0tIypN64ZfJy4YzXXcRx6E+fOzc8uAGTK6xPeO9k2A==' (SHA512)
 Tags: tcpipmanager tcp ipnetwork configuration manager
 Software Site: https://tcpipmanager.sourceforge.io/
 Software License: https://www.gnu.org/licenses/gpl-3.0.txt
 Software Source: https://sourceforge.net/p/tcpipmanager/code/HEAD/tree
 Issues: https://sourceforge.net/p/tcpipmanager/bugs
 Summary: TCP/IP Manager is designed to help computer users keep track of their network configuration in different locations.
 Description: TCP/IP Manager is designed to help computer users keep track of their network configuration in different locations. At home or at work, changing network settings is now just one click away!

  ## Features
  - Save your network settings in an unlimited number of profiles
  - Support for switching TCP/IP settings (including multiple IP/Gateway/DNS servers)
  - Support for switching proxy settings, computer and workgroup names
  - Support for MAC spoofing
  - Easy switching between profiles (with tray icon and hotkeys)
  - Generate batch files from network profiles
  - Import current system settings
  - Very fast and easy to use interface
  - Run at Windows startup
  - WebUpdate (complete with news) and statistics modules
  - Installer and standalone (7z) versions for both 32-bit and 64-bit platforms

  ![screenshot](https://cdn.jsdelivr.net/gh/chtof/chocolatey-packages/manual/tcpipmanager/screenshot.png)
 Release Notes: https://sourceforge.net/p/tcpipmanager/news

orangec 6.0.42.1 [Approved]
 Title: Orange C/C++ Compiler (Install) | Published: 20/08/2019
 Package approved by Pauby on août 21 2019 11:11:04.
 Package testing status: Passing on août 20 2019 22:54:48.
 Number of Downloads: 129 | Downloads for this version: 129
 Package url
 Chocolatey Package Source: https://github.com/bcurran3/ChocolateyPackages/tree/master/orangec
 Package Checksum: 'jJf3Cbo4ncUMSKJvrWzwyyRuonP9zYqoCRiJopxbROswbhhrcW0FNWL+j5CGiN7hPA2iPSxNjedSxsrn1ertFg==' (SHA512)
 Tags: orangec compiler c c++ foss cross-platform
 Software Site: http://ladsoft.tripod.com/orange_c_compiler.html
 Software License: https://github.com/LADSoft/OrangeC/tree/master/license
 Software Source: https://github.com/LADSoft/OrangeC/tree/master/src
 Documentation: https://orangec.readthedocs.io/en/latest/Tools/
 Issues: https://github.com/LADSoft/OrangeC/issues
 Summary: OrangeC Compiler And Tool Chain
 Description: ---

  ###[choco://orangec](choco://orangec)
  To use choco:// protocol URLs, install [(unofficial) choco:// Protocol  support](https://chocolatey.org/packages/choco-protocol-support)

  ---

  The Orange C/C++ Compiler is new work which includes an optimizing compiler, a tool chain, and an IDE.  The compiler itself uses various standard techniques, as well as some interesting techniques mentioned in literature.

  This compiler has support for the various C standards through C11, and full support for C++ 14.  The IDE for the compiler is a full featured C/C++ language IDE including a colorizing editor with code completion, integrated make facility, debugger, and a WIN32 resource editor.

  The tool chain is highly generic and the possibility exists to customize it for embedded platforms (or for that matter for example for other operating systems) using various linker customization files along with backend code generation programs.  The existing backend code generation programs support WIN32 and MSDOS executable formats, along with a backend generator that will output Intel and Motorola hex files.  The assembler uses a simple architecture description language to customize the code generation.  The C Run time library this compiler uses is an enhancement of the RTL used by CC386.  The Run time library in this package has WIN32 headers and an import library, many windows programs will compile with it although there are a few incompatibilities.

  Documentation for this compiler and toolchain may be found at http://orangec.readthedocs.io/en/latest/Tools/.
  Continuous integration for the project is being done at https://ci.appveyor.com/project/LADSoft/orangec and you may be able to find a working beta of the next version of the compiler there.
  An interesting variation on this compiler is the MSIL version which can generate either DLL or EXE files for .net.

  This compiler will run on WIN32 and also on DOS, and generate 32-bit programs for both.   However, unlike in CC386, the DOS version is the same build as the WIN32 version, and relies on Japheth's HXDOS extender to operate in DOS.  But it will still build traditional DPMI targets e.g. for DOS32A and other extenders; the only feature missing that the DOS version of CC386 had is support for far pointers.

  **[PACKAGE NOTES](https://github.com/bcurran3/ChocolateyPackages/blob/master/orangec/readme.md)**

  ---

  **Click here to [Patreon-ize](https://www.patreon.com/bcurran3) the package maintainer.**

  ---
 Release Notes: https://github.com/LADSoft/OrangeC/releases

jpdftweak 1.1 [Approved]
 Title: jPdf Tweak - Swiss Army Knife for PDF files | Published: 15/08/2019
 Package approved by Pauby on août 20 2019 18:16:54.
 Package testing status: Passing on août 15 2019 14:22:07.
 Number of Downloads: 107 | Downloads for this version: 107
 Package url
 Chocolatey Package Source: https://github.com/chtof/chocolatey-packages/tree/master/automatic/jpdftweak
 Package Checksum: 'Ay/KpriK6VWq8NGUhJSBn17e6IR/avHeKml4gG9WPVYQD6KXStp7NE7C04whaFpScqRrEuYNTmDMecDJJae9LQ==' (SHA512)
 Tags: jpdftweak tool PDF
 Software Site: http://jpdftweak.sourceforge.net/
 Software License: https://www.gnu.org/licenses/agpl-3.0.txt
 Software Source: https://sourceforge.net/p/jpdftweak/code/HEAD/tree
 Documentation: http://jpdftweak.sourceforge.net/manual/index.html
 Summary: jPDF Tweak is a Java Swing application that can combine, split, rotate, reorder, watermark, encrypt, sign, and otherwise tweak PDF files.
 Description: jPDF Tweak is a Java Swing application that can combine, split, rotate, reorder, watermark, encrypt, sign, and otherwise tweak PDF files.

  You can use it to make printable booklets from your PDFs, to add PDF bookmarks, effects (page transitions), to combine multiple PDF files, to watermark them, to rotate pages that do not fit, to attach files to your PDF, to encrypt and sign your PDFs, to change metadata (like author or keywords), and much more.

  You might want to have a look at the [manual](http://jpdftweak.sourceforge.net/manual/index.html).

  jPDF Tweak uses the excellent [iText](http://www.lowagie.com/iText) library for manipulating PDF files, and [JGoodies Forms](http://www.jgoodies.com/freeware/forms) for the GUI.

  ![screenshot](https://cdn.jsdelivr.net/gh/chtof/chocolatey-packages/automatic/jpdftweak/screenshot.png)

nip2 8.7.0 [Approved]
 Title: nip2 | Published: 11/08/2019
 Package approved by flcdrg on août 17 2019 06:23:36.
 Package testing status: Passing on août 11 2019 11:08:01.
 Number of Downloads: 80 | Downloads for this version: 80
 Package url
 Chocolatey Package Source: https://github.com/chtof/chocolatey-packages/tree/master/automatic/nip2
 Package Checksum: '7768kOlZhD8l8AhUbPFG9jzcNj4nZ3pIbUe+ayYHkN4QzaROe61U2E1/g9iYRsjUyddT7gs/NcL8wTXqaaAsLg==' (SHA512)
 Tags: nip2 gui user interface vips image processing library
 Software Site: https://github.com/libvips/nip2
 Software License: https://raw.githubusercontent.com/libvips/nip2/master/COPYING
 Software Source: https://github.com/libvips/nip2
 Issues: https://github.com/libvips/nip2/issues
 Summary: A user interface for the VIPS image processing library.
 Description: nip2 is a GUI for the [VIPS image processing library](https://libvips.github.io/libvips). It's a little like a spreadsheet: you create a set of formula connecting your objects together, and on a change nip2 recalculates.

  ![screenshot](https://cdn.jsdelivr.net/gh/chtof/chocolatey-packages/automatic/nip2/screenshot.png)
 Release Notes: https://github.com/libvips/nip2/releases

paraview 5.6.1 [Approved] Downloads cached for licensed users
 Title: paraview (Install) | Published: 16/08/2019
 Package approved by gep13 on août 27 2019 06:53:32.
 Package testing status: Passing on août 16 2019 03:09:35.
 Number of Downloads: 546 | Downloads for this version: 546
 Package url
 Chocolatey Package Source: n/a
 Package Checksum: 'eiD2SoKATm5kIBOJCrhRtABIy7Y/UamUpo6gL38I2x8PNrdLwgbTb4APkh0j+Yz3LZ099nAeWne8x1YxTYTRjQ==' (SHA512)
 Tags: Kitware paraview postviewer opencae
 Software Site: https://www.kitware.com/platforms/#paraview
 Software License: n/a
 Summary: OpenSource post viewer for CAE
 Description: OpenSource post viewer for CAE

  paraview description. https://www.paraview.org/

  ## Paramaters

  `cinst -y praview -s`

prometheus-sql-exporter 0.5 [Approved] Downloads cached for licensed users
 Title: Prometheus Sql exporter | Published: 19/08/2019
 Package approved by gep13 on août 27 2019 07:15:30.
 Package testing status: Passing on août 19 2019 12:03:16.
 Number of Downloads: 120 | Downloads for this version: 120
 Package url
 Chocolatey Package Source: https://github.com/espressolab/chocolatey-packages/tree/master/automatic/prometheus-sql-exporter
 Package Checksum: '3AwILyYmPAY7EwEE1vcmlfwtaalbCBO3zo6nA8LQZLQFWIuvzRmdHulTofy53CnkR2YHLNf2Xbas5lmC8xD+Ag==' (SHA512)
 Tags: prometheus-sql-exporter prometheus sql monitoring
 Software Site: https://github.com/free/sql_exporter
 Software License: https://github.com/free/sql_exporter/blob/master/LICENSE
 Documentation: https://github.com/free/sql_exporter/blob/master/README.md
 Issues: https://github.com/free/sql_exporter/issues
 Summary: Database agnostic SQL exporter for Prometheus.
 Description: SQL Exporter is a configuration driven exporter that exposes metrics gathered from DBMSs, for use by the Prometheus monitoring system.
  The collected metrics and the queries that produce them are entirely configuration defined.
 Release Notes: https://github.com/free/sql_exporter/releases

sdcard-formatter 5.0.1 [Approved] Downloads cached for licensed users
 Title: sdcard-formatter (Install) | Published: 17/08/2019
 Package approved by gep13 on août 27 2019 07:04:46.
 Package testing status: Passing on août 17 2019 14:58:16.
 Number of Downloads: 229 | Downloads for this version: 229
 Package url
 Chocolatey Package Source: n/a
 Package Checksum: 'Yxn3YkbMhGUw/YGJJojezBdIgdyfLWdxJ964m8JJrQ+spjhLubu+NjACzbj9wnQtmEQlztlqryyEpHsgY2LWkw==' (SHA512)
 Tags: sdcard-formatter formatter sdcard
 Software Site: https://www.sdcard.org/downloads/formatter/
 Software License: n/a
 Summary: SDCard Formatter
 Description: The SD Memory Card Formatter formats SD Memory Card, SDHC Memory Card and SDXC Memory Card (respectively SD/SDHC/SDXC Cards) complying with the SD File System Specification created by the SD Association (SDA).

iecv 1.79 [Approved]
 Title: IECookiesView | Published: 17/08/2019
 Package approved by gep13 on août 26 2019 07:21:44.
 Package testing status: Passing on août 17 2019 16:03:30.
 Number of Downloads: 68 | Downloads for this version: 68
 Package url
 Chocolatey Package Source: https://github.com/chtof/chocolatey-packages/tree/master/manual/iecv
 Package Checksum: 'grC6VMyPPE2ka6JMwJIGd/sCU/YfWbg80aWvAFNWai116QAy87qPmr3nGxV7n61rVCb6iXNx5wrGuRZTZ4DCAg==' (SHA512)
 Tags: iecv IE cookie view display detail
 Software Site: https://www.nirsoft.net/utils/iecookies.html
 Software License: https://www.nirsoft.net/utils/iecookies.html
 Documentation: https://www.nirsoft.net/utils/internet_explorer_cookies_view.html
 Issues: https://www.nirsoft.net/contact-new.html
 Summary: IECookiesView is a small utility that displays the details of all cookies that Internet Explorer stores on your computer.
 Description: IECookiesView is a small utility that displays the details of all cookies that Internet Explorer stores on your computer.
  In addition, It allows you to do the following actions:
  - Sort the cookies list by any column you want, by clicking the column header. A second click sorts the column in descending order.
  - Find a cookie in the list by specifying the name of the Web site.
  - Select and delete the unwanted cookies.
  - Save the cookies to a readable text file.
  - Copy cookie information into the clipboard.
  - Automatically refresh the cookies list when a Web site sends you a cookie.
  - Display the cookies of other users and from other computers.
  - Open the IECookiesView utility directly from Internet Explorer toolbar.
  - Change the content of a cookie !
  - Export your cookies to Netscape/Mozilla cookies file.
  - Block specific Web sites from using cookies through the cookies blocking mechanism of Internet Explorer 6.0.

  ## Advantages of this utility
  - This utility is completely freeware ! You don't have to pay anything in order to continue using it.
  - The utility is a standalone executable. it doesn't require any additional DLLs, and installation is not required.
  - The executable (iecv.exe) is small and compact. Only 55KB !
  - If you have a network, you can watch the cookies of other computers, as long as you have a read permission on the cookies folder of other computers.
  - On Windows NT/2000/XP, You can watch the cookies of other users on the same computer, as long as you have the right access permissions on the cookies folders.

  ## Disclaimer
  The software is provided AS

  ![screenshot](https://cdn.jsdelivr.net/gh/chtof/chocolatey-packages/manual/iecv/screenshot.png)
 Release Notes: https://www.nirsoft.net/utils/internet_explorer_cookies_view.html

dotmemory-console 2019.2.1 [Approved]
 Title: JetBrains dotMemory Console Profiler | Published: 22/08/2019
 Package approved by gep13 on août 26 2019 06:15:38.
 Package testing status: Passing on août 22 2019 05:20:28.
 Number of Downloads: 78 | Downloads for this version: 78
 Package url
 Chocolatey Package Source: https://github.com/flcdrg/au-packages/tree/master/dotMemory-Console
 Package Checksum: 'YaLNwTXSOaWOtbpwE+cwcyYAxIaNyfx+XXDAZqinUTvFaDT7OEHK1YGDu+MDh6OiIsOCST6UX8J+G/wXJU+NxQ==' (SHA512)
 Tags: dotmemory jetbrains
 Software Site: https://www.jetbrains.com/dotmemory/unit/
 Software License: https://www.jetbrains.com/legal/agreements/user.html
 Documentation: https://www.jetbrains.com/help/dotmemory/Working_with_dotMemory_Command-Line_Profiler.html
 Mailing List: https://dotnettools-support.jetbrains.com/hc/en-us/community/topics/200379845-dotMemory
 Issues: https://youtrack.jetbrains.com/issues/DMRY
 Summary: profile .NET memory usage from the command line
 Description: dotMemory Command Line Tools is a free package that lets you profile .NET memory usage from the command line and is available under a separate license.

  The tool automates collecting memory snapshots, which helps integrate memory profiling into the Continuous Integration workflow.
 Release Notes: https://www.jetbrains.com/dotmemory/whatsnew/
```




