## <a name="firewall-or-proxy"></a>Pare-feu ou proxy
Pour plus d’informations sur la fourniture d’informations de proxy pour votre passerelle, consultez [Configuration des paramètres de proxy pour les passerelles Power BI](../service-gateway-proxy.md).

Vous pouvez effectuer un test pour voir si votre pare-feu ou proxy bloque les connexions en exécutant [Test-NetConnection](https://docs.microsoft.com/powershell/module/nettcpip/test-netconnection) à partir d’une invite PowerShell. Cette opération teste la connectivité à Azure Service Bus. Ce test s’applique uniquement à la connectivité réseau et ne concerne pas le service du serveur cloud ni la passerelle. Il permet de déterminer si votre ordinateur peut réellement atteindre Internet.

    Test-NetConnection -ComputerName watchdog.servicebus.windows.net -Port 9350

> [!NOTE]
> La commande Test-NetConnection est uniquement disponible sur Windows Server 2012 R2 et versions ultérieures. Elle est également disponible sur Windows 8.1 et versions ultérieures. Dans les versions antérieures du système d’exploitation, vous pouvez utiliser Telnet pour tester la connectivité des ports.
> 
> 

Le résultat doit ressembler à ce qui suit. La différence sera avec TcpTestSucceeded. Si **TcpTestSucceeded** n’a pas la valeur *true*, vous pouvez être bloqué par un pare-feu.

    ComputerName           : watchdog.servicebus.windows.net
    RemoteAddress          : 70.37.104.240
    RemotePort             : 5672
    InterfaceAlias         : vEthernet (Broadcom NetXtreme Gigabit Ethernet - Virtual Switch)
    SourceAddress          : 10.120.60.105
    PingSucceeded          : False
    PingReplyDetails (RTT) : 0 ms
    TcpTestSucceeded       : True

Si vous voulez être exhaustif, remplacez les valeurs **ComputerName** et **Port** par celles répertoriées pour les [ports](../service-gateway-onprem.md#ports)

Le pare-feu peut également bloquer les connexions effectuées par Azure Service Bus vers les centres de données Azure. Si tel est le cas, nous vous conseillons d’ajouter à la liste verte (débloquer) les adresses IP de votre région pour ces centres de données. Vous pouvez obtenir une liste des adresses IP Azure [ici](https://www.microsoft.com/download/details.aspx?id=41653).

