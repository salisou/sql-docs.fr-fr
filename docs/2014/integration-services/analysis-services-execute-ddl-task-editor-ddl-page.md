---
title: Éditeur de tâche DDL d’exécution de Analysis Services (page DDL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asexecuteddltask.ddl.f1
helpviewer_keywords:
- Analysis Services Execute DDL Task Editor
ms.assetid: f21bf8d0-ec5f-4c18-9de0-8875addb927b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2b57ad76be3811352bbfb8774fb56c748efa1ac8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66061605"
---
# <a name="analysis-services-execute-ddl-task-editor-ddl-page"></a>Éditeur de tâche DDL d'exécution d'Analysis Services (page DDL)
  Utilisez la page **DDL** de la boîte de dialogue **Éditeur de tâche DDL d’exécution d’Analysis Services** pour spécifier une connexion à un projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ou à une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et fournir des informations sur la source des instructions de langage de définition de données (DDL).  
  
 Pour en savoir plus sur cette tâche, consultez [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md).  
  
## <a name="static-options"></a>Options statiques  
 **Connection**  
 Sélectionnez un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] projet ou un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] gestionnaire de connexions dans la liste ou cliquez \<sur **nouvelle connexion...**> et utilisez la boîte de dialogue Ajouter un gestionnaire de **connexions Analysis Services** pour créer une nouvelle connexion.  
  
 **Rubriques connexes :** [Référence de l'interface utilisateur de la boîte de dialogue Ajout d’un gestionnaire de connexions Analysis Services](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md), [Gestionnaire de connexions Analysis Services](connection-manager/analysis-services-connection-manager.md)  
  
 **Telle**  
 Spécifiez le type de source des instructions DDL. Cette propriété dispose des options répertoriées dans le tableau suivant :  
  
|Value|Description|  
|-----------|-----------------|  
|**Entrée directe**|Définissez la source de l'instruction DDL enregistrée dans la zone de texte **SourceDirect** . Sélectionnez cette valeur pour afficher l'option dynamique de la section suivante.|  
|**Connexion de fichiers**|Définissez la source par un fichier qui contient l'instruction DDL. Sélectionnez cette valeur pour afficher l'option dynamique de la section suivante.|  
|**Variable**|Définissez la source par une variable. Sélectionnez cette valeur pour afficher l'option dynamique de la section suivante.|  
  
## <a name="dynamic-options"></a>Options dynamiques  
  
### <a name="sourcetype--direct-input"></a>SourceType = Entrée directe  
 **Source**  
 Tapez les instructions DDL ou cliquez sur les points de suspension **(...)** , puis tapez les instructions dans la boîte de dialogue **instructions DDL** .  
  
### <a name="sourcetype--file-connection"></a>SourceType = Connexion de fichiers  
 **Source**  
 Sélectionnez une connexion de fichiers dans la liste ou cliquez \<sur **nouvelle connexion...**> et utilisez la boîte de dialogue **Gestionnaire de connexions de fichiers** pour créer une nouvelle connexion.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md)  
  
### <a name="sourcetype--variable"></a>SourceType = Variable  
 **Source**  
 Sélectionnez une variable dans la liste ou cliquez sur \<**Nouvelle variable**> et utilisez la boîte de dialogue **Ajouter une variable** pour créer une variable.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services de référence des erreurs et des messages](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Analysis Services éditeur de tâche DDL d’exécution &#40;page général&#41;](general-page-of-integration-services-designers-options.md)   
 [Page expressions](expressions/expressions-page.md)   
 [Flux de contrôle](control-flow/control-flow.md)   
 [Analysis Services&#41; référence du langage de script &#40;ASSL](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)   
 [Référence XML for Analysis &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)  
  
  
