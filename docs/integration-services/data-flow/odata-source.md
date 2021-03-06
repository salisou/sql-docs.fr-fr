---
title: Source OData | Microsoft Docs
ms.date: 09/17/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.custom: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.DTS.DESIGNER.ODATASOURCE.F1
- sql13.dts.designer.odatasource.connection.f1
- sql13.dts.designer.odatasource.columns.f1
- sql13.dts.designer.odatasource.erroroutput.f1
ms.assetid: cc9003c9-638e-432b-867e-e949d50cec90
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2177b4d1c4454aca803f11980340407362236c8c
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "75546535"
---
# <a name="odata-source"></a>Source OData

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


Utilisez le composant source OData dans un package SSIS pour consommer les données provenant d’un service OData (Open Data Protocol).

## <a name="supported-protocols-and-data-formats"></a>Protocoles et formats de données pris en charge

Le composant prend en charge les protocoles OData v3 et v4.  
  
-   Pour le protocole OData V3, le composant prend en charge les formats de données JSON et ATOM.  
  
-   Pour le protocole OData V4, le composant prend en charge le format de données JSON.  

## <a name="supported-data-sources"></a>Sources de données prises en charge

La source OData prend en charge les sources de données suivantes :
-   Microsoft Dynamics AX Online et Microsoft Dynamics CRM Online,
-   Listes SharePoint. Pour voir toutes les listes d’un serveur SharePoint, utilisez l’URL suivante : `https://<server>/_vti_bin/ListData.svc`. Pour plus d'informations sur les conventions d'URL SharePoint, consultez [Interface REST de SharePoint Foundation](https://msdn.microsoft.com/library/ff521587.aspx).

## <a name="supported-data-types"></a>Types de données pris en charge

La source OData prend en charge les types de données simples suivants : int, byte[], bool, byte, DateTime, DateTimeOffset, decimal, double, Guid, Int16, Int32, Int64, sbyte, float, string et TimeSpan.

Pour découvrir les types de données des colonnes dans votre source de données, consultez la page `https://<OData feed endpoint>/$metadata`.

Pour le type de données **Decimal**, la précision et l’échelle sont déterminées par les métadonnées sources. Si les métadonnées sources ne spécifient pas les propriétés **Précision** et **Échelle**, les données peuvent être tronquées.

> [!IMPORTANT]
> Le composant Source OData ne prend pas en charge les types complexes, comme les éléments à choix multiple, dans des listes SharePoint.

## <a name="odata-format-and-performance"></a>Format OData et performances
 La plupart des services OData retournent les résultats dans plusieurs formats. Vous pouvez spécifier le format du jeu de résultats à l’aide de l’option de requête `$format`. Les formats comme JSON et JSON Light sont plus efficaces qu’ATOM ou XML, et peuvent offrir un gain de performances en cas de transfert d’un grand volume de données. Le tableau suivant fournit les résultats des tests. Comme vous pouvez le voir, le passage d’ATOM à JSON s’est traduit par un gain de performances de 30 à 53 %, et le passage d’ATOM au nouveau format JSON Light (disponible dans WCF Data Services 5.1) a entraîné un gain de performances de 67 %.  
  
|Lignes|ATOM|JSON|JSON (Light)|  
|-|-|-|-|  
|10000|113 secondes|74 secondes|68 secondes|  
|1000000|1110 secondes|853 secondes|665 secondes|  
  
## <a name="related-topics-in-this-section"></a>Rubriques connexes de cette section  
  
-   [Tutoriel : Utiliser la source OData](../../integration-services/data-flow/tutorial-using-the-odata-source.md)  
  
-   [Modifier la requête de la source OData à l’exécution](../../integration-services/data-flow/modify-odata-source-query-at-runtime.md)  
  
-   [Propriétés de la source OData](../../integration-services/data-flow/odata-source-properties.md)  
  
## <a name="odata-source-editor-connection-page"></a>Éditeur de source OData (page Connexion)
  La page **Connexion** de la boîte de dialogue **Éditeur de source OData** vous permet de sélectionner le gestionnaire de connexions OData pour la source OData. Cette page vous permet également de spécifier une collection ou un chemin d'accès de ressources et toutes les options de requête permettant de spécifier quelles données doivent être récupérées à partir de la source OData. 
  
### <a name="static-options"></a>Options statiques  
 **Gestionnaire de connexions OData**  
 Sélectionnez un gestionnaire de connexions existant dans la liste ou créez une nouvelle connexion en cliquant sur **Nouveau**.  
  
 Après la sélection ou la création d’un gestionnaire de connexions, la boîte de dialogue affiche la version du protocole OData qui utilise le gestionnaire de connexions.  
  
 **Nouveau**  
 Créez un gestionnaire de connexions à l’aide de la boîte de dialogue **Éditeur du gestionnaire de connexions OData** .  
  
 **Utilisez une collection ou un chemin d'accès de ressource.**  
 Spécifiez la méthode de sélection des données dans la source.  
  
|Option|Description|  
|------------|-----------------|  
|Collection|Extrayez les données de la source OData à l'aide d'un nom de collection.|  
|Chemin d'accès de ressource|Extrayez les données de la source OData à l'aide d'un chemin d'accès de ressource.|  
  
 **Options de requête**  
 Permet d'indiquer les options de la requête. Par exemple : `$top=5` 
  
 **URL du flux**  
 Affiche l’URL du flux en lecture seule en fonction des options sélectionnées dans la boîte de dialogue.  
  
 **Préversion**  
 Affichez un aperçu des résultats à l’aide de la boîte de dialogue **Aperçu** . L’**Aperçu** peut afficher jusqu’à 20 lignes.  
  
### <a name="dynamic-options"></a>Options dynamiques  
  
#### <a name="use-collection-or-resource-path--collection"></a>Utilisez une collection ou un chemin d'accès de ressource = Collection.  
 **Collection**  
 Sélectionnez une collection dans la liste déroulante.  
  
#### <a name="use-collection-or-resource-path--resource-path"></a>Utilisez une collection ou un chemin d'accès de ressource = Resource Path.  
 **Resource path**  
 Type de chemin d'accès de ressource. Par exemple : Employees  
  
## <a name="odata-source-editor-columns-page"></a>Éditeur de source OData (page Colonnes)
  Utilisez la page **Colonnes** de la boîte de dialogue **Éditeur de source OData** pour sélectionner des colonnes externes (source) à inclure dans la sortie et pour les mapper aux colonnes de la sortie.  
  
### <a name="options"></a>Options  
 **Colonnes externes disponibles**  
 Affiche la liste des colonnes sources disponibles dans la source de données. Utilisez les cases à cocher dans la liste pour ajouter ou supprimer des colonnes sur la table au bas de la page. Les colonnes sélectionnées sont ajoutées à la sortie.  
  
 **Colonne externe**  
 Affichez les colonnes sources à inclure dans la sortie.  
  
 **Colonne de sortie**  
 Spécifiez un nom unique pour chaque colonne de sortie. Le nom par défaut est celui de la colonne externe (source) sélectionnée ; vous pouvez néanmoins choisir n'importe quel nom unique et significatif.  
  
## <a name="odata-source-editor-error-output-page"></a>Éditeur de source OData (page Sortie d'erreur)
  La page **Sortie d'erreur** de la boîte de dialogue **Éditeur de source OData** vous permet de sélectionner les options de gestion des erreurs et de définir les propriétés sur les colonnes de sortie d'erreur.  
  
### <a name="options"></a>Options  
 **Entrée/sortie**  
 Affichez le nom de la source de données.  
  
 **Colonne**  
 Indique les colonnes externes (source) que vous avez sélectionnées dans la page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de source OData** .  
  
 **Error**  
 Indiquez ce qui doit se produire lorsqu'une erreur se produit : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Rubriques connexes :** [Gestion des erreurs dans les données](../../integration-services/data-flow/error-handling-in-data.md)  
  
 **Troncation**  
 Indiquez ce qui doit se produire lorsqu'une troncation se produit : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Description**  
 Affiche la description de l'erreur.  
  
 **Définir cette valeur sur les cellules sélectionnées**  
 Indiquez ce qui doit se produire pour l'ensemble des cellules sélectionnées lorsqu'une erreur ou une troncation se produit : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Appliquer**  
 Appliquez l'option de gestion des erreurs aux cellules sélectionnées.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de connexions OData](../../integration-services/connection-manager/odata-connection-manager.md)  
  
  
