---
title: Éditeur de transformation de recherche (page connexion) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.referencetable.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: e90d6b69-5a26-43c5-8433-5c3c9588e08c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7985f713093e839d258a0c9b80bb5d4e6e58f37f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66057953"
---
# <a name="lookup-transformation-editor-connection-page"></a>Éditeur de transformation de recherche (page Connexion)
  Utilisez la page **Connexion** de la boîte de dialogue **Éditeur de transformation de recherche** pour sélectionner un gestionnaire de connexions. Si vous sélectionnez un gestionnaire de connexions OLE DB, vous sélectionnez également une requête, une table ou une vue pour générer le dataset de référence.  
  
 Pour en savoir plus sur la transformation de recherche, consultez [Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Options  
 Les options suivantes sont disponibles quand vous sélectionnez **Cache complet** et **Gestionnaire de connexions du cache** dans la page Général de la boîte de dialogue **Éditeur de transformation de recherche** .  
  
 **Gestionnaire de connexions du cache**  
 Sélectionnez un gestionnaire de connexions du cache existant dans la liste ou créez une connexion en cliquant sur **Nouveau**.  
  
 **Nouvelle**  
 Créez une connexion à l’aide de la boîte de dialogue **Éditeur du gestionnaire de connexions du cache** .  
  
 Les options suivantes sont disponibles quand vous sélectionnez **Cache complet**, **Cache partiel**ou **Aucun cache**et **Gestionnaire de connexions OLE DB**dans la page Général de la boîte de dialogue **Éditeur de transformation de recherche** .  
  
 **Gestionnaire de connexions OLE DB**  
 Sélectionnez un gestionnaire de connexions OLE DB existant dans la liste ou créez une connexion en cliquant sur **Nouveau**.  
  
 **Nouvelle**  
 Crée une connexion en utilisant la boîte de dialogue **Configurer le gestionnaire de connexions OLE DB** .  
  
 **Utiliser une table ou une vue**  
 Sélectionnez une table ou une vue existante dans la liste, ou créez une nouvelle table en cliquant sur **nouveau**.  
  
> [!NOTE]  
>  Si vous spécifiez une instruction SQL dans la page **Avancé** de l’ **Éditeur de transformation de recherche**, cette instruction SQL substitue et remplace le nom de table a sélectionné ici. Pour plus d’informations, consultez [Éditeur de transformation de recherche &#40;page Avancé&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md).  
  
 **Nouvelle**  
 Utilisez la boîte de dialogue **Créer une table** pour créer une table.  
  
 **Utiliser les résultats d'une requête SQL**  
 Choisissez cette option pour rechercher une requête existante, générer une requête, vérifier la syntaxe d'une requête et afficher un aperçu des résultats d'une requête.  
  
 **Générer la requête**  
 Créez l’instruction Transact-SQL à exécuter à l’aide du **Générateur de requêtes**. Cet outil graphique permet de créer des requêtes en explorant les données.  
  
 **Parcourir**  
 Permet de rechercher une requête existante enregistrée dans un fichier.  
  
 **Analyser la requête**  
 Contrôle la syntaxe d'une requête.  
  
 **PRÉVERSION**  
 Affichez un aperçu des résultats à l’aide de la boîte de dialogue **Visualiser les résultats de la requête** . Cette option affiche jusqu'à 200 lignes.  
  
## <a name="external-resources"></a>Ressources externes  
 Entrée de blog, [Lookup cache modes](https://go.microsoft.com/fwlink/?LinkId=219518) sur blogs.msdn.com  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de transformation de recherche &#40;page général&#41;](general-page-of-integration-services-designers-options.md)   
 [Éditeur de transformation de recherche &#40;page colonnes&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md)   
 [Éditeur de transformation de recherche &#40;&#41;de page avancé](../../2014/integration-services/lookup-transformation-editor-advanced-page.md)   
 [Éditeur de transformation de recherche &#40;page sortie d’erreur&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)   
 [transformation de recherche floue](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
