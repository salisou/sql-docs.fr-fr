---
title: 'Compteurs de performances pour les objets ReportServer : service et ReportServerSharePoint : service performance | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Server service, performance counters
ms.assetid: 2bcacab2-3a4f-4aae-b123-19d756b9b9ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ca5a4561c4b3f55044eb63068036105d878f150c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "78175078"
---
# <a name="performance-counters-for-the-reportserverservice--and-reportserversharepointservice-performance-objects"></a>Performance Counters for the ReportServer:Service  and ReportServerSharePoint:Service Performance Objects
  Cette rubrique décrit les compteurs de performance pour les objets de performance [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] suivants :

-   `ReportServer:Service`

-   `ReportServerSharePoint:Service`

> [!NOTE]
>  Les objets de performance sont utilisés pour contrôler des événements sur le serveur de rapports local. Si vous exécutez un serveur de rapports dans un déploiement avec montée en puissance parallèle, les chiffres s'appliquent au serveur actuel et non au déploiement avec montée en puissance parallèle dans son ensemble.

 Les objets de performance sont disponibles dans l’Analyseur de performances Windows (**Perfmon.exe**). Pour plus d'informations, consultez la documentation Windows. [Profilage de runtime](https://msdn.microsoft.com/library/w4bz2147.aspx) (https://msdn.microsoft.com/library/w4bz2147.aspx).

 Dans cette rubrique :

