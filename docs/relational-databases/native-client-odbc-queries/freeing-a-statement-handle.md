---
title: Libération d’un descripteur d’instruction | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- reusing statement handles
- freeing statement handles
- statements [ODBC], statement handles
- SQLFreeStmt function
- ODBC applications, statements
- statement handles [ODBC]
ms.assetid: 96fdff84-0ca7-460a-a240-94ee826ea41c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7e954773f85afc434d1e5bd18f7ffb76e28a1438
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81297891"
---
# <a name="freeing-a-statement-handle"></a>Libération d'un descripteur d'instruction
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il est plus efficace de réutiliser des descripteurs d'instruction que de les supprimer et d'en allouer de nouveaux. Avant d'exécuter une nouvelle instruction SQL sur un descripteur d'instruction, les applications doivent s'assurer que les paramètres de l'instruction actuelle sont appropriés. Cela inclut les attributs d'instruction, les liaisons de paramètres et les liaisons de jeux de résultats. En règle générale, les paramètres et les jeux de résultats de l’ancienne instruction SQL doivent être détachés en appelant [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) avec les options SQL_RESET_PARAMS et SQL_UNBIND, puis reliés pour la nouvelle instruction SQL.  
  
 Lorsque l’application a terminé d’utiliser l’instruction, elle appelle [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) pour libérer l’instruction. Notez que **SQLDisconnect** libère automatiquement toutes les instructions sur une connexion.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de requêtes &#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
