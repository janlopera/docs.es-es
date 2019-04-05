---
title: Procedimiento para portar una aplicación WPF a .NET Core 3.0
description: Aprenderá a portar una aplicación de Windows Presentation Foundation de .NET Framework a .NET Core 3.0 para Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/27/2019
ms.custom: ''
ms.openlocfilehash: 29ea308ee5147cfb18df312887e933615e349803
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2019
ms.locfileid: "58677559"
---
# <a name="how-to-port-a-wpf-desktop-app-to-net-core"></a><span data-ttu-id="70482-103">Procedimiento Procedimiento para portar una aplicación de escritorio WPF a .NET Core</span><span class="sxs-lookup"><span data-stu-id="70482-103">How to: Port a WPF desktop app to .NET Core</span></span>

<span data-ttu-id="70482-104">En este artículo se describe cómo portar la aplicación de escritorio basada en Windows Presentation Foundation (WPF) de .NET Framework a .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="70482-104">This article describes how to port your Windows Presentation Foundation-based (WPF) desktop app from .NET Framework to .NET Core 3.0.</span></span> <span data-ttu-id="70482-105">El SDK de .NET Core 3.0 incluye compatibilidad para las aplicaciones WPF.</span><span class="sxs-lookup"><span data-stu-id="70482-105">The .NET Core 3.0 SDK includes support for WPF applications.</span></span> <span data-ttu-id="70482-106">WPF sigue siendo un marco de solo Windows y únicamente se ejecuta en Windows.</span><span class="sxs-lookup"><span data-stu-id="70482-106">WPF is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="70482-107">En este ejemplo se usa la CLI del SDK de .NET Core para crear y administrar un proyecto.</span><span class="sxs-lookup"><span data-stu-id="70482-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="70482-108">En este artículo, se usan diferentes nombres para identificar los tipos de archivos que se utilizan para la migración.</span><span class="sxs-lookup"><span data-stu-id="70482-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="70482-109">Al migrar su proyecto, sus archivos se nombrarán de manera diferente, así que establezca una relación mental con los que se enumeran a continuación:</span><span class="sxs-lookup"><span data-stu-id="70482-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="70482-110">Archivo</span><span class="sxs-lookup"><span data-stu-id="70482-110">File</span></span> | <span data-ttu-id="70482-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="70482-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="70482-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="70482-112">**MyApps.sln**</span></span> | <span data-ttu-id="70482-113">Nombre del archivo de la solución.</span><span class="sxs-lookup"><span data-stu-id="70482-113">The name of the solution file.</span></span> |
| <span data-ttu-id="70482-114">**MyWPF.csproj**</span><span class="sxs-lookup"><span data-stu-id="70482-114">**MyWPF.csproj**</span></span> | <span data-ttu-id="70482-115">Nombre del proyecto de WPF de .NET Framework para portar.</span><span class="sxs-lookup"><span data-stu-id="70482-115">The name of the .NET Framework WPF project to port.</span></span> |
| <span data-ttu-id="70482-116">**MyWPFCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="70482-116">**MyWPFCore.csproj**</span></span> | <span data-ttu-id="70482-117">Nombre del nuevo proyecto de .NET Core que crea.</span><span class="sxs-lookup"><span data-stu-id="70482-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="70482-118">**MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="70482-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="70482-119">Aplicación ejecutable WPF de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="70482-119">The .NET Core WPF app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="70482-120">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="70482-120">Prerequisites</span></span>

- <span data-ttu-id="70482-121">[Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=wpf+core) para cualquier trabajo de diseñador que desee hacer.</span><span class="sxs-lookup"><span data-stu-id="70482-121">[Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=wpf+core) for any designer work you want to do.</span></span>

  <span data-ttu-id="70482-122">Instale las cargas de trabajo de Visual Studio siguientes:</span><span class="sxs-lookup"><span data-stu-id="70482-122">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="70482-123">Desarrollo de escritorio de .NET</span><span class="sxs-lookup"><span data-stu-id="70482-123">.NET desktop development</span></span>
  - <span data-ttu-id="70482-124">Desarrollo multiplataforma de .NET</span><span class="sxs-lookup"><span data-stu-id="70482-124">.NET cross-platform development</span></span>

