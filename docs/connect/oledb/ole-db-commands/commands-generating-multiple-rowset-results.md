---
title: Commandes générant des résultats dans plusieurs ensembles de lignes | Microsoft Docs
description: Commandes générant des résultats dans plusieurs ensembles de lignes
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- OLE DB Driver for SQL Server, commands
- OLE DB Driver for SQL Server, multiple rowsets
- commands [OLE DB]
- multiple-rowset results
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 5374e1ccd1024993369091b431a025676bccf1f0
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "68016058"
---
# <a name="commands-generating-multiple-rowset-results"></a>Commandes générant des résultats dans plusieurs ensembles de lignes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver pour SQL Server peut retourner plusieurs ensembles de lignes à partir d'instructions [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les instructions [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] retournent des résultats dans plusieurs ensembles de lignes dans les conditions suivantes :  
  
-   des instructions SQL groupées sont soumises en tant que commande unique ;  
  
-   des procédures stockées implémentent un lot d'instructions SQL ;  
  
## <a name="batches"></a>Lots  
 OLE DB Driver pour SQL Server reconnaît le point-virgule comme un séparateur de lot pour les instructions SQL :  
  
```  
WCHAR*       wSQLString = L"SELECT * FROM Categories; "  
                          L"SELECT * FROM Products";  
```  
  
 Il est plus efficace d'envoyer plusieurs instructions SQL dans un lot que d'exécuter chaque instruction SQL séparément. L'envoi d'un lot réduit les allers-retours sur le réseau entre le client et le serveur.  
  
## <a name="stored-procedures"></a>Procédures stockées  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] retourne un jeu de résultats pour chaque instruction dans une procédure stockée ; ainsi, la plupart des procédures stockées [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] retournent plusieurs jeux de résultats.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Utilisation d’IMultipleResults pour traiter plusieurs jeux de résultats](../../oledb/ole-db-commands/using-imultipleresults-to-process-multiple-result-sets.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes](../../oledb/ole-db-commands/commands.md)  
  
  
