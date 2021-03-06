---
title: Procedimiento para crear un contrato de datos básico para una clase o estructura
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
ms.openlocfilehash: 15c59f3ee7cbefafef7a304cfd1477685fff68f2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968459"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a>Procedimiento para crear un contrato de datos básico para una clase o estructura
En este tema se muestran los pasos básicos para crear un contrato de datos usando una clase o estructura. Para obtener más información sobre los contratos de datos y cómo se usan, consulte [uso de contratos de datos](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Para ver un tutorial que le guía por los pasos necesarios para crear un servicio y un cliente de Windows Communication Foundation básico (WCF), consulte el [tutorial de introducción](../../../../docs/framework/wcf/getting-started-tutorial.md). Para obtener una aplicación de ejemplo funcional formada por un servicio y un cliente básicos, vea [contrato de datos básico](../../../../docs/framework/wcf/samples/basic-data-contract.md).  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a>Crear un contrato de datos básicos para una clase o estructura  
  
1. Declare que el tipo tiene un contrato de datos aplicando el atributo <xref:System.Runtime.Serialization.DataContractAttribute> a la clase. Observe que todos los tipos públicos, incluidos aquéllos sin atributos, son serializables. <xref:System.Runtime.Serialization.DataContractSerializer> deduce un contrato de datos si el atributo <xref:System.Runtime.Serialization.DataContractAttribute> está ausente. Para obtener más información, vea [tipos serializables](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
2. Defina los miembros (propiedades, campos o eventos) que se serializan aplicando el atributo <xref:System.Runtime.Serialization.DataMemberAttribute> a cada miembro. Estos miembros se denominan miembros de datos. De forma predeterminada, todos los tipos públicos son serializables. Para obtener más información, vea [tipos serializables](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
    > [!NOTE]
    > Puede aplicar el atributo <xref:System.Runtime.Serialization.DataMemberAttribute> a los campos privados y, de este modo, se expondrán los datos a otros. Asegúrese de que el miembro no contiene información confidencial.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, se muestra cómo crear un contrato de datos para el tipo `Person` mediante la aplicación de los atributos <xref:System.Runtime.Serialization.DataContractAttribute> y <xref:System.Runtime.Serialization.DataMemberAttribute> a la clase y sus miembros.  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a>Vea también

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Utilización de contratos de datos](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Tutorial de introducción](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [Introducción](../../../../docs/framework/wcf/samples/getting-started-sample.md)
