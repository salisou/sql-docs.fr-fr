---
title: sp_help_fulltext_catalog_components (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_catalog_components_TSQL
- sp_help_fulltext_catalog_components
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_catalog_components
ms.assetid: fbd6a3d4-6a4c-42a2-bff8-2a5eb0745e47
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 213cc6ea9be57590d52755fdbba3151882ac0a38
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68055172"
---
# <a name="sp_help_fulltext_catalog_components-transact-sql"></a>sp_help_fulltext_catalog_components (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne la liste de tous les composants (filtres, analyseurs lexicaux et gestionnaires de protocoles) utilisés pour tous les catalogues de texte intégral dans la base de données active.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_fulltext_catalog_components  
```  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom du catalogue de texte intégral**|**int**|Nom du catalogue de texte intégral.|  
|**ID de catalogue de texte intégral**|**sysname**|Identificateur du catalogue de texte intégral.|  
|**componenttype**|**sysname**|Type de composant. Celui-ci peut avoir l'une des valeurs suivantes :<br /><br /> Filtrer<br /><br /> Gestionnaire de protocole<br /><br /> Analyseur lexical|  
|**componentname**|**sysname**|Nom du composant.|  
|**clsid**|**uniqueidentifier**|Identificateur de classe du composant.|  
|**FullPath**|**nvarchar(256)**|Chemin d'accès de l'emplacement du composant.<br /><br /> NULL = l’appelant n’est pas membre du rôle serveur fixe **ServerAdmin** .|  
|**version**|**nvarchar(30)**|Numéro de version du composant.|  
|**manufacturer**|**sysname**|Nom du fabricant du composant.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de recherche en texte intégral et de recherche sémantique &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)   
 [sys. fulltext_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md)   
 [sp_help_fulltext_system_components &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md)   
 [Recherche en texte intégral](../../relational-databases/search/full-text-search.md)  
  
  
