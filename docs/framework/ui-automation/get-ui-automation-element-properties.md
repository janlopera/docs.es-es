---
title: Obtener propiedades del elemento de la UI Automation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: 1b82302ff89d2e8407871cbfba6c10e8322ac4e7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435501"
---
# <a name="get-ui-automation-element-properties"></a>Obtener propiedades del elemento de la UI Automation
> [!NOTE]
> Esta documentación está dirigida a los desarrolladores de .NET Framework que quieran usar las clases [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] administradas definidas en el espacio de nombres <xref:System.Windows.Automation>. Para ver la información más reciente acerca de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: automatización de la interfaz de usuario](/windows/win32/winauto/entry-uiauto-win32).  
  
 En este tema se muestra cómo recuperar las propiedades de un elemento [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
### <a name="get-a-current-property-value"></a>Obtiene un valor de propiedad actual.  
  
1. Obtenga el <xref:System.Windows.Automation.AutomationElement> cuya propiedad desea obtener.  
  
2. Llame a <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, o recupere la estructura de la propiedad <xref:System.Windows.Automation.AutomationElement.Current%2A> y obtenga el valor de uno de sus miembros.  
  
### <a name="get-a-cached-property-value"></a>Obtiene el valor de una propiedad almacenada en caché  
  
1. Obtenga el <xref:System.Windows.Automation.AutomationElement> cuya propiedad desea obtener. La propiedad se debe haber especificado en el <xref:System.Windows.Automation.CacheRequest>.  
  
2. Llame a <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, o recupere la estructura de la propiedad <xref:System.Windows.Automation.AutomationElement.Cached%2A> y obtenga el valor de uno de sus miembros.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestran varias maneras de recuperar las propiedades actuales de un <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>Vea también

- [UI Automation Properties for Clients](ui-automation-properties-for-clients.md)
- [Uso del almacenamiento en caché en la Automatización de la interfaz de usuario](use-caching-in-ui-automation.md)
- [Caching in UI Automation Clients](caching-in-ui-automation-clients.md)
