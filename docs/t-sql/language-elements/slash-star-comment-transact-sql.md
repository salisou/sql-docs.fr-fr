---
title: Barre oblique étoile (bloc de commentaire) (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- /*...*/_TSQL
- Comment
- /*...*/
dev_langs:
- TSQL
helpviewer_keywords:
- nonexecuting text strings [SQL Server]
- /*...*/ (comment)
- remarks [SQL Server]
- comments [SQL Server]
ms.assetid: 4d9ab1b2-4bbb-4c16-beb1-cafc1af7417c
author: rothja
ms.author: jroth
ms.openlocfilehash: c1bee651b2dd74564ebaff47add5acd4b62c5018
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68121679"
---
# <a name="slash-star-block-comment-transact-sql"></a>Barre oblique étoile (bloc de commentaire) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]


  Indique un texte défini par l'utilisateur. Le texte placé entre /* et \*/ n’est pas évalué par le serveur.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
/*  
text_of_comment  
*/  
```  
  
## <a name="arguments"></a>Arguments  
 *text_of_comment*  
 Texte du commentaire. Correspond à une ou plusieurs chaînes de caractères.  
  
## <a name="remarks"></a>Notes  
 Il est possible d'insérer des commentaires sur une ligne distincte ou à l'intérieur d'une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)]. Les commentaires de plusieurs lignes doivent être signalés par /* et \*/. Par convention, les commentaires de plusieurs lignes utilisent souvent /\* au début de la première ligne, \*\* au début des lignes suivantes et \*/ pour signaler la fin du commentaire.  
  
 Il n'y a pas de longueur maximale pour les commentaires.  
  
 Les commentaires imbriqués ne sont pas pris en charge. Un modèle de caractère /* situé n’importe où dans un commentaire existant est traité comme le début d’un commentaire imbriqué et nécessite dès lors une marque de commentaire de fermeture \*/. En l'absence de marque de commentaire de fermeture, une erreur est générée.  
  
 Par exemple, le code suivant génère une erreur.  
  
```  
DECLARE @comment AS varchar(20);  
GO  
/*  
SELECT @comment = '/*';  
*/   
SELECT @@VERSION;  
GO   
```  
  
 Pour corriger cette erreur, apportez la modification suivante.  
  
```  
DECLARE @comment AS varchar(20);  
GO  
/*  
SELECT @comment = '/*';  
*/ */  
SELECT @@VERSION;  
GO  
  
```  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise des commentaires afin d'expliquer ce que la section du code est supposée faire.  
  
```  
USE AdventureWorks2012;  
GO  
/*  
This section of the code joins the Person table with the Address table,   
by using the Employee and BusinessEntityAddress tables in the middle to   
get a list of all the employees in the AdventureWorks2012 database   
and their contact information.  
*/  
SELECT p.FirstName, p.LastName, a.AddressLine1, a.AddressLine2, a.City, a.PostalCode  
FROM Person.Person AS p  
JOIN HumanResources.Employee AS e ON p.BusinessEntityID = e.BusinessEntityID   
JOIN Person.BusinessEntityAddress AS ea ON e.BusinessEntityID = ea.BusinessEntityID  
JOIN Person.Address AS a ON ea.AddressID = a.AddressID;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [-- &#40;Comment&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/comment-transact-sql.md)   
 [Langage de contrôle de flux &#40;Transact-SQL&#41;](~/t-sql/language-elements/control-of-flow.md)  
  
  

