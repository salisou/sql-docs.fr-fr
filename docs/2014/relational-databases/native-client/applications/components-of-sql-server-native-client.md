---
title: Composants de SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], components
- components [SQL Server Native Client]
- SQLNCLI, about SQL Server Native Client
ms.assetid: 65f932d5-daa1-4eff-b6df-ee633fcf2a7c
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cef49e2df4a6e15784bcad28f8f8619aa5625367
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37410424"
---
# <a name="components-of-sql-server-native-client"></a>Composants de SQL Server Native Client
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client contient les composants suivants :  
  
|Composant|Description|  
|---------------|-----------------|  
|sqlncli11.dll|Fichier DDL (Dynamic-Link Library) contenant l'ensemble des fonctionnalités [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Sont inclus le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client et le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|sqlnclir11.rll|Fichier de ressources d'accompagnement pour la bibliothèque [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|s10ch_sqlncli.chm|Fichier d'aide de l'Assistant Source de données qui explique comment créer une source de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l'aide du pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ou du fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|sqlncli.h|En-tête de fichier [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client contenant toutes les nouvelles définitions nécessaires pour pouvoir utiliser [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Ce fichier d'en-tête remplace les fichiers odbcss.h et sqloledb.h. **Remarque :** vous ne pouvez pas référencer sqlncli.h et odbcss.h dans le même programme, mais vous pouvez référencer sqlncli.h et sqloledb.h dans même programme tant que sqloledb.h soit défini en premier.|  
|sqlncli11.lib|Le fichier bibliothèque nécessaire pour appeler directement la **bcp** fonctions utilitaires qui font partie de la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client. **Remarque :** si vous référencez le fichier sqlncli11.lib dans votre code de programmation, vous devez vous assurer que le fichier sqlncli11.dll est dans votre chemin système et dans le chemin d’accès système des utilisateurs qui emploient votre application.|  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’applications avec SQL Server Native Client](building-applications-with-sql-server-native-client.md)  
  
  