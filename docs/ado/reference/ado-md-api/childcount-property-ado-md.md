---
title: Propriété ChildCount (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ChildCount
- Member::ChildCount
helpviewer_keywords:
- ChildCount property [ADO MD]
ms.assetid: 5463be22-ca50-43ea-9c92-468fc8eda280
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a8e6f6a7cb749ff2b22a1f7563b43ce07e060aab
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67911553"
---
# <a name="childcount-property-ado-md"></a>ChildCount, propriété (ADO MD)
Indique le nombre de membres pour lesquels l’objet [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md) actuel est le parent dans une hiérarchie.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un entier **long** et est en lecture seule.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **ChildCount** pour retourner une estimation du nombre d’enfants d’un **membre** . Les enfants réels d’un **membre** peuvent être retournés par la propriété [Children](../../../ado/reference/ado-md-api/children-property-ado-md.md) .  
  
 Pour les objets **membres** d’un objet [position](../../../ado/reference/ado-md-api/position-object-ado-md.md) , le nombre maximal retourné est 65536. Si le nombre réel d’enfants dépasse 65536, la valeur retournée sera toujours 65536. Par conséquent, l’application doit interpréter un **ChildCount** de 65536 en tant que supérieur ou égal à 65536 enfants.  
  
 Pour les objets **membres** d’un objet [Level](../../../ado/reference/ado-md-api/level-object-ado-md.md) , utilisez la propriété ADO collection [Count](../../../ado/reference/ado-api/count-property-ado.md) sur la collection **Children** pour déterminer le nombre exact d’enfants. La détermination du nombre exact d’enfants peut être lente si le nombre d’enfants dans la collection est important.  
  
## <a name="applies-to"></a>S'applique à  
 [Member, objet (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Propriété Children (ADO MD)](../../../ado/reference/ado-md-api/children-property-ado-md.md)   
 [Count, propriété (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Members, collection (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)
