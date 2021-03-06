---
title: sp_cycle_errorlog (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cycle_errorlog_TSQL
- sp_cycle_errorlog
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cycle_errorlog
ms.assetid: 61a12cbf-78a3-4052-8604-3b29d07573fd
author: stevestein
ms.author: sstein
ms.openlocfilehash: c15a36678bf0bd1ff5fc933eb79bff96b6780b60
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68108339"
---
# <a name="sp_cycle_errorlog-transact-sql"></a>sp_cycle_errorlog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ferme le journal d'erreurs en cours et parcourt les numéros d'extension du journal d'erreurs, comme lors du redémarrage d'un serveur. Le nouveau journal d'erreurs contient le numéro de version, des informations sur les droits d'auteur, ainsi qu'une ligne indiquant que le nouveau journal a été créé.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_cycle_errorlog  
```  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="remarks"></a>Notes  
 Chaque fois [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que démarre, le journal des erreurs en cours est renommé **ErrorLog. 1**; **ErrorLog. 1** devient **ErrorLog. 2**, **ErrorLog. 2** devient **ErrorLog. 3**, et ainsi de suite. **sp_cycle_errorlog** vous permet de parcourir les fichiers journaux d’erreurs sans arrêter ni redémarrer le serveur.  
  
## <a name="permissions"></a>Autorisations  
 Les autorisations d’exécution pour **sp_cycle_errorlog** sont limitées aux membres du rôle serveur fixe **sysadmin** .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant parcourt le journal d'erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
EXEC sp_cycle_errorlog ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_cycle_agent_errorlog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cycle-agent-errorlog-transact-sql.md)  
  
  
