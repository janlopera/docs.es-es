---
title: _EFN_GetManagedObjectFieldInfo (Función)
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectFieldInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectFieldInfo
helpviewer_keywords:
- _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type:
- apiref
ms.openlocfilehash: 42f7020212dd2db793b7c7d20a15c129157e7261
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860765"
---
# <a name="_efn_getmanagedobjectfieldinfo-function"></a>\_EFN\_GetManagedObjectFieldInfo función)
Obtiene el desplazamiento desde el inicio de un objeto hasta un campo y el valor del campo, a partir del puntero de objeto y nombre de campo especificados.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a>Parámetros  
 `Client`  
 de Puntero al cliente de depuración.  
  
 `objAddr`  
 de Puntero de objeto administrado.  
  
 szFieldName  
 de Puntero de objeto administrado al nombre del campo.  
  
 `pValue`  
 enuncia Valor del campo. Este parámetro puede ser NULL.  
  
 `pOffset`  
 enuncia Desplazamiento desde `objAddr` hasta el campo. Este parámetro puede ser NULL.  
  
## <a name="remarks"></a>Comentarios  
 Si el desplazamiento es 0, no se escribe ningún desplazamiento.  
  
 Si no hay código administrado en el subproceso actualmente en contexto, la función devuelve HRESULT SOS_E_NOMANAGEDCODE con un valor de instalación de 0XA0 y un código de error de 0x1000.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** SOS_Stacktrace. h  
  
 **Versión de .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte también

- [Funciones estáticas globales para la depuración](debugging-global-static-functions.md)
