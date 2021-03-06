---
title: Codes de retour | Microsoft Docs
description: Codes de retour
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB error handling, return codes
- OLE DB Driver for SQL Server, errors
- failed function [OLE DB]
- successful function [OLE DB]
- S_FALSE
- IS_ERROR macro
- DB_S_ERRORSOCCURRED return
- return codes [OLE DB]
- S_OK
- FAILED macro
- errors [OLE DB], return codes
author: pmasl
ms.author: pelopes
ms.openlocfilehash: a1deedd8903f69268ebc5e7f5caafaa79a7f7b18
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67994928"
---
# <a name="return-codes"></a>Codes de retour
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Au niveau le plus élémentaire, une fonction membre réussit ou échoue. À un niveau plus précis, une fonction peut réussir, mais son succès peut ne pas être ce que le développeur d'applications prévoyait.  
  
 Pour plus d’informations sur les codes de retour OLE DB, consultez [Codes de retour (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631).  
  
 Lorsqu'une fonction membre OLE DB Driver pour SQL Server retourne S_OK, la fonction a réussi.  
  
 Quand une fonction membre du pilote OLE DB pour SQL Server ne retourne pas S_OK, les macros OLE/COM FAILED et IS_ERROR de décompactage de HRESULT peuvent déterminer le succès ou l’échec global d’une fonction.  
  
 Si FAILED ou IS_ERROR retourne la valeur TRUE, le consommateur du pilote OLE DB pour SQL Server a l’information selon laquelle l’exécution de la fonction membre a échoué. Si FAILED ou IS_ERROR retourne FALSE et que HRESULT n'est pas égal à S_OK, le consommateur OLE DB Driver pour SQL Server est assuré que la fonction a réussi d'une façon ou d'une autre. Le consommateur peut extraire des informations détaillées sur ce retour « réussite avec informations » à partir des interfaces d’erreur du pilote OLE DB pour SQL Server. De même, dans le cas où une fonction échoue clairement (la macro FAILED retourne TRUE), les informations d’erreur étendues sont disponibles via les interfaces d’erreur du pilote OLE DB pour SQL Server.  
  
 Les consommateurs OLE DB Driver pour SQL Server rencontrent généralement le retour HRESULT de DB_S_ERRORSOCCURRED « réussi avec informations ». En général, les fonctions membres qui retournent DB_S_ERRORSOCCURRED définissent un ou plusieurs paramètres qui remettent les valeurs d'état au consommateur. Il est possible que le consommateur ne dispose d’aucune information d’erreur autre que celle retournée dans les paramètres état-valeur : les consommateurs doivent donc implémenter la logique d’application nécessaire pour extraire les valeurs d’état quand elles sont disponibles.  
  
 Les fonctions membres OLE DB Driver pour SQL Server ne retournent pas le code de réussite S_FALSE. Toutes les fonctions membres OLE DB Driver pour SQL Server retournent toujours S_OK pour indiquer le succès.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs](../../oledb/ole-db-errors/errors.md)  
  
  
