---
title: Améliorations des types de données de date et d’heure (OLE DB)
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB]
- OLE DB, date/time improvements
ms.assetid: 71614aaf-0fa4-4fe0-b522-68e2e0b66f43
author: markingmyname
ms.author: maghan
ms.custom: seo-dt-2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7dadb038bcb77ee13abdbead023aed164cbe2a8b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306120"
---
# <a name="date-and-time-improvements-ole-db"></a>Améliorations des types de données de date et d’heure (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] introduit de nouveaux types de données de date et d'heure. Cette section décrit comment ces nouveaux types sont exposés en tant qu' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] extensions dans Native Client. Pour obtenir une vue d' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ensemble de la prise en charge native client pour les nouveaux types de données de date et d’heure, consultez améliorations de la [date et](../../relational-databases/native-client/features/date-and-time-improvements.md)de l’heure. Pour obtenir un exemple, voir [Utiliser les fonctionnalités de date et d’heure améliorées &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md).  
  
 Pour plus d'informations sur les types de données de date et d'heure, consultez [datetime &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime-transact-sql.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en charge des types de données pour les améliorations de date et d’heure OLE DB](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
 Fournit des informations sur les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types OLE DB (Native Client) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui prennent en charge les types de données de date et d’heure.  
  
 [Métadonnées &#40;OLE DB&#41;](https://msdn.microsoft.com/library/605e3be5-aeea-4573-9847-b866ed3c8bff)  
 Contient des informations sur la structure DBBINDING, **ICommandWithParameters::GetParameterInfo**, **ICommandWithParameters::SetParameterInfo**, **IColumnsRowset::GetColumnsRowset** et I**ColumnsInfo::GetColumnInfo**. Contient aussi des informations sur les mises à jour des ensembles de lignes de schéma OLE DB.  
  
 [Liaisons et conversions &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/conversions-ole-db.md)  
 Décrit les règles de conversion entre le serveur et le client pour les types date nouveaux et existants.  
  
 [Modifications de copie en bloc pour les types de date et d’heure améliorés &#40;OLE DB et ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 Décrit les améliorations des types date/time pour prendre en charge les opérations de copie en bloc.  
  
 [Prise en charge des API OLE DB pour les améliorations de date et d’heure](../../relational-databases/native-client-ole-db-date-time/ole-db-api-support-for-date-and-time-enhancements.md)  
 Décrit les API OLE DB qui prennent en charge les fonctionnalités améliorées des types date/time.  
  
 [Comparabilité pour IRowsetFind](../../relational-databases/native-client-ole-db-date-time/comparability-for-irowsetfind.md)  
 Décrit les types date/time et **IRowsetFind**.  
  
 [Nouvelles fonctionnalités de date et d’heure avec des versions antérieures de SQL Server &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/new-date-and-time-features-with-previous-sql-server-versions-ole-db.md)  
 Décrit le comportement attendu lorsqu'une application cliente qui utilise les fonctionnalités améliorées des types date et time communique avec une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], et lorsqu'un client compilé avec une version précédente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client envoie des commandes à un serveur qui prend en charge les fonctionnalités améliorées des types date et time.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
