---
title: 'Tutorial: Crear una aplicación accesible basada en Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
dev_langs:
- csharp
- vb
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
ms.openlocfilehash: b8f0c7c4584505d382e78aca68e2e99c9fa7748f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834626"
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a>Tutorial: Crear una aplicación accesible basada en Windows

Crear una aplicación accesible conlleva importantes implicaciones empresariales. Muchos gobiernos tienen normativas sobre accesibilidad aplicadas a la compra de software. El logotipo “Certificado para Windows” incluye requisitos de accesibilidad. Tan solo en EE. UU hay aproximadamente unos 30 millones de ciudadanos, muchos de ellos clientes potenciales, que se ven afectados por la accesibilidad del software.

En este tutorial se tratan los cinco requisitos de accesibilidad para el logotipo “Certificado para Windows”. Según estos requisitos, una aplicación accesible deberá:

- Admitir la configuración de la entrada, la fuente, el color y el tamaño en el Panel de control. La barra de menús, la barra de título, los bordes y la barra de estado cambiarán de tamaño cuando el usuario cambie la configuración del Panel de control. No se requiere ningún otro cambio en los controles o el código en esta aplicación.

- Admitir el modo de contraste alto.

- Proporcionar acceso mediante teclado a todas las características (y documentarlo).

- Exponer la ubicación del foco del teclado de manera visual y mediante programación.

- Evitar ofrecer información importante solo mediante sonido.

Para más información, consulte [Recursos para diseñar aplicaciones accesibles](/visualstudio/ide/reference/resources-for-designing-accessible-applications).

Para información sobre la compatibilidad con diversas distribuciones de teclado, consulte [Procedimientos recomendados para desarrollar aplicaciones de uso internacional](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).

## <a name="creating-the-project"></a>Crear el proyecto

En este tutorial se crea la interfaz de usuario de una aplicación que admite pedidos de pizzas. La interfaz consta de un <xref:System.Windows.Forms.TextBox> para el nombre del cliente, un grupo <xref:System.Windows.Forms.RadioButton> para seleccionar el tamaño de la pizza, un <xref:System.Windows.Forms.CheckedListBox> para seleccionar los ingredientes, dos controles de botón (Button) con la etiqueta Order y Cancel y un menú con un comando Exit.

El usuario escribe el nombre del cliente, el tamaño de la pizza y los ingredientes que desea. Cuando el usuario hace clic en el botón Order, aparece un cuadro de mensaje con un resumen del pedido y su costo, y los controles se borran y quedan listos para el siguiente pedido. Cuando el usuario hace clic en el botón Cancelar, los controles se borran y quedan listos para el siguiente pedido. Cuando el usuario hace clic en el elemento de menú Exit, el programa se cierra.

El énfasis de este tutorial no recae en el código para un sistema de pedidos de venta directa, sino en la accesibilidad de la interfaz de usuario. En el tutorial se muestran las características de accesibilidad de varios controles de uso frecuente, como botones, botones de radio, cuadros de texto y etiquetas.

#### <a name="to-begin-making-the-application"></a>Para comenzar a crear la aplicación

- Cree una nueva aplicación de Windows en Visual Basic o C#visual. Asigne al proyecto el nombre **PizzaOrder**. Para obtener más información, vea [crear nuevas soluciones y proyectos](/visualstudio/ide/creating-solutions-and-projects).

## <a name="adding-the-controls-to-the-form"></a>Agregar controles al formulario

Cuando agregue controles a un formulario, tenga en cuenta las siguientes instrucciones para crear una aplicación accesible:

- Establezca las propiedades <xref:System.Windows.Forms.Control.AccessibleDescription%2A> y <xref:System.Windows.Forms.Control.AccessibleName%2A>. En este ejemplo, la configuración predeterminada para <xref:System.Windows.Forms.Control.AccessibleRole%2A> es suficiente. Para más información sobre las propiedades de accesibilidad, consulte [Proporcionar información de accesibilidad de controles en Windows Forms](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).

- Establezca el tamaño de la fuente en 10 puntos o más.

  > [!NOTE]
  > Si establece el tamaño de la fuente del formulario en 10 al empezar, todos los controles que agregue posteriormente al formulario tendrán un tamaño de fuente de 10.

- Asegúrese de que los controles Label que describen controles TextBox precedan inmediatamente al TextBox en el orden de tabulación.

