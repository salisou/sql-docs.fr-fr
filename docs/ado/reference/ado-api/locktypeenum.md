---
title: LockTypeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- LockTypeEnum
helpviewer_keywords:
- LockTypeEnum enumeration [ADO]
ms.assetid: d2894eaf-4450-4ace-aa51-c8b875fd3010
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0ae822794b1b06a975e1cc3cd397b5a5f00036dc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67918254"
---
# <a name="locktypeenum"></a>LockTypeEnum
Spécifie le type de verrou placé sur les enregistrements lors de la modification.  
  
|Constant|Value|Description|  
|--------------|-----------|-----------------|  
|**adLockBatchOptimistic**|4|Indique les mises à jour optimistes par lot. Requis pour le mode de mise à jour par lot.|  
|**adLockOptimistic**|3|Indique un verrouillage optimiste, enregistrement par enregistrement. Le fournisseur utilise le verrouillage optimiste et le verrouillage des enregistrements uniquement lorsque vous appelez la méthode de [mise à jour](../../../ado/reference/ado-api/update-method.md) .|  
|**adLockPessimistic**|2|Indique le verrouillage pessimiste, enregistrement par enregistrement. Le fournisseur effectue ce qui est nécessaire pour garantir la réussite de la modification des enregistrements, en généralement en verrouillant les enregistrements au niveau de la source de données immédiatement après la modification.|  
|**adLockReadOnly**|1|Indique des enregistrements en lecture seule. Vous ne pouvez pas modifier les données.|  
|**adLockUnspecified**|-1|Ne spécifie pas de type de verrou. Pour les clones, le clone est créé avec le même type de verrou que l’original.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums.LockType.BATCHOPTIMISTIC|  
|AdoEnums.LockType.OPTIMISTIC|  
|AdoEnums.LockType.PESSIMISTIC|  
|AdoEnums.LockType.READONLY|  
|AdoEnums.LockType.UNSPECIFIED|  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Clone, méthode (ADO)](../../../ado/reference/ado-api/clone-method-ado.md)|[LockType, propriété (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)|  
|[Open, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[WillExecute, événement (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|
