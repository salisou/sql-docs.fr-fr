---
title: Personnalisation de DataFactory | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory customization in RDS [ADO]
ms.assetid: 86d77985-a0d0-405a-8587-c85a20540a0e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1bdc406778bea0d6355e747998d2517b841fc17b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67922772"
---
# <a name="datafactory-customization"></a>Personnalisation de DataFactory
RDS (Remote Data Service) offre un moyen d’accéder facilement aux données dans un système client/serveur à trois niveaux. Un contrôle de données client spécifie des paramètres de chaîne de connexion et de commande pour exécuter une requête sur une source de données distante, ou des paramètres de chaîne de connexion et d’objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) pour effectuer une mise à jour.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Les paramètres sont passés à un programme serveur, qui effectue l’opération d’accès aux données sur la source de données distante. RDS fournit un programme serveur par défaut appelé l’objet [RDSServer. DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) . L’objet **RDSServer. DataFactory** retourne tout objet **Recordset** produit par une requête au client.  
  
 Toutefois, l’analyseur **RDSServer. DataFactory** est limité à l’exécution de requêtes et de mises à jour. Il ne peut pas effectuer de validation ou de traitement sur les chaînes de connexion ou de commande.  
  
 Avec ADO, vous pouvez spécifier que le **DataFactory** fonctionne conjointement avec un autre type de programme serveur appelé *Gestionnaire*. Le gestionnaire peut modifier les chaînes de connexion et de commande du client avant de les utiliser pour accéder à la source de données. En outre, le gestionnaire peut appliquer des droits d’accès qui régissent la capacité du client à lire et écrire des données dans la source de données.  
  
 Les paramètres utilisés par le gestionnaire pour modifier les paramètres du client et les droits d’accès sont spécifiés dans les sections d’un fichier de personnalisation.  
  
 Les rubriques suivantes fournissent plus d’informations sur la personnalisation de l’objet **DataFactory** .  
  
-   [Présentation du fichier de personnalisation](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)  
  
-   [Fichier de personnalisation, section connect](../../../ado/guide/remote-data-service/customization-file-connect-section.md)  
  
-   [Fichier de personnalisation, section SQL](../../../ado/guide/remote-data-service/customization-file-sql-section.md)  
  
-   [Fichier de personnalisation, section UserList](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)  
  
-   [Fichier de personnalisation, section Logs](../../../ado/guide/remote-data-service/customization-file-logs-section.md)  
  
-   [Paramètres client obligatoires](../../../ado/guide/remote-data-service/required-client-settings.md)  
  
-   [Écriture d’un gestionnaire personnalisé](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


