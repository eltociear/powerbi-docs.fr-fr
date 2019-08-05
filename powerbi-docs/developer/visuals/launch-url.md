---
title: URL de lancement
description: Les visuels Power BI peuvent ouvrir l’URL dans un nouvel onglet
author: Guy-Moses
ms.author: guymos
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 1a7002c3b45f341c0cbc0db683bc4f8a113e21f9
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424858"
---
# <a name="launch-url"></a>URL de lancement

L’URL de lancement permet d’ouvrir un nouvel onglet de navigateur (ou une fenêtre) en déléguant le travail réel à Power BI.

## <a name="sample"></a>Exemple

```typescript
   this.host.launchUrl('https://powerbi.microsoft.com');
```

## <a name="usage"></a>Utilisation

Utilisez l’appel d’API `host.launchUrl()`, en passant l’URL de destination en tant qu’argument de chaîne :

```typescript
this.host.launchUrl('http://some.link.net');
```

## <a name="restrictions"></a>Restrictions

* Utilisez uniquement des chemins d’accès absolus, pas des chemins d’accès relatifs. `http://some.link.net/subfolder/page.html` est parfait, `/page.html` ne sera pas ouvert.
* Actuellement, seuls les protocoles `http` et `https` sont pris en charge. Évitez `ftp`,`mailto` ainsi de suite.

## <a name="best-practices"></a>Meilleures pratiques

1. Dans la plupart des cas, il est préférable d’ouvrir un lien uniquement en réponse à une action explicite de l’utilisateur. Permettez à l’utilisateur de comprendre facilement que le fait de cliquer sur le lien ou le bouton entraîne l’ouverture d’un nouvel onglet. Le déclenchement d’un appel `launchUrl()` sans action d’un utilisateur ou comme effet secondaire d’une autre action peut être confus ou frustrant pour l’utilisateur.
2. Si le lien n’est pas crucial pour le bon fonctionnement du visuel, il est recommandé de fournir à l’auteur du rapport un moyen de désactiver et de masquer le lien. Cela s’avère particulièrement utile pour les cas spéciaux d’utilisation de Power BI, tels que l’incorporation d’un rapport dans une application tierce ou sa publication sur le Web.
3. Évitez de déclencher un appel `launchUrl()` à partir d’une boucle, la fonction `update` du visuel ou tout autre code récurrent fréquent.

## <a name="step-by-step-example"></a>Exemple de procédure pas à pas

### <a name="adding-a-link-launching-element"></a>Ajout d’un élément de lancement de lien

Les lignes suivantes ont été ajoutées à la fonction `constructor` du visuel :

```typescript
    this.helpLinkElement = this.createHelpLinkElement();
    options.element.appendChild(this.helpLinkElement);
```

Et, une fonction privée créant et attachant l’élément d’ancrage a été ajoutée :

```typescript
private createHelpLinkElement(): Element {
    let linkElement = document.createElement("a");
    linkElement.textContent = "?";
    linkElement.setAttribute("title", "Open documentation");
    linkElement.setAttribute("class", "helpLink");
    linkElement.addEventListener("click", () => {
        this.host.launchUrl("https://docs.microsoft.com/power-bi/developer/custom-visual-develop-tutorial");
    });
    return linkElement;
};
```

Enfin, une entrée dans le fichier visual.less définit le style de l’élément de lien :

```less
.helpLink {
    position: absolute;
    top: 0px;
    right: 12px;
    display: block;
    width: 20px;
    height: 20px;
    border: 2px solid #80B0E0;
    border-radius: 20px;
    color: #80B0E0;
    text-align: center;
    font-size: 16px;
    line-height: 20px;
    background-color: #FFFFFF;
    transition: all 900ms ease;

    &:hover {
        background-color: #DDEEFF;
        color: #5080B0;
        border-color: #5080B0;
        transition: all 250ms ease;
    }

    &.hidden {
        display: none;
    }
}
```

### <a name="adding-a-toggling-mechanism"></a>Ajout d’un mécanisme de basculement

Cela nécessite l’ajout d’un objet statique (voir [didacticiel sur les objets statiques](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties)), afin que l’auteur du rapport puisse modifier la visibilité de l’élément de lien (la valeur par défaut est définie sur Masqué).
Un objet statique booléen `showHelpLink` a été ajouté à l’entrée des objets `capabilities.json` :

```typescript
"objects": {
    "generalView": {
            "displayName": "General View",
            "properties":
                "showHelpLink": {
                    "displayName": "Show Help Button",
                    "type": {
                        "bool": true
                    }
                }
            }
        }
    }
```

![Basculement de l’URL de lancement](./media/launchurl-toggle.png)

Les lignes suivantes ont été ajoutées à la fonction `update` du visuel :

```typescript
if (settings.generalView.showHelpLink) {
    this.helpLinkElement.classList.remove("hidden");
} else {
    this.helpLinkElement.classList.add("hidden");
}
```

La classe `hidden` est définie dans visual.less pour contrôler l’affichage de l’élément.
