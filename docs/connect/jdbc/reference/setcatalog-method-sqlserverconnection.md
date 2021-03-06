---
title: Méthode setCatalog (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setCatalog
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 553c0603-c07d-436a-86eb-3ba6b51bd696
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3a7da2d69f4865eda439b0fb1219be6357c1c40e
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80929094"
---
# <a name="setcatalog-method-sqlserverconnection"></a>Méthode setCatalog (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le nom de catalogue donné pour sélectionner un sous-espace de la base de données de cet objet [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) servant d’emplacement de travail.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setCatalog(java.lang.String catalog)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *catalog*  
  
 **Chaîne** contenant le nom du catalogue.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setCatalog est spécifiée par la méthode setCatalog de l’interface java.sql.Connection.  
  
 L'argument du *catalogue* est placé automatiquement par [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Cette méthode permet de définir la propriété catalog de l’objet Connection. La propriété n'est pas définie implicitement de quelque autre façon.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
