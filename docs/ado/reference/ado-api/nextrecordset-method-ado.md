---
title: NextRecordset, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- NextRecordset
- Recordset15::NextRecordset
- Recordset15::raw_NextRecordset
helpviewer_keywords:
- NextRecordset method [ADO]
ms.assetid: ab1fa449-a695-4987-b1ee-bc68f89418dd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3c7af4f5d217670ab23e71a3c53ccd5cf7944b0c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67932034"
---
# <a name="nextrecordset-method-ado"></a>NextRecordset, méthode (ADO)
Efface l’objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) actuel et retourne le **jeu d’enregistrements** suivant en progressant dans une série de commandes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set recordset2 = recordset1.NextRecordset(RecordsAffected )  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un objet **Recordset** . Dans le modèle de syntaxe, *Recordset1* et *Recordset2* peuvent être le même objet **Recordset** , ou vous pouvez utiliser des objets distincts. Lorsque vous utilisez des objets **Recordset** distincts, la réinitialisation de la propriété **ActiveConnection** sur l' **objet Recordset** d’origine (*Recordset1*) après l’appel de **NextRecordset** génère une erreur.  
  
#### <a name="parameters"></a>Paramètres  
 *RecordsAffected*  
 Facultatif. Variable de **type long** à laquelle le fournisseur retourne le nombre d’enregistrements affectés par l’opération en cours.  
  
> [!NOTE]
>  Ce paramètre retourne uniquement le nombre d’enregistrements affectés par une opération. elle ne retourne pas un nombre d’enregistrements à partir d’une instruction SELECT utilisée pour générer le **Recordset**.  
  
## <a name="remarks"></a>Notes  
 Utilisez la méthode **NextRecordset** pour retourner les résultats de la commande suivante dans une instruction de commande composée ou une procédure stockée qui retourne plusieurs résultats. Si vous ouvrez un objet **Recordset** basé sur une instruction de commande composée (par exemple, « \* SELECT FROM table1 ; SELECT \* from table2») à l’aide de la méthode [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) sur une [commande](../../../ado/reference/ado-api/command-object-ado.md) ou de la méthode [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) sur un **Recordset**, ADO exécute uniquement la première commande et retourne les résultats à *Recordset*. Pour accéder aux résultats des commandes suivantes dans l’instruction, appelez la méthode **NextRecordset** .  
  
 Tant qu’il existe des résultats supplémentaires et que le **jeu d’enregistrements** contenant les instructions composées n’est pas déconnecté ou marshalé entre les limites de processus, la méthode **NextRecordset** continue à retourner des objets **Recordset** . Si une commande de retour de ligne s’exécute correctement mais ne retourne aucun enregistrement, l’objet **Recordset** retourné est ouvert, mais vide. Pour tester ce cas, vérifiez que les propriétés [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) et [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) sont toutes les deux **vraies**. Si une commande qui ne retourne pas de lignes s’exécute correctement, l’objet **Recordset** retourné est fermé, ce que vous pouvez vérifier en testant la propriété [State](../../../ado/reference/ado-api/state-property-ado.md) sur le **Recordset**. Lorsqu’il n’y a plus de résultats, *Recordset* prend la valeur *Nothing*.  
  
 La méthode **NextRecordset** n’est pas disponible sur un objet **Recordset** déconnecté, où [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) a été défini sur **Nothing** (dans Microsoft Visual Basic) ou null (dans d’autres langues).  
  
 Si une modification est en cours alors qu’elle est en mode de mise à jour immédiate, l’appel de la méthode **NextRecordset** génère une erreur. appelez d’abord la méthode [Update](../../../ado/reference/ado-api/update-method.md) ou [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) .  
  
 Pour passer des paramètres pour plusieurs commandes dans l’instruction composée en remplissant la collection de [paramètres](../../../ado/reference/ado-api/parameters-collection-ado.md) , ou en passant un tableau avec l’appel d' **ouverture** ou d' **exécution** d’origine, les paramètres doivent être dans le même ordre dans la collection ou le tableau que leurs commandes respectives dans la série de commandes. Vous devez terminer la lecture de tous les résultats avant de lire les valeurs des paramètres de sortie.  
  
 Votre fournisseur de OLE DB détermine le moment où chaque commande dans une instruction composée est exécutée. Par exemple, le [fournisseur Microsoft OLE DB pour SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)exécute toutes les commandes d’un lot lors de la réception de l’instruction composée. Les **jeux d’enregistrements** résultants sont simplement retournés lorsque vous appelez **NextRecordset**.  
  
 Toutefois, d’autres fournisseurs peuvent exécuter la commande suivante dans une instruction uniquement après l’appel de NextRecordset. Pour ces fournisseurs, si vous fermez explicitement l’objet **Recordset avant d'** exécuter l’instruction de commande dans son intégralité, ADO n’exécute jamais les commandes restantes.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [NextRecordset, exemple de méthode (VB)](../../../ado/reference/ado-api/nextrecordset-method-example-vb.md)   
 [NextRecordset, exemple de méthode (VC++)](../../../ado/reference/ado-api/nextrecordset-method-example-vc.md)   
