---
title: Compatibilité entre les versions | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), cross-version compatibility
ms.assetid: 5f14850b-b85c-41e2-8116-6f5b3f5e0856
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7990072ac539addf733720fd8c1eaba0652f5d70
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304506"
---
# <a name="cross-version-compatibility"></a>Compatibilité des versions
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les conflits de version peuvent se produire lorsque les instances client ou serveur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] sont censées traiter les paramètres table.  
  
 En général, les fonctionnalités des paramètres table ne sont accessibles qu'aux clients [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (avec SQL Server Native Client 10.0) ou version ultérieure connectés aux serveurs [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (ou version ultérieure). Les nouvelles colonnes des jeux de résultats de la fonction catalogue ne sont présentes qu' [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] en cas de connexion à un serveur (ou version ultérieure).  
  
 Si une application cliente compilée avec une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client exécute des instructions qui attendent des paramètres table, le serveur détecte cette situation via une erreur de conversion de données, et ODBC retourne celle-ci comme SQLSTATE 07006, avec le message « Violation de l'attribut de type de données restreint ».  
  
 Si une application cliente qui a été [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compilée avec Native Client 10,0 ou une version ultérieure tente d’utiliser des paramètres table quand elle est connectée à une instance de serveur antérieure à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client détecte cela, et les appels SQLBindCol, SQLBindParameter, SQLSetDescFields et SQLSetDescRec échouent avec SQLSTATE 07006 et le message «violation de l’attribut de type de données restreint (la version de SQL Server pour cette connexion ne prend  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
