---
title: cursor (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- cursor data type
ms.assetid: fbea16ef-f2cc-4734-9149-ec2598fd3cca
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c25550ed5e985f643f81b0b41e749f007eef0df3
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "71682070"
---
# <a name="cursor-transact-sql"></a>cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Type de données pour les variables ou les paramètres OUTPUT des procédures stockées contenant une référence à un curseur.
  
## <a name="remarks"></a>Notes  
Les opérations suivantes peuvent référencer des variables et des paramètres ayant un type de données **cursor** :
-   les instructions DECLARE *\@local_variable* et SET *\@local_variable* ;  
-   les instructions de curseur OPEN, FETCH, CLOSE et DEALLOCATE ;  
-   les paramètres de sortie des procédures stockées ;  
-   la fonction CURSOR_STATUS ;  
-   les procédures stockées système **sp_cursor_list**, **sp_describe_cursor**, **sp_describe_cursor_tables** et **sp_describe_cursor_columns**.  
  
La colonne de sortie **cursor_name** de **sp_cursor_list** et **sp_describe_cursor** retourne le nom de la variable de curseur.
  
Toutes les variables créées avec le type de données **cursor** acceptent la valeur Null.
  
Il n’est pas possible d’utiliser le type de données **cursor** dans une colonne d’une instruction CREATE TABLE.
  
## <a name="see-also"></a>Voir aussi
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CURSOR_STATUS &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-status-transact-sql.md)  
[Conversion de type de données &#40;moteur de base de données&#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE CURSOR &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)
  
  
