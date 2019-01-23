---
title: Método ISOSDacInterface::GetMethodDescData
ms.date: 01/16/2019
api.name:
- ISOSDacInterface::GetMethodDescData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescData Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescData Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 3f22752446413c622a20340541b0ac328f63c77b
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416735"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="116cf-102">Método ISOSDacInterface::GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="116cf-102">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="116cf-103">Obtiene los datos para la dada [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="116cf-103">Gets the data for the given [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="116cf-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="116cf-104">Syntax</span></span>

```
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    void                       *data,
    ULONG                      cRevertedRejitVersions,
    void                      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

### <a name="parameters"></a><span data-ttu-id="116cf-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="116cf-105">Parameters</span></span>

<span data-ttu-id="116cf-106">`methodDesc` [in] La dirección de la MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="116cf-106">`methodDesc` [in] The address of the MethodDesc.</span></span>

<span data-ttu-id="116cf-107">`ip` [in] La dirección IP del método.</span><span class="sxs-lookup"><span data-stu-id="116cf-107">`ip` [in] The IP address of the method.</span></span>

<span data-ttu-id="116cf-108">`data` [out] Los datos asociados con el MethodDesc devuelto desde las API internas.</span><span class="sxs-lookup"><span data-stu-id="116cf-108">`data` [out] The data associated with the MethodDesc as returned from the internal APIs.</span></span> <span data-ttu-id="116cf-109">La estructura necesita al menos 168 bytes.</span><span class="sxs-lookup"><span data-stu-id="116cf-109">The structure needs at least 168 bytes.</span></span>

<span data-ttu-id="116cf-110">`cRevertedRejitVersions` [out] El número de versiones de rejit revertida.</span><span class="sxs-lookup"><span data-stu-id="116cf-110">`cRevertedRejitVersions` [out] The number of reverted rejit versions.</span></span>

<span data-ttu-id="116cf-111">`rgRevertedRejitData` [out] Los datos asociados con las versiones de rejit revertida devuelto desde las API internas.</span><span class="sxs-lookup"><span data-stu-id="116cf-111">`rgRevertedRejitData` [out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span> <span data-ttu-id="116cf-112">La estructura necesita al menos 24 bytes.</span><span class="sxs-lookup"><span data-stu-id="116cf-112">The structure needs at least 24 bytes.</span></span>

<span data-ttu-id="116cf-113">`pcNeededRevertedRejitData` [out] El número de bytes necesarios para almacenar los datos asociados con las versiones de ReJit revertidas.</span><span class="sxs-lookup"><span data-stu-id="116cf-113">`pcNeededRevertedRejitData` [out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="116cf-114">Comentarios</span><span class="sxs-lookup"><span data-stu-id="116cf-114">Remarks</span></span>

<span data-ttu-id="116cf-115">El método proporcionado forma parte de la `ISOSDacInterface` interfaz y corresponde a la ranura de la tabla de métodos virtuales 20.</span><span class="sxs-lookup"><span data-stu-id="116cf-115">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="116cf-116">También la `CLRDATA_ADDRESS` son enteros de 64 bits sin signo.</span><span class="sxs-lookup"><span data-stu-id="116cf-116">Also the `CLRDATA_ADDRESS` are 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="116cf-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="116cf-117">Requirements</span></span>

<span data-ttu-id="116cf-118">**Plataformas:** Consulte [Requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="116cf-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="116cf-119">**Encabezado**: Ninguna</span><span class="sxs-lookup"><span data-stu-id="116cf-119">**Header:** None</span></span>  
<span data-ttu-id="116cf-120">**Biblioteca:** Ninguna</span><span class="sxs-lookup"><span data-stu-id="116cf-120">**Library:** None</span></span>  
<span data-ttu-id="116cf-121">**Versiones de .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="116cf-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="116cf-122">Vea también</span><span class="sxs-lookup"><span data-stu-id="116cf-122">See Also</span></span>

- [<span data-ttu-id="116cf-123">Depuración</span><span class="sxs-lookup"><span data-stu-id="116cf-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="116cf-124">Interfaz ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="116cf-124">ISOSDacInterface Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md)