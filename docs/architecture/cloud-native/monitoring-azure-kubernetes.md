---
title: Supervisión en Azure Kubernetes Service
description: Supervisión en Azure Kubernetes Service
ms.date: 02/05/2020
ms.openlocfilehash: 5c46b9e8599f70d430ad26cf1364343454d30a16
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450068"
---
# <a name="monitoring-in-azure-kubernetes-services"></a>Supervisión en Azure Kubernetes Service

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

El registro integrado en Kubernetes es primitivo. Sin embargo, hay algunas opciones excelentes para obtener los registros de Kubernetes y en un lugar donde se pueden analizar correctamente. Si necesita supervisar los clústeres de AKS, la configuración de la pila elástica para Kubernetes es una solución excelente.

## <a name="azure-monitor-for-containers"></a>Azure Monitor para contenedores

[Azure monitor para contenedores](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-overview) admite el consumo de registros no solo de Kubernetes, sino también de otros motores de orquestación como DC/os, Docker Swarm y Red Hat OpenShift.

![consumo de registros de varios contenedores](./media/containers-diagram.png)
la **figura 7-10**. Consumo de registros de varios contenedores

[Prometheus](https://prometheus.io/) es una conocida solución de supervisión de métricas de código abierto. Forma parte de la base de cálculo nativa de la nube. Normalmente, el uso de Prometheus requiere la administración de un servidor de Prometheus con su propio almacén. Sin embargo, [Azure monitor para contenedores proporciona integración directa con puntos de conexión de métricas de Prometheus](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-prometheus-integration), por lo que no es necesario un servidor independiente.

La información de registro y métrica se recopila no solo de los contenedores que se ejecutan en el clúster, sino también de los propios hosts del clúster. Permite correlacionar la información de registro de las dos, lo que hace que sea mucho más fácil realizar un seguimiento de un error.

La instalación de los recopiladores de registros es diferente en los clústeres de [Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) y [Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) . Sin embargo, en ambos casos, la colección de registros se implementa como un [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)Kubernetes, lo que significa que el recopilador de registros se ejecuta como un contenedor en cada uno de los nodos.

Independientemente del orquestador o del sistema operativo que ejecute el demonio de Azure Monitor, la información de registro se reenvía a las mismas herramientas de Azure Monitor con las que los usuarios están familiarizados. Esto garantiza una experiencia paralela en entornos que mezclen distintos orígenes de registro, como un entorno híbrido de Kubernetes/Azure Functions.

![un panel de ejemplo que muestra información de registro y métrica de varios contenedores en ejecución.](./media/containers-dashboard.png)
**figura 7-11**. Un panel de ejemplo que muestra información de registro y métrica de varios contenedores en ejecución.

## <a name="logfinalize"></a>Log. Finalize ()

El registro es una de las partes más informadas y, a la mayor parte de lo importante, de la implementación de cualquier aplicación a escala. A medida que aumentan el tamaño y la complejidad de las aplicaciones, lo que hace es la dificultad de depurarlos. Tener los registros de alta calidad disponibles hace que la depuración sea mucho más fácil y la mueve del dominio "casi imposible" a la "experiencia agradable".

>[!div class="step-by-step"]
>[Anterior](logging-with-elastic-stack.md)
>[Siguiente](azure-monitor.md)
