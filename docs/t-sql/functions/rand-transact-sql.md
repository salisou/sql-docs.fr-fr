---
title: RAND (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- RAND
- RAND_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- RAND function
- values [SQL Server], random float
- random float value
ms.assetid: 363c84d6-b9fa-49ba-9a75-e44f27535ff6
author: julieMSFT
ms.author: jrasnick
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0c6df52fdaa5108c6cab057573f34d0f545f94c4
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82823758"
---
# <a name="rand-transact-sql"></a>RAND (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Retourne une valeur **float** pseudo-aléatoire, comprise entre 0 et 1, valeurs exclues.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RAND ( [ seed ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *seed*  
 [Expression](../../t-sql/language-elements/expressions-transact-sql.md) entière (**tinyint**, **smallint** ou **int**) qui fournit la valeur de départ. Si la valeur *seed* n’est pas spécifiée, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] affecte une valeur de départ aléatoire. Pour une valeur de départ spécifiée, le résultat retourné est toujours le même.  
  
## <a name="return-types"></a>Types de retour  
 **float**  
  
## <a name="remarks"></a>Notes  
 Les appels répétitifs de RAND() avec la même valeur de départ retournent les mêmes résultats.  
  
 Pour une connexion, si RAND() est appelé avec une valeur de départ spécifiée, tous les appels ultérieurs de RAND() produisent des résultats en fonction de l'appel de départ RAND(). Ainsi, la requête suivante produit toujours la même séquence de numéros.  
  
```sql  
SELECT RAND(100), RAND(), RAND()   
```  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant produit quatre numéros aléatoires différents avec la fonction RAND.  
  
```sql  
DECLARE @counter smallint;  
SET @counter = 1;  
WHILE @counter < 5  
   BEGIN  
      SELECT RAND() Random_Number  
      SET @counter = @counter + 1  
   END;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions mathématiques &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  
