---
title: DROP XML SCHEMA COLLECTION (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/25/2015
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP XML SCHEMA COLLECTION
- DROP_XML_SCHEMA_COLLECTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting XML schema collections
- XML schema collections [SQL Server], removing
- schema collections [SQL Server], removing
- removing XML schema collections
- dropping XML schema collections
- DROP XML SCHEMA COLLECTION statement
ms.assetid: d686f2f5-e03a-4ffe-a566-6036628f46f1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c2a02ae5bc9572265cc33392a02c596cfcfec0ff
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68072007"
---
# <a name="drop-xml-schema-collection-transact-sql"></a>DROP XML SCHEMA COLLECTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Supprime toute la collection de schémas XML et tous ses composants.  
  
![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP XML SCHEMA COLLECTION [ relational_schema. ]sql_identifier  
```  
  
## <a name="arguments"></a>Arguments  
*relational_schema*  
Identifie le nom du schéma relationnel. Si cet argument n'est pas spécifié, le schéma relationnel par défaut est utilisé.  
  
*sql_identifier*  
Nom de la collection de schémas XML à supprimer.  
  
## <a name="remarks"></a>Notes  
La suppression d'une collection de schémas XML est une opération transactionnelle. Lorsque vous supprimez une collection de schémas XML dans une transaction et que vous annulez cette transaction par la suite, la collection n'est pas supprimée.  
  
Vous ne pouvez pas supprimer une collection de schémas XML en cours d'utilisation. Donc, la collection à supprimer ne peut pas être :  
  
-   associée à un paramètre ou à une colonne de type **xml** ;  
  
-   spécifiée dans des contraintes de table ;  
  
-   référencée dans une fonction ou une procédure stockée liée à un schéma. Par exemple, la fonction suivante verrouille la collection de schémas XML `MyCollection` car elle spécifie `WITH SCHEMABINDING`. Si vous la supprimez, il n'y a aucun verrou sur XML SCHEMA COLLECTION.  
  
    ```  
    CREATE FUNCTION dbo.MyFunction()  
    RETURNS int  
    WITH SCHEMABINDING  
    AS  
    BEGIN  
       ...  
       DECLARE @x XML(MyCollection)  
       ...  
    END;  
    ```  
  
## <a name="permissions"></a>Autorisations  
La suppression d'une collection de schémas XML nécessite l'autorisation DROP sur la collection.  
  
## <a name="examples"></a>Exemples  
Le code exemple suivant montre comment supprimer une collection de schémas XML.  
  
```  
DROP XML SCHEMA COLLECTION ManuInstructionsSchemaCollection;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)   
 [ALTER XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-xml-schema-collection-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [Comparer du XML typé et du XML non typé](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Spécifications et limitations relatives aux collections de schémas XML sur le serveur](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
