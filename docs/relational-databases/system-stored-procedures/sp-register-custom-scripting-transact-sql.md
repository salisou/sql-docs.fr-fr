---
title: sp_register_custom_scripting (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_register_custom_scripting
- sp_register_custom_scripting_TSQL
helpviewer_keywords:
- sp_register_custom_scripting
ms.assetid: a8159282-de3b-4b9e-bdc9-3d3fce485c7f
author: stevestein
ms.author: sstein
ms.openlocfilehash: c10451148c6f9b2fda231691b770bca3928517f2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68075747"
---
# <a name="sp_register_custom_scripting-transact-sql"></a>sp_register_custom_scripting (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La réplication permet aux procédures stockées personnalisées définies par l'utilisateur de remplacer une ou plusieurs procédures par défaut utilisées dans la réplication transactionnelle. Lorsqu'une modification de schéma est apportée à une table répliquée, ces procédures stockées sont recréées. **sp_register_custom_scripting** inscrit une procédure stockée ou [!INCLUDE[tsql](../../includes/tsql-md.md)] un fichier de script qui est exécuté lorsqu’une modification de schéma se produit pour générer le script de la définition d’une nouvelle procédure stockée personnalisée définie par l’utilisateur. Cette nouvelle procédure stockée personnalisée définie par l'utilisateur doit refléter le nouveau schéma de la table. **sp_register_custom_scripting** est exécutée sur la base de données de publication sur le serveur de publication, et le fichier de script ou la procédure stockée inscrit est exécuté sur l’abonné lorsqu’une modification de schéma se produit.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_register_custom_scripting [ @type  = ] 'type'  
    [ @value = ] 'value'   
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @type = ] 'type'`Type de la procédure stockée ou du script personnalisé en cours d’inscription. *type* **varchar (16)**, sans valeur par défaut, et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Insérer**|La procédure stockée personnalisée inscrite est exécutée lorsqu'une instruction INSERT est répliquée.|  
|**mise à jour**|La procédure stockée personnalisée inscrite est exécutée lorsqu'une instruction UPDATE est répliquée.|  
|**delete**|La procédure stockée personnalisée inscrite est exécutée lorsqu'une instruction DELETE est répliquée.|  
|**custom_script**|Le script est exécuté à la fin du déclencheur DDL (Data Definition Language).|  
  
`[ @value = ] 'value'`Nom d’une procédure stockée ou d’un nom et d’un chemin [!INCLUDE[tsql](../../includes/tsql-md.md)] d’accès complet au fichier de script en cours d’inscription. la *valeur* est de type **nvarchar (1024)**, sans valeur par défaut.  
  
> [!NOTE]  
>  La spécification de NULL pour le paramètre de *valeur*annule l’inscription d’un script précédemment inscrit, ce qui revient à exécuter [sp_unregister_custom_scripting](../../relational-databases/system-stored-procedures/sp-unregister-custom-scripting-transact-sql.md).  
  
 Lorsque la valeur de *type* est **custom_script**, le nom et le chemin d’accès [!INCLUDE[tsql](../../includes/tsql-md.md)] complet d’un fichier de script sont attendus. Dans le cas contraire, la *valeur* doit être le nom d’une procédure stockée enregistrée.  
  
`[ @publication = ] 'publication'`Nom de la publication pour laquelle la procédure stockée ou le script personnalisé est en cours d’enregistrement. *publication* est de **type sysname**, avec **null**comme valeur par défaut.  
  
`[ @article = ] 'article'`Nom de l’article pour lequel la procédure stockée ou le script personnalisé est en cours d’enregistrement. *article* est de **type sysname**, avec **null**comme valeur par défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_register_custom_scripting** est utilisé dans la réplication transactionnelle et d’instantané.  
  
 Vous devez exécuter cette procédure stockée avant d'apporter une modification de schéma à une table répliquée. Pour plus d’informations sur l’utilisation de cette procédure stockée, consultez [régénérer des procédures transactionnelles personnalisées pour refléter les modifications de schéma](../../relational-databases/replication/transactional/transactional-articles-regenerate-to-reflect-schema-changes.md).  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** , du rôle de base de données fixe **db_owner** ou du rôle de base de données fixe **db_ddladmin** peuvent exécuter **sp_register_custom_scripting**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_unregister_custom_scripting &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unregister-custom-scripting-transact-sql.md)  
  
  