- Agregue una tecla de acceso, utilizando el carácter "&", a <xref:System.Windows.Forms.Control.Text%2A> la propiedad de cualquier control al que el usuario desee navegar.

- Agregue una tecla de acceso, utilizando el carácter "&", a <xref:System.Windows.Forms.Control.Text%2A> la propiedad de la etiqueta que precede a un control al que el usuario puede desear navegar. Establezca la propiedad <xref:System.Windows.Forms.Label.UseMnemonic%2A> de las etiquetas en `true`, de modo que el foco se centre en el siguiente control del orden de tabulación cuando el usuario presione la tecla de acceso.

- Agregue teclas de acceso a todos los elementos de menú.

#### <a name="to-make-your-windows-application-accessible"></a>Para hacer accesible la aplicación Windows

- Agregue los controles al formulario y establezca las propiedades como se describe a continuación. Consulte la imagen al final de la tabla para ver un modelo de cómo organizar los controles en el formulario.

   |Object|Property|Valor|
   |------------|--------------|-----------|
   |Form1|AccessibleDescription|Formulario de pedido|
   ||AccessibleName|Formulario de pedido|
   ||Tamaño de fuente|10|
   ||Text|Pizza Order Form|
   |PictureBox|Name|logo|
   ||AccessibleDescription|Porción de pizza|
   ||AccessibleName|Logotipo de la compañía|
   ||Image|Cualquier icono o mapa de bits|
   |Etiqueta|Name|companyLabel|
   ||Text|Good Pizza|
   ||TabIndex|1|
   ||AccessibleDescription|Nombre de la compañía|
   ||AccessibleName|Nombre de la compañía|
   ||Backcolor|Azul|
   ||Forecolor|Amarillo|
   ||Tamaño de fuente|18|
   |Etiqueta|Name|customerLabel|
   ||Text|&Nombre|
   ||TabIndex|2|
   ||AccessibleDescription|Etiqueta de nombre de cliente|
   ||AccessibleName|Etiqueta de nombre de cliente|
   ||UseMnemonic|True|
   |TextBox|Name|customerName|
   ||Text|(ninguno)|
   ||TabIndex|3|
   ||AccessibleDescription|Nombre del cliente|
   ||AccessibleName|Nombre del cliente|
   |GroupBox|Name|sizeOptions|
   ||AccessibleDescription|Opciones de tamaño de pizza|
   ||AccessibleName|Opciones de tamaño de pizza|
   ||Text|Pizza size|
   ||TabIndex|4|
   |RadioButton|Name|smallPizza|
   ||Text|&Small $6.00|
   ||Activado|True|
   ||TabIndex|0|
   ||AccessibleDescription|Pizza pequeña|
   ||AccessibleName|Pizza pequeña|
   |RadioButton|Name|largePizza|
   ||Text|&Large $10.00|
   ||TabIndex|1|
   ||AccessibleDescription|Pizza grande|
   ||AccessibleName|Pizza grande|
   |Etiqueta|Name|toppingsLabel|
   ||Text|&Toppings ($0.75 each)|
   ||TabIndex|5|
   ||AccessibleDescription|Etiqueta de ingredientes|
   ||AccessibleName|Etiqueta de ingredientes|
   ||UseMnemonic|True|
   |CheckedListBox|Name|toppings|
   ||TabIndex|6|
   ||AccessibleDescription|Ingredientes disponibles|
   ||AccessibleName|Ingredientes disponibles|
   ||Elementos|Pepperoni, Sausage, Mushrooms|
   |Botón|Name|orden|
   ||Text|&Ordenar|
   ||TabIndex|7|
   ||AccessibleDescription|Total del pedido|
   ||AccessibleName|Total del pedido|
   |Botón|Name|cancel|
   ||Text|&Cancelar|
   ||TabIndex|8|
   ||AccessibleDescription|Cancelar el pedido|
   ||AccessibleName|Cancelar pedido|
   |MainMenu|Name|theMainMenu|
   |MenuItem|Name|fileCommands|
   ||Text|&Archivo|
   |MenuItem|Name|exitApp|
   ||Text|&Salir|

   El formulario tendrá un aspecto similar al de la siguiente imagen:

   ![El formulario de pedido de pizza con un cuadro de texto de nombre y la selección de tamaño y de subpings.](./media/walkthrough-creating-an-accessible-windows-based-application/visual-basic-pizza-order-form.gif)

