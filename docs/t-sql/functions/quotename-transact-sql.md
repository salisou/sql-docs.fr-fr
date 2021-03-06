---
title: QUOTENAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- QUOTENAME_TSQL
- QUOTENAME
dev_langs:
- TSQL
helpviewer_keywords:
- delimited identifiers [SQL Server]
- input strings [SQL Server]
- Unicode [SQL Server], delimited identifiers
- QUOTENAME function
- valid identifiers [SQL Server]
ms.assetid: 34d47f1e-2ac7-4890-8c9c-5f60f115e076
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b83a3dbe28848a335e414a0dd39ef1fafdffff17
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81634914"
---
# <a name="quotename-transact-sql"></a>QUOTENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne une chaîne Unicode avec les délimiteurs ajoutés afin que la chaîne d'entrée soit un identificateur délimité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
QUOTENAME ( 'character_string' [ , 'quote_character' ] )   
```  
  
## <a name="arguments"></a>Arguments  
 '*character_string*'  
 Représente une chaîne de caractères au format Unicode. *character_string* est de type **sysname** et est limité à 128 caractères. Les entrées de plus de 128 caractères retournent une valeur NULL.  
  
 '*quote_character*'  
 Représente une chaîne d'un seul caractère à utiliser en tant que délimiteur. Il peut s’agir d’une apostrophe ( **'** ), d’un crochet droit ou gauche ( **[]** ), d’un guillemet double ( **"** ), d’une parenthèse gauche ou droite ( **()** ), d’un signe inférieur ou supérieur à ( **><** ), d’une accolade gauche ou droite ( **{}** ) ou d’un accent grave ( **\`** ). La valeur NULL est retournée si un caractère non autorisé est fourni. Si *quote_character* n’est pas spécifié, les crochets sont utilisés.  
  
## <a name="return-types"></a>Types de retour  
 **nvarchar(258)**  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant prend la chaîne de caractères `abc[]def` et utilise les caractères `[``]` pour créer un identificateur délimité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide.  
  
```  
SELECT QUOTENAME('abc[]def');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
[abc[]]def]  
  
(1 row(s) affected)  
```  
  
 Vous remarquerez que dans la chaîne `abc[]def`, le crochet de droite est doublé pour indiquer un caractère d'échappement.  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L'exemple suivant prend la chaîne de caractères `abc def` et utilise les caractères `[``]` pour créer un identificateur délimité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide.  
  
```  
SELECT QUOTENAME('abc def');   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
[abc def]  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [PARSENAME &#40;Transact-SQL&#41;](../../t-sql/functions/parsename-transact-sql.md)  
 [CONCAT &#40;Transact-SQL&#41;](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)  
 [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [REPLACE &#40;Transact-SQL&#41;](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE &#40;Transact-SQL&#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40;Transact-SQL&#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF &#40;Transact-SQL&#41;](../../t-sql/functions/stuff-transact-sql.md)  
 [TRANSLATE &#40;Transact-SQL&#41;](../../t-sql/functions/translate-transact-sql.md)  
 [Fonctions de chaîne &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  

