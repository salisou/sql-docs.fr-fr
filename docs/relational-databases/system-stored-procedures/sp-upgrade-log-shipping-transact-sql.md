---
title: sp_upgrade_log_shipping (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_upgrade_log_shipping
- sp_upgrade_log_shipping_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_upgrade_log_shipping
ms.assetid: ee01092f-9caf-4e88-888b-ec7b84223705
author: stevestein
ms.author: sstein
ms.openlocfilehash: 493fcac9f5de8ee85a2e3c014763045c697bbe0e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68119444"
---
# <a name="sp_upgrade_log_shipping-transact-sql"></a>sp_upgrade_log_shipping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La procédure stockée sp_upgrade_log_shipping est appelée automatiquement pour mettre à niveau les métadonnées spécifiques à la copie des journaux de session.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_upgrade_log_shipping  
```  
  
## <a name="arguments"></a>Arguments  
 Aucune.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (autre)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune.  
  
## <a name="remarks"></a>Notes  
 Cette procédure stockée est appelée automatiquement lors de la mise à niveau de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour mettre à niveau les métadonnées pour la copie des journaux de transaction. Vous n'avez pas besoin d'exécuter cette procédure explicitement, à moins qu'un problème survienne avec les métadonnées au cours de la mise à niveau.  
  
 La procédure sp_upgrade_log_shipping doit s'exécuter à partir de la base de données master sur le serveur principal, secondaire ou moniteur.  
  
## <a name="permissions"></a>Autorisations  
 Requiert l’appartenance au rôle serveur fixe **sysadmin** .  
  
## <a name="see-also"></a>Voir aussi  
 [À propos de la copie des journaux de &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
