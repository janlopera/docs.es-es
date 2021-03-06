---
title: Ocultar columnas en el control DataGridView mediante el diseñador
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: c5344e10a69d86b1733f5462f9c2df0f0e71b8d5
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628844"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Cómo: Ocultar columnas en el control DataGridView de formularios Windows Forms mediante el Diseñador
Algunas veces querrá mostrar solo algunas de las columnas que están disponibles en un control <xref:System.Windows.Forms.DataGridView> de Windows Forms. Por ejemplo, puede que desee mostrar una columna de sueldo de empleado a los usuarios con credenciales de administración mientras la ocultan de otros usuarios. Como alternativa, puede enlazar el control a un origen de datos que contenga muchas columnas, solo algunas de las cuales desea mostrar. En este caso, normalmente se quitarán las columnas que no le interesa Mostrar en lugar de ocultarlas. Para obtener más información, vea [Cómo: agregar y quitar columnas en el control DataGridView Windows Forms mediante el diseñador](add-and-remove-columns-in-the-datagrid-using-the-designer.md).

 El procedimiento siguiente requiere un proyecto de **aplicación Windows** con un formulario que contenga un control <xref:System.Windows.Forms.DataGridView>. Para obtener información sobre cómo configurar este tipo de proyecto, vea [Cómo: crear un proyecto de aplicación de Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) y [Cómo: agregar controles a Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-hide-a-column-using-the-designer"></a>Para ocultar una columna mediante el diseñador

1. Haga clic en el glifo de acciones del diseñador (![flecha negra pequeña](./media/designer-actions-glyph.gif)) en la esquina superior derecha del control <xref:System.Windows.Forms.DataGridView> y, a continuación, seleccione **Editar columnas**.

2. Seleccione una columna de la lista **columnas seleccionadas** .

3. En la cuadrícula **propiedades de columna** , establezca la propiedad <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> en `false`.

    > [!NOTE]
    > También puede ocultar una columna al agregarla desactivando la casilla **visible** en el cuadro de diálogo **Agregar columna** .

## <a name="see-also"></a>Consulte también

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [Agregar y quitar columnas en el control DataGridView de Windows Forms mediante el Diseñador](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Cómo: crear un proyecto de aplicación de Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Cómo: Agregar controles a Windows Forms](how-to-add-controls-to-windows-forms.md)
