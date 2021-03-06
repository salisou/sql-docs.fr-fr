---
title: Méthode setTrustServerCertificate (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- setTrustServerCertificate Method (SQLServerDataSource)
apilocation:
- setTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 6c37b518-147e-4cd9-9eff-b48a3f5888c6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ea37bbfb1582836db8f0c12b383b59c2d527f5ef
ms.sourcegitcommit: 54cfeb36c9caa51ec68fa8f4a1918e305db5e00a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81219190"
---
# <a name="settrustservercertificate-method-sqlserverdatasource"></a>Méthode setTrustServerCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit une valeur **booléenne** qui indique si la propriété trustServerCertificate est activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setTrustServerCertificate(boolean trustServerCertificate)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *trustServerCertificate*  
  
 **true** si le certificat TLS (Transport Layer Security), anciennement SSL (Secure Sockets Layer), du serveur doit être automatiquement approuvé quand la couche de communication est chiffrée avec TLS. Dans le cas contraire, la valeur est **false**.  
  
## <a name="remarks"></a>Notes  
 Si la propriété trustServerCertificate a la valeur **true**, le certificat TLS/SSL [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est automatiquement approuvé quand la couche de communication est chiffrée avec TLS. En d’autres termes, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] ne valide pas le certificat TLS/SSL [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La valeur par défaut est **false**.  
  
 Si la propriété trustServerCertificate a la valeur **false**, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] valide le certificat TLS/SSL du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
