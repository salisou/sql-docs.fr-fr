---
title: Examiner les différences entre les tables répliquées (procédures stockées de réplication)
description: Utilisez les procédures stockées de réplication pour connaître les différences entre les tables répliquées sur le serveur de publication et sur l’Abonné.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- tablediff utility
- comparing replicated tables
ms.assetid: cd253a17-0c85-42b4-912c-690169ebe799
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 6130acf6a503f3a803978b7db5a9a23b9918a3c7
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "76286866"
---
# <a name="compare-differences-between-replicated-tables-replication-programming"></a>Examiner les différences entre les tables répliquées (programmation de réplication)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  La validation d'article est utilisée pour déterminer si les données publiées pour les articles de table sur le serveur de publication et sur l'Abonné ne sont pas identiques, ce qui peut indiquer une non-convergence. Pour plus d’informations, consultez [Valider des données répliquées](../../../relational-databases/replication/validate-data-at-the-subscriber.md). Toutefois, la validation retourne uniquement des informations de succès ou d'échec et ne fournit pas d'informations sur les différences entre les tables sources et les tables cibles. L’utilitaire d’invite de commandes **tablediff** retourne des informations détaillées sur les différences entre les deux tables et peut même générer un script [!INCLUDE[tsql](../../../includes/tsql-md.md)] pour établir la convergence de l’abonnement avec les données sur le serveur de publication.  
  
> [!NOTE]  
>  L’utilitaire **tablediff** est pris en charge uniquement pour les serveurs [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
### <a name="to-compare-replicated-tables-for-differences-using-tablediff"></a>Pour comparer les différences des tables répliquées à l'aide de tablediff  
  
1.  À partir de l'invite de commandes sur un serveur quelconque d'une topologie de réplication, exécutez l' [tablediff Utility](../../../tools/tablediff-utility.md). Spécifiez les paramètres suivants :  
  
    -   **-sourceserver** - nom du serveur sur lequel les données sont reconnues comme correctes, habituellement le serveur de publication.  
  
    -   **-sourcedatabase** - nom de la base de données contenant les données correctes.  
  
    -   **-sourcetable** - nom de la table source pour l'article comparé.  
  
    -   (Facultatif) **-sourceschema** - propriétaire du schéma de la table source, sinon le schéma par défaut.  
  
    -   (Facultatif) **-sourceuser** et **-sourcepassword** en cas d'utilisation de l'authentification SQL Server pour se connecter au serveur de publication.  
  
        > [!IMPORTANT]  
        >  Lorsque c'est possible, utilisez l'authentification Windows. Si vous devez utiliser l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , invitez les utilisateurs à entrer les informations d'identification de sécurité pendant l'exécution. Si vous devez enregistrer les informations d'identification dans un fichier de script, vous devez sécuriser le fichier pour empêcher un accès non autorisé.  
  
    -   **-destinationserver** - nom du serveur sur lequel les données sont comparées, habituellement un Abonné.  
  
    -   **-destinationdatabase** - nom de la base de données en cours de comparaison.  
  
    -   **-destinationtable** - nom de la table qui est comparée.  
  
    -   (Facultatif) **-destinationschema** - propriétaire du schéma de la table cible, sinon le schéma par défaut.  
  
    -   (Facultatif) **-destinationuser** et **-destinationpassword** en cas d'utilisation de l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour se connecter à l'Abonné.  
  
        > [!IMPORTANT]  
        >  Lorsque c'est possible, utilisez l'authentification Windows. Si vous devez utiliser l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , invitez les utilisateurs à entrer les informations d'identification de sécurité pendant l'exécution. Si vous devez enregistrer les informations d'identification dans un fichier de script, vous devez sécuriser le fichier pour empêcher un accès non autorisé.  
  
    -   (Facultatif) Utilisez **-c** pour faire une comparaison au niveau des colonnes.  
  
    -   (Facultatif) Utilisez **- q** pour faire une comparaison rapide du nombre de lignes et du schéma uniquement.  
  
    -   (Facultatif) Spécifiez un nom de fichier et un chemin d'accès pour **-o** pour générer la sortie des résultats dans un fichier.  
  
    -   (Facultatif) Spécifiez une table de la base de données d'abonnement dans laquelle insérer les résultats pour **-et**. Si la table existe déjà, spécifiez **-dt** pour supprimer d'abord la table.  
  
    -   (Facultatif) Utilisez **-f** pour générer un fichier [!INCLUDE[tsql](../../../includes/tsql-md.md)] et corriger les données sur l'Abonné afin qu'elles correspondent à celles du serveur de publication. Utilisez **-df** pour spécifier le nombre d'instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)] dans chaque fichier.  
  
    -   (Facultatif) Utilisez **-rc** et **-ri** pour spécifier le nombre de tentatives autorisées pour une opération et l'intervalle avant chaque nouvelle tentative.  
  
    -   (Facultatif) Utilisez **-strict** pour mettre en vigueur la comparaison stricte de schémas entre les tables sources et les tables cibles.  
  
## <a name="see-also"></a>Voir aussi  
 [Valider des données sur l’abonné](../../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  
