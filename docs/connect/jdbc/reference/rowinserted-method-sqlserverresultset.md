---
title: Méthode rowInserted (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.rowInserted
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e7c10372-0be8-4baa-87f7-ed6b66003357
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5b471631bb5111f6bc6af5889ecf0d4444e4742c
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80903849"
---
# <a name="rowinserted-method-sqlserverresultset"></a>rowInserted, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si la ligne actuelle a eu une insertion.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean rowInserted()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si une ligne a eu une insertion et que des insertions sont détectées. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode rowUpdated est spécifiée par la méthode rowUpdated dans l’interface java.sql.ResultSet.  
  
 La valeur retournée dépend de la possibilité pour l’objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) de détecter des insertions visibles.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne détecte les lignes insérées d’aucun type de curseur.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
