---
title: ¿Qué es Docker?
description: Arquitectura de microservicios de .NET para aplicaciones .NET en contenedor | ¿Qué es Docker?
ms.date: 08/31/2018
ms.openlocfilehash: 7f7844f51e96914c1432332d9b641ea65bf48f07
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674862"
---
# <a name="what-is-docker"></a><span data-ttu-id="a5c72-103">¿Qué es Docker?</span><span class="sxs-lookup"><span data-stu-id="a5c72-103">What is Docker?</span></span>

<span data-ttu-id="a5c72-104">[Docker](https://www.docker.com/) es un [proyecto de código abierto](https://github.com/docker/docker) para automatizar la implementación de aplicaciones como contenedores portátiles y autosuficientes que se pueden ejecutar en la nube o localmente.</span><span class="sxs-lookup"><span data-stu-id="a5c72-104">[Docker](https://www.docker.com/) is an [open-source project](https://github.com/docker/docker) for automating the deployment of applications as portable, self-sufficient containers that can run on the cloud or on-premises.</span></span> <span data-ttu-id="a5c72-105">Docker es también una [empresa](https://www.docker.com/) que promueve e impulsa esta tecnología, en colaboración con proveedores de la nube, Linux y Windows, incluido Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a5c72-105">Docker is also a [company](https://www.docker.com/) that promotes and evolves this technology, working in collaboration with cloud, Linux, and Windows vendors, including Microsoft.</span></span>

![Los contenedores de Docker se pueden ejecutar en cualquier lugar, a nivel local en el centro de datos de cliente, en un proveedor de servicios externo o en la nube, en Azure.](./media/image2.png)

<span data-ttu-id="a5c72-107">**Figura 2-2**.</span><span class="sxs-lookup"><span data-stu-id="a5c72-107">**Figure 2-2**.</span></span> <span data-ttu-id="a5c72-108">Docker implementa contenedores en todas las capas de la nube híbrida</span><span class="sxs-lookup"><span data-stu-id="a5c72-108">Docker deploys containers at all layers of the hybrid cloud</span></span>

<span data-ttu-id="a5c72-109">Los contenedores de imagen de Docker se pueden ejecutar de forma nativa en Linux y Windows.</span><span class="sxs-lookup"><span data-stu-id="a5c72-109">Docker image containers can run natively on Linux and Windows.</span></span> <span data-ttu-id="a5c72-110">Sin embargo, las imágenes de Windows solo pueden ejecutarse en hosts de Windows y las imágenes de Linux pueden ejecutarse en hosts de Linux y hosts de Windows (con una máquina virtual Linux de Hyper-V, hasta el momento), donde host significa un servidor o una máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="a5c72-110">However, Windows images can run only on Windows hosts and Linux images can run on Linux hosts and Windows hosts (using a Hyper-V Linux VM, so far), where host means a server or a VM.</span></span>

<span data-ttu-id="a5c72-111">Los desarrolladores pueden usar entornos de desarrollo en Windows, Linux o macOS.</span><span class="sxs-lookup"><span data-stu-id="a5c72-111">Developers can use development environments on Windows, Linux, or macOS.</span></span> <span data-ttu-id="a5c72-112">En el equipo de desarrollo, el desarrollador ejecuta un host de Docker en que se implementan imágenes de Docker, incluidas la aplicación y sus dependencias.</span><span class="sxs-lookup"><span data-stu-id="a5c72-112">On the development computer, the developer runs a Docker host where Docker images are deployed, including the app and its dependencies.</span></span> <span data-ttu-id="a5c72-113">Los desarrolladores que trabajan en Linux o en Mac usan un host de Docker basado en Linux y pueden crear imágenes solo para contenedores de Linux.</span><span class="sxs-lookup"><span data-stu-id="a5c72-113">Developers who work on Linux or on the Mac use a Docker host that is Linux based, and they can create images only for Linux containers.</span></span> <span data-ttu-id="a5c72-114">(Los desarrolladores que trabajan en Mac pueden editar código o ejecutar la CLI de Docker en macOS, pero en el momento de redactar este artículo, los contenedores no se ejecutan directamente en macOS). Los desarrolladores que trabajan en Windows pueden crear imágenes para contenedores de Windows o Linux.</span><span class="sxs-lookup"><span data-stu-id="a5c72-114">(Developers working on the Mac can edit code or run the Docker CLI from macOS, but as of the time of this writing, containers don't run directly on macOS.) Developers who work on Windows can create images for either Linux or Windows Containers.</span></span>

<span data-ttu-id="a5c72-115">Para hospedar contenedores en entornos de desarrollo y proporcionar herramientas de desarrollador adicionales, Docker entrega [Docker Community Edition (CE)](https://www.docker.com/community-edition) para Windows o macOS.</span><span class="sxs-lookup"><span data-stu-id="a5c72-115">To host containers in development environments and provide additional developer tools, Docker ships [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows or for macOS.</span></span> <span data-ttu-id="a5c72-116">Estos productos instalan la máquina virtual necesaria (el host de Docker) para hospedar los contenedores.</span><span class="sxs-lookup"><span data-stu-id="a5c72-116">These products install the necessary VM (the Docker host) to host the containers.</span></span> <span data-ttu-id="a5c72-117">Docker también pone a disposición [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), que está diseñado para el desarrollo empresarial y se usa en los equipos de TI que crean, envían y ejecutan aplicaciones críticas para la empresa en producción.</span><span class="sxs-lookup"><span data-stu-id="a5c72-117">Docker also makes available [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), which is designed for enterprise development and is used by IT teams who build, ship, and run large business-critical applications in production.</span></span>

<span data-ttu-id="a5c72-118">Para ejecutar [contenedores de Windows](/virtualization/windowscontainers/about/), hay dos tipos de tiempos de ejecución:</span><span class="sxs-lookup"><span data-stu-id="a5c72-118">To run [Windows Containers](/virtualization/windowscontainers/about/), there are two types of runtimes:</span></span>

- <span data-ttu-id="a5c72-119">Los contenedores de Windows Server ofrecen aislamiento de aplicaciones a través de tecnología de aislamiento de proceso y de espacio de nombres.</span><span class="sxs-lookup"><span data-stu-id="a5c72-119">Windows Server Containers provide application isolation through process and namespace isolation technology.</span></span> <span data-ttu-id="a5c72-120">Un contenedor de Windows Server comparte el kernel con el host de contenedor y con todos los contenedores que se ejecutan en el host.</span><span class="sxs-lookup"><span data-stu-id="a5c72-120">A Windows Server Container shares a kernel with the container host and with all containers running on the host.</span></span>

- <span data-ttu-id="a5c72-121">Los contenedores de Hyper-V amplían el aislamiento que ofrecen los contenedores de Windows Server mediante la ejecución de cada contenedor en una máquina virtual altamente optimizada.</span><span class="sxs-lookup"><span data-stu-id="a5c72-121">Hyper-V Containers expand on the isolation provided by Windows Server Containers by running each container in a highly optimized virtual machine.</span></span> <span data-ttu-id="a5c72-122">En esta configuración, el kernel del host del contenedor no se comparte con los contenedores de Hyper-V, lo que proporciona un mejor aislamiento.</span><span class="sxs-lookup"><span data-stu-id="a5c72-122">In this configuration, the kernel of the container host isn't shared with the Hyper-V Containers, providing better isolation.</span></span>

<span data-ttu-id="a5c72-123">Las imágenes de estos contenedores se crean y funcionan de la misma manera.</span><span class="sxs-lookup"><span data-stu-id="a5c72-123">The images for these containers are created the same way and function the same.</span></span> <span data-ttu-id="a5c72-124">La diferencia radica en cómo se crea el contenedor desde la imagen ejecutando un contenedor de Hyper-V que requiere un parámetro adicional.</span><span class="sxs-lookup"><span data-stu-id="a5c72-124">The difference is in how the container is created from the image running a Hyper-V Container requires an extra parameter.</span></span> <span data-ttu-id="a5c72-125">Para más información, vea [Contenedores de Hyper-V](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container).</span><span class="sxs-lookup"><span data-stu-id="a5c72-125">For details, see [Hyper-V Containers](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container).</span></span>

## <a name="comparing-docker-containers-with-virtual-machines"></a><span data-ttu-id="a5c72-126">Comparación de los contenedores de Docker con las máquinas virtuales</span><span class="sxs-lookup"><span data-stu-id="a5c72-126">Comparing Docker containers with virtual machines</span></span>

<span data-ttu-id="a5c72-127">En la figura 2-3 se muestra una comparación entre las máquinas virtuales y los contenedores de Docker.</span><span class="sxs-lookup"><span data-stu-id="a5c72-127">Figure 2-3 shows a comparison between VMs and Docker containers.</span></span>

| <span data-ttu-id="a5c72-128">Máquinas virtuales</span><span class="sxs-lookup"><span data-stu-id="a5c72-128">Virtual Machines</span></span> | <span data-ttu-id="a5c72-129">Contenedores de Docker</span><span class="sxs-lookup"><span data-stu-id="a5c72-129">Docker Containers</span></span> |
| -----------------| ------------------|
|![Para las máquinas virtuales, hay tres niveles de base en el servidor host, de manera ascendente: infraestructura, sistema operativo host y un hipervisor y, encima de todo eso, cada máquina virtual tiene su propio sistema operativo y todas las bibliotecas necesarias.](./media/image3.png)|![En el caso de Docker, el servidor host solo tiene la infraestructura y el sistema operativo y, encima de eso, el motor de contenedor, que mantiene el contenedor aislado, pero con el uso compartido de los servicios del sistema operativo de base.](./media/image4.png)|
|<span data-ttu-id="a5c72-132">Las máquinas virtuales incluyen la aplicación, las bibliotecas o los archivos binarios necesarios y un sistema operativo invitado completo.</span><span class="sxs-lookup"><span data-stu-id="a5c72-132">Virtual machines include the application, the required libraries or binaries, and a full guest operating system.</span></span> <span data-ttu-id="a5c72-133">La virtualización completa requiere más recursos que la inclusión en contenedores.</span><span class="sxs-lookup"><span data-stu-id="a5c72-133">Full virtualization requires more resources than containerization.</span></span> | <span data-ttu-id="a5c72-134">Los contenedores incluyen la aplicación y todas sus dependencias.</span><span class="sxs-lookup"><span data-stu-id="a5c72-134">Containers include the application and all its dependencies.</span></span> <span data-ttu-id="a5c72-135">Sin embargo, comparten el kernel del sistema operativo con otros contenedores, que se ejecutan como procesos aislados en el espacio de usuario en el sistema operativo host.</span><span class="sxs-lookup"><span data-stu-id="a5c72-135">However, they share the OS kernel with other containers, running as isolated processes in user space on the host operating system.</span></span> <span data-ttu-id="a5c72-136">(Excepto en los contenedores de Hyper-V, en que cada contenedor se ejecuta dentro de una máquina virtual especial por contenedor).</span><span class="sxs-lookup"><span data-stu-id="a5c72-136">(Except in Hyper-V containers, where each container runs inside of a special virtual machine per container.)</span></span> |

<span data-ttu-id="a5c72-137">**Figura 2-3**.</span><span class="sxs-lookup"><span data-stu-id="a5c72-137">**Figure 2-3**.</span></span> <span data-ttu-id="a5c72-138">Comparación de las máquinas virtuales tradicionales con los contenedores de Docker</span><span class="sxs-lookup"><span data-stu-id="a5c72-138">Comparison of traditional virtual machines to Docker containers</span></span>

<span data-ttu-id="a5c72-139">Dado que los contenedores requieren muchos menos recursos (por ejemplo, no necesitan un sistema operativo completo), se inician rápidamente y son fáciles de implementar.</span><span class="sxs-lookup"><span data-stu-id="a5c72-139">Because containers require far fewer resources (for example, they don't need a full OS), they're easy to deploy and they start fast.</span></span> <span data-ttu-id="a5c72-140">Esto permite tener una mayor densidad, lo que significa que se pueden ejecutar más servicios en la misma unidad de hardware, reduciendo así los costos.</span><span class="sxs-lookup"><span data-stu-id="a5c72-140">This allows you to have higher density, meaning that it allows you to run more services on the same hardware unit, thereby reducing costs.</span></span>

<span data-ttu-id="a5c72-141">Como efecto secundario de la ejecución en el mismo kernel, obtiene menos aislamiento que las máquinas virtuales.</span><span class="sxs-lookup"><span data-stu-id="a5c72-141">As a side effect of running on the same kernel, you get less isolation than VMs.</span></span>

<span data-ttu-id="a5c72-142">El objetivo principal de una imagen es que hace que el entorno (dependencias) sea el mismo entre las distintas implementaciones.</span><span class="sxs-lookup"><span data-stu-id="a5c72-142">The main goal of an image is that it makes the environment (dependencies) the same across different deployments.</span></span> <span data-ttu-id="a5c72-143">Esto significa que puede depurarlo en su equipo y, a continuación, implementarlo en otra máquina con el mismo entorno garantizado.</span><span class="sxs-lookup"><span data-stu-id="a5c72-143">This means that you can debug it on your machine and then deploy it to another machine with the same environment guaranteed.</span></span>

<span data-ttu-id="a5c72-144">Una imagen de contenedor es una manera de empaquetar una aplicación o un servicio e implementarlo de forma confiable y reproducible.</span><span class="sxs-lookup"><span data-stu-id="a5c72-144">A container image is a way to package an app or service and deploy it in a reliable and reproducible way.</span></span> <span data-ttu-id="a5c72-145">Podría decir que Docker no solo es una tecnología, sino también una filosofía y un proceso.</span><span class="sxs-lookup"><span data-stu-id="a5c72-145">You could say that Docker isn't only a technology but also a philosophy and a process.</span></span>

<span data-ttu-id="a5c72-146">Al usar Docker, no escuchará a los desarrolladores decir "Si funciona en mi máquina, ¿por qué no en producción?".</span><span class="sxs-lookup"><span data-stu-id="a5c72-146">When using Docker, you won't hear developers say, "It works on my machine, why not in production?"</span></span> <span data-ttu-id="a5c72-147">Pueden decir simplemente "Se ejecuta en Docker", porque la aplicación de Docker empaquetada puede ejecutarse en cualquier entorno de Docker compatible, y se ejecuta de la forma prevista en todos los destinos de implementación (como desarrollo, control de calidad, ensayo y producción).</span><span class="sxs-lookup"><span data-stu-id="a5c72-147">They can simply say, "It runs on Docker", because the packaged Docker application can be executed on any supported Docker environment, and it runs the way it was intended to on all deployment targets (such as Dev, QA, staging, and production).</span></span>

## <a name="a-simple-analogy"></a><span data-ttu-id="a5c72-148">Una analogía simple</span><span class="sxs-lookup"><span data-stu-id="a5c72-148">A simple analogy</span></span>

<span data-ttu-id="a5c72-149">Quizás una analogía simple puede ayudar a entender el concepto básico de Docker.</span><span class="sxs-lookup"><span data-stu-id="a5c72-149">Perhaps a simple analogy can help getting the grasp of the core concept of Docker.</span></span>

<span data-ttu-id="a5c72-150">Vamos a remontarnos a la década de 1950 por un momento.</span><span class="sxs-lookup"><span data-stu-id="a5c72-150">Let's go back in time to the 1950s for a moment.</span></span> <span data-ttu-id="a5c72-151">No había ningún procesador de texto y las fotocopiadoras se utilizaban en todas partes y de todo tipo.</span><span class="sxs-lookup"><span data-stu-id="a5c72-151">There were no word processors, and the photocopiers were used everywhere (kind of).</span></span>

<span data-ttu-id="a5c72-152">Imagine que es responsable de enviar lotes de cartas, según proceda, para enviarlas por correo a los clientes en papel y sobres reales, que se entregarán físicamente en la dirección postal de cada cliente (entonces no existía el correo electrónico).</span><span class="sxs-lookup"><span data-stu-id="a5c72-152">Imagine you're responsible for quickly issuing batches of letters as required, to mail them to customers, using real paper and envelopes, to be delivered physically to each customer's address (there was no email back then).</span></span>

<span data-ttu-id="a5c72-153">En algún momento, se da cuenta de que las cartas no son más que una composición de un conjunto grande de párrafos, que se eligen y ordenan según proceda, según el propósito de la carga, por lo que diseña un sistema para emitir cartas rápidamente, esperando conseguir una increíble mejora.</span><span class="sxs-lookup"><span data-stu-id="a5c72-153">At some point, you realize the letters are just a composition of a large set of paragraphs, which are picked and arranged as needed, according to the purpose of the letter, so you devise a system to issue letters quickly, expecting to get a hefty raise.</span></span>

<span data-ttu-id="a5c72-154">El sistema es simple:</span><span class="sxs-lookup"><span data-stu-id="a5c72-154">The system is simple:</span></span>

1. <span data-ttu-id="a5c72-155">Comience con un conjunto de hojas transparentes que contienen un párrafo.</span><span class="sxs-lookup"><span data-stu-id="a5c72-155">You begin with a deck of transparent sheets containing one paragraph each.</span></span>

2. <span data-ttu-id="a5c72-156">Para emitir un conjunto de cartas, elija las hojas con los párrafos necesarios, apílelas y alinéelas para que queden y se lean bien.</span><span class="sxs-lookup"><span data-stu-id="a5c72-156">To issue a set of letters, you pick the sheets with the paragraphs you need, then you stack and align them so they look and read fine.</span></span>

3. <span data-ttu-id="a5c72-157">Por último, colóquelas en la fotocopiadora y presione inicio para producir tantas cartas como sean necesarias.</span><span class="sxs-lookup"><span data-stu-id="a5c72-157">Finally, you place the set in the photocopier and press start to produce as many letters as required.</span></span>

<span data-ttu-id="a5c72-158">Por tanto, para simplificar, esa es la idea principal de Docker.</span><span class="sxs-lookup"><span data-stu-id="a5c72-158">So, simplifying, that's the core idea of Docker.</span></span>

<span data-ttu-id="a5c72-159">En Docker, cada capa es el conjunto resultante de los cambios que se producen en el sistema de archivos después de ejecutar un comando, como instalar un programa.</span><span class="sxs-lookup"><span data-stu-id="a5c72-159">In Docker, each layer is the resulting set of changes that happen to the filesystem after executing a command, such as, installing a program.</span></span>

<span data-ttu-id="a5c72-160">Por lo tanto, al "Examinar" el sistema de archivos después de que se ha copiado la capa, verá todos los archivos, incluida la capa cuando se instaló el programa.</span><span class="sxs-lookup"><span data-stu-id="a5c72-160">So, when you "look" at the filesystem after the layer has been copied, you see all the files, included the layer when the program was installed.</span></span>

<span data-ttu-id="a5c72-161">Puede pensar en una imagen como un disco duro de solo lectura auxiliar listo para instalarse en un "equipo" donde el sistema operativo ya está instalado.</span><span class="sxs-lookup"><span data-stu-id="a5c72-161">You can think of an image as an auxiliary read-only hard disk ready to be installed in a "computer" where the operating system is already installed.</span></span>

<span data-ttu-id="a5c72-162">De forma similar, puede pensar en un contenedor como el "equipo" con el disco duro de imagen instalado.</span><span class="sxs-lookup"><span data-stu-id="a5c72-162">Similarly, you can think of a container as the "computer" with the image hard disk installed.</span></span> <span data-ttu-id="a5c72-163">El contenedor, como un equipo, se puede apagar o desactivar.</span><span class="sxs-lookup"><span data-stu-id="a5c72-163">The container, just like a computer, can be powered on or off.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a5c72-164">[Anterior](index.md)
>[Siguiente](docker-terminology.md)</span><span class="sxs-lookup"><span data-stu-id="a5c72-164">[Previous](index.md)
[Next](docker-terminology.md)</span></span>