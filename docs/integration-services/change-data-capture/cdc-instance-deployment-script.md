---
title: Script de déploiement d’instance CDC | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8fa82822-ac99-48ef-a18d-f4f3a77105b4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 595af36a5eb19ff6fd019df8a2b9203537350c5a
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "71298910"
---
# <a name="cdc-instance-deployment-script"></a>Script de déploiement d'instance CDC

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Boîte de dialogue de script de déploiement d'instance de capture de données modifiées qui affiche le script de déploiement d'instance de capture de données modifiées. Ce script peut être utilisé pour recréer la base de données CDC avec tous ses artefacts sur une autre instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 À la fin du script de déploiement, vous devez vous assurer de ce qui suit :  
  
-   Le script de déploiement suppose que l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cible a été préparée pour la capture de données modifiées Oracle, à l'aide de la console de configuration du service de capture de données modifiées Oracle ou à l'aide du **script de préparation** créé par le programme.  
  
-   La partie du script utilisée pour activer la base de données pour la capture de données modifiées doit être exécutée par un `sysadmin`.  
  
-   Le script ne conserve pas le mot de passe d'exploration de données de journaux Oracle. Il doit être défini manuellement une fois le script exécuté et le service de capture de données modifiées Oracle démarré.  
  
 Sélectionnez les options suivantes dans la boîte de dialogue **Script de déploiement d'instance CDC** .  
  
 **Enregistrer sous**  
 Enregistre le script dans un fichier texte que vous pouvez enregistrer dans n'importe quel emplacement de votre choix. Vous pouvez copier le fichier script vers tout autre serveur en vue de l'exécuter.  
  
 **Copy**  
 Copie le script dans le Presse-papiers. Vous pouvez ensuite coller le script dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou dans un éditeur de texte pour exécuter des scripts ultérieurement.  
  
## <a name="see-also"></a>Voir aussi  
 [Préparer SQL Server pour CDC](../../integration-services/change-data-capture/prepare-sql-server-for-cdc.md)  
  
  
