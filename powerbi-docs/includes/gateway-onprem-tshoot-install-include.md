## <a name="update-to-the-latest-version"></a>Procéder à une mise à jour vers la dernière version
De nombreux problèmes peuvent faire surface quand la version de la passerelle est obsolète.  Nous vous recommandons de vérifier que vous possédez bien la dernière version.  Si vous n’avez pas mis à jour la passerelle depuis un mois ou plus, vous pouvez envisager d’installer la dernière version de la passerelle pour voir si vous pouvez reproduire le problème.

## <a name="common-issues"></a>Problèmes courants
Voici quelques problèmes courants et solutions qui ont aidé un certain nombre de clients dans les environnements qui limitent l’accès à Internet.

<iframe width="560" height="315" src="https://www.youtube.com/embed/-t7RO6mHATI?showinfo=0" frameborder="0" allowfullscreen></iframe>

### <a name="authentication-to-proxy-server"></a>Authentification auprès du serveur proxy
Votre proxy peut nécessiter l’authentification à partir d’un compte utilisateur de domaine. Par défaut, la passerelle utilise un SID de service pour l’utilisateur de connexion au service Windows. Remplacer l’utilisateur de connexion par un utilisateur de domaine peut vous y aider. Pour plus d’informations, voir [Remplacement du compte de service de passerelle par un utilisateur de domaine](../service-gateway-proxy.md#changing-the-gateway-service-account-to-a-domain-user).

### <a name="your-proxy-only-allows-ports-80-and-443-traffic"></a>Votre proxy autorise uniquement le trafic vers les ports 80 et 443.
Certains proxys limitent le trafic aux ports 80 et 443. Par défaut, la communication avec Azure Service Bus a lieu sur des ports différents du port 443.

Vous pouvez forcer la passerelle pour communiquer avec Azure Service Bus à l’aide de HTTPS au lieu de Direct TCP. Vous devez modifier le fichier *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*. Modifiez la valeur de `AutoDetect` à `Https`. Ce fichier se trouve, par défaut, dans *C:\Program Files\On-premises data gateway*.

```
<setting name="ServiceBusSystemConnectivityModeString" serializeAs="String">
    <value>Https</value>
</setting>
```

## <a name="installation"></a>Installation
### <a name="error-failed-to-add-user-to-group---2147463168---pbiegwservice---performance-log-users---"></a>Erreur : Impossible d’ajouter l’utilisateur au groupe.  (-2147463168   PBIEgwService   Utilisateurs du journal de performances   )
Vous pouvez recevoir cette erreur si vous essayez d’installer la passerelle sur un contrôleur de domaine. Le déploiement sur un contrôleur de domaine n’est pas pris en charge. Vous devez déployer la passerelle sur un ordinateur qui n’est pas un contrôleur de domaine.

### <a name="installation-fails"></a>Échec de l’installation
Vous pouvez rencontrer des échecs d’installation si le logiciel antivirus sur l’ordinateur d’installation est obsolète. Vous pouvez mettre à jour l’installation de l’antivirus, ou désactiver l’antivirus seulement pendant la durée de l’installation de la passerelle, puis réactiver l’antivirus.

