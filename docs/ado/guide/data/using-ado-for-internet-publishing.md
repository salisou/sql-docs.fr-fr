---
title: Utilisation d’ADO pour la publication Internet | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, Internet publishing
- publishing to Internet [ADO]
- Internet publishing [ADO]
- urls [ADO]
ms.assetid: d399fce4-b70b-418f-8110-3deb3448863c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: decbc7c3b377234d91fe6b3e662d9449298041c1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67923616"
---
# <a name="using-ado-for-internet-publishing"></a>Utilisation d’ADO pour la publication Internet
[Le fournisseur OLE DB pour la publication Internet](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md) montre un exemple spécifique d’accès à des données hétérogènes avec ADO. Bien que les exemples de cette section soient spécifiques à l’utilisation du fournisseur de publication Internet, les principes présentés doivent être similaires lorsque vous utilisez ADO avec d’autres fournisseurs pour des données hétérogènes, par exemple un fournisseur dans un magasin de messagerie électronique.  
  
## <a name="urls"></a>URLs  
 Les URL (Uniform Resource Locators) peuvent être utilisées comme alternative aux chaînes de connexion et texte de commande pour spécifier des sources de données et l’emplacement des fichiers et des répertoires. Vous pouvez utiliser des URL avec la [connexion](../../../ado/reference/ado-api/connection-object-ado.md) existante et les objets **Recordset** et avec les objets **Record** et **Stream** .  
  
 Pour plus d’informations sur l’utilisation des URL, consultez [URL absolues et relatives](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="record-fields"></a>Champs d’enregistrement  
 La différence entre les données hétérogènes et les données homogènes réside dans le fait que, pour la première, chaque ligne de données ou **enregistrement**peut avoir un ensemble différent de colonnes ou de **champs**. Pour les données homogènes, chaque ligne a le même ensemble de colonnes. Pour plus d’informations sur les champs spécifiques au fournisseur de publication Internet, consultez [enregistrements et champs supplémentaires fournis par le fournisseur](../../../ado/guide/data/records-and-provider-supplied-fields.md).  
  
### <a name="appending-new-fields"></a>Ajout de nouveaux champs  
 Plusieurs objets ADO ont été améliorés pour fonctionner conjointement avec les objets **Record** et **Stream** .  
  
-   La méthode [Append](../../../ado/reference/ado-api/append-method-ado.md) de la collection [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) , qui crée et ajoute un objet [Field](../../../ado/reference/ado-api/field-object.md) à la collection, peut également spécifier la valeur du **champ**.  
  
-   La méthode [Update](../../../ado/reference/ado-api/update-method.md) finalise l’ajout ou la suppression de champs à la collection.  
  
-   Comme raccourci et alternative à la méthode **Append** , vous pouvez créer des champs en affectant une valeur à un champ non défini ou supprimé.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Fournisseur OLE DB pour la publication Internet](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md)  
  
-   [Scénario de publication Internet](../../../ado/guide/data/internet-publishing-scenario.md)  
  
-   [URL absolues et relatives](../../../ado/guide/data/absolute-and-relative-urls.md)  
  
-   [Enregistrements et champs fournis par le fournisseur](../../../ado/guide/data/records-and-provider-supplied-fields.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Record, objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)   
 [Historique d’ADO](../../../ado/guide/ado-history.md)
