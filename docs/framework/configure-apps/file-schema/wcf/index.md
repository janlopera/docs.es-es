---
title: Esquema de configuración de WCF
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: 866b0639f4391e1898bbe36e458df87e3c24bfff
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448664"
---
# <a name="wcf-configuration-schema"></a>Esquema de configuración de WCF
Los elementos de configuración de Windows Communication Foundation (WCF) le permiten configurar el servicio WCF y las aplicaciones cliente. Puede usar la [herramienta Editor de configuración (SvcConfigEditor.exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) para crear y modificar los archivos de configuración para clientes y servicios. Puesto que los archivos de certificado tiene el formato como XML, debe familiarizarse con XML si desea modificarlos manualmente con un editor de texto. De lo contrario, puede encontrarse con problemas como no encontrar un atributo o una etiqueta de elemento XML. Esto se debe a que los atributos y las etiquetas del elemento XML distinguen entre mayúsculas y minúsculas.  
  
 El sistema de configuración de WCF se basa en el espacio de nombres <xref:System.Configuration>. Por consiguiente, puede usar todas las características estándar proporcionadas por el espacio de nombres <xref:System.Configuration>, como el bloqueo de configuración, el cifrado y la combinación para aumentar la seguridad de su aplicación y su configuración. Para obtener más información acerca del uso de estos conceptos, consulte los temas siguientes.  
  
 [Cifrar información de configuración](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100))  
  
 [Bloquear opciones de configuración](https://docs.microsoft.com/previous-versions/aspnet/55th21y4(v=vs.100))  
  
 En esta sección se describen todos los valores posibles de cada elemento de configuración y cómo interactúa con otros elementos de configuración de WCF. En el mapa siguiente se muestra el esquema de configuración de WCF:  
  
 ![Diagrama que muestra el esquema de configuración de WCF.](./media/index/windows-communication-foundation-configuration-schema.gif)  
  
> [!CAUTION]
> Debe proteger las secciones de configuración de WCF en los archivos de configuración de la aplicación (App. config) con las listas de Access Control (ACL) adecuadas para evitar posibles amenazas de seguridad.  Por ejemplo, debería asegurarse de que sólo las personas adecuadas pueden tener acceso o modificar la configuración de seguridad en enlaces de la aplicación, o la sección modelo de servicio del archivo de configuración de un servicio.  
  
## <a name="in-this-section"></a>En esta sección  
 [\<system.serviceModel>](system-servicemodel.md)  
 Describe el elemento `ServiceModel`.  
  
 [\<system.serviceModel.activation>](system-servicemodel-activation.md)  
 Configura la herramienta SMSvcHost.exe.  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
 El elemento de nivel superior para establecer opciones al usar serializadores como <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Configurar aplicaciones de Windows Communication Foundation](../../../wcf/configuring-services.md)  
 Describe cómo configurar los clientes y servicios de WCF.
