---
title: 'Étape 2 : Ajout et configuration de la journalisation | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 56105f3f-e500-4669-8c8e-acf434527727
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ef4f5d42ae3451d4199e84480a5672e437d7ca5f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62892435"
---
# <a name="step-2-adding-and-configuring-logging"></a>Étape 2 : Activation et configuration du mode d’écriture dans un journal
  Dans cette tâche, vous allez activer la journalisation pour le flux de données dans le package Lesson 3.dtsx. Vous allez ensuite configurer un module fournisseur d'informations pour les fichiers texte, pour enregistrer les événements PipelineExecutionPlan et PipelineExecuteTrees. Le module fournisseur d'informations pour les fichiers texte crée des journaux faciles à créer et à déplacer. La simplicité de ces fichiers journaux les rend particulièrement utiles pendant la phase de test de base d'un package. Vous pouvez également consulter les entrées du journal dans la fenêtre Journaux d'événements du Concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
### <a name="to-add-logging-to-the-package"></a>Pour activer le mode d'écriture dans un journal pour le package  
  
1.  Dans le menu **SSIS** , cliquez sur **Enregistrement**.  
  
2.  Dans le volet **Conteneurs** de la boîte de dialogue **Configurer les journaux SSIS** , vérifiez si l’objet situé au niveau le plus élevé, et qui représente le package Lesson 3, est sélectionné.  
  
3.  Sous l’onglet **Fournisseurs et journaux** , dans la zone **Type de fournisseur** , sélectionnez **Module fournisseur d’informations SSIS pour les fichiers texte**, puis cliquez sur **Ajouter**.  
  
     Integration Services ajoute un nouveau module fournisseur d’informations pour les fichiers texte au package avec le nom par défaut : **Module fournisseur d’informations SSIS pour les fichiers texte**. Vous pouvez maintenant configurer le nouveau module fournisseur d'informations.  
  
4.  Dans la colonne **nom** , tapez `Lesson 3 Log File`.  
  
5.  Modifiez éventuellement les informations figurant dans **Description**.  
  
6.  Dans la colonne **configuration** , cliquez sur ** \<nouvelle connexion>** pour spécifier la destination dans laquelle les informations du journal sont écrites.  
  
     Dans la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers** , pour **Type d’utilisation**, sélectionnez **Créer un fichier**, puis cliquez sur **Parcourir**. Par défaut, la boîte de dialogue **Sélectionner un fichier** qui s’affiche présente le dossier du projet, mais il est possible d’enregistrer les informations de journal n’importe où ailleurs.  
  
7.  Dans la boîte de dialogue **Sélectionner le fichier** , dans la zone nom `TutorialLog.log`de **fichier** , tapez, puis cliquez sur **ouvrir**.  
  
8.  Cliquez sur **OK** pour fermer la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers** .  
  
9. Dans le volet **Conteneurs** , développez tous les nœuds de la hiérarchie des conteneurs du package, puis décochez toutes les cases, notamment la case **Extract Sample Currency Data** . Maintenant, cochez la case **Extract Sample Currency Data** pour extraire uniquement les événements de ce nœud.  
  
    > [!IMPORTANT]  
    >  Si la case à cocher **Extract Sample Currency Data** n’apparaît pas sélectionnée mais grisée, la tâche utilise les paramètres du journal du conteneur parent et vous ne pouvez pas activer les journaux d’événements propres à cette tâche.  
  
10. Dans le volet **Détails** , dans la colonne **Événements** , sélectionnez les événements **PipelineExecutionPlan** et **PipelineExecutionTrees** .  
  
11. Cliquez sur **Avancés** pour vérifier les informations détaillées que le module de fournisseur d’informations enregistrera dans le journal pour chaque événement. Par défaut, toutes les catégories d'informations sont automatiquement sélectionnées pour les événements que vous avez spécifiés.  
  
12. Cliquez sur **De base** pour masquer les catégories d’informations.  
  
13. Sous l’onglet **fournisseur et journaux** , dans la colonne **nom** , sélectionnez `Lesson 3 Log File`. Une fois que vous avez créé un module fournisseur d'informations pour votre package, vous pouvez éventuellement le désélectionner temporairement pour désactiver la journalisation, sans avoir à supprimer puis à recréer un module fournisseur d'informations.  
  
14. Cliquez sur **OK**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Étape 3 : Test du package du tutoriel de la leçon 3](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
  
