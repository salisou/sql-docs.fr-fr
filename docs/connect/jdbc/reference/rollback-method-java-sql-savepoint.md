---
title: Méthode rollback (java.sql.Savepoint) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.rollback (java.sql.Savepoint)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d5dbd9ef-194f-4130-bfcc-7901a4fa8ded
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2e1ac014ddeee1d3763dc3cebe720751c4c1ec94
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80903884"
---
# <a name="rollback-method-javasqlsavepoint"></a>Méthode rollback (java.sql.Savepoint)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Annule toutes les modifications effectuées après la définition de l’objet [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void rollback(java.sql.Savepoint s)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *s*  
  
 Objet SavePoint de destination de la restauration.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode rollBack est spécifiée par la méthode rollBack de l’interface java.sql.Connection.  
  
 Cette méthode doit être utilisée uniquement lorsque le mode de validation automatique a été désactivé.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode rollback &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md)   
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
