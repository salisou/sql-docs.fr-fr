---
title: " Page Options de SQL Server – Environnement – Démarrage"
ms.date: 11/05/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 13814422be321a3b26577909588385af43ad3406
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75252220"
---
# <a name="options-environment---startup-page"></a>Options (Environnement – Page Démarrage)

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Utilisez la boîte de dialogue **Options** pour configurer les actions de démarrage [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], les options de gestion des fenêtres générales ainsi que d’autres paramètres généraux. Dans le menu **Outils**, cliquez sur **Options**, développez le dossier **Environnement**, puis cliquez sur **Démarrage**.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

**Au démarrage**

Sélectionnez l'action que [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] doit exécuter au démarrage. Les options sont :

- **Ouvrir l'Explorateur d'objets** : demande l'établissement d'une connexion, puis ouvre l'Explorateur d'objets.

- **Ouvrir la fenêtre de nouvelle requête** : demande l'établissement d'une connexion, puis ouvre l'Éditeur de requête SQL.

- **Ouvrir l'Explorateur d'objets et la fenêtre Requête** : demande l'établissement d'une connexion, puis ouvre l'Explorateur d'objets et l'Éditeur de requête SQL également.

- **Ouvrir l'Explorateur d'objets et le Moniteur d'activité**

- **Ouvrir l'environnement vide** : ouvre [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] sans la fenêtre de l'Éditeur de requête SQL et sans connecter l'Explorateur d'objets à un serveur.

**Masquer les objets système dans l'Explorateur d'objets**

Cocher cette case pour enlever les bases de données système, les tables système, les vues système et les procédures stockées système de l'arborescence de l'Explorateur d'objets. Les fonctions système et les types de données système ne sont pas masqués. Cette option s'applique uniquement aux instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et n'affecte pas les serveurs déjà connectés à l'Explorateur d'objets.

## <a name="see-also"></a>Voir aussi

- [Aide (F1) des boîtes de dialogue Options](options-dialog-boxes-f1-help.md)
- [Options (Environnement - Page Général)](options-environment-general-page.md)
