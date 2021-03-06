---
title: ADD SENSITIVITY CLASSIFICATION (Transact-SQL) | Microsoft Docs
ms.date: 03/25/2019
ms.reviewer: ''
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
ms.custom: ''
ms.manager: craigg
ms.author: giladm
author: giladmit
f1_keywords:
- ADD SENSITIVITY CLASSIFICATION
- ADD_SENSITIVITY_CLASSIFICATION
dev_langs:
- TSQL
helpviewer_keywords:
- ADD SENSITIVITY CLASSIFICATION statement
- add labels
- adding labels
- adding labels
- classification [SQL]
- labels [SQL]
- information types
- data classification
- rank
monikerRange: " >= sql-server-linux-ver15 || >= sql-server-ver15 || = azuresqldb-current || = sqlallproducts-allversions"
ms.openlocfilehash: e3b5ba45e03a27f8b07f854cd94f515daefa5dec
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81631961"
---
# <a name="add-sensitivity-classification-transact-sql"></a>AJOUTER UNE CLASSIFICATION DE SENSIBILITÉ (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2012-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-asdw-xxx-md.md)]

Ajoute des métadonnées relatives à la classification de sensibilité à une ou plusieurs colonnes de base de données. La classification peut inclure une étiquette de sensibilité et un type d’information.

Pour SQL Server, cela a été introduit dans SQL Server 2019.

Classifier des données sensibles dans votre environnement de base de données permet d’étendre la visibilité et d’améliorer la protection. Vous trouverez des informations supplémentaires dans [Mise en route avec SQL Information Protection](https://aka.ms/sqlip)

## <a name="syntax"></a>Syntaxe  

```syntaxsql
ADD SENSITIVITY CLASSIFICATION TO
    <object_name> [, ...n ]
    WITH ( <sensitivity_option> [, ...n ] )     

<object_name> ::=
{
    [schema_name.]table_name.column_name
}

<sensitivity_option> ::=  
{   
    LABEL = string |
    LABEL_ID = guidOrString |
    INFORMATION_TYPE = string |
    INFORMATION_TYPE_ID = guidOrString | 
    RANK = NONE | LOW | MEDIUM | HIGH | CRITICAL
}
```  

## <a name="arguments"></a>Arguments  

*object_name* ([schema_name.]table_name.column_name)

Est le nom de la colonne de base de données à classifier. Actuellement, seule la classification de colonne est prise en charge.
    - *schema_name* (facultatif) : nom du schéma auquel appartient la colonne classifiée.
    - *table_name* : nom du schéma auquel appartient la table classifiée.
    - *column_name* : nom de la colonne classifiée.

*LABEL*

Nom explicite de l’étiquette de sensibilité. Les étiquettes de sensibilité représentent la sensibilité des données stockées dans la colonne de base de données.

*LABEL_ID*

Identificateur associé à l’étiquette de sensibilité. Il est souvent utilisé par les plateformes de protection des informations centralisées pour identifier les étiquettes dans le système.

*INFORMATION_TYPE*

Nom explicite du type d’information. Les types d’informations sont utilisés pour décrire le type de données stockées dans la colonne de la base de données.

*INFORMATION_TYPE_ID*

Il s’agit d’un identificateur associé au type d’information. Il est souvent utilisé par les plateformes de protection des informations centralisées pour identifier les types d’informations dans le système.

*RANK*

Identificateur basé sur un ensemble prédéfini de valeurs qui définissent le rang de sensibilité. Il est utilisé par d’autres services tels que le service Advanced Threat Protection pour détecter les anomalies en fonction de leur rang.


## <a name="remarks"></a>Notes  

- Seule une classification peut être ajoutée à un objet unique. L’ajout d’une classification à un objet déjà classifié remplacera la classification existante.
- Plusieurs objets peuvent être classifiés avec une seule instruction `ADD SENSITIVITY CLASSIFICATION`.
- L’affichage du système [sys.sensitivity_classifications](../../relational-databases/system-catalog-views/sys-sensitivity-classifications-transact-sql.md) peut être utilisé pour récupérer les informations de classification de sensibilité d’une base de données.


## <a name="permissions"></a>Autorisations

Requiert une autorisation ALTER ANY SENSITIVITY CLASSIFICATION. La classification ALTER ANY SENSITIVITY CLASSIFICATION est impliquée par l’autorisation de base de données ALTER, ou par l’autorisation de serveur CONTROL SERVER.


## <a name="examples"></a>Exemples  

### <a name="a-classifying-two-columns"></a>R. Classification de deux colonnes

L’exemple suivant classifie les colonnes **dbo.sales.price** et **dbo.sales.discount** avec l’étiquette de sensibilité **Hautement confidentiel** et le Type d’informations **Financier**.

```sql
ADD SENSITIVITY CLASSIFICATION TO
    dbo.sales.price, dbo.sales.discount
    WITH ( LABEL='Highly Confidential', INFORMATION_TYPE='Financial' )
```  

### <a name="b-classifying-only-a-label"></a>B. Classification d’une seule étiquette
L’exemple suivant classifie la colonne **dbo.customer.comments** portant l’étiquette **Confidentiel** et ID d’étiquette **643f7acd-776a-438d-890c-79c3f2a520d6**. Le type d’information n’est pas classifié pour cette colonne.

```sql
ADD SENSITIVITY CLASSIFICATION TO
    dbo.customer.comments
    WITH ( LABEL='Confidential', LABEL_ID='643f7acd-776a-438d-890c-79c3f2a520d6' )
```  

## <a name="see-also"></a>Voir aussi  

[DROP SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[sys.sensitivity_classifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sensitivity-classifications-transact-sql.md)

[Autorisations (moteur de base de données)](https://docs.microsoft.com/sql/relational-databases/security/permissions-database-engine)

[Prise en main de SQL Information Protection](https://aka.ms/sqlip)
