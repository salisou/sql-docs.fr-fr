---
title: sp_dbcmptlevel (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dbcmptlevel
- sp_dbcmptlevel_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbcmptlevel
ms.assetid: 508c686d-2bd4-41ba-8602-48ebca266659
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0f6ffcb7a43fbfc2a840cbbbeb95de4bbb875cbe
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68108207"
---
# <a name="sp_dbcmptlevel-transact-sql"></a>sp_dbcmptlevel (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Définit certains comportements de base de données pour qu'ils soient compatibles avec la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifiée.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Utilisez à la place le [niveau de compatibilité ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_dbcmptlevel [ [ @dbname = ] name ]   
    [ , [ @new_cmptlevel = ] version ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @dbname = ] name`Nom de la base de données pour laquelle le niveau de compatibilité doit être modifié. Les noms de base de données doivent être conformes aux règles relatives aux identificateurs. *Name* est de **type sysname**, avec NULL comme valeur par défaut.  
  
`[ @new_cmptlevel = ] version`Version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec laquelle la base de données doit être compatible. *version* est de **type tinyint**, avec NULL comme valeur par défaut. La valeur doit être l'une des suivantes :  
  
 **90** = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
 **100** = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
 **110** = [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
 **120** = [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
 **130** = [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Si aucun paramètre n’est spécifié ou si le paramètre *Name* n’est pas spécifié, **sp_dbcmptlevel** retourne une erreur.  
  
 Si le *nom* est spécifié sans *version*, [!INCLUDE[ssDE](../../includes/ssde-md.md)] le retourne un message indiquant le niveau de compatibilité actuel de la base de données spécifiée.  
  
## <a name="remarks"></a>Notes  
 Pour obtenir une description des niveaux de compatibilité, consultez [niveau de compatibilité ALTER database &#40;&#41;Transact-SQL ](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="permissions"></a>Autorisations  
 Seul le propriétaire de la base de données, les membres du rôle serveur fixe **sysadmin** et le rôle de base de données fixe **db_owner** (si vous modifiez la base de données actuelle) peuvent exécuter cette procédure.  
  
## <a name="see-also"></a>Voir aussi  
 [Moteur de base de données des procédures stockées &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [Mots clés réservés &#40;Transact-SQL&#41;](../../t-sql/language-elements/reserved-keywords-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
