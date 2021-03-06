---
title: sp_dropanonymousagent (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropanonymousagent
- sp_dropanonymousagent_TSQL
helpviewer_keywords:
- sp_dropanonymousagent
ms.assetid: 4cb96efa-9358-44a3-a8ee-a7e181bed089
ms.author: vanto
author: VanMSFT
ms.openlocfilehash: 7e82023ed750c77d87a2536debfb5fceb7321db4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67911952"
---
# <a name="sp_dropanonymousagent-transact-sql"></a>sp_dropanonymousagent (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime du serveur de publication un Agent anonyme destiné à la surveillance de la réplication sur le serveur de distribution. Cette procédure stockée est exécutée sur n'importe quelle base de données du serveur de publication.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sp_dropanonymousagent [ @subid= ] sub_id    , [ @type= ] type  
```  
  
## <a name="arguments"></a>Arguments  
`[ @subid = ] sub_id`Identificateur global d’un abonnement anonyme. *sub_id* est de type **uniqueidentifier**, sans valeur par défaut. Cet identificateur peut être récupéré sur l’abonné à l’aide de **sp_helppullsubscription**. La valeur du champ **subid** du jeu de résultats retourné est cet identificateur global.  
  
`[ @type = ] type`Type d’abonnement. le *type* est **int**, sans valeur par défaut. Les valeurs valides sont **1** ou **2**. Spécifiez **1**, si la réplication d’instantané ou la réplication transactionnelle à l’aide de l’agent de distribution. Spécifiez **2**si la réplication de fusion utilise l’agent de fusion.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_dropanonymousagent** est utilisé dans tous les types de réplications.  
  
 Cette procédure stockée permet de supprimer uniquement les Agents d'abonnement anonymes et ne permet pas de supprimer les abonnements connus.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle de base de données fixe **db_owner** dans la base de données de distribution peuvent exécuter **sp_dropanonymousagent**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
