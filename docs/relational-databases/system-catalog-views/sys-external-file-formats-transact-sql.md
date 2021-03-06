---
title: sys. external_file_formats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a89efb2c-0a3a-4b64-9284-6e93263e29ac
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: eae119fe16b916f47f1acdcd2ebe15efd96e51e9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68048391"
---
# <a name="sysexternal_file_formats-transact-sql"></a>sys. external_file_formats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Contient une ligne pour chaque format de fichier externe de la base de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]données [!INCLUDE[ssSDS](../../includes/sssds-md.md)]active pour [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], et.  
  
 Contient une ligne pour chaque format de fichier externe sur le serveur [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]pour.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|file_format_id|**int**|ID d’objet pour le format de fichier externe.||  
|name|**sysname**|Nom du format de fichier. dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], cela est unique pour la base de données. Dans [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], il est unique pour le serveur.||  
|format_type|**tinyint**|Type de format de fichier.|DELIMITEDTEXT, RCFILE, ORC, PARQUET|  
|field_terminator|**nvarchar(10**|Pour format_type = DELIMITEDTEXT, il s’agit de l’indicateur de fin de champ.||  
|string_delimiter|**nvarchar(10**|Pour format_type = DELIMITEDTEXT, il s’agit du délimiteur de chaîne.||  
|date_format|**nvarchar(50)**|Pour format_type = DELIMITEDTEXT, il s’agit du format de date et d’heure défini par l’utilisateur.||  
|use_type_default|**bit**|Pour format_type = texte délimité, spécifie comment gérer les valeurs manquantes lorsque Polybase importe des données à partir de fichiers [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]texte HDFS dans.|0-stocker les valeurs manquantes en tant que chaîne « NULL ».<br /><br /> 1-stocker les valeurs manquantes en tant que valeur par défaut de la colonne.|  
|serde_method|**nvarchar(255)**|Pour format_type = RCFILE, il s’agit de la méthode de sérialisation/désérialisation.||  
|row_terminator|**nvarchar(10**|Pour format_type = DELIMITEDTEXT, il s’agit de la chaîne de caractères qui termine chaque ligne dans le fichier Hadoop externe.|Toujours' \n'.|  
|encodage|**nvarchar(10**|Pour format_type = DELIMITEDTEXT, il s’agit de la méthode d’encodage pour le fichier Hadoop externe.|Toujours’UTF8 '.|  
|data_compression|**nvarchar(255)**|Méthode de compression des données pour les données externes.|Pour format_type = DELIMITEDTEXT :<br /><br /> -'org. Apache. Hadoop. IO. compress. DefaultCodec'<br />-'org. Apache. Hadoop. IO. compress. GzipCodec'<br /><br /> Pour format_type = RCFILE :<br /><br /> -'org. Apache. Hadoop. IO. compress. DefaultCodec'<br /><br /> Pour format_type = ORC :<br /><br /> -'org. Apache. Hadoop. IO. compress. DefaultCodec'<br />-'org. Apache. Hadoop. IO. compress. SnappyCodec'<br /><br /> Pour format_type = PARQUET :<br /><br /> -'org. Apache. Hadoop. IO. compress. GzipCodec'<br />-'org. Apache. Hadoop. IO. compress. SnappyCodec'|  
  
## <a name="permissions"></a>Autorisations  
 La visibilité des métadonnées dans les affichages catalogue est limitée aux éléments sécurisables qu'un utilisateur détient ou pour lesquels des autorisations lui ont été accordées.  Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [sys. external_data_sources &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)   
 [sys. external_tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-tables-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)  
  
  
