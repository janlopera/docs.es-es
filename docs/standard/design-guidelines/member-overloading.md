---
title: Sobrecarga de miembro
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
ms.openlocfilehash: c9cb178e838aab99c22089b527a6bd2e86b325de
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727838"
---
# <a name="member-overloading"></a>Sobrecarga de miembro
La sobrecarga de miembros implica la creación de dos o más miembros en el mismo tipo que solo difieren en el número o tipo de parámetros, pero tienen el mismo nombre. Por ejemplo, en el siguiente caso, el método `WriteLine` está sobrecargado:

```csharp
public static class Console {
    public void WriteLine();
    public void WriteLine(string value);
    public void WriteLine(bool value);
    ...
}
```

 Dado que solo los métodos, los constructores y las propiedades indizadas pueden tener parámetros, solo esos miembros se pueden sobrecargar.

 La sobrecarga es una de las técnicas más importantes para mejorar la facilidad de uso, la productividad y la legibilidad de las bibliotecas reutilizables. La sobrecarga en el número de parámetros permite proporcionar versiones más sencillas de constructores y métodos. La sobrecarga en el tipo de parámetro permite usar el mismo nombre de miembro para los miembros que realizan operaciones idénticas en un conjunto seleccionado de tipos diferentes.

 ✔️ intente usar nombres de parámetro descriptivos para indicar el valor predeterminado usado por las sobrecargas más cortas.

 ❌ evitar los nombres de parámetro que varían arbitrariamente en las sobrecargas. Si un parámetro de una sobrecarga representa la misma entrada que un parámetro en otra sobrecarga, los parámetros deben tener el mismo nombre.

 ❌ evitar ser incoherentes en el orden de los parámetros en los miembros sobrecargados. Los parámetros con el mismo nombre deben aparecer en la misma posición en todas las sobrecargas.

 ✔️ hacer solo la sobrecarga más larga virtual (si se requiere extensibilidad). Las sobrecargas más cortas simplemente deben llamar a a través de una sobrecarga más larga.

 ❌ no use los modificadores `ref` o `out` para sobrecargar los miembros.

 Algunos lenguajes no pueden resolver llamadas a sobrecargas como esta. Además, estas sobrecargas suelen tener una semántica completamente diferente y probablemente no deberían ser sobrecargas, sino dos métodos independientes.

 ❌ no tienen sobrecargas con parámetros en la misma posición y tipos similares, pero con una semántica diferente.

 ✔️ permitir que se pasen `null` para los argumentos opcionales.

 ✔️ usar la sobrecarga de miembros en lugar de definir miembros con argumentos predeterminados.

 Los argumentos predeterminados no son conformes a CLS.

 *Partes © 2005, 2009 Microsoft Corporation. Todos los derechos reservados.*

 *Material reimpreso con el consentimiento de Pearson Education, Inc. y extraído de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) (Instrucciones de diseño de .NET Framework: convenciones, expresiones y patrones para bibliotecas .NET reutilizables, 2.ª edición), de Krzysztof Cwalina y Brad Abrams, publicado el 22 de octubre de 2008 por Addison-Wesley Professional como parte de la serie Microsoft Windows Development.*

## <a name="see-also"></a>Consulte también

- [Instrucciones de diseño de miembros](../../../docs/standard/design-guidelines/member.md)
- [Instrucciones de diseño de .NET Framework](../../../docs/standard/design-guidelines/index.md)
