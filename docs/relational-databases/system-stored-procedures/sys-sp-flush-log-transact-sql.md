---
title: sys. sp_flush_log (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_flush_log_TSQL
- sys.sp_flush_log
- sys.sp_flush_log_TSQL
- sp_flush_log
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_flush_log
ms.assetid: 75cc9f52-3b1f-4754-b1e7-ce0dd3323bc9
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 61c4cceab6c816d63226216a54d4f647e92e592d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68066684"
---
# <a name="syssp_flush_log-transact-sql"></a>sys.sp_flush_log (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Vide sur le disque le journal des transactions de la base de données active, renforçant ainsi toutes les transactions durables différées déjà validées.  
  
 Si vous choisissez d'utiliser la durabilité différée des transactions en raison des avantages qu'elle offre en matière de performances, mais que vous voulez également disposer d'une limite garantie sur la quantité de données qui sont perdues en cas de défaillance ou de basculement du serveur, exécutez `sys.sp_flush_log` lors d'une planification régulière. Par exemple, si vous souhaitez vous assurer que vous ne perdez pas plus de x secondes de données, vous devez exécuter `sp_flush_log` toutes les x secondes.  
  
 L'exécution de `sys.sp_flush_log` garantit que toutes les transactions durables différées déjà validées sont rendues durables. Pour plus d’informations, consultez la rubrique conceptuelle relative à la [durabilité des transactions](../../relational-databases/logs/control-transaction-durability.md) .  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
  
sys.sp_flush_log  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucune.  
  
## <a name="return-code-values"></a>Codet de retour  
 Un code de retour de 1 indique un succès.  Toute autre valeur signale un échec.  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune.  
  
## <a name="sample-code"></a>Exemple de code  
  
```sql  
.  
EXECUTE sys.sp_flush_log  
  
```  
  
  
