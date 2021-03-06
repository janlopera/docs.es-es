---
title: Procedimiento Definir una plantilla de un control GroupBox
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
ms.openlocfilehash: dd53af87ec2d12b2ed0dcf2b23374d76e8f631a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910525"
---
# <a name="how-to-define-a-groupbox-template"></a>Procedimiento Definir una plantilla de un control GroupBox
En este ejemplo se muestra cómo crear una plantilla para un <xref:System.Windows.Controls.GroupBox> control.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se define un <xref:System.Windows.Controls.GroupBox> plantilla de control mediante el uso de un <xref:System.Windows.Controls.Grid> control para el diseño. La plantilla utiliza un <xref:System.Windows.Controls.BorderGapMaskConverter> para definir el borde de la <xref:System.Windows.Controls.GroupBox> para que el borde no oculte el <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> contenido.  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a>Vea también

- <xref:System.Windows.Controls.GroupBox>
- [Cómo: Crear un control GroupBox](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748321(v=vs.90))
