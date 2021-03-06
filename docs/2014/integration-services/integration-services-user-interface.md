---
title: Interface utilisateur d’Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services, SSIS Designer
- tools [Integration Services], SSIS Designer
- SSIS Designer
- SSIS, SSIS Designer
- Integration Services, SSIS Designer
ms.assetid: d2c48cff-46f4-4c70-b1f3-c88f9b8757f3
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 55b09057927fa9c5102b8d816c42e1741bc0883a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "62767671"
---
# <a name="integration-services-user-interface"></a>Interface utilisateur d'Integration Services
  En plus des surfaces de dessin disponibles sous les onglets du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , l'interface utilisateur donne accès aux fenêtres et boîtes de dialogue suivantes permettant d'ajouter des fonctionnalités aux packages et de configurer les propriétés d'objets de packages.  
  
-   Les boîtes de dialogue et fenêtres que vous utilisez pour ajouter des fonctionnalités telles que la journalisation et les configurations de packages.  
  
-   Les éditeurs personnalisés pour la configuration des propriétés des objets de packages. Presque chaque type de conteneur, tâche et composant de flux de données possède son propre éditeur personnalisé.  
  
-   La boîte de dialogue **Éditeur avancé** , un éditeur générique qui propose des options de configuration plus détaillées pour de nombreux composants de flux de données.  
  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] fournit également des fenêtres et des boîtes de dialogue pour la configuration de l'environnement et l'utilisation des packages.  
  
## <a name="dialog-boxes-and-windows"></a>Boîtes de dialogue et fenêtres  
 Après l'ouverture ou la création d'un package dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , les boîtes de dialogue et fenêtres suivantes sont disponibles.  
  
 Ce tableau répertorie les boîtes de dialogue disponibles à partir du menu **SSIS** et des surfaces de dessin du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
|Boîte de dialogue|Objectif|Accès|  
|----------------|-------------|------------|  
|**Prise en main**|Accédez aux exemples, didacticiels et vidéos.|Sur l’aire de conception de l’onglet **Flux de contrôle** ou de l’onglet **Flux de données** , cliquez avec le bouton droit, puis cliquez sur **Prise en main**.<br /><br /> Pour afficher automatiquement la fenêtre **Mise en route** lorsque vous créez un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , sélectionnez **Afficher toujours dans un nouveau projet** en bas de la fenêtre.|  
|**Configurer les journaux SSIS**|Configuration de la journalisation pour un package et ses tâches en ajoutant des journaux et en définissant des détails de journalisation.|Dans le menu **SSIS** , cliquez sur **Enregistrement**.<br /><br /> -ou-<br /><br /> Cliquez n’importe où sur l’aire de conception de l’onglet **Flux de contrôle** , puis cliquez sur **Journalisation**.|  
|**Bibliothèque des configurations du package**|Ajout et modification de configurations de package. L'exécution de l'Assistant Configuration de package s'effectue à partir de cette boîte de dialogue.|Dans le menu **SSIS** , cliquez sur **Configurations du package**.<br /><br /> -ou-<br /><br /> Cliquez n’importe où sur l’aire de conception de l’onglet **Flux de contrôle** , puis cliquez sur **Configurations du package**.|  
|**Signature numérique**|Signature d'un package ou suppression de la signature d'un package.|Dans le menu **SSIS** , cliquez sur **Signature numérique**.<br /><br /> -ou-<br /><br /> Cliquez n’importe où sur l’aire de conception de l’onglet **Flux de contrôle** , puis cliquez sur **Signature numérique**.|  
|**Définir des points d’arrêt**|Activation des points d'arrêt sur des tâches et définition des propriétés des points d'arrêt.|Sur l’aire de conception de l’onglet **Flux de contrôle** , cliquez avec le bouton droit sur une tâche ou un conteneur, puis cliquez sur **Modifier les points d’arrêt**. Pour définir un point d’arrêt sur le package, cliquez n’importe où sur l’aire de conception de l’onglet **Flux de contrôle** , puis cliquez sur **Modifier les points d’arrêt**.|  
  
 La fenêtre **Mise en route** fournit des liens vers des exemples, des didacticiels et des vidéos. Pour ajouter des liens à des contenus supplémentaires, modifiez le fichier SamplesSites.xml inclus avec la version actuelle de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Nous vous recommandons de ne pas modifier la valeur de l’élément \<GettingStartedSamples> qui spécifie l’URL du flux RSS. Le fichier se trouve dans le dossier *\<lecteur>* :\Program Files\Microsoft SQL Server\110\DTS\Binn. Sur un ordinateur 64 bits, le fichier se trouve dans le dossier *\<lecteur>* :\Program Files(x86)\Microsoft SQL Server\110\DTS\Binn  
  
 Si le fichier SamplesSites.xml est endommagé, remplacez le xml dans le fichier par le xml par défaut suivant.  
  
 `<?xml version="1.0" ?>`  
  
 `- <SamplesSites>`  
  
 `<GettingStartedSamples>https://go.microsoft.com/fwlink/?LinkID=203147</GettingStartedSamples>`  
  
 `- <ToolboxSamples>`  
  
 `<Site>https://go.microsoft.com/fwlink/?LinkID=203286&query=SSIS%20{0}</Site>`  
  
 `</ToolboxSamples>`  
  
 `</SamplesSites>`  
  
 Ce tableau répertorie les fenêtres disponibles à partir des menus **SSIS** et **Affichage** et des surfaces de dessin du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
