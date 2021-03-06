---
title: IServerVirtualDeviceSet2::BeginConfiguration
titlesuffix: SQL Server VDI reference
description: Cet article fournit des informations de référence sur la commande IServerVirtualDeviceSet2::BeginConfiguration.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fea109e55b9efa5619bdccb11d692ffebd1a6847
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "70847480"
---
# <a name="iservervirtualdeviceset2beginconfiguration-vdi"></a>IServerVirtualDeviceSet2::BeginConfiguration (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Le serveur appelle la fonction **BeginConfiguration** pour commencer la configuration de l’ensemble d’appareils virtuels.

## <a name="syntax"></a>Syntaxe

```c
HRESULT IServerVirtualDeviceSet2::BeginConfiguration (
   DWORD   dwFeatures,
   DWORD   dwAlignment,
   DWORD   dwBlockSize,
   DWORD   dwMaxTransferSize,
   DWORD   dwTimeout
);
```

## <a name="parameters"></a>Paramètres

*dwFeatures* : le masque des fonctionnalités modifiées. VDF_WriteMedia et/ou VDF_ReadMedia.

*dwAlignment* : l’alignement final. Si sa valeur est 0, dwBlockSize est utilisé par défaut. Doit être une puissance de 2, >= dwBlockSize et <= 64 Ko.

*dwBlockSize* : unité minimale de transfert, en octets. Doit être une puissance de 2, >= 512 et <= 64 Ko.

*dwMaxTransferSize* : le plus gros transfert qui sera tenté. Doit être un multiple de 64 Ko.

*dwTimeout* : nombre de millisecondes à attendre que le client principal termine de déclarer les zones de mémoire tampon qu’il fournit.

## <a name="return-value"></a>Valeur de retour

|Valeur de retour | Explication |
|---|---|
| NOERROR | L’ensemble d’appareils virtuels est dans l’état Configurable. |
| VD_E_ABORT | SignalAbort a été appelé. |
| VD_E_PROTOCOL | L’ensemble d’appareils virtuels n’est pas dans l’état Connected (Connecté). |

## <a name="remarks"></a>Notes

Après l’appel de cette fonction, l’ensemble d’appareils virtuels passe à l’état Configurable, dans lequel la disposition de la mémoire tampon est décidée.
Une fois la configuration de base définie (en fonction des paramètres), ces valeurs restent fixes pour la durée de vie de l’ensemble d’appareils virtuels. La propriété d’alignement de l’ensemble d’appareils virtuels est utilisée pour contrôler l’alignement des mémoires tampons de données. Cette valeur définit une valeur d’alignement minimale qui peut être remplacée individuellement pour chaque mémoire tampon.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez [Vue d’ensemble des informations de référence sur l’interface des appareils virtuels SQL Server](reference-virtual-device-interface.md).