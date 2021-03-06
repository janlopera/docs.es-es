---
title: CorThreadSafetyOptions (Enumeración)
ms.date: 03/30/2017
api_name:
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
ms.openlocfilehash: 93dd8c56176890d04d792f3c336492e4f232825b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442468"
---
# <a name="corthreadsafetyoptions-enumeration"></a>CorThreadSafetyOptions (Enumeración)

Especifica marcas para seleccionar opciones de seguridad para subprocesos.

## <a name="syntax"></a>Sintaxis

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a>Miembros

|Miembro|Descripción|
|------------|-----------------|
|`MDThreadSafetyDefault`|Valor predeterminado. Igual que `MDThreadSafetyOff`.|
|`MDThreadSafetyOff`|Indica que no se puede establecer un bloqueo de lector/escritor.|
|`MDThreadSafetyOn`|Indica que se puede establecer un bloqueo de lectura/escritura.|

## <a name="requirements"></a>Requisitos

**Plataformas:** Vea [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).

**Encabezado:** CorHdr. h

**Versiones de .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Vea también

- [Enumeraciones para metadatos](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
