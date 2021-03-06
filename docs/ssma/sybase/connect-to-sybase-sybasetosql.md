---
title: Se connecter à Sybase (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 524f95ef-10bd-497c-84ca-c06a0ae794fb
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 6cb2f4196737cceec2f60684de1b7409f5e383a0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68083391"
---
# <a name="connect-to-sybase-sybasetosql"></a>Se connecter à Sybase (SybaseToSQL)
Utilisez la boîte de dialogue **se connecter à Sybase** pour vous connecter à l’instance de Sybase Adaptive Server Enterprise (ASE) que vous souhaitez migrer.  
  
Pour accéder à cette boîte de dialogue, dans le menu **fichier** , sélectionnez **se connecter à Sybase**. Si vous vous êtes connecté précédemment, la commande se **reconnecte à Sybase**.  
  
## <a name="options"></a>Options  
**Fournisseur**  
Sélectionnez l’un des fournisseurs installés sur l’ordinateur pour la connexion au serveur Sybase.  
  
**Mode**  
Sélectionnez le mode de connexion standard ou avancé. En mode standard, vous entrez ou sélectionnez des valeurs pour le nom du serveur, le port, le nom d’utilisateur et le mot de passe. En mode avancé, vous fournissez une chaîne de connexion.  
  
**Nom du serveur**  
Entrez ou sélectionnez le nom ou l’adresse IP du serveur adaptatif. Le nom du serveur par défaut est le même que le nom de l’ordinateur. Il s’agit d’une option de mode standard.  
  
**Port du serveur**  
Si vous utilisez un port autre que celui par défaut pour les connexions à l’ASE, entrez le numéro de port. Le numéro de port par défaut est 5000. Il s’agit d’une option de mode standard.  
  
**Nom d'utilisateur**  
Entrez le nom d’utilisateur utilisé pour se connecter à l’ASE. Il s’agit d’une option de mode standard.  
  
**Mot de passe**  
Entrez le mot de passe correspondant au nom d'utilisateur indiqué. Il s’agit d’une option de mode standard.  
  
**Chaîne de connexion**  
Entrez la chaîne de connexion complète pour la connexion à l’ASE.  
  
Les chaînes de connexion se composent de paires nom de paramètre/valeur. Les noms des paramètres varient en fonction du fournisseur utilisé.  
  
**Les paramètres de connexion de différents fournisseurs sont les suivants :**  
  
1.  Paramètres de connexion pour le **fournisseur de OLE DB**  
  
    |Paramètre|Paramètre Sybase 12,5|Paramètre Sybase 15|  
    |-----------|-------------------------|-----------------------|  
    |Nom du serveur|Nom du serveur|Server (Serveur)|  
    |Port|Adresse du port du serveur|Port|  
    |Nom d'utilisateur|ID d'utilisateur|ID d'utilisateur|  
    |Mot de passe|Mot de passe|Mot de passe|  
    |Fournisseur|Fournisseur|Fournisseur|  
  
    Pour Sybase ASE 12,5, un exemple de chaîne de connexion est le suivant :  
  
    `Server Name=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider=Sybase.ASEOLEDBProvider;`  
  
    Pour Sybase ASE 15, un exemple de chaîne de connexion est le suivant :  
  
    `Server=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider=ASEOLEDB;Port=5000;`  
  
2.  Paramètres de connexion pour le **fournisseur ODBC**  
  
    |Paramètre|Paramètre Sybase 12,5/15|  
    |-----------|-----------------------------|  
    |Nom du pilote|pilote|  
    |Nom du serveur|Server (Serveur)|  
    |User Name|Codé|  
    |Mot de passe|Pwd|  
    |Numéro de port|Port|  
  
    Pour Sybase ASE 12,5 ou 15, un exemple de chaîne de connexion est le suivant :  
  
    `driver=Adaptive Server Enterprise;Server=sybserver;uid=MyUserID;pwd=MyP@$$word;Port=5000;`  
  
3.  Paramètres de connexion pour le **fournisseur ADO.net**  
  
    |Paramètre|Paramètre Sybase 12,5/15|  
    |-----------|-----------------------------|  
    |Nom du serveur|Server (Serveur)|  
    |User Name|Codé|  
    |Mot de passe|Pwd|  
    |Numéro de port|Port|  
  
    Voici un exemple de chaîne de connexion pour le fournisseur ADO.NET :  
  
    `Server=sybserver;Port=5000;uid=MyUserID;pwd=MyP@$$word;`  
  
Pour plus d’informations, consultez la documentation de l’ASE.  
  
Il s’agit d’une option de mode avancé.  
  
