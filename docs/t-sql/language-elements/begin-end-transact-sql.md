---
title: BEGIN...END (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- BEGIN
- BEGIN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- enclosing statements [SQL Server]
- BEGIN statement
- control-of-flow language [SQL Server], BEGIN...END statement
- BEGIN...END keyword
- grouping statements, BEGIN...END statement
- executing Transact-SQL statements together [SQL Server]
- statements [SQL Server], grouping
ms.assetid: fc2c7f76-f1f9-4f91-beef-bc8ef0da2feb
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ad484c4e830dde52a9845c0d45293463d240d977
ms.sourcegitcommit: e922721431d230c45bbfb5dc01e142abbd098344
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82138244"
---
# <a name="beginend-transact-sql"></a>BEGIN...END (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Délimite une série d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] pour permettre l'exécution groupée d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)]. BEGIN et END sont des mots clés du langage de contrôle de flux.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
BEGIN  
    { sql_statement | statement_block }   
END  
```  
  
## <a name="arguments"></a>Arguments  
 { *sql_statement* | *statement_block* }  
 Représente toute instruction ou tout groupe d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] valide tel que défini dans un bloc d'instructions.  
  
## <a name="remarks"></a>Notes  
 Les blocs BEGIN...END peuvent être imbriqués.  
  
 Bien que toutes les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] soient valides à l’intérieur d’un bloc BEGIN…END, certaines instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] ne doivent pas être regroupées à l’intérieur d’un même lot ou bloc d’instructions.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple suivant, `BEGIN` et `END` délimitent une série d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] qui sont exécutées ensemble. Si le bloc `BEGIN...END` ne figurait pas dans l'exemple, les deux instructions `ROLLBACK TRANSACTION` seraient exécutées et les deux messages `PRINT` seraient renvoyés.  
  
```sql
USE AdventureWorks2012
GO  
BEGIN TRANSACTION
GO  
IF @@TRANCOUNT = 0  
BEGIN  
    SELECT FirstName, MiddleName   
    FROM Person.Person WHERE LastName = 'Adams'
    ROLLBACK TRANSACTION
    PRINT N'Rolling back the transaction two times would cause an error.'
END
ROLLBACK TRANSACTION
PRINT N'Rolled back the transaction.'
GO  
/*  
Rolled back the transaction.  
*/  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Dans l’exemple suivant, `BEGIN` et `END` définissent une série d’instructions [!INCLUDE[DWsql](../../includes/dwsql-md.md)] qui s’exécutent ensemble. Si le bloc `BEGIN...END` n’est pas inclus, l’exemple suivant est dans une boucle continue.  
  
```sql
-- Uses AdventureWorks  

DECLARE @Iteration Integer = 0  
WHILE @Iteration <10  
BEGIN  
    SELECT FirstName, MiddleName   
    FROM dbo.DimCustomer WHERE LastName = 'Adams'
    SET @Iteration += 1  
END
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [Langage de contrôle de flux &#40;Transact-SQL&#41;](~/t-sql/language-elements/control-of-flow.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [END &#40;BEGIN...END&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/end-begin-end-transact-sql.md)
