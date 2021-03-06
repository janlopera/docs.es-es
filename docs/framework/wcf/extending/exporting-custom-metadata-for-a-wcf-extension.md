---
title: Exportación de metadatos personalizados para una extensión WCF
ms.date: 03/30/2017
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
ms.openlocfilehash: 540dd9011be83d349495a0b05283b83f3d55dc2c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797186"
---
# <a name="exporting-custom-metadata-for-a-wcf-extension"></a>Exportación de metadatos personalizados para una extensión WCF
En Windows Communication Foundation (WCF), la exportación de metadatos es el proceso de describir extremos de servicio y proyectarlos en una representación paralela y estandarizada que pueden usar los clientes para entender cómo utilizar el servicio. Los metadatos personalizados están compuestos de elementos XML que los exportadores de metadatos proporcionados por el sistema no pueden exportar. Normalmente, esto incluye elementos WSDL personalizados para los elementos de enlace y los comportamientos definidos por el usuario y las aserciones de directiva sobre las funciones y requisitos de los enlaces y contratos.  
  
 Esta sección describe la exportación de WSDL o aserciones de directivas personalizados y no se centra en el propio proceso de exportación. Para obtener más información sobre cómo usar los tipos que exportan e importan metadatos independientemente de si los metadatos son personalizados o construidos por el sistema, vea [exportar e importar metadatos](../feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Información general  
 Cuando los metadatos se publican mediante <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> el <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType>, se examinan y se generan XSD y WSDL, incluidas las aserciones de Directiva, para todos los contratos y enlaces que WCF puede admitir mediante enlaces y atributos proporcionados por el sistema. Sin embargo, los atributos de comportamiento o los elementos de enlace personalizados requieren la compatibilidad antes de que se puedan exportar correctamente.  
  
 En esta sección se describe:  
  
1. Cómo implementar y utilizar la interfaz <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType>, que expone los datos de generación de WSDL a usted antes de publicar el WSDL.  
  
2. Cómo implementar y utilizar la interfaz <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType>, que le expone los datos de la directiva antes de exportar las aserciones de directiva a datos del WSDL.  
  
 Para obtener más información sobre cómo importar WSDL y aserciones de directivas personalizadas, vea [importar metadatos personalizados para una extensión WCF](importing-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-custom-wsdl-elements"></a>Exportación de elementos WSDL personalizados  
 Implemente <xref:System.ServiceModel.Description.IWsdlExportExtension> en un comportamiento de la operación, comportamiento del contrato, comportamiento del extremo o elemento de enlace (<xref:System.ServiceModel.Description.IOperationBehavior>, <xref:System.ServiceModel.Description.IContractBehavior>, <xref:System.ServiceModel.Description.IEndpointBehavior>o <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> respectivamente) e inserte los comportamientos o elementos de enlace en la descripción del servicio que está intentando exportar. (Para obtener más información sobre cómo insertar comportamientos, vea [configuración y extensión del tiempo de ejecución con comportamientos](configuring-and-extending-the-runtime-with-behaviors.md)). Se llama a <xref:System.ServiceModel.Description.IWsdlExportExtension> para cada punto de conexión y cada punto de conexión exporta primero el contrato si aún no se ha exportado. Puede participar en cualquier proceso de exportación, dependiendo de sus necesidades:  
  
- Utilice el <xref:System.ServiceModel.Description.WsdlContractConversionContext> para modificar los metadatos exportados en el método <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A>.  
  
- Utilice <xref:System.ServiceModel.Description.WsdlEndpointConversionContext> para modificar los metadatos exportados para el punto de conexión en el método <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A>.  
  
 Se llama al método <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> en todas las implementaciones de <xref:System.ServiceModel.Description.IWsdlExportExtension> dentro de la instancia de  <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> que se está exportando.  Se llama al método <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> en todas las implementaciones <xref:System.ServiceModel.Description.IWsdlExportExtension> con la instancia <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> que se está exportando.  
  
 Para obtener más información, consulte [Cómo Exportar WSDL](how-to-export-custom-wsdl.md) personalizado y la [publicación WSDL personalizada](../samples/custom-wsdl-publication.md)de ejemplo.  
  
## <a name="exporting-custom-policy-assertions"></a>Exportación de aserciones de directivas personalizadas  
 Implemente <xref:System.ServiceModel.Description.IPolicyExportExtension> en un <xref:System.ServiceModel.Channels.BindingElement> y agregue el elemento de enlace al enlace para escribir las aserciones de directivas personalizadas sobre compatibilidad de enlaces y funciones de contrato en WSDL. Se llama a <xref:System.ServiceModel.Description.IPolicyExportExtension> una vez al exportar el elemento de enlace implementado en un enlace y pasa <xref:System.ServiceModel.Description.PolicyConversionContext> al método <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A>. Puede utilizar los métodos en la instancia <xref:System.ServiceModel.Description.PolicyConversionContext> para agregar a las aserciones de directiva adjuntas al enlace WSDL en el mensaje, operación o sujetos del extremo.  
  
 Para obtener más información, vea [Cómo: Exportar aserciones](how-to-export-custom-policy-assertions.md)de directivas personalizadas.  
  
## <a name="see-also"></a>Vea también

- [Procedimientos: Exportar WSDL personalizado](how-to-export-custom-wsdl.md)
- [Cómo: Exportar aserciones de directivas personalizadas](how-to-export-custom-policy-assertions.md)
- [Importación de metadatos personalizados para una extensión WCF](importing-custom-metadata-for-a-wcf-extension.md)
