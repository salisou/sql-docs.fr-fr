---
title: ALTER EXTERNAL DATA SOURCE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER EXTERNAL DATA SOURCE
- ALTER_EXTERNAL_DATA_SOURCE
dev_langs:
- TSQL
helpviewer_keywords:
- polybase, alter external data source statement
- ALTER EXTERNAL DATA SOURCE statement
ms.assetid: a34b9e90-199d-46d0-817a-a7e69387bf5f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a28f86d1e5a87f41a8894dad22f4cf887602af02
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81628109"
---
# <a name="alter-external-data-source-transact-sql"></a>ALTER EXTERNAL DATA SOURCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Modifie une source de données externe utilisée pour créer une table externe. La source de données externe peut être un stockage Hadoop ou d’objets blob Azure (WASBS) pour SQL SERVER et un stockage d’objets blob Azure (WASBS) ou Azure Data Lake (ABFSS/ADL) pour Azure SQL Data Warehouse. 

## <a name="syntax"></a>Syntaxe  

```syntaxsql
-- Modify an external data source
-- Applies to: SQL Server (2016 or later) and APS
ALTER EXTERNAL DATA SOURCE data_source_name SET
    {   
        LOCATION = 'server_name_or_IP' [,] |
        RESOURCE_MANAGER_LOCATION = <'IP address;Port'> [,] |
        CREDENTIAL = credential_name
    }  
    [;]  

-- Modify an external data source pointing to Azure Blob storage
-- Applies to: SQL Server (starting with 2017)
ALTER EXTERNAL DATA SOURCE data_source_name
    SET
        LOCATION = 'https://storage_account_name.blob.core.windows.net'
        [, CREDENTIAL = credential_name ] 

-- Modify an external data source pointing to Azure Blob storage or Azure Data Lake storage
-- Applies to: Azure SQL Data Warehouse
ALTER EXTERNAL DATA SOURCE data_source_name
    SET
        [LOCATION = '<location prefix>://<location path>']
        [, CREDENTIAL = credential_name ] 
```

## <a name="arguments"></a>Arguments  
 data_source_name Spécifie le nom défini par l’utilisateur de la source de données. Le nom doit être unique.

 LOCATION = 'server_name_or_IP' Fournit le protocole de connectivité et le chemin de la source de données externe.

 RESOURCE_MANAGER_LOCATION = '\<Adresse IP;Port>' (Non applicable à Azure SQL Data Warehouse) Spécifie l’emplacement du Gestionnaire des ressources Hadoop. S’il est spécifié, l’optimiseur de requête peut choisir de prétraiter les données d’une requête PolyBase en utilisant les fonctionnalités de calcul d’Hadoop. C’est une décision basée sur les coûts. Appelée pushdown de prédicats, cette opération peut considérablement réduire le volume des données transférées entre Hadoop et SQL, et donc améliorer les performances des requêtes.

 CREDENTIAL = Credential_Name Spécifie les informations d’identification nommées. Consultez [CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).

TYPE = [HADOOP | BLOB_STORAGE]   
**S’applique à :** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)].
Pour les opérations en bloc uniquement, `LOCATION` doit être valide dans l’URL vers le stockage Blob Azure. Ne placez pas **/** , le nom du fichier ou les paramètres de signature d’accès partagé à la fin de l’URL `LOCATION`.
Les informations d’identification utilisées doivent être créées avec `SHARED ACCESS SIGNATURE` comme identité. Pour plus d’informations sur les signatures d’accès partagé, consultez [Utilisation des signatures d’accès partagé (SAP)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1).

  

## <a name="remarks"></a>Notes
 Une seule une source peut être modifiée à la fois. Des demandes simultanées de modifications de la même source provoquent l’attente d’une instruction. Toutefois, différentes sources peuvent être modifiés en même temps. Cette instruction peut s’exécuter en même temps que d’autres instructions.

## <a name="permissions"></a>Autorisations  
 Exige l’autorisation ALTER ANY EXTERNAL DATA SOURCE.
 > [!IMPORTANT]  
 > L’autorisation ALTER ANY EXTERNAL DATA SOURCE accorde à n’importe quel principal la possibilité de créer et de modifier tout objet de source de données externe. Par conséquent, elle permet également d’accéder à toutes les informations d’identification délimitées à la base de données. Cette autorisation doit être considérée comme fournissant des privilèges très élevés, et doit donc être accordée uniquement aux principaux de confiance du système.


## <a name="examples"></a>Exemples  
 L’exemple suivant modifie l’emplacement d’une source de données existante ainsi que l’emplacement de son gestionnaire de ressources.

```  
ALTER EXTERNAL DATA SOURCE hadoop_eds SET
     LOCATION = 'hdfs://10.10.10.10:8020',
     RESOURCE_MANAGER_LOCATION = '10.10.10.10:8032'
    ;
  
```

 L’exemple suivant modifie les informations d’identification permettant de se connecter à une source de données existante.

```  
ALTER EXTERNAL DATA SOURCE hadoop_eds SET
   CREDENTIAL = new_hadoop_user
    ;
```

 L’exemple suivant modifie les informations d’identification vers un nouvel emplacement. Cet exemple est une source de données externe créée pour Azure SQL Data Warehouse. 

```  
ALTER EXTERNAL DATA SOURCE AzureStorage_west SET
   LOCATION = 'wasbs://loadingdemodataset@updatedproductioncontainer.blob.core.windows.net',
   CREDENTIAL = AzureStorageCredential
```
