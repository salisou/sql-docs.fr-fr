---
title: Objets de la source de données (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], data source objects
- SQL Server Native Client, data source objects
- SQLNCLI, data source objects
- SQL Server Native Client OLE DB provider, data source objects
- OLE DB data source objects [SQL Server Native Client]
- data source objects [OLE DB]
- CLSID
ms.assetid: c1d4ed20-ad3b-4e33-a26b-38d7517237b7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6b602695720e0d6567e44e4fbe8fd06b6d496a6e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63130599"
---
# <a name="data-source-objects-ole-db"></a>Objets source de données (OLE DB)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client utilise le terme source de données pour l’ensemble des interfaces de OLE DB utilisées pour établir un lien vers un magasin de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], tel que. La création d’une instance de l’objet source de données du fournisseur est la première tâche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’un consommateur Native Client.  
  
 Chaque fournisseur OLE DB déclare un identificateur de classe (CLSID) pour lui-même. Le CLSID du fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB Native Client est le GUID C/C++ CLSID_SQLNCLI10 (le symbole SQLNCLI_CLSID sera résolu en ProgID correct dans le fichier sqlncli. h que vous référencez). Avec le CLSID, le consommateur utilise la fonction OLE **CoCreateInstance** pour fabriquer une instance de l’objet source de données.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client est un serveur in-process. Les instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des objets Native Client OLE DB fournisseur sont créées à l’aide de la macro CLSCTX_INPROC_SERVER pour indiquer le contexte de l’exécutable.  
  
 L' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objet de source de données du fournisseur OLE DB Native Client expose les interfaces d’initialisation OLE DB qui permettent au consommateur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se connecter aux bases de données existantes.  
  
 Chaque connexion effectuée via le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client définit automatiquement ces options :  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 Cet exemple utilise la macro d’identificateur de classe pour créer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un objet Native Client OLE DB fournisseur de source de données et obtenir une référence à son interface **IDBInitialize** .  
  
```  
IDBInitialize*   pIDBInitialize;  
HRESULT          hr;  
  
hr = CoCreateInstance(CLSID_SQLNCLI10, NULL, CLSCTX_INPROC_SERVER,  
    IID_IDBInitialize, (void**) &pIDBInitialize);  
  
if (SUCCEEDED(hr))  
{  
    //  Perform necessary processing with the interface.  
    pIDBInitialize->Uninitialize();  
    pIDBInitialize->Release();  
}  
else  
{  
    // Display error from CoCreateInstance.  
}  
```  
  
 Avec la réussite de la création d’une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance d’un objet Native Client OLE DB fournisseur de source de données, l’application consommateur peut continuer en initialisant la source de données et en créant des sessions. Les sessions OLE DB présentent des interfaces qui permettent d'accéder à des données et de les manipuler.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client établit sa première connexion à une instance spécifiée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de dans le cadre de l’initialisation réussie de la source de données. La connexion est maintenue tant qu’une référence est conservée dans toutes les interfaces d’initialisation de source de données, ou jusqu’à l’appel de la méthode **IDBInitialize::Uninitialize**.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Propriétés de la source de données &#40;OLE DB&#41;](data-source-properties-ole-db.md)  
  
-   [Propriétés des informations de la source de données](data-source-information-properties.md)  
  
-   [Propriétés d'initialisation et d'autorisation](initialization-and-authorization-properties.md)  
  
-   [Sessions](sessions.md)  
  
-   [Propriétés de session](session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [Objets source de données persistants](persisted-data-source-objects.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