|Fenêtre|Objectif|Accès|  
|------------|-------------|------------|  
|**Variables**|Ajout et gestion de variables personnalisées.|Dans le menu **SSIS** , cliquez sur **Variables**.<br /><br /> -ou-<br /><br /> Cliquez n’importe où sur l’aire de conception des onglets **Flux de contrôle** et **Flux de données** , puis cliquez sur **Variables**.<br /><br /> -ou-<br /><br /> Dans le menu **Affichage** , pointez sur **Autres fenêtres**, puis cliquez sur **Variables**.|  
|**Journaux d'événements**|Affichage des entrées de journaux au moment de l'exécution.|Dans le menu **SSIS** , cliquez sur **Journaux d'événements**.<br /><br /> -ou-<br /><br /> Cliquez n’importe où sur l’aire de conception des onglets **Flux de contrôle** et **Flux de données** , puis cliquez sur **Journaux d’événements**.<br /><br /> -ou-<br /><br /> Dans le menu **Affichage** , pointez sur **Autres fenêtres**, puis cliquez sur **Journaux d'événements**.|  
  
## <a name="custom-editors"></a>Éditeurs personnalisés  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] fournit une boîte de dialogue personnalisée pour la plupart des conteneurs, tâches, sources, transformations et destinations.  
  
 Le tableau suivant décrit comment accéder aux boîtes de dialogue personnalisées.  
  
|Type d'éditeur|Accès|  
|-----------------|------------|  
|Conteneur. Pour plus d’informations, consultez [Conteneurs Integration Services](control-flow/integration-services-containers.md).|Sur l’aire de conception de l’onglet **Flux de contrôle** , double-cliquez sur le conteneur.|  
|Tâche. Pour plus d’informations, consultez [Tâches Integration Services](control-flow/integration-services-tasks.md).|Sur l’aire de conception de l’onglet **Flux de contrôle** , double-cliquez sur la tâche.|  
|Source.|Sur l’aire de conception de l’onglet **Flux de données** , double-cliquez sur la source.|  
|Transformation. Pour plus d’informations, consultez [Transformations Integration Services](data-flow/transformations/integration-services-transformations.md).|Sur l’aire de conception de l’onglet **Flux de données** , double-cliquez sur la transformation.|  
|Destination.|Sur l’aire de conception de l’onglet **Flux de données** , double-cliquez sur la destination.|  
  
## <a name="advanced-editor"></a>Éditeur avancé  
 La boîte de dialogue **Éditeur avancé** est une interface utilisateur permettant de configurer des composants de flux de données. Elle présente les propriétés du composant selon une disposition générique. La boîte de dialogue **Éditeur avancé** n'est pas accessible aux transformations [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] qui possèdent plusieurs entrées.  
  
 Pour ouvrir cet éditeur, cliquez sur **Afficher l’éditeur avancé** dans la fenêtre **Propriétés** ou cliquez avec le bouton droit sur un composant de flux de données, puis cliquez sur **Afficher l’éditeur avancé**.  
  
 Si vous créez une source, une transformation ou une destination personnalisée mais vous ne souhaitez pas écrire d'interface utilisateur personnalisée, vous pouvez utiliser l' **Éditeur avancé** .  
  
## <a name="sql-server-data-tools-features"></a>Fonctionnalités des outils de données SQL Server  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] propose des fenêtres, des boîtes de dialogue et des options de menu pour l'utilisation des packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 Voici un récapitulatif des fenêtres et menus disponibles :  
  
-   La fenêtre **Explorateur de solutions** répertorie les projets (y compris le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dans lequel vous développez des packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ) et les fichiers de projets.  
  
     Pour trier par nom les packages contenus dans un projet, cliquez avec le bouton droit sur le nœud **Packages SSIS** , puis cliquez sur **Trier par nom**.  
  
-   La fenêtre **Boîte à outils** répertorie les éléments de création de flux de contrôle et de flux de données.  
  
-   La fenêtre **Propriétés** répertorie les propriétés d'objets.  
  
-   Le menu **Format** fournit des options de dimensionnement et d'alignement de contrôles dans un package.  
  
-   Le menu **Edition** fournit une fonctionnalité de copier-coller pour la copie d'objets sur les surfaces de dessin.  
  
-   Le menu **Affichage** fournit des options de modification de la représentation graphique des objets dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 Pour plus d'informations sur les fenêtres et menus supplémentaires, consultez la documentation de Visual Studio.  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d’informations sur la création de packages dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], consultez [Créer des packages dans les outils de données SQL Server](create-packages-in-sql-server-data-tools.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteur SSIS](ssis-designer.md)  
  
  
