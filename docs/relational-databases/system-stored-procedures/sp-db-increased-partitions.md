---
title: sp_db_increased_partitions | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_db_increased_partitions_TSQL
- sp_db_increased_partitions
dev_langs:
- TSQL
helpviewer_keywords:
- sp_db_increased_partitions
ms.assetid: a8c043ec-b504-4929-ac0e-8babaa99d989
author: stevestein
ms.author: sstein
ms.openlocfilehash: 83a40c9070db1c997f30db71a6cff226cd0430d6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68108264"
---
# <a name="sp_db_increased_partitions"></a>sp_db_increased_partitions
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Active ou désactive la prise en charge de 15 000 partitions maximum pour la base de données spécifiée.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_dp_increased_partitions   
[ @dbname ] = 'database_name'   
[ , [ @increased_partitions = ] 'increased_partitions' ] [;]  
```  
  
## <a name="arguments"></a>Arguments  
 [ @dbname= ] '*database_name*'  
 Nom de la base de données. *dbname* est de **type sysname** , avec NULL comme valeur par défaut. Si *dbname* n’est pas spécifié, la base de données active est utilisée.  
  
 [ @increased_partitions= ] '*increased_partitions*'  
 Active ou désactive la prise en charge de 15 000 partitions sur la base de données spécifiée. *increased_partitions* est de type **varchar (6)** avec NULL comme valeur par défaut. Les valeurs acceptées sont ON ou TRUE pour activer la prise en charge et OFF ou FALSE pour la désactiver. Si *increased_partitions* n’est pas spécifié, la procédure retourne la valeur 1 pour indiquer que la prise en charge est activée pour la base de données spécifiée ou 0 pour indiquer que la prise en charge est désactivée.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation ALTER DATABASE sur la base de données spécifiée.  
  
  
