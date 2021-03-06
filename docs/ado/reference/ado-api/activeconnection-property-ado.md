---
title: ActiveConnection, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::ActiveConnection
- Recordset15::get_ActiveConnection
- _Record::ActiveConnection
helpviewer_keywords:
- ActiveConnection property [ADO]
ms.assetid: 52d0a96c-14fb-4ad9-b004-4d821bc0a6db
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8dabf974e36b1f6beaff36f3a4888c128d7dfe1b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67921510"
---
# <a name="activeconnection-property-ado"></a>ActiveConnection, propriété (ADO)
Indique à quel objet de [connexion](../../../ado/reference/ado-api/connection-object-ado.md) la [commande](../../../ado/reference/ado-api/command-object-ado.md), le [jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md)ou l’objet d' [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) spécifiés appartiennent actuellement.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur de **chaîne** qui contient une définition pour une connexion si la connexion est fermée ou un **Variant** contenant l’objet de **connexion** actuel si la connexion est ouverte. La valeur par défaut est une référence d’objet null. Consultez la propriété [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) .  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **ActiveConnection** pour déterminer l’objet de **connexion** sur lequel l’objet de **commande** spécifié s’exécutera ou l’objet **Recordset** spécifié sera ouvert.  
  
## <a name="command"></a>Commande  
 Pour les objets de **commande** , la propriété **ActiveConnection** est en lecture/écriture.  
  
 Si vous tentez d’appeler la méthode [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) sur un objet **Command** avant de définir cette propriété sur un objet de **connexion** ouvert ou une chaîne de connexion valide, une erreur se produit.  
  
 Si un objet de **connexion** est affecté à la propriété **ActiveConnection** , l’objet doit être ouvert. L’attribution d’un objet de connexion fermé provoque une erreur.  
  
### <a name="note"></a>Remarque  
 **Visual Basic Microsoft** L’affectation de la valeur *Nothing* à la propriété **ActiveConnection** dissocie l’objet **Command** de la **connexion** actuelle et oblige le fournisseur à libérer toutes les ressources associées sur la source de données. Vous pouvez ensuite associer l’objet de **commande** à la même ou à un autre objet de **connexion** . Certains fournisseurs vous permettent de modifier le paramètre de propriété d’une **connexion** à une autre, sans devoir d’abord affecter la valeur *Nothing*à la propriété.  
  
 Si la collection [Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md) de l’objet **Command** contient des paramètres fournis par le fournisseur, la collection est effacée si vous définissez la propriété **ActiveConnection** sur *Nothing* ou sur un autre objet **Connection** . Si vous créez manuellement des objets de [paramètre](../../../ado/reference/ado-api/parameter-object.md) et que vous les utilisez pour remplir la collection de **paramètres** de l’objet de **commande** , la définition de la propriété **ActiveConnection** sur *Nothing* ou sur un autre objet de **connexion** laisse la collection **Parameters** intacte.  
  
 La fermeture de l’objet **Connection** auquel un objet **Command** est associé affecte à la propriété **ActiveConnection** la valeur *Nothing*. La définition de cette propriété sur un objet de **connexion** fermé génère une erreur.  
  
## <a name="recordset"></a>Ensemble d'enregistrements  
 Pour les objets **Recordset** ouverts ou pour les objets **Recordset** dont la propriété [source](../../../ado/reference/ado-api/source-property-ado-recordset.md) est définie sur un objet **Command** valide, la propriété **ActiveConnection** est en lecture seule. Dans le cas contraire, elle est en lecture/écriture.  
  
 Vous pouvez définir cette propriété sur un objet de **connexion** valide ou sur une chaîne de connexion valide. Dans ce cas, le fournisseur crée un objet de **connexion** à l’aide de cette définition et ouvre la connexion. En outre, le fournisseur peut définir cette propriété sur le nouvel objet de **connexion** pour vous permettre d’accéder à l’objet de **connexion** pour les informations d’erreur étendues ou d’exécuter d’autres commandes.  
  
 Si vous utilisez l’argument *ActiveConnection* de la méthode [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) pour ouvrir un objet **Recordset** , la propriété **ActiveConnection** hérite de la valeur de l’argument.  
  
 Si vous définissez la **propriété source** de l’objet **Recordset** sur une variable d’objet **Command** valide, la propriété **ActiveConnection** de l’objet **Recordset** hérite du paramètre de la propriété **ActiveConnection** de l’objet **Command** .  
  
> [!NOTE]
>  **Utilisation des services de données distants** Lorsqu’elle est utilisée sur un objet **Recordset** côté client, cette propriété ne peut être définie qu’à une chaîne de connexion ou (dans Microsoft Visual Basic ou Visual Basic, édition de scripts) à *Nothing*.  
  
## <a name="record"></a>Enregistrement  
 Cette propriété est en lecture/écriture lorsque l’objet **enregistrement** est fermé et peut contenir une chaîne de connexion ou une référence à un objet de **connexion** ouvert. Cette propriété est en lecture seule lorsque l’objet **enregistrement** est ouvert et contient une référence à un objet de **connexion** ouvert.  
  
 Un objet de **connexion** est créé implicitement lorsque l’objet **enregistrement** est ouvert à partir d’une URL. Ouvrez l' **enregistrement** avec un objet de **connexion** ouvert existant en affectant l’objet de **connexion** à cette propriété, ou en utilisant l’objet de **connexion** en tant que paramètre dans l’appel de la méthode [Open](../../../ado/reference/ado-api/open-method-ado-record.md) . Si l' **enregistrement** est ouvert à partir d' **un enregistrement** ou [d’un jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md)existant, il est automatiquement associé à cet **enregistrement** ou à l’objet de **connexion** de l’objet **Recordset** .  
  
> [!NOTE]
>  Les URL utilisant le schéma http appellera automatiquement le [fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Pour plus d’informations, consultez [URL absolues et relatives](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Record, objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [ActiveConnection, CommandText, CommandTimeout, CommandType, size et direction, exemple de propriétés (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, size et direction, exemple de propriétés (VC + +)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, size et direction, exemple de propriétés (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [Connection, objet (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [ConnectionString, propriété (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md)