-   [ReportServer:compteurs de performance de service (serveur de rapports en mode natif)](#bkmk_ReportServer)

-   [ReportServerSharePoint:Service (serveur de rapports en mode SharePoint)](#bkmk_ReportServerSharePoint)

-   [Utiliser des applets de commande PowerShell pour retourner des listes](#bkmk_powershell)

 [!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Mode SharePoint | Mode natif.

##  <a name="reportserverservice-performance-counters-native-mode-report-server"></a><a name="bkmk_ReportServer"></a> ReportServer:compteurs de performance de service (serveur de rapports en mode natif)
 L'objet de performance `ReportServer:Service` inclut une collection de compteurs utilisée pour suivre les événements liés au protocole HTTP et les événements relatifs à la mémoire pour une instance du serveur de rapports. Cet objet de performance apparaît une fois pour chaque instance de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] sur l'ordinateur, et vous pouvez ajouter ou supprimer des compteurs de l'objet de performance pour chaque instance. Les compteurs de l'instance par défaut apparaissent avec le format `ReportServer:Service`. Les compteurs pour les instances nommées s’affichent au format `ReportServer$<` *instance_name*`>:Service`.

 L' `ReportServer:Service` objet de performance est une [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]nouveauté dans et fournit un sous-ensemble de compteurs inclus avec Internet Information Services (IIS) et dans [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] les versions antérieures de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Ces nouveaux compteurs sont spécifiques à [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], et ils suivent les événements liés à HTTP pour le serveur de rapports, comme les requêtes, les connexions et les tentatives d'ouverture de session. En outre, cet objet de performance inclut des compteurs pour suivre les événements de gestion de la mémoire.

 Le tableau suivant répertorie les compteurs inclus dans l'objet de performance `ReportServer:Service`.

 ![Contenu relatif à PowerShell](../media/rs-powershellicon.jpg "Contenu relatif à PowerShell") Le script Windows PowerShell suivant retourne la liste des compteurs de performance pour le compteur de performance CounterSetName.

```
(get-counter -listset "ReportServer:Service").paths
```

|Compteur|Description|
|-------------|-----------------|
|`Active connections`|Nombre de connexions actives sur le serveur.|
|`Bytes Received Total`|Nombre d'octets reçus par le serveur. Ce compteur compte les octets bruts reçus en tout par le Gestionnaire de rapports et le serveur de rapports.|
|`Bytes Received/sec`|Nombre d'octets reçus par seconde par le serveur. Ce compteur n'est mis à jour qu'au terme d'un transfert. Cela signifie que le compteur reste à 0 tant qu'un transfert n'est pas terminé.|
|`Bytes Sent Total`|Nombre d'octets envoyés à partir du serveur. Ce compteur compte les octets bruts envoyés en tout par le Gestionnaire de rapports et le serveur de rapports.|
|`Bytes Sent/sec`|Nombre d'octets envoyés par seconde à partir du serveur. Ce compteur n'est mis à jour qu'au terme d'un transfert. Cela signifie que le compteur reste à 0 tant qu'un transfert n'est pas terminé.|
|`Errors Total`|Nombre total d'erreurs qui se produisent au cours du traitement des requêtes HTTP. Ces erreurs incluent les codes d'état HTTP 400 et 500.|
|`Errors/sec`|Nombre total d'erreurs qui se produisent par seconde au cours du traitement des requêtes HTTP. Ces erreurs incluent les codes d'état HTTP 400 et 500.|
|`Logon Attempts Total`|Nombre de tentatives d'ouverture de session effectuées à partir de types d'authentification RSWindows. Les types d'authentification RSWindows incluent RSWindowsNegotiate, RSWindowsNTLM, RSWindowsKerberos et RSWindowsBasic. La valeur zéro (0) représente l'authentification personnalisée.|
|`Logon Attempts/sec`|Taux de tentatives d'ouverture de session.|
|`Logon Successes Total`|Nombre d'ouvertures de session réussies pour les types d'authentification RSWindows. Les types d'authentification RSWindows incluent RSWindowsNegotiate, RSWindowsNTLM, RSWindowsKerberos et RSWindowsBasic. La valeur zéro (0) représente l'authentification personnalisée.|
|`Logon Successes/sec`|Taux d'ouvertures de session réussies.|
|`Memory Pressure State`|Nombre, compris entre 1 et 5, qui indique l'état de mémoire actuel du serveur :<br /><br /> 1 : Aucune sollicitation<br /><br /> 2 : Sollicitation faible<br /><br /> 3 : Sollicitation moyenne<br /><br /> 4 : Sollicitation élevée<br /><br /> 5 : Sollicitation dépassée|
|`Memory Shrink Amount`|Nombre d'octets demandés par le serveur pour réduire la mémoire utilisée.|
|`Memory Shrink Notifications/sec`|Nombre de notifications émises par le serveur au cours de la dernière seconde pour réduire la mémoire utilisée. Cette valeur indique la fréquence à laquelle le serveur se trouve en situation de sollicitation de la mémoire.|
|`Requests Disconnected`|Nombre de requêtes qui sont déconnectées en raison d'un échec de communication.|
|`Requests Executing`|Nombre de requêtes en cours de traitement.|
|`Requests Not Authorized`|Nombre de requêtes qui échouent avec le code d'état HTTP 401.|
|`Requests Rejected`|Nombre total de requêtes qui n'ont pas été traitées en raison de ressources serveur insuffisantes. Ce compteur représente le nombre de requêtes qui retournent un code d'état HTTP 503, indiquant que le serveur est trop occupé.|
|`Requests Total`|Nombre total de requêtes reçues par le service du serveur de rapports depuis le démarrage. Ce compteur compte les requêtes envoyées au Gestionnaire de rapports et celles envoyées par le Gestionnaire de rapports au serveur de rapports.|
|`Requests/sec`|Nombre de requêtes traitées par seconde. Cette valeur représente le débit actuel de l'application.|
|`Tasks Queued`|Nombre de tâches en attente d'un thread pour pouvoir être traitées. Chaque requête adressée au serveur de rapports correspond à une ou plusieurs tâches. Ce compteur représente uniquement le nombre de tâches prêtes à être traitées ; il n'inclut pas le nombre de tâches en cours d'exécution.|

##  <a name="reportserversharepointservice-sharepoint-mode-report-server"></a><a name="bkmk_ReportServerSharePoint"></a>ReportServerSharePoint : service (serveur de rapports en mode SharePoint)
 L' `ReportServerSharePoint:Service` objet de performance a été [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]ajouté dans.

 ![Contenu relatif à PowerShell](../media/rs-powershellicon.jpg "Contenu relatif à PowerShell") Le script Windows PowerShell suivant retourne la liste des compteurs de performance pour le compteur de performance CounterSetName.

```
(get-counter -listset "ReportServerSharePoint:Service").paths
```

|Compteur|
|-------------|
|`Memory Pressure State`|
|`Memory Shrink Amount`|
|`Memory Shrink Notifications/Sec`|

##  <a name="use-powershell-cmdlets-to-return-lists"></a><a name="bkmk_powershell"></a>Utiliser des applets de commande PowerShell pour retourner des listes
 ![Contenu relatif à PowerShell](../media/rs-powershellicon.jpg "Contenu relatif à PowerShell") Le script Windows PowerShell suivant retourne la liste des compteurs de performance pour le compteur de performance CounterSetName « ReportServerSharePoint:Service » :

```
(get-counter -listset "ReportServerSharePoint:Service").paths
```

## <a name="see-also"></a>Voir aussi
 [Analyse](monitoring-report-server-performance.md) [des compteurs de performance des performances du serveur de rapports pour le service Web MSRS 2014 et les objets de performance du service windows MSRS 2014 &#40;les&#41;en mode natif](../report-server/performance-counters-msrs-2011-web-service-performance-objects.md) [compteurs de performances du service Web MSRS 2014 en mode SharePoint et du service Windows MSRS 2014 objets de performance en mode sharepoint &#40;mode SharePoint&#41;]. /performance-counters-msrs-2011-sharepoint-mode-performance-objects.md)


