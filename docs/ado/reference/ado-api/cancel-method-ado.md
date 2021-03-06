---
title: Cancel, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::Cancel
- _Record::Cancel
- _Connection::Cancel
- Command25::Cancel
- _Stream::Cancel
helpviewer_keywords:
- Cancel method [ADO]
ms.assetid: e0db4e15-6787-41e2-8f13-9e9b524d620a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: db369b32737c0e2dae4603a4a5a6c26cdd3a7142
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67920236"
---
# <a name="cancel-method-ado"></a>Cancel, méthode (ADO)
Annule l’exécution d’un appel de méthode asynchrone en attente.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.Cancel  
```  
  
## <a name="remarks"></a>Notes  
 Utilisez la méthode **Cancel** pour terminer l’exécution d’un appel de méthode asynchrone : autrement dit, une méthode appelée avec l’option **adAsyncConnect**, **adAsyncExecute**ou **adAsyncFetch** .  
  
 Le tableau suivant indique la tâche qui se termine lorsque vous utilisez la méthode **Cancel** sur un type particulier d’objet.  
  
|Si l' *objet* est un|Le dernier appel asynchrone à cette méthode est terminé|  
|----------------------|-------------------------------------------------------------|  
|[Commande](../../../ado/reference/ado-api/command-object-ado.md)|[Effectue](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[Connection](../../../ado/reference/ado-api/connection-object-ado.md)|[Exécuter](../../../ado/reference/ado-api/execute-method-ado-connection.md) ou [ouvrir](../../../ado/reference/ado-api/open-method-ado-connection.md)|  
|[Enregistrement](../../../ado/reference/ado-api/record-object-ado.md)|[CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md), [DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md), [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md)ou [Open](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)|[Ouvrir](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[STREAM](../../../ado/reference/ado-api/stream-object-ado.md)|[Ouvrir](../../../ado/reference/ado-api/open-method-ado-stream.md)|  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Connection, objet (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Record, objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)||  
  
## <a name="see-also"></a>Voir aussi  
 [Cancel, exemple de méthode (VB)](../../../ado/reference/ado-api/cancel-method-example-vb.md)   
 [Cancel, exemple de méthode (VBScript)](../../../ado/reference/rds-api/cancel-method-example-vbscript.md)   
 [Cancel, exemple de méthode (VC + +)](../../../ado/reference/ado-api/cancel-method-example-vc.md)   
 [Cancel, méthode (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [Méthode CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [CancelUpdate, méthode (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [CancelUpdate, méthode (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Execute, méthode (commande ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)   
 [Execute, méthode (connexion ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [Open, méthode (connexion ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)
