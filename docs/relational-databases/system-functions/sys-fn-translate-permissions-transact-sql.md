---
title: sys. fn_translate_permissions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_translate_permissions
- sys.fn_translate_permissions_TSQL
- fn_translate_permissions
- fn_translate_permissions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- permissions bitmask [SQL Server]
- sys.fn_translate_permissions function
- fn_translate_permissions function
ms.assetid: ac97121f-2bd0-4f71-8e45-42c8584edbc5
author: rothja
ms.author: jroth
ms.openlocfilehash: c08fd2235750a8a7be99b5290813331141ddf0de
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "68055373"
---
# <a name="sysfn_translate_permissions-transact-sql"></a>sys.fn_translate_permissions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Convertit le masque de bits des autorisations retourné par la trace SQL en une table de noms d'autorisations.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.fn_translate_permissions ( level , perms )  
```  
  
## <a name="arguments"></a>Arguments  
 *niveau*  
 Type d'élément sécurisable auquel l'autorisation est appliquée. le *niveau* est **nvarchar (60)**.  
  
 *perms*  
 Masque de bits retourné dans la colonne d'autorisations. *perms* est **de type varbinary (16)**.  
  
## <a name="returns"></a>Retours  
 **table**  
  
## <a name="remarks"></a>Notes  
 La valeur retournée dans la colonne **permissions** d’une trace SQL est une représentation d’entier d' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un masque de réutilisation utilisé par pour calculer les autorisations effectives. Chacun des 25 types d'éléments sécurisables possède son propre jeu d'autorisations avec des valeurs numériques correspondantes. **sys. fn_translate_permissions** convertit ce masque de masque en une table de noms d’autorisations.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="example"></a>Exemple  
 La requête suivante utilise `sys.fn_builtin_permissions` pour afficher les autorisations qui s’appliquent aux certificats, puis `sys.fn_translate_permissions` utilise pour retourner les résultats du masque de sous-masque des autorisations.  
  
```  
SELECT * FROM sys.fn_builtin_permissions('CERTIFICATE');  
SELECT '0001' AS Input, * FROM sys.fn_translate_permissions('CERTIFICATE', 0001);  
SELECT '0010' AS Input, * FROM sys.fn_translate_permissions('CERTIFICATE', 0010);  
SELECT '0011' AS Input, * FROM sys.fn_translate_permissions('CERTIFICATE', 0011);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Autorisations &#40;Moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [sys. server_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)   
 [sys.database_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)  
  
  
