## <a name="general"></a>Général
**Question :** Quel est le nom de ce service Windows ?  
**Réponse :** Il s’agit du service de passerelle de données locale qui est disponible dans Services.

**Question :** Quelle est la configuration requise pour utiliser la passerelle ?  
**Réponse :** Consultez la section relative à la configuration requise dans l’[article général sur la passerelle](../service-gateway-onprem.md).

**Question :** Quelles sont les sources de données prises en charge par la passerelle ?  
**Réponse :** Consultez le tableau des sources de données disponible dans l’[article général sur la passerelle](../service-gateway-onprem.md).

**Question :** Ai-je besoin d’une passerelle pour les sources de données cloud telles qu’Azure SQL Database ?  
**Réponse :** Non. Ce service est en mesure de se connecter à la source de données sans passerelle.

**Question :** Existe-t-il une connexion entrante vers la passerelle à partir du cloud ?  
**Réponse :** non. La passerelle crée des connexions sortantes vers Azure Service Bus.

**Question :** Que se passe-t-il si je bloque les connexions sortantes ? Que dois-je ouvrir ?  
**Réponse :** Consultez la [liste des ports](../service-gateway-onprem.md#ports) et des hôtes utilisés par la passerelle.

**Question :** Dois-je installer la passerelle sur le même ordinateur que la source de données ?  
**Réponse :** non. La passerelle se connecte à la source de données en utilisant les informations de connexion fournies. En ce sens, considérez la passerelle comme une application cliente. Elle doit simplement être en mesure de se connecter au serveur portant le nom fourni.

**Question :** Quelle est la latence d’exécution des requêtes d’une source de données vers la passerelle ? Quelle est la meilleure architecture ?  
**Réponse :** Pour éviter la latence du réseau, nous vous recommandons de placer la passerelle le plus proche possible de la source de données. Si vous pouvez installer la passerelle sur la source de données réelle, cela réduira la latence. Vous pouvez aussi utiliser des centres de données. Par exemple, si votre service utilise un centre de données situé dans États-Unis de l'Ouest et que vous disposez de SQL Server hébergé sur une machine virtuelle Azure, nous vous conseillons de placer également cette machine virtuelle Azure dans États-Unis de l'Ouest. Vous pouvez ainsi réduire la latence et éviter les frais d’acheminement des données sur la machine virtuelle Azure.

**Question :** Existe-t-il une configuration requise pour la bande passante réseau ?  
**Réponse :** Il est recommandé d’avoir un débit relativement élevé pour votre connexion réseau. Chaque environnement est différent. La configuration dépend de la quantité de données envoyées. L’utilisation d’ExpressRoute peut contribuer à garantir un niveau de débit entre les centres de données Azure et locaux.

Vous pouvez utiliser l’[application tierce Azure Speed Test](http://azurespeedtest.azurewebsites.net/) pour évaluer votre débit.

**Question :** Le portail du service Windows peut-il fonctionner avec un compte Azure Active Directory ?  
**Réponse :** non. Le service Windows doit posséder un compte Windows valide. Il fonctionne par défaut avec le SID du service, *NT SERVICE\PBIEgwService*.

**Question :** Comment les résultats sont-ils renvoyés vers le cloud ?  
**Réponse :** Cette opération est effectuée via Azure Service Bus. Pour en savoir plus, observez [son fonctionnement](../service-gateway-onprem.md#how-the-gateway-works).

**Question :** Où sont stockées mes informations d’identification ?  
**Réponse :** Les informations d’identification que vous entrez pour une source de données sont stockées dans le service cloud de la passerelle. Les informations d’identification sont déchiffrées au niveau de la passerelle locale.

**Question :** Puis-je placer la passerelle dans un réseau de périmètre (également appelé DMZ ou sous-réseau filtré) ?  
**Réponse :** La passerelle nécessite une connexion à la source de données. Si la source de données n’est pas située dans votre réseau de périmètre, il se peut que la passerelle ne puisse pas s’y connecter. Par exemple, votre serveur SQL Server peut ne pas être situé dans votre réseau de périmètre. Vous ne pouvez pas vous connecter à SQL Server à partir du réseau de périmètre. Si vous avez placé la passerelle dans votre réseau de périmètre, elle n’est pas en mesure d’atteindre le serveur SQL Server.

**Question :** Est-il possible de forcer la passerelle à utiliser le trafic HTTPS avec Azure Service Bus au lieu de TCP ?  
**Réponse :** Oui. Toutefois, cela réduit considérablement les performances. Vous souhaitez modifier le fichier *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*. Vous souhaitez modifier la valeur de `AutoDetect` à `Https`. Ce fichier se trouve, par défaut, dans *C:\Program Files\On-premises data gateway*.

**Question :** Dois-je autoriser la liste d’adresses IP des centres de données Azure ? Où puis-je obtenir la liste ?  
**Réponse :** si vous bloquez le trafic IP sortant, vous devrez peut-être autoriser la liste d’adresses IP des centres de données Azure. Actuellement, la passerelle communique avec Azure Service Bus à l’aide de l’adresse IP et du nom de domaine complet. La liste d’adresses IP des centres de données Azure est mise à jour chaque semaine. Vous pouvez télécharger la [liste des adresses IP de centre de données Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653).

```
<setting name="ServiceBusSystemConnectivityModeString" serializeAs="String">
    <value>Https</value>
</setting>
```

## <a name="high-availabilitydisaster-recovery"></a>Haute disponibilité/reprise d’activité
**Question :** Existe-t-il des plans pour activer les scénarios de haute disponibilité avec la passerelle ?  
**Réponse :** Oui, il s’agit d’un domaine sur lequel l’équipe Power BI travaille activement. Pour les autres mises à jour de cette fonctionnalité, consultez le [blog Power BI](https://powerbi.microsoft.com/blog/).

**Question :** Quelles options sont disponibles pour la reprise d’activité ?  
**Réponse :** Vous pouvez utiliser la clé de récupération pour restaurer ou déplacer une passerelle. Lorsque vous installez la passerelle, indiquez la clé de récupération.

**Question :** Quel est l’avantage de la clé de récupération ?  
**Réponse :** Elle permet de migrer ou de récupérer vos paramètres de passerelle. Elle est également utilisée pour la reprise d’activité.

## <a name="troubleshooting"></a>Résolution des problèmes
**Question :** Où sont situés les journaux de la passerelle ?  
**Réponse :** Consultez la section Outils de l’article [Résolution des problèmes](../service-gateway-onprem-tshoot.md#tools-for-troubleshooting).

**Question :** Comment puis-je savoir quelles requêtes sont envoyées vers la source de données locale ?  
**Réponse :** Vous pouvez activer le suivi des requêtes.  Cette fonctionnalité s’applique aux requêtes envoyées. N’oubliez pas de rétablir ses paramètres d’origine une fois le problème résolu. L’activation du suivi des requêtes augmente la taille des journaux.

Vous pouvez également examiner les outils de votre source de données pour le suivi des requêtes. Par exemple, pour SQL Server et Analysis Services, vous pouvez utiliser l’outil Événements étendus ou Générateur de profils SQL Server.

