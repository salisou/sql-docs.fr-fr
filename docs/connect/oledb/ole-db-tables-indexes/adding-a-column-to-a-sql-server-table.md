---
title: Ajout d'une colonne à une table SQL Server | Microsoft Docs
description: Ajout d’une colonne à une table SQL Server à l’aide d’OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- AddColumn function
- OLE DB Driver for SQL Server, columns
- adding columns
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 2c6cd539e499f80342a30371d047c9870c4fda08
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67994103"
---
# <a name="adding-a-column-to-a-sql-server-table"></a>Ajout d'une colonne à une table SQL Server.
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver pour SQL Server expose la fonction **ITableDefinition::AddColumn**. Cela permet aux consommateurs d’ajouter une colonne à une table [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Lorsque vous ajoutez une colonne à une table [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], le consommateur OLE DB Driver pour SQL Server est contraint comme suit :  
  
-   Si DBPROP_COL_AUTOINCREMENT est VARIANT_TRUE, DBPROP_COL_NULLABLE doit être VARIANT_FALSE.  
  
-   Si la colonne est définie en utilisant le type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **timestamp**, DBPROP_COL_NULLABLE doit être VARIANT_FALSE.  
  
-   Pour toute autre définition de colonne, DBPROP_COL_NULLABLE doit être VARIANT_TRUE.  
  
 Les consommateurs spécifient le nom de table en tant que chaîne de caractères Unicode dans le membre *pwszName* de l’union *uName* dans le paramètre *pTableID*. Le membre *eKind* de *pTableID* doit être DBKIND_NAME.  
  
 Le nouveau nom de colonne est spécifié en tant que chaîne de caractères Unicode dans le membre *pwszName* de l’union *uName* dans le membre *dbcid* du paramètre DBCOLUMNDESC *pColumnDesc*. Le membre *eKind* doit être DBKIND_NAME.  
  
## <a name="see-also"></a>Voir aussi  
 [Tables et index](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md)  
  
  
