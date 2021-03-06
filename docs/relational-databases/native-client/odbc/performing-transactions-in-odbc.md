---
title: Transactions dans ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, transactions
- transactions [ODBC]
- ODBC, transactions
ms.assetid: c5a87fa5-827a-4e6f-a0d9-924bac881eb0
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 093eae04962409b5ac426713aedc74aa1bd0703b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303652"
---
# <a name="performing-transactions-in-odbc"></a>Exécution de transactions dans ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les transactions dans ODBC sont gérées connexion par connexion. Lorsqu'une application termine une transaction, elle valide ou restaure tout le travail effectué par le biais de tous les handles d'instruction sur cette connexion. Pour valider ou restaurer une transaction, les applications doivent appeler [SQLEndTran](../../../relational-databases/native-client-odbc-api/sqlendtran.md) au lieu de soumettre une instruction COMMIT ou ROLLBACK.  
  
 Une application appelle [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) pour basculer entre les deux modes ODBC de gestion des transactions :  
  
-   Mode de validation automatique  
  
     Chaque instruction est validée automatiquement lorsqu'elle est effectuée avec succès. Lorsque vous utilisez le mode de validation automatique, aucune autre fonction de gestion des transactions n'est requise.  
  
-   Mode de validation manuelle  
  
     Toutes les instructions exécutées sont incluses dans la même transaction jusqu'à ce qu'elle soit arrêtée spécifiquement en appelant **SQLEndTran**.  
  
 Le mode de validation automatique est le mode de gestion par défaut des transactions pour ODBC. Lorsqu'une connexion est établie, elle est en mode de validation automatique jusqu'à ce que **SQLSetConnectAttr** soit appelé pour basculer en mode de validation manuelle en désactivant le mode de validation automatique. Lorsqu'une application désactive la validation automatique, l'instruction suivante envoyée à la base de données démarre une transaction. La transaction reste ensuite active jusqu'à ce que l'application appelle **SQLEndTran** avec les options SQL_COMMIT ou SQL_ROLLBACK. La commande envoyée à la base de données après **SQLEndTran** démarre la transaction suivante.  
  
 Si une application bascule du mode de validation manuelle au mode de validation automatique, le pilote valide toutes les transactions actuellement ouvertes sur la connexion.  
  
 Les applications ODBC ne doivent pas utiliser d'instructions de transaction Transact-SQL telles que BEGIN TRANSACTION, COMMIT TRANSACTION ou ROLLBACK TRANSACTION, car cela peut provoquer un comportement indéterminé dans le pilote. Une application ODBC doit s'exécuter en mode de validation automatique et ne doit pas utiliser les instructions ni les fonctions de gestion des transactions, ou elle doit s'exécuter en mode de validation manuelle et utiliser la fonction ODBC **SQLEndTran** pour valider ou restaurer des transactions.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de transactions &#40;ODBC&#41;](https://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
  
