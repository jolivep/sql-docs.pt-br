---
title: Configurar o serviço Kubernetes do Azure para implantações do SQL Server de 2019 CTP 2.0 | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: ee1faae6d43cbf2cc6c8a23086600241ad15e061
ms.sourcegitcommit: ef78cc196329a10fc5c731556afceaac5fd4cb13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49460891"
---
# <a name="configure-azure-kubernetes-service-for-sql-server-2019-ctp-20"></a>Configurar o serviço de Kubernetes do Azure para SQL Server 2019 CTP 2.0

Serviço de Kubernetes do Azure (AKS) facilita criar, configurar e gerenciar um cluster de máquinas virtuais que são pré-configuradas com um cluster Kubernetes para executar aplicativos em contêineres. 

Isso permite que você use suas habilidades existentes ou explore um grande e crescente Conhecimento da comunidade, para implantar e gerenciar aplicativos baseados em contêiner no Microsoft Azure.

Este artigo descreve as etapas para implantar o Kubernetes no AKS usando a CLI do Azure. Se você não tiver uma assinatura do Azure, crie uma conta gratuita, antes de começar.

> [!TIP] 
> Para um script de python de exemplo que implanta o cluster de big data do AKS e o SQL Server, consulte [implantar um cluster de big data no serviço de Kubernetes do Azure (AKS) do SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks).

## <a name="prerequisites"></a>Prerequisites

- Para um ambiente de AKS, o requisito mínimo de VM é pelo menos duas VMs de agente (além de mestre) tamanho mínimo [Standard_DS3_v2](https://docs.microsoft.com/azure/virtual-machines/windows/sizes-general#dsv2-series). Os recursos mínimos necessários para cada VM são 4 CPUs e 14 GB de memória.
  
   > [!NOTE]
   > Se você planeja executar trabalhos de big data ou de vários aplicativos de Spark, o tamanho mínimo é [Standard_D8_v3](https://docs.microsoft.com/azure/virtual-machines/windows/sizes-general#dv3-series-sup1sup), e os recursos mínimos necessários por VM são 8 CPUs e 32 GB de memória.

- Nesta seção requer que você esteja executando a CLI do Azure versão 2.0.4 ou posterior. Se você precisar instalar ou atualizar, consulte [instalar o Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-azure-cli). Executar `az --version` para localizar a versão, se necessário.

- Instale [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/). Cluster de Big Data do SQL Server requer que qualquer versão secundária dentro do intervalo de 1,10 versão para Kubernetes, para o servidor e cliente. Para instalar uma versão específica no cliente kubectl, consulte [instalar kubectl binário por meio de rotação](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl). Para o AKS, será necessário usar `--kubernetes-version` parâmetro para especificar uma versão diferente do padrão. Observe que o período de tempo de lançamento CTP 2.0, o AKS oferece suporte apenas à versões 1.10.7 e 1.10.8. 


> [!NOTE]
Observe que a versão de cliente/servidor que é distorção com suporte é + /-1 versão secundária. A documentação do Kubernetes afirma que "um cliente deve ser distorcida não mais de uma versão secundária do mestre, mas pode levar o mestre por até uma versão secundária. Por exemplo, um mestre v1.3 deve funcionar com a versão 1.1, v 1.2 e nós v1.3 e deve funcionar com v1.2, v1.3 e v1.4 clientes." Para obter mais informações, consulte [Kubernetes suporte para versões e componente distorção](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

Além disso, observe que `az aks kubernetes install-cli` instalará o cliente kubectl com uma versão inferior que o 1.10 necessária. Siga acima instruções para instalar a versão correta do cliente kubectl.

## <a name="create-a-resource-group"></a>Criar um grupo de recursos

Um grupo de recursos do Azure é um grupo lógico no qual Azure recursos são implantados e gerenciados. As etapas a seguir entrar no Azure e criar um grupo de recursos para o cluster do AKS.

> [!TIP]
> Se você estiver usando o Windows, use o PowerShell para o restante das etapas.

1. No prompt de comando, execute o seguinte comando e siga os prompts para fazer logon em sua assinatura do Azure:

    ```bash
    az login
    ```

1. Se você tiver várias assinaturas, você pode exibir todas as suas assinaturas, executando o seguinte comando:

   ```bash
   az account list
   ```

1. Se você quiser alterar para uma assinatura diferente, você pode executar este comando:

   ```bash
   az account set --subscription <subscription id>
   ```

1. Criar um grupo de recursos com o **criar grupo de az** comando. O exemplo a seguir cria um grupo de recursos denominado `sqlbigdatagroup` no `westus2` local.

   ```bash
   az group create --name sqlbigdatagroup --location westus2
   ```

## <a name="create-a-kubernetes-cluster"></a>Criar um cluster Kubernetes

1. Criar um cluster Kubernetes no AKS com o [criar az aks](https://docs.microsoft.com/cli/azure/aks) comando. O exemplo a seguir cria um cluster Kubernetes chamado *kubcluster* com Linux de um nó mestre dois nós de agente do Linux. Certifique-se de que criar o cluster do AKS no mesmo grupo de recursos que você usou nas seções anteriores.

    ```bash
   az aks create --name kubcluster \
    --resource-group sqlbigdatagroup \
    --generate-ssh-keys \
    --node-vm-size Standard_DS3_v2 \
    --node-count 2 \
    --kubernetes-version 1.10.7
    ```

    Você pode aumentar ou diminuir a contagem de agentes padrão alterando o `--node-count <n>` onde `<n>` é o número de nós de agente que você deseja ter.

    Após alguns minutos, o comando for concluído e retorna informações formatadas em JSON sobre o cluster.

1. Salve a saída JSON do comando anterior para uso posterior.

## <a name="connect-to-the-cluster"></a>Conectar-se ao cluster

1. Para configurar o kubectil para conectar-se ao cluster Kubernetes, execute as [az aks get-credentials](https://docs.microsoft.com/cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials) comando. Esta etapa baixa credenciais e configura o kubectl CLI para usá-los.

   ```bash
   az aks get-credentials --resource-group=sqlbigdatagroup --name kubcluster
   ```

1. Para verificar a conexão ao seu cluster, use o [kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) comando para retornar uma lista de nós do cluster.  O exemplo a seguir mostra a saída se você tem 1 mestre e nós de agente 3.

   ```bash
   kubectl get nodes
   ```

## <a name="next-steps"></a>Próximas etapas

As etapas neste artigo configurado um cluster Kubernetes no AKS. A próxima etapa é implantar o SQL Server de 2019 Big Data para o cluster.

[Implantar um cluster do SQL Server de 2019 Big Data no Kubernetes](quickstart-big-data-cluster-deploy.md)