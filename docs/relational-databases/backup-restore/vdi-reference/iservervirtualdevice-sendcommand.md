---
title: IServerVirtualDevice::SendCommand
titlesuffix: SQL Server VDI reference
description: Cet article fournit des informations de référence sur la commande IServerVirtualDevice::SendCommand.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c75cd206557547f55d47eec0a7aec52cc0069b71
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "70847510"
---
# <a name="iservervirtualdevicesendcommand-vdi"></a>IServerVirtualDevice::SendCommand (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

La fonction **SendCommand** envoie une commande au client en utilisant un objet d’appareil virtuel retourné depuis IServerVirtualDeviceSet2::OpenDevice.

## <a name="syntax"></a>Syntaxe

```c
HRESULT IServerVirtualDevice::SendCommand (
   VDS_Command*   pCmd
);
```

## <a name="parameters"></a>Paramètres

*pCmd* : un pointeur vers un bloc de demande de commande. Pour plus d’informations, consultez Commandes. Le champ completionFunction doit être défini de façon à pointer vers l’adresse d’une fonction avec la signature suivante :

```c
void callbackFunction ( VDS_Command *pCmd);
```

Ce rappel est effectué par l’agent d’achèvement quand le client indique qu’une commande a été exécutée. SQL Server définit le champ completionContext du pCmd. Son objectif est de fournir un contexte à la fonction de rappel.

## <a name="return-value"></a>Valeur de retour

|Valeur de retour | Explication |
|---|---|
| NOERROR | La commande est correctement mise en file d’attente sur le client. |
| VD_E_QUEUE_FULL | La file d’attente de l’appareil est pleine. |
| VD_E_IO_ERROR | L’appareil est dans un état IO-ERROR. |
| VD_E_PROTOCOL | L’appareil n’est pas actif. |

## <a name="remarks"></a>Notes

Quand une erreur se produit lors de la tentative d’envoi de la commande, la fonction de rappel est appelée et le completionCode dans la mémoire tampon de commande est défini comme suit :

| completionCode | Error |
|---|---|
| VD_E_QUEUE_FULL | ERROR_NO_SYSTEM_RESOURCES |
| VD_E_IO_ERROR   | ERROR_IO_DEVICE |
| VD_E_PROTOCOL   | ERROR_INVALID_HANDLE |
| VD_E_ABORT      | ERROR_OPERATION_ABORTED |

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez [Vue d’ensemble des informations de référence sur l’interface des appareils virtuels SQL Server](reference-virtual-device-interface.md).