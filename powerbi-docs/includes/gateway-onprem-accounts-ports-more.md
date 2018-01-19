## <a name="sign-in-account"></a>Compte de connexion
Les utilisateurs doivent se connecter en utilisant un compte professionnel ou scolaire. Il s’agit du compte de votre organisation. Si vous avez souscrit une offre Office 365 et que vous n’avez pas fourni votre adresse de messagerie professionnelle, il peut ressembler à nancy@contoso.onmicrosoft.com. Votre compte, au sein d’un service cloud, est stocké dans un locataire, dans Azure Active Directory (AAD). Généralement, le nom d’utilisateur principal (ou UPN) de votre compte AAD correspond à votre adresse de messagerie.

## <a name="windows-service-account"></a>Compte de service Windows
La passerelle de données locale est configurée pour utiliser *NT SERVICE\PBIEgwService* pour les informations d’identification de connexion au service Windows. Par défaut, elle a le droit de se connecter en tant que service. Cela dépend de l’ordinateur sur lequel vous installez la passerelle.

> [!NOTE]
> Si vous avez sélectionné le mode Personal, vous devez configurer le compte de service Windows séparément.
> 
> 

Il ne s’agit pas du compte utilisé pour se connecter aux sources de données locales.  Il ne s’agit pas non plus du compte professionnel ou scolaire que vous utilisez pour vous connecter aux services cloud.

Si vous rencontrez des problèmes avec votre serveur proxy, en raison de l’authentification, vous pouvez remplacer le compte de service Windows par un compte d’utilisateur de domaine ou de service administré. Vous pouvez apprendre à changer de compte dans la [configuration du proxy](../service-gateway-proxy.md#changing-the-gateway-service-account-to-a-domain-user).

## <a name="ports"></a>Ports
La passerelle crée une connexion sortante vers Azure Service Bus. Elle communique sur des ports de sortie : TCP 443 (valeur par défaut), 5671, 5672, 9350 à 9354.  La passerelle ne nécessite pas de ports d’entrée. [En savoir plus](https://azure.microsoft.com/documentation/articles/service-bus-fundamentals-hybrid-solutions/)

Nous vous recommandons d’ajouter les adresses IP de votre région de données à la liste verte dans votre pare-feu. Vous pouvez télécharger la [liste des adresses IP de centre de données Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653). Cette liste est mise à jour chaque semaine. La passerelle communique avec Azure Service Bus à l’aide de l’adresse IP et du nom de domaine complet. Si vous forcez la passerelle à communiquer à l’aide de HTTPS, elle utilise uniquement un nom de domaine complet et aucune communication n’est établie au moyen des adresses IP.

> [!NOTE]
> Les adresses IP répertoriées dans la liste d’adresses IP du centre de données Azure sont en notation CIDR. Par exemple, 10.0.0.0/24 ne signifie pas de 10.0.0.0 à 10.0.0.24. En savoir plus sur la notation [CIDR](http://whatismyipaddress.com/cidr).
> 
> 

Voici la liste des noms de domaine complets utilisés par la passerelle.

| Noms de domaine | Ports de sortie | Description |
| --- | --- | --- |
| *.download.microsoft.com |80 |HTTP utilisé pour télécharger le programme d’installation. |
| *.powerbi.com |443 |HTTPS |
| *.analysis.windows.net |443 |HTTPS |
| *.login.windows.net |443 |HTTPS |
| *.servicebus.windows.net |5671-5672 |AMQP (Advanced Message Queuing Protocol) |
| *.servicebus.windows.net |443, 9350-9354 |Écouteurs sur Service Bus Relay via TCP (nécessite 443 pour l’acquisition de jeton de contrôle d’accès) |
| *.frontend.clouddatahub.net |443 |HTTPS |
| *.core.windows.net |443 |HTTPS |
| login.microsoftonline.com |443 |HTTPS |
| *.msftncsi.com |443 |Utilisé pour tester la connectivité Internet si la passerelle n’est pas accessible par le service Power BI. |
| *.microsoftonline-p.com |443 |Utilisé pour l’authentification en fonction de la configuration. |

> [!NOTE]
> Le trafic dirigé vers visualstudio.com ou visualstudioonline.com est réservé à Application Insights et n’est pas requis pour le fonctionnement de la passerelle.
> 
> 

## <a name="forcing-https-communication-with-azure-service-bus"></a>Forcer les communications HTTPS avec Azure Service Bus
Vous pouvez forcer la passerelle pour communiquer avec Azure Service Bus à l’aide de HTTPS au lieu de Direct TCP. Cela peut avoir un impact sur les performances. Pour ce faire, modifiez le fichier *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config* en modifiant la valeur de `AutoDetect` à `Https`, comme indiqué dans l’extrait de code qui suit directement ce paragraphe. Par défaut, ce fichier se trouve dans le dossier *C:\Program Files\Passerelle de données locale*.

```
<setting name="ServiceBusSystemConnectivityModeString" serializeAs="String">
    <value>Https</value>
</setting>
```

La valeur du paramètre *ServiceBusSystemConnectivityModeString* respecte la casse. Les valeurs valides sont *AutoDetect* et *Https*.

Depuis la version de [mars 2017](https://powerbi.microsoft.com/blog/power-bi-gateways-march-update/), vous pouvez également forcer la passerelle à adopter ce comportement à l’aide de l’interface utilisateur associée. Dans l’interface utilisateur de la passerelle, sélectionnez **Réseau**, puis définissez le paramètre **Mode de connectivité Azure Service Bus** sur **Activé**.

![](./media/gateway-onprem-accounts-ports-more/gw-onprem_01.png)

Une fois les modifications effectuées, lorsque vous sélectionnez **Appliquer** (un bouton qui n’apparaît que lorsque vous apportez une modification), le *service Windows de passerelle* redémarre automatiquement afin que la modification puisse prendre effet.

Pour référence future, vous pouvez redémarrer le *service Windows de passerelle* à partir de la boîte de dialogue d’interface utilisateur en sélectionnant **Paramètres de service**, puis *Redémarrer maintenant*.

![](./media/gateway-onprem-accounts-ports-more/gw-onprem_02.png)

## <a name="support-for-tls-1112"></a>Prise en charge de TLS 1.1/1.2
À partir de la mise à jour d’août 2017, la passerelle de données locale utilise, par défaut, le protocole TLS 1.1 ou 1.2 pour communiquer avec le **service Power BI**. Les versions précédentes de la passerelle de données locale utilisent le protocole TLS 1.0 par défaut. Le 15 mars 2018, le protocole TLS 1.0 ne sera plus pris en charge, en particulier la capacité de la passerelle à interagir avec le **service Power BI** avec TLS 1.0. Vous devez donc mettre à niveau vos installations de passerelle de données locale vers la version d’août 2017 ou une version ultérieure avant cette date, afin que vos passerelles continuent à fonctionner.

Il est important de noter que le protocole TLS 1.0 reste pris en charge par la passerelle de données locale jusqu’au 31 octobre, et est utilisé par celle-ci en tant que mécanisme de secours. Pour vous assurer que tout le trafic de passerelle utilise les protocoles TLS 1.1 ou 1.2 (et pour empêcher l’utilisation du protocole TLS 1.0 sur votre passerelle), vous devez ajouter ou modifier les clés de Registre suivantes sur l’ordinateur exécutant le service de passerelle :

        [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]"SchUseStrongCrypto"=dword:00000001
        [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319]"SchUseStrongCrypto"=dword:00000001

> [!NOTE]
> L’ajout ou la modification de ces clés de Registre s’appliquent à toutes les applications .NET. Pour plus d’informations sur les modifications du Registre qui affectent le protocole TLS pour d’autres applications, voir [Paramètres de Registre pour le protocole TLS](https://docs.microsoft.com/windows-server/security/tls/tls-registry-settings).
> 
> 

## <a name="how-to-restart-the-gateway"></a>Comment redémarrer la passerelle
La passerelle s’exécute en tant que service Windows. Vous pouvez la démarrer et l’arrêter comme n’importe quel service Windows. Il existe plusieurs manières de procéder. Voici comment faire à partir de l’invite de commandes.

1. Sur l’ordinateur sur lequel la passerelle est en cours d’exécution, lancez une invite de commandes d’administration.
2. Utilisez la commande suivante pour arrêter le service.
   
   net stop PBIEgwService
3. Utilisez la commande suivante pour démarrer le service.
   
   net start PBIEgwService

