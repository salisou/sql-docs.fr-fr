---
title: Key, objet (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Key
helpviewer_keywords:
- Key object [ADOX]
ms.assetid: 55f116fe-4d56-4892-bffe-0cdd6fc727c9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f7e405cfdde86a4f19590a87035ff574e1d255c9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67965905"
---
# <a name="key-object-adox"></a>Key, objet (ADOX)
Représente un champ clé primaire, étrangère ou unique d’une table de base de données.  
  
## <a name="remarks"></a>Notes  
 Le code suivant crée une nouvelle **clé**:  
  
```  
Dim obj As New Key  
```  
  
 Avec les propriétés et les collections d’un objet **clé** , vous pouvez :  
  
-   Identifiez la clé avec la propriété [Name](../../../ado/reference/adox-api/name-property-adox.md) .  
  
-   Déterminez si la clé est primaire, étrangère ou unique avec la propriété [type](../../../ado/reference/adox-api/type-property-key-adox.md) .  
  
-   Accédez aux colonnes de base de données de la clé avec la collection [Columns](../../../ado/reference/adox-api/columns-collection-adox.md) .  
  
-   Spécifiez le nom de la table associée à l’aide de la propriété [RelatedTable](../../../ado/reference/adox-api/relatedtable-property-adox.md) .  
  
-   Déterminez l’action effectuée lors de la suppression ou de la mise à jour d’une clé primaire avec les propriétés [DeleteRule](../../../ado/reference/adox-api/deleterule-property-adox.md) et [UpdateRule](../../../ado/reference/adox-api/updaterule-property-adox.md) .  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de l’objet Key](../../../ado/reference/adox-api/key-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes Append des clés, type de clé, RelatedColumn, RelatedTable et UpdateRule, exemple de propriétés (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Columns, collection (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Keys, collection (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)