## <a name="supporting-high-contrast-mode"></a>Compatibilidad con el modo de contraste alto

El modo de contraste alto es una configuración de sistema de Windows que mejora la legibilidad mediante el uso de colores de contraste y tamaños de fuente que son beneficiosos para los usuarios con discapacidades visuales. La <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> propiedad se proporciona para determinar si el modo de contraste alto está establecido.

Si SystemInformation.HighContrast es `true`, la aplicación debe:

- Mostrar todos los elementos de interfaz de usuario mediante la combinación de colores del sistema

- Ofrecer mediante indicaciones visuales o sonoras cualquier información que se ofrezca mediante el color. Por ejemplo, si se resaltan determinados elementos de una lista mediante una fuente de color rojo, también se podría aplicar negrita a la fuente para que el usuario pueda ver, sin percibir el color, que los elementos están resaltados.

- Omitir las imágenes o tramas detrás del texto

La aplicación debe comprobar la configuración de <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> cuando se inicia la aplicación y responder al evento de sistema <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>. El evento <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> se genera siempre que el valor de <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> cambia.

En nuestra aplicación, el único elemento que no usa la configuración de color del sistema es `lblCompanyName`. La <xref:System.Drawing.SystemColors> clase se usa para cambiar la configuración de color de la etiqueta a los colores del sistema seleccionados por el usuario.

#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a>Para habilitar el modo de contraste alto de forma eficaz

1. Cree un método para establecer los colores de la etiqueta en los colores del sistema.

    ```vb
    Private Sub SetColorScheme()
        If SystemInformation.HighContrast Then
            companyLabel.BackColor = SystemColors.Window
            companyLabel.ForeColor = SystemColors.WindowText
        Else
            companyLabel.BackColor = Color.Blue
            companyLabel.ForeColor = Color.Yellow
        End If
    End Sub
    ```

    ```csharp
    private void SetColorScheme()
    {
        if (SystemInformation.HighContrast)
        {
            companyLabel.BackColor = SystemColors.Window;
            companyLabel.ForeColor = SystemColors.WindowText;
        }
        else
        {
            companyLabel.BackColor = Color.Blue;
            companyLabel.ForeColor = Color.Yellow;
        }
    }
    ```

