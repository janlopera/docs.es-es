---
title: <c> - Guía de programación de C#
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: d5b28ee6db52d191f8454592d792ac0a1e1dc73b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793450"
---
# <a name="c-c-programming-guide"></a>\<c> (Guía de programación de C#)

## <a name="syntax"></a>Sintaxis

```xml
<c>text</c>
```

## <a name="parameters"></a>Parámetros

- `text`

  El texto que le gustaría indicar como código.

## <a name="remarks"></a>Comentarios

La etiqueta \<c> le proporciona una manera de indicar que el texto dentro de una descripción debe marcarse como código. Use [\<code>](./code.md) para indicar varias líneas como código.

Compile con [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para procesar los comentarios de documentación de un archivo.

## <a name="example"></a>Ejemplo

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a>Vea también

- [Guía de programación de C#](../index.md)
- [Etiquetas recomendadas para los comentarios de documentación](./recommended-tags-for-documentation-comments.md)
