---
title: Valider des informations de partition (Fusion)
description: Décrit comment valider des informations de partition pour un Abonné de fusion dans SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication data validation [SQL Server replication], partitions
- parameterized filters [SQL Server replication], validating partition information
- validating partition information
ms.assetid: c059553e-df2c-4333-ba79-e8d6e2890c34
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da57b7586fb80346dda466004a9cd47a3bb08884
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "75321547"
---
# <a name="validate-partition-information-for-a-merge-subscriber"></a>Valider des informations de partition pour un Abonné de fusion
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Quand vous définissez un filtre de lignes paramétrable pour une publication de fusion, vous utilisez une fonction qui référence des informations de l'Abonné, telles que son nom de connexion. Par défaut, la réplication valide les informations de l'Abonné sur la base de cette fonction avant chaque synchronisation et si un instantané est appliqué à l'Abonné. Le processus de validation vérifie que ces données sont partitionnées correctement pour chaque Abonné. Le fonctionnement de la validation est contrôlé par la propriété de publication **validate_subscriber_info**, qui peut être modifiée à l’aide de [sp_changemergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md) ou sur la page **Options d’abonnement** de la boîte de dialogue **Propriétés de la publication**. Pour plus d'informations sur la modification des propriétés d'une publication, consultez [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
## <a name="how-partition-validation-works"></a>Fonctionnement de la validation de partition  
 Lorsqu'une publication est filtrée par exemple à l'aide de la fonction **SUSER_SNAME()** , l'Agent de fusion applique l'instantané initial à chaque Abonné en fonction des données qui sont valides pour l'expression **SUSER_SNAME()** .  
  
 Si la validation est activée, quand l'Abonné se reconnecte au serveur de publication pour la synchronisation suivante, l'Agent de fusion valide les informations sur l'Abonné et vérifie que la partition de chaque Abonné est la même que celle reçue dans l'instantané initial. Pour chaque application de fusion ou d'instantané suivante, l'Agent de fusion valide la partition de chaque abonné.  
  
 Si l'Agent de fusion détecte que la fonction utilisée dans l'expression de filtrage renvoie une valeur différente de celle qu'elle a renvoyée lors de l'instantané initial, l'application de fusion ou d'instantané échoue, et l'abonnement de cet Abonné peut nécessiter une réinitialisation. La réinitialisation peut être nécessaire pour empêcher des problèmes qui peuvent survenir si les paramètres de fusion d'un Abonné ont changé, mais elle peut être suffisante pour ramener les informations sur l'Abonné, par exemple le nom de connexion, à la valeur utilisée au moment de l'instantané original.  
  
 Quand l'Agent de fusion valide une partition, en plus de valider la partition relativement aux valeurs renvoyées par toutes les fonctions utilisées dans les expressions de filtrage, l'agent vérifie également si l'instantané a été généré avant des modifications qui l'invalident, par exemple des opérations de nettoyage des métadonnées ou des modifications de schéma. Si un instantané partitionné est trop ancien, l'Agent de fusion renvoie une erreur et vous devez régénérer un instantané partitionné pour cet Abonné sur la base d'un instantané normal en cours.  
  
## <a name="see-also"></a>Voir aussi  
 [FAQ sur l’administration de la réplication](../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md)   
 [Best Practices for Replication Administration](../../relational-databases/replication/administration/best-practices-for-replication-administration.md)   
 [Réinitialiser des abonnements](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Valider des données répliquées](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  
