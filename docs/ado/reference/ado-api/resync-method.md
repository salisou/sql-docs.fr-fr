---
title: Resync, méthode | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::raw_Resync
- Fields::Resync
- Recordset20::Resync
- Fields::raw_Resync
helpviewer_keywords:
- Resync method [ADO]
ms.assetid: 73b355d4-a4c0-434b-bfc4-039b1c76b32e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7e2f83a3637af8f0e89c4125d3207c8c54b86763
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917159"
---
# <a name="resync-method"></a>Resync, méthode
Actualise les données de la base de données sous-jacente de l’objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) actuel ou de la collection [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) d’un objet [Record](../../../ado/reference/ado-api/record-object-ado.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Recordset.Resync AffectRecords, ResyncValues Record.Fields.Resync ResyncValues  
```  
  
#### <a name="parameters"></a>Paramètres  
 *AffectRecords*  
 Facultatif. Valeur [AffectEnum](../../../ado/reference/ado-api/affectenum.md) qui détermine le nombre d’enregistrements affectés par la méthode **Resync** . La valeur par défaut est **adAffectAll**. Cette valeur n’est pas disponible avec la méthode **Resync** de la collection **Fields** d’un objet **Record** .  
  
 *ResyncValues*  
 Facultatif. Valeur de [ResyncEnum](../../../ado/reference/ado-api/resyncenum.md) qui spécifie si les valeurs sous-jacentes sont remplacées. La valeur par défaut est **adResyncAllValues**.  
  
## <a name="remarks"></a>Notes  
  
## <a name="recordset"></a>Ensemble d'enregistrements  
 Utilisez la méthode **Resync** pour resynchroniser les enregistrements dans le **jeu d'** enregistrements actuel avec la base de données sous-jacente. Cela est utile si vous utilisez un curseur statique ou avant uniquement, mais que vous souhaitez voir toutes les modifications apportées à la base de données sous-jacente.  
  
 Si vous définissez la propriété [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) sur **adUseClient**, **Resync** n’est disponible que pour les objets **Recordset** qui ne sont pas en lecture seule.  
  
 Contrairement à la méthode [Requery](../../../ado/reference/ado-api/requery-method.md) , la méthode **Resync** ne réexécute pas la commande sous-jacente de l’objet **Recordset** . Les nouveaux enregistrements de la base de données sous-jacente ne seront pas visibles.  
  
 Si la tentative de resynchronisation échoue en raison d’un conflit avec les données sous-jacentes (par exemple, un enregistrement a été supprimé par un autre utilisateur), le fournisseur renvoie des avertissements à la collection d' [Erreurs](../../../ado/reference/ado-api/errors-collection-ado.md) et une erreur d’exécution se produit. Utilisez la propriété [Filter](../../../ado/reference/ado-api/filter-property.md) (**adFilterConflictingRecords**) et la propriété [Status](../../../ado/reference/ado-api/status-property-ado-recordset.md) pour localiser les enregistrements avec conflits.  
  
 Si les propriétés dynamiques de la [table unique](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) et de la [commande Resync](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md) sont définies et que le **jeu d’enregistrements** est le résultat de l’exécution d’une opération de jointure sur plusieurs tables, la méthode **Resync** exécute la commande spécifiée dans la propriété **Resync Command** uniquement sur la table nommée dans la propriété de **table unique** .  
  
## <a name="fields"></a>Champs  
 Utilisez la méthode **Resync** pour resynchroniser les valeurs de la collection **Fields** d’un objet **Record** avec la source de données sous-jacente. La propriété [Count](../../../ado/reference/ado-api/count-property-ado.md) n’est pas affectée par cette méthode.  
  
 Si *ResyncValues* est défini sur **adResyncAllValues** (valeur par défaut), les propriétés [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md), [value](../../../ado/reference/ado-api/value-property-ado.md)et [OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) des objets [Field](../../../ado/reference/ado-api/field-object.md) de la collection sont synchronisées. Si *ResyncValues* a la valeur **adResyncUnderlyingValues**, seule la propriété **UnderlyingValue** est synchronisée.  
  
 La valeur de la propriété **Status** pour chaque objet **Field** au moment de l’appel affecte également le comportement de **Resync**. Pour les objets de **champ** qui ont des valeurs d' **État** **adFieldPendingUnknown** ou **adFieldPendingInsert**, la **resynchronisation** n’a aucun effet. Pour les valeurs d' **État** de **adFieldPendingChange** ou **adFieldPendingDelete**, **Resync** synchronise les valeurs de données pour les champs qui existent toujours au niveau de la source de données.  
  
 La **resynchronisation** ne modifiera pas les valeurs d' **État** des objets **Field** à moins qu’une erreur ne se produise lors de l’appel de **Resync** . Par exemple, si le champ n’existe plus, le fournisseur retourne une valeur d' **État** appropriée pour l’objet de **champ** , par exemple **adFieldDoesNotExist**. Les valeurs d' **État** retournées peuvent être combinées logiquement dans la valeur de la propriété **Status** .  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Fields, collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|[Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Resync, exemple de méthode (VB)](../../../ado/reference/ado-api/resync-method-example-vb.md)   
 [Resync, exemple de méthode (VC + +)](../../../ado/reference/ado-api/resync-method-example-vc.md)   
 [Clear, méthode (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [UnderlyingValue, propriété](../../../ado/reference/ado-api/underlyingvalue-property.md)
