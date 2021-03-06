---
title: Usar tipos de excepciones estándar
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: 3caa94d9a39966614161e4b19201dcf6065776a2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743544"
---
# <a name="using-standard-exception-types"></a>Usar tipos de excepciones estándar
En esta sección se describen las excepciones estándar proporcionadas por el marco de trabajo y los detalles de su uso. La lista no es exhaustiva. Consulte la documentación de referencia de .NET Framework para ver el uso de otros tipos de excepción de marco de trabajo.

## <a name="exception-and-systemexception"></a>Excepción y SystemException
 ❌ no inician <xref:System.Exception?displayProperty=nameWithType> ni <xref:System.SystemException?displayProperty=nameWithType>.

 ❌ no detecta `System.Exception` ni `System.SystemException` en el código del marco de trabajo, a menos que pretenda volver a producirlo.

 ❌ evitar la detección de `System.Exception` o `System.SystemException`, excepto en los controladores de excepciones de nivel superior.

## <a name="applicationexception"></a>ApplicationException
 ❌ no inician o derivan de <xref:System.ApplicationException>.

## <a name="invalidoperationexception"></a>InvalidOperationException
 ✔️ iniciar una <xref:System.InvalidOperationException> si el objeto está en un estado inadecuado.

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException, ArgumentNullException y ArgumentOutOfRangeException
 ✔️ inician <xref:System.ArgumentException> o uno de sus subtipos si se pasan argumentos no válidos a un miembro. Prefiere el tipo de excepción más derivado, si procede.

 ✔️ establecer la propiedad `ParamName` al iniciar una de las subclases de `ArgumentException`.

 Esta propiedad representa el nombre del parámetro que provocó que se produjera la excepción. Tenga en cuenta que la propiedad se puede establecer mediante una de las sobrecargas del constructor.

 ✔️ usar `value` para el nombre del parámetro de valor implícito de los establecedores de propiedad.

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException, IndexOutOfRangeException y AccessViolationException
 ❌ no permiten que las API que se pueden llamar públicamente inicien <xref:System.NullReferenceException>, <xref:System.AccessViolationException>o <xref:System.IndexOutOfRangeException>de forma explícita o implícita. Estas excepciones están reservadas y iniciadas por el motor de ejecución y, en la mayoría de los casos, indican un error.

 Realice una comprobación de argumentos para evitar producir estas excepciones. Producir estas excepciones expone los detalles de implementación del método que pueden cambiar con el tiempo.

## <a name="stackoverflowexception"></a>StackOverflowException
 ❌ no inician <xref:System.StackOverflowException>explícitamente. La excepción solo debe iniciarse explícitamente en CLR.

 ❌ no se detectan `StackOverflowException`.

 Es casi imposible escribir código administrado que permanezca coherente en la presencia de desbordamientos de pila arbitrarios. Las partes no administradas de CLR siguen siendo coherentes mediante el uso de sondeos para trasladar desbordamientos de pila a lugares bien definidos en lugar de deshacer la copia de seguridad desde desbordamientos de pila arbitrarios.

## <a name="outofmemoryexception"></a>OutOfMemoryException
 ❌ no inician <xref:System.OutOfMemoryException>explícitamente. Esta excepción solo la debe iniciar la infraestructura de CLR.

## <a name="comexception-sehexception-and-executionengineexception"></a>COMException, SEHException y ExecutionEngineException
 ❌ no inician explícitamente <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>y <xref:System.Runtime.InteropServices.SEHException>. Estas excepciones solo se producirán en la infraestructura de CLR.

 *Partes © 2005, 2009 Microsoft Corporation. Todos los derechos reservados.*

 *Material reimpreso con el consentimiento de Pearson Education, Inc. y extraído de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) (Instrucciones de diseño de .NET Framework: convenciones, expresiones y patrones para bibliotecas .NET reutilizables, 2.ª edición), de Krzysztof Cwalina y Brad Abrams, publicado el 22 de octubre de 2008 por Addison-Wesley Professional como parte de la serie Microsoft Windows Development.*

## <a name="see-also"></a>Consulte también

- [Instrucciones de diseño de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Instrucciones de diseño de excepciones](../../../docs/standard/design-guidelines/exceptions.md)
