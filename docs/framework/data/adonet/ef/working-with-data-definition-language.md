---
title: Trabajar con lenguaje de definición de datos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: 83d6fc1294f6aa37389db9e517b02866ef000b50
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854224"
---
# <a name="working-with-data-definition-language"></a>Trabajar con lenguaje de definición de datos
A partir de la versión 4 de .NET Framework, el Entity Framework admite el lenguaje de definición de datos (DDL). Esto le permite crear o eliminar una instancia de la base de datos basada en la cadena de conexión y los metadatos del modelo de almacenamiento (SSDL).  
  
 Los siguientes métodos de <xref:System.Data.Objects.ObjectContext> utilizan la cadena de conexión y el contenido SSDL para crear o eliminar la base de datos, comprobar si la base de datos existe y ver el script DDL generado:  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
> La ejecución de los comandos DDL supone que se cuenta con los permisos necesarios.  
  
 Los métodos enumerados anteriormente delegan la mayoría del trabajo en el proveedor de datos de ADO.NET subyacente. Es responsabilidad del proveedor asegurarse de que la convención de nomenclatura utilizada para generar los objetos de base de datos es coherente con las convenciones utilizadas para las consultas y las actualizaciones.  
  
 En el siguiente ejemplo se muestra cómo generar la base de datos en función del modelo existente. También agrega un nuevo objeto entidad al contexto del objeto y, a continuación, lo guarda en la base de datos.  
  
## <a name="procedures"></a>Procedimientos  
  
### <a name="to-define-a-database-based-on-the-existing-model"></a>Para definir una base de datos en función del modelo existente  
  
1. Cree una aplicación de consola.  
  
2. Agregue un modelo existente a la aplicación.  
  
    1. Agregue un modelo vacío denominado `SchoolModel`. Para crear un modelo vacío, vea el [procedimiento: Cree un nuevo tema del archivo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) . edmx.  
  
     El archivo SchoolModel.edmx se añade al proyecto.  
  
    1. Copie el contenido conceptual, de almacenamiento y de asignación para el modelo School en el tema [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) .  
  
    2. Abra el archivo SchoolModel.edmx y pegue el contenido dentro de las etiquetas `edmx:Runtime`.  
  
3. Agregue el siguiente código a la función principal. El código inicializa la cadena de conexión en el servidor de bases de datos, ve el script DDL, crea la base de datos, agrega una nueva entidad al contexto y guarda los cambios en la base de datos.  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
