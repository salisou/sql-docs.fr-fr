---
title: Méthode getWorkstationID (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getWorkstationID
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f6a701de-a8fa-4668-9310-99a8c6e32c88
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2848ed26d2ce9df960170d3f7a1d3e4c49b630ab
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80910152"
---
# <a name="getworkstationid-method-sqlserverdatasource"></a>Méthode getWorkstationID (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne le nom de l'ordinateur client utilisé pour la connexion à la source de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getWorkstationID()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **Chaîne** contenant le nom de l’ordinateur client.  
  
## <a name="remarks"></a>Notes  
 Le workstationID est le nom de l'ordinateur client ou du poste de travail. Si la propriété workstationID n’est pas définie, la valeur par défaut est construite par un appel à la méthode InetAddress.getLocalHost().getHostName(). Si getHostName retourne une valeur vide, la méthode getHostAddress().toString() est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
