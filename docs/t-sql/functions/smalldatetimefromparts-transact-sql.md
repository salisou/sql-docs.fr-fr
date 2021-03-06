---
title: SMALLDATETIMEFROMPARTS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SMALLDATETIMEFROMPARTS
- SMALLDATETIMEFROMPARTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SMALLDATETIMEFROMPARTS function
ms.assetid: 7467fdab-e588-419c-9e29-42caec34a9ea
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8f18ee84c1bbb2234672d198923e93af4d99374f
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "67907104"
---
# <a name="smalldatetimefromparts-transact-sql"></a>SMALLDATETIMEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Renvoie une valeur **smalldatetime** pour la date et l’heure spécifiées.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SMALLDATETIMEFROMPARTS ( year, month, day, hour, minute )  
```  
  
## <a name="arguments"></a>Arguments  
 *year*  
 Expression entière spécifiant une année.  
  
 *month*  
 Expression entière spécifiant un mois.  
  
 *day*  
 Expression entière spécifiant un jour.  
  
 *hour*  
 Expression entière spécifiant des heures.  
  
 *minute*  
 Expression entière spécifiant des minutes.  
  
## <a name="return-types"></a>Types de retour  
 **smalldatetime**  
  
## <a name="remarks"></a>Notes  
 Cette fonction agit comme un constructeur pour une valeur **smalldatetime** complètement initialisée. Si les arguments ne sont pas valides, une erreur est générée. Si les arguments obligatoires sont NULL, la valeur NULL est retournée.  
  
 Cette fonction peut être exécutée à distance sur des serveurs [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et versions ultérieures. Elle ne peut pas être exécutée à distance sur des serveurs dont la version est antérieure à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="examples"></a>Exemples  
  
```  
SELECT SMALLDATETIMEFROMPARTS ( 2010, 12, 31, 23, 59 ) AS Result  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------------------  
2010-12-31 23:59:00  
  
(1 row(s) affected)  
```  
  

