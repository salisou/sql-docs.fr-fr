---
title: PI (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- PI_TSQL
- PI
dev_langs:
- TSQL
helpviewer_keywords:
- constant value of PI
- PI function
ms.assetid: d7c4575b-ba1c-4ef7-a633-9a379d7f01fd
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 119b6b789ec19ca33839ae324024ae467a7dc014
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "67914333"
---
# <a name="pi-transact-sql"></a>PI (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne la valeur constante de PI.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
PI ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 **float**  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne la valeur de `PI`.  
  
```  
SELECT PI();  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
------------------------  
3.14159265358979  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions mathématiques &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  

