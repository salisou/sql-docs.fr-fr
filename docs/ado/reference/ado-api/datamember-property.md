---
title: DataMember, propriété | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::DataMember
helpviewer_keywords:
- DataMember property
ms.assetid: 2c8fb09e-10ad-49b5-ab41-2603771780d9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 623f9b1f1e8873ddc4819bb8500c11edf09f5f76
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67919219"
---
# <a name="datamember-property"></a>DataMember, propriété
Indique le nom du membre de données qui sera récupéré à partir du [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) référencé par la propriété [DataSource](../../../ado/reference/ado-api/datasource-property-ado.md) .  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur de **chaîne** . Ce nom ne respecte pas la casse.  
  
## <a name="remarks"></a>Notes  
 Cette propriété est utilisée pour créer des contrôles liés aux données avec l’environnement de données. L’environnement de données conserve des collections de données (sources de données) contenant des objets nommés (membres de données) qui seront représentés sous la forme d’un objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
 Les propriétés **DataMember** et **DataSource** doivent être utilisées ensemble.  
  
 La propriété **DataMember** détermine l’objet spécifié par la propriété **DataSource** qui est représenté sous la forme d’un objet **Recordset** . L’objet **Recordset** doit être fermé avant que cette propriété soit définie. Une erreur est générée si la propriété **DataMember** n’est pas définie avant la propriété **DataSource** , ou si le nom **DataMember** n’est pas reconnu par l’objet spécifié dans la propriété **DataSource** .  
  
## <a name="usage"></a>Usage  
  
```  
Dim rs as New ADODB.Recordset  
rs.DataMember = "Command"     'Name of the rowset to bind to  
Set rs.DataSource = myDE      'Name of the object containing an IRowset  
```  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DataSource, propriété (ADO)](../../../ado/reference/ado-api/datasource-property-ado.md)