2. Llame al procedimiento `SetColorScheme` en el constructor del formulario (`Public Sub New()` en Visual Basic y `public Form1()` en Visual C#). Para acceder al constructor en Visual Basic, deberá expandir la región denominada **Código generado por el Diseñador de Windows Forms**.

    ```vb
    Public Sub New()
        MyBase.New()
        InitializeComponent()
        SetColorScheme()
    End Sub
    ```

    ```csharp
    public Form1()
    {
        InitializeComponent();
        SetColorScheme();
    }
    ```

3. Cree un procedimiento de evento con la firma apropiada para responder al evento <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.

    ```vb
    Protected Sub UserPreferenceChanged(sender As Object, _
    e As Microsoft.Win32.UserPreferenceChangedEventArgs)
        SetColorScheme()
    End Sub
    ```

    ```csharp
    public void UserPreferenceChanged(object sender,
    Microsoft.Win32.UserPreferenceChangedEventArgs e)
    {
        SetColorScheme();
    }
    ```

4. Agregue código al constructor del formulario, después de la llamada a `InitializeComponents`, para enlazar el procedimiento de evento al evento del sistema. Este método llama al procedimiento `SetColorScheme`.

    ```vb
    Public Sub New()
        MyBase.New()
        InitializeComponent()
        SetColorScheme()
        AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _
           AddressOf Me.UserPreferenceChanged
    End Sub
    ```

    ```csharp
    public Form1()
    {
        InitializeComponent();
        SetColorScheme();
        Microsoft.Win32.SystemEvents.UserPreferenceChanged
           += new Microsoft.Win32.UserPreferenceChangedEventHandler(
           this.UserPreferenceChanged);
    }
    ```

5. Agregue código al método <xref:System.Windows.Forms.Control.Dispose%2A> del formulario, antes de llamar al método <xref:System.Windows.Forms.Control.Dispose%2A> de la clase base, para liberar el evento cuando se cierre la aplicación. Para tener acceso al método <xref:System.Windows.Forms.Control.Dispose%2A> en Visual Basic, deberá expandir la región denominada Código generado por el Diseñador de Windows Forms.

    > [!NOTE]
    > El código de evento del sistema ejecuta un subproceso independiente de la aplicación principal. Si no libera el evento, el código que enlazó al evento se ejecutará incluso después de cerrar el programa.

    ```vb
    Protected Overloads Overrides Sub Dispose(ByVal disposing As Boolean)
        If disposing AndAlso components IsNot Nothing Then
            components.Dispose()
        End If
        RemoveHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _
           AddressOf Me.UserPreferenceChanged
        MyBase.Dispose(disposing)
    End Sub
    ```

    ```csharp
    protected override void Dispose(bool disposing)
    {
        if(disposing && components != null)
        {
            components.Dispose();
        }
        Microsoft.Win32.SystemEvents.UserPreferenceChanged
           -= new Microsoft.Win32.UserPreferenceChangedEventHandler(
           this.UserPreferenceChanged);
        base.Dispose( disposing );
    }
    ```

6. Presione F5 para ejecutar la aplicación.

## <a name="conveying-important-information-by-means-other-than-sound"></a>Ofrecer información importante por medios diferentes del sonido

En esta aplicación no se muestra ninguna información solo mediante sonido. Si usa sonido en la aplicación, también debe proporcionar la información de algún otro modo.

#### <a name="to-supply-information-by-some-other-means-than-sound"></a>Para proporcionar información por otros medios distintos del sonido

1. Haga parpadear la barra de título flash con la función de API de Windows FlashWindow. Para obtener un ejemplo de cómo llamar a las funciones de la [API de Windows, vea Tutorial: Llamando a las](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)API de Windows.

    > [!NOTE]
    > El usuario puede tener el servicio SoundSentry de Windows habilitado, que también hace que la ventana parpadee cuando se reproducen los sonidos del sistema a través de los altavoces integrados en el equipo.

2. Muestre la información importante en una ventana no modal para que el usuario pueda responder a ella.

3. Muestre un cuadro de mensaje que adquiera el foco del teclado. Evite usar este método cuando el usuario esté escribiendo.

4. Muestre un indicador de estado en el área de notificación de estado de la barra de tareas. Para ver detalles, consulte [Cómo: Agregar iconos de aplicación a la barra de tareas con el componente NotifyIcon de Windows Forms](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).

## <a name="testing-the-application"></a>Probar la aplicación

Antes de implementar la aplicación, pruebe las características de accesibilidad que se han implementado.

#### <a name="to-test-accessibility-features"></a>Para probar las características de accesibilidad

1. Para probar el acceso mediante teclado, desconecte el mouse y desplácese por cada característica de la interfaz de usuario usando solo el teclado. Asegúrese de que todas las tareas pueden realizarse utilizando únicamente el teclado.

2. Para probar la compatibilidad de contraste alto, elija el icono de opciones de accesibilidad en el Panel de control. Haga clic en la ficha Pantalla y seleccione la casilla Usar contraste alto. Desplácese por todos los elementos de la interfaz de usuario para asegurarse de que se reflejan los cambios de color y fuente. Asegúrese también de que se omiten las imágenes o las tramas que se representan detrás del texto.

    > [!NOTE]
    > Windows NT 4 no tiene un icono de opciones de accesibilidad en el Panel de control. Por lo tanto, este procedimiento para cambiar el valor SystemInformation.HighContrast no funciona en Windows NT 4.

3. Hay otras herramientas disponibles para probar la accesibilidad de una aplicación.

4. Para probar la exposición del foco de teclado, ejecute la Lupa. (Para abrirla, haga clic en **Inicio**, elija **Programas**, **Accesorios** y **Accesibilidad**, y haga clic en **Lupa**). Desplácese por la interfaz de usuario usando tanto la tabulación de teclado como el mouse. Asegúrese de que la **Lupa** siga correctamente todos los desplazamientos.

5. Para probar la exposición de los elementos de pantalla, ejecute Inspeccionar y use el mouse y la tecla TAB para desplazarse a cada elemento. Asegúrese de que la información contenida en los campos de nombre, estado, rol, ubicación y valor de la ventana Inspeccionar es significativa para el usuario en relación a cada objeto de la interfaz de usuario.