- <span data-ttu-id="70482-125">Proyecto de WPF en funcionamiento en una solución que se compila y ejecuta sin problemas.</span><span class="sxs-lookup"><span data-stu-id="70482-125">A working WPF project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="70482-126">El proyecto debe codificarse en C#.</span><span class="sxs-lookup"><span data-stu-id="70482-126">Your project must be coded in C#.</span></span> 
- <span data-ttu-id="70482-127">Instale la versión preliminar de [.NET Core 3.0](https://aka.ms/netcore3download) más reciente.</span><span class="sxs-lookup"><span data-stu-id="70482-127">Install the latest [.NET Core 3.0](https://aka.ms/netcore3download) preview.</span></span>


>[!NOTE]
><span data-ttu-id="70482-128">**Visual Studio 2017** no es compatible con proyectos de .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="70482-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="70482-129">**Visual Studio 2019 Preview/RC** admite proyectos de .NET Core 3.0, pero todavía no admite el diseñador de objetos visuales para los proyectos WPF de .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="70482-129">**Visual Studio 2019 Preview/RC** supports .NET Core 3.0 projects but doesn't yet support the visual designer for .NET Core 3.0 WPF projects.</span></span> <span data-ttu-id="70482-130">Para usar el diseñador de objetos visuales, debe tener un proyecto WPF de .NET en la solución en el que se compartan los archivos con el proyecto de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="70482-130">To use the visual designer, you must have a .NET WPF project in your solution that shares its files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="70482-131">Tenga en cuenta que:</span><span class="sxs-lookup"><span data-stu-id="70482-131">Consider</span></span>

<span data-ttu-id="70482-132">Al portar una aplicación WPF de .NET Framework, hay algunas cosas que debe tener en cuenta.</span><span class="sxs-lookup"><span data-stu-id="70482-132">When porting a .NET Framework WPF application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="70482-133">Compruebe que la aplicación cumple los requisitos para la migración.</span><span class="sxs-lookup"><span data-stu-id="70482-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="70482-134">Use el [analizador de portabilidad de .NET](../../standard/analyzers/portability-analyzer.md) para determinar si el proyecto se migrará a .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="70482-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="70482-135">Si el proyecto tiene problemas con .NET Core 3.0, el analizador le ayuda a identificar esos problemas.</span><span class="sxs-lookup"><span data-stu-id="70482-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="70482-136">Está usando otra versión de WPF.</span><span class="sxs-lookup"><span data-stu-id="70482-136">You're using a different version of WPF.</span></span>

    <span data-ttu-id="70482-137">Cuando se publicó .NET Core 3.0 Preview 1, WPF se puso a disposición de los usuarios como código abierto en GitHub.</span><span class="sxs-lookup"><span data-stu-id="70482-137">When .NET Core 3.0 Preview 1 was released, WPF went open-source on GitHub.</span></span> <span data-ttu-id="70482-138">El código para WPF de .NET Core es una bifurcación de la base de código de WPF de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="70482-138">The code for .NET Core WPF is a fork of the .NET Framework WPF code base.</span></span> <span data-ttu-id="70482-139">Es posible que existan algunas diferencias y la aplicación no se migre.</span><span class="sxs-lookup"><span data-stu-id="70482-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="70482-140">El [paquete de compatibilidad de Windows][compat-pack] puede ayudarle con la migración.</span><span class="sxs-lookup"><span data-stu-id="70482-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="70482-141">Algunas API que están disponibles en .NET Framework no están disponibles en .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="70482-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="70482-142">El [paquete de compatibilidad de Windows][compat-pack] agrega muchas de estas API y puede ayudar a que la aplicación WPF sea compatible con .NET Core.</span><span class="sxs-lookup"><span data-stu-id="70482-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your WPF app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="70482-143">Actualice los paquetes de NuGet utilizados por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="70482-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="70482-144">Siempre se recomienda usar las últimas versiones de los paquetes de NuGet antes de cualquier migración.</span><span class="sxs-lookup"><span data-stu-id="70482-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="70482-145">Si la aplicación hace referencia a cualquier paquete de NuGet, actualícelo a la versión más reciente.</span><span class="sxs-lookup"><span data-stu-id="70482-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="70482-146">Asegúrese de que la aplicación se compila correctamente.</span><span class="sxs-lookup"><span data-stu-id="70482-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="70482-147">Tras la actualización, si se han producido errores en el paquete, cambie el paquete a la versión más reciente que no rompa el código.</span><span class="sxs-lookup"><span data-stu-id="70482-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="70482-148">En Visual Studio 2019 Preview/RC todavía no se admite WPF Designer para .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="70482-148">Visual Studio 2019 Preview/RC doesn't yet support the WPF Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="70482-149">En la actualidad, debe mantener el archivo de proyecto de WPF de .NET Framework existente si quiere usar WPF Designer de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="70482-149">Currently, you need to keep your existing .NET Framework WPF project file if you want to use the WPF Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="70482-150">Creación de un nuevo proyecto de SDK</span><span class="sxs-lookup"><span data-stu-id="70482-150">Create a new SDK project</span></span>

<span data-ttu-id="70482-151">El nuevo proyecto .NET Core 3.0 que cree debe estar en un directorio diferente de su proyecto de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="70482-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="70482-152">Si ambos están en el mismo directorio, es posible que tenga conflictos con los archivos que se generan en el directorio **obj**.</span><span class="sxs-lookup"><span data-stu-id="70482-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="70482-153">En este ejemplo, se creará un directorio denominado **MyWPFAppCore** en el directorio **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="70482-153">In this example, you'll create a directory named **MyWPFAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore      <--- New folder for core project
```

<span data-ttu-id="70482-154">A continuación, tendrá que crear el proyecto **MyWPFCore.csproj** en el directorio **MyWPFAppCore**.</span><span class="sxs-lookup"><span data-stu-id="70482-154">Next, you need to create the **MyWPFCore.csproj** project in the **MyWPFAppCore** directory.</span></span> <span data-ttu-id="70482-155">Puede crear este archivo manualmente utilizando el editor de texto que prefiera.</span><span class="sxs-lookup"><span data-stu-id="70482-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="70482-156">Pegue el siguiente XML:</span><span class="sxs-lookup"><span data-stu-id="70482-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="70482-157">Si no desea crear manualmente el archivo de proyecto, puede usar Visual Studio o el SDK de .NET Core para generar el proyecto.</span><span class="sxs-lookup"><span data-stu-id="70482-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="70482-158">Sin embargo, debe eliminar todos los demás archivos generados por la plantilla de proyecto, excepto el archivo de proyecto.</span><span class="sxs-lookup"><span data-stu-id="70482-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="70482-159">Para usar el SDK, ejecute el siguiente comando desde el directorio **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="70482-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```cli
dotnet new wpf -o MyWPFAppCore -n MyWPFCore
```

<span data-ttu-id="70482-160">Después de crear **MyWPFCore.csproj**, la estructura de directorios debe ser similar a la siguiente:</span><span class="sxs-lookup"><span data-stu-id="70482-160">After you create the **MyWPFCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore
    └───MyWPFCore.csproj
```

<span data-ttu-id="70482-161">Tendrá que agregar el proyecto **MyWPFCore.csproj** a **MyApps.sln** con Visual Studio o la CLI de .NET Core desde el directorio **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="70482-161">You'll want to add the **MyWPFCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet sln add .\MyWPFAppCore\MyWPFCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="70482-162">Corrección de la generación de información de ensamblado</span><span class="sxs-lookup"><span data-stu-id="70482-162">Fix assembly info generation</span></span>

<span data-ttu-id="70482-163">Los proyectos de Windows Presentation Foundation que se han creado con .NET Framework incluyen un archivo `AssemblyInfo.cs`, que contiene los atributos de ensamblado, como la versión del ensamblado que se va a generar.</span><span class="sxs-lookup"><span data-stu-id="70482-163">Windows Presentation Foundation projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="70482-164">Los proyectos de estilo SDK generan automáticamente esta información basándose en el archivo de proyecto de SDK.</span><span class="sxs-lookup"><span data-stu-id="70482-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="70482-165">Tener ambos tipos de "información de ensamblado" crea un conflicto.</span><span class="sxs-lookup"><span data-stu-id="70482-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="70482-166">Resuelva este problema deshabilitando la generación automática, lo que obliga al proyecto a usar su archivo `AssemblyInfo.cs` existente.</span><span class="sxs-lookup"><span data-stu-id="70482-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="70482-167">Hay tres opciones para agregar al nodo `<PropertyGroup>` principal.</span><span class="sxs-lookup"><span data-stu-id="70482-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span> 

- <span data-ttu-id="70482-168">**GenerateAssemblyInfo**\\</span><span class="sxs-lookup"><span data-stu-id="70482-168">**GenerateAssemblyInfo**\\</span></span>
<span data-ttu-id="70482-169">Al establecer esta propiedad en `false`, no se generan los atributos del ensamblado.</span><span class="sxs-lookup"><span data-stu-id="70482-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="70482-170">Esto evita el conflicto con el archivo `AssemblyInfo.cs` existente en el proyecto de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="70482-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="70482-171">**AssemblyName**\\</span><span class="sxs-lookup"><span data-stu-id="70482-171">**AssemblyName**\\</span></span>
<span data-ttu-id="70482-172">El valor de esta propiedad es el binario de salida que se crea al compilar.</span><span class="sxs-lookup"><span data-stu-id="70482-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="70482-173">El nombre no necesita una extensión agregada.</span><span class="sxs-lookup"><span data-stu-id="70482-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="70482-174">Por ejemplo, el uso de `MyCoreApp` genera `MyCoreApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="70482-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="70482-175">**RootNamespace**\\</span><span class="sxs-lookup"><span data-stu-id="70482-175">**RootNamespace**\\</span></span>
<span data-ttu-id="70482-176">El espacio de nombres predeterminado que utiliza el proyecto.</span><span class="sxs-lookup"><span data-stu-id="70482-176">The default namespace used by your project.</span></span> <span data-ttu-id="70482-177">Debe coincidir con el espacio de nombres predeterminado del proyecto de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="70482-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="70482-178">Agregue estos tres elementos al nodo `<PropertyGroup>` en el archivo `MyWPFCore.csproj`:</span><span class="sxs-lookup"><span data-stu-id="70482-178">Add these three elements to the `<PropertyGroup>` node in the `MyWPFCore.csproj` file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>MyWPF</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a><span data-ttu-id="70482-179">Adición de código fuente</span><span class="sxs-lookup"><span data-stu-id="70482-179">Add source code</span></span>
<span data-ttu-id="70482-180">Ahora, el proyecto **MyWPFCore.csproj** no compila ningún código.</span><span class="sxs-lookup"><span data-stu-id="70482-180">Right now, the **MyWPFCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="70482-181">De forma predeterminada, los proyectos de .NET Core incluyen automáticamente todo el código fuente en el directorio actual y los directorios secundarios.</span><span class="sxs-lookup"><span data-stu-id="70482-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="70482-182">Debe configurar el proyecto para incluir código del proyecto de .NET Framework con una ruta de acceso relativa.</span><span class="sxs-lookup"><span data-stu-id="70482-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="70482-183">Si en el proyecto de .NET Framework se han usado archivos **.resx** para los iconos y los recursos de las ventanas y los controles, también tendrá que incluirlos.</span><span class="sxs-lookup"><span data-stu-id="70482-183">If your .NET Framework project used **.resx** files for icons and resources for your windows and controls, you'll need to include those too.</span></span> 

<span data-ttu-id="70482-184">El primer nodo `<ItemGroup>` que tiene que agregar al proyecto incluye el archivo **App.xaml**, que representa la configuración de inicio y los recursos que usa la aplicación.</span><span class="sxs-lookup"><span data-stu-id="70482-184">The first `<ItemGroup>` node you need to add to your project includes the **App.xaml** file that represents the startup config and resources your app uses.</span></span> <span data-ttu-id="70482-185">El archivo **App.xaml** también tiene un archivo **App.xaml.cs** complementario, pero se incluirá de forma automática en otro elemento `<ItemGroup>`.</span><span class="sxs-lookup"><span data-stu-id="70482-185">The **App.xaml** file also has an accompanying **App.xaml.cs** file, but it will be automatically included in a different `<ItemGroup>`.</span></span>

```xml
  <ItemGroup>
    <ApplicationDefinition Include="..\MyWPFApp\App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
  </ItemGroup>
```

<span data-ttu-id="70482-186">A continuación, agregue el siguiente nodo `<ItemGroup>` al proyecto.</span><span class="sxs-lookup"><span data-stu-id="70482-186">Next, add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="70482-187">Cada instrucción incluye un patrón global de archivo que incluye los directorios secundarios.</span><span class="sxs-lookup"><span data-stu-id="70482-187">Each statement includes a file glob pattern that includes child directories.</span></span> <span data-ttu-id="70482-188">Incluye el código fuente para el proyecto, los archivos de configuración y todos los recursos.</span><span class="sxs-lookup"><span data-stu-id="70482-188">It includes the source code for your project, any settings files, and any resources.</span></span> <span data-ttu-id="70482-189">El directorio **obj** se ha excluido de forma explícita.</span><span class="sxs-lookup"><span data-stu-id="70482-189">The **obj** directory is explicitly excluded.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyWPFApp\**\*.cs" Exclude="..\MyWPFApp\obj\**" />
    <None Include="..\MyWPFApp\**\*.settings" />
    <EmbeddedResource Include="..\MyWPFApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="70482-190">A continuación, incluya otro nodo `<ItemGroup>` con una entrada `<Page>` para cada archivo **xaml**, del proyecto, excepto para el archivo **App.xaml**.</span><span class="sxs-lookup"><span data-stu-id="70482-190">Next, include another `<ItemGroup>` node that contains a `<Page>` entry for every **xaml** file in your project except the **App.xaml** file.</span></span> <span data-ttu-id="70482-191">Estos archivos contienen todas las ventanas, páginas y recursos que están en formato **xaml**.</span><span class="sxs-lookup"><span data-stu-id="70482-191">These contain all of the windows, pages, and resources that are in **xaml** format.</span></span> <span data-ttu-id="70482-192">Aquí no se puede usar un patrón global y debe agregar una entrada para cada archivo e indicar el elemento `<Generator>` que se usa.</span><span class="sxs-lookup"><span data-stu-id="70482-192">You cannot use a glob pattern here and must add an entry for every file and indicate the `<Generator>` used.</span></span>

```xml
  <ItemGroup>
    <Page Include="..\MyWPFApp\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
  </ItemGroup>
```

## <a name="add-nuget-packages"></a><span data-ttu-id="70482-193">Adición de paquetes NuGet</span><span class="sxs-lookup"><span data-stu-id="70482-193">Add NuGet packages</span></span>

<span data-ttu-id="70482-194">Agregue cada paquete NuGet al que hace referencia el proyecto de .NET Framework al proyecto de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="70482-194">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span> 

<span data-ttu-id="70482-195">Lo más probable es que la aplicación WPF de .NET Framework tenga un archivo **packages.config** en el que se incluya una lista de todos los paquetes NuGet a los que hace referencia su proyecto.</span><span class="sxs-lookup"><span data-stu-id="70482-195">Most likely your .NET Framework WPF app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="70482-196">Puede buscar en esta lista para determinar qué paquetes de NuGet se agregarán al proyecto de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="70482-196">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="70482-197">Por ejemplo, si el proyecto de .NET Framework hace referencia al paquete NuGet `MahApps.Metro`, agréguelo al proyecto con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="70482-197">For example, if the .NET Framework project references the `MahApps.Metro` NuGet package, add it to the project with Visual Studio.</span></span> <span data-ttu-id="70482-198">También puede agregar la referencia del paquete con la CLI de .NET Core desde el directorio **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="70482-198">You can also add the package reference with the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package MahApps.Metro -v 2.0.0-alpha0262
```

<span data-ttu-id="70482-199">El comando anterior agregaría las siguientes referencias de NuGet al proyecto **MyWPFCore.csproj**:</span><span class="sxs-lookup"><span data-stu-id="70482-199">The previous command would add the following NuGet reference to the **MyWPFCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MahApps.Metro" Version="2.0.0-alpha0262" />
  </ItemGroup>
```

## <a name="problems-compiling"></a><span data-ttu-id="70482-200">Problemas de compilación</span><span class="sxs-lookup"><span data-stu-id="70482-200">Problems compiling</span></span>

<span data-ttu-id="70482-201">Si tiene problemas al compilar los proyectos, puede que esté usando algunas API solo de Windows que están disponibles en .NET Framework, pero no en .NET Core.</span><span class="sxs-lookup"><span data-stu-id="70482-201">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="70482-202">Puede intentar agregar el paquete de NuGet del [paquete de compatibilidad de Windows][compat-pack] al proyecto.</span><span class="sxs-lookup"><span data-stu-id="70482-202">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="70482-203">Este paquete solo se ejecuta en Windows y agrega aproximadamente 20 000 API de Windows a los proyectos de .NET Core y .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="70482-203">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="70482-204">El comando anterior agrega lo siguiente al proyecto **MyWPFCore.csproj**:</span><span class="sxs-lookup"><span data-stu-id="70482-204">The previous command adds the following to the **MyWPFCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="wpf-designer"></a><span data-ttu-id="70482-205">WPF Designer</span><span class="sxs-lookup"><span data-stu-id="70482-205">WPF Designer</span></span>

<span data-ttu-id="70482-206">Como se ha detallado en este artículo, Visual Studio 2019 Preview/RC solo admite WPF Designer en los proyectos de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="70482-206">As detailed in this article, Visual Studio 2019 Preview/RC only supports the WPF Designer in .NET Framework projects.</span></span> <span data-ttu-id="70482-207">Mediante la creación de un proyecto de .NET Core en paralelo, puede probar el proyecto con .NET Core mientras utiliza el proyecto de .NET Framework para diseñar formularios.</span><span class="sxs-lookup"><span data-stu-id="70482-207">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="70482-208">El archivo de solución incluye proyectos de .NET Framework y .NET Core.</span><span class="sxs-lookup"><span data-stu-id="70482-208">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="70482-209">Agregue y diseñe sus formularios y controles en el proyecto de .NET Framework, y en función de los patrones globales de archivos que agreguemos a los proyectos de .NET Core, cualquier archivo nuevo o modificado se incluirá automáticamente en los proyectos de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="70482-209">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="70482-210">Una vez que Visual Studio 2019 sea compatible con WPF Designer, podrá copiar y pegar el contenido del archivo de proyecto de .NET Core en el archivo de proyecto de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="70482-210">Once Visual Studio 2019 supports the WPF Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="70482-211">A continuación, elimine los patrones globales de archivo agregados con los elementos `<Source>` y `<EmbeddedResource>`.</span><span class="sxs-lookup"><span data-stu-id="70482-211">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="70482-212">Corrija las rutas a cualquier referencia de proyecto utilizada por su aplicación.</span><span class="sxs-lookup"><span data-stu-id="70482-212">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="70482-213">Esto actualiza eficazmente el proyecto de .NET Framework a un proyecto de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="70482-213">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>
 
## <a name="next-steps"></a><span data-ttu-id="70482-214">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="70482-214">Next steps</span></span>

* <span data-ttu-id="70482-215">Obtenga más información sobre el [paquete de compatibilidad de Windows][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="70482-215">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
* <span data-ttu-id="70482-216">Vea un [vídeo sobre cómo portar](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) el proyecto de WPF de .NET Framework a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="70482-216">Watch a [video on porting](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) your .NET Framework WPF project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md