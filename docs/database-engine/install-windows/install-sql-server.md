---
title: Guia de instalação do SQL Server
ms.description: 'An index of content that helps you install SQL Server and associated components through various options such as the installation wizard, command prompt, or sysprep. '
ms.custom: ''
ms.date: 11/14/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- AdventureWorks sample database
- installing SQL Server, preparing to install
- installation [SQL Server]
ms.assetid: 0300e777-d56b-4d10-9c33-c9ebd2489ee5
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 30155a37f57391edeee916cd2b6629d63a1dcaaa
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "75688250"
---
# <a name="sql-server-installation-guide"></a>Guia de instalação do SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Este artigo é um índice de conteúdo que fornece diretrizes para a instalação do SQL Server no Windows.

Para ver outros cenários de implantação, confira:

- [Linux](../../linux/sql-server-linux-setup.md)
- [Contêineres do Docker](../../linux/sql-server-linux-configure-docker.md)
- [Kubernetes – Clusters de Big Data](../../big-data-cluster/deploy-get-started.md)

A partir do [!INCLUDE[sssql15](../../includes/sssql15-md.md)], o [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] só está disponível como um aplicativo de 64 bits. Aqui estão os detalhes importantes sobre como obter o SQL Server e como instalá-lo.

## <a name="getting-started"></a>Introdução
  
* **Edições e recursos**: Examine os recursos compatíveis com as diferentes edições e versões do SQL Server para determinar qual é a mais adequada às suas necessidades de negócios. 
    - [[!INCLUDE[ss2019](../../includes/sssqlv15-md.md)]](~/sql-server/editions-and-components-of-sql-server-version-15.md).  
    - [[!INCLUDE[ss2017](../../includes/sssqlv14-md.md)]](~/sql-server/editions-and-components-of-sql-server-2017.md).  
    - [[!INCLUDE[ss2016](../../includes/sssql15-md.md)]](~/sql-server/editions-and-components-of-sql-server-2016.md).  
    - [[!INCLUDE[ss2014](../../includes/sssql14-md.md)]](https://technet.microsoft.com/library/cc645993(v=sql.120).aspx)

*  **Requisitos**: Examine os requisitos de instalação, as verificações de configuração do sistema e as considerações sobre segurança em [Como planejar uma instalação do SQL Server](../../sql-server/install/planning-a-sql-server-installation.md) 
  
* **Exemplos de bancos de dados e exemplo de código**: 
    * Eles não são instalados como parte da instalação do SQL Server por padrão, mas podem ser encontrados 
    * Para instalá-los em edições não Express do SQL Server, confira [Onde estão as amostras](../../samples/sql-samples-where-are.md)
    

## <a name="installation-media"></a>Mídia de instalação

O local de download para [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] depende da edição:

* **SQL Server Enterprise, Standard, e Express Editions** são licenciadas para uso em produção. Para as Edições Enterprise e Standard, entre em contato com seu fornecedor de software para obter a mídia de instalação. Encontre informações de compra e um diretório de parceiros da Microsoft na [página de licenciamento da Microsoft](https://www.microsoft.com/licensing/product-licensing/sql-server).
* [Versão gratuita: mais recente](https://www.microsoft.com/sql-server/sql-server-downloads)
* [Versão gratuita: outras](https://www.microsoft.com/evalcenter/evaluate-sql-server)


Outros componentes do SQL Server podem ser encontrados aqui: 

* [Todas as atualizações cumulativas](https://sqlserverbuilds.blogspot.com/)
* [SQL Server Reporting Services](https://www.microsoft.com/download/details.aspx?id=100122). 
* [SQL Server Management Studio](https://aka.ms/ssmsfullsetup)
* [Azure Data Studio](https://go.microsoft.com/fwlink/?linkid=2109256)


## <a name="sql-server-installation"></a>Instalação do SQL Server
 
|Artigo|Descrição|  
|-----------|-----------------|  
|[Assistente de Instalação](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)|Instale o SQL Server usando a GUI do Assistente de Instalação iniciada na mídia de instalação do setup.exe. |  
|[Prompt de comando](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)|Sintaxe de exemplo e parâmetros de instalação para executar uma instalação do SQL Server por meio do prompt de comando. | 
|[Server Core](../../database-engine/install-windows/install-sql-server-on-server-core.md)|Instale o [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] no Windows Server Core.|  
|[Verificar parâmetros do Verificador de Configuração do Sistema](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md)|Discute a função do Verificador de Configuração do Sistema (SCC).|   
|[Arquivo de configuração](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md)|Sintaxe de exemplo e parâmetros de instalação para executar a Instalação por meio de um arquivo de configuração.|  
|[SysPrep](../../database-engine/install-windows/install-sql-server-using-sysprep.md)|Sintaxe de exemplo e parâmetros de instalação para executar a Instalação por meio do SysPrep.|
|[Adicionar recursos a uma instância](../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md)|Atualize os componentes de uma instância existente do [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)].|  
|[Instalação do cluster de failover do SQL Server](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)| Instale uma instância de cluster de failover do SQL Server.  | 
|[Reparar uma instalação com falha do [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]](../../database-engine/install-windows/repair-a-failed-sql-server-installation.md)|Repare uma instalação corrompida do [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)].|  
|[Renomear um computador com o SQL Server](../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)|Atualize os metadados do sistema armazenados em sys.servers depois que o nome do host de um computador que hospeda uma instância autônoma do SQL Server for renomeado. |  
|[Instalar as atualizações de manutenção do [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]](../../database-engine/install-windows/install-sql-server-servicing-updates.md)|Instale as atualizações do [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)].|  
|[Arquivos de log da instalação](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)| Veja e leia os erros nos arquivos de log da instalação do SQL Server. |  
|[Validar uma instalação](../../database-engine/install-windows/validate-a-sql-server-installation.md)|Analise o uso do relatório de Descoberta SQL para verificar a versão do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e os recursos do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instalados no computador.|  
  
  
## <a name="individual-component-installation"></a>Instalação de componente individual 
  
|Artigo|Descrição|  
|-----------|-----------------|  
|[Mecanismo de Banco de Dados do SQL Server](../../database-engine/install-windows/install-sql-server-database-engine.md)|Instale e configure o [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Replicação do SQL Server](../../database-engine/install-windows/install-sql-server-replication.md)|Instale e configure a Replicação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Distributed Replay](../../tools/distributed-replay/install-distributed-replay-overview.md)|Lista os artigos para instalar o recurso Distributed Replay.|  
|[Ferramentas de Gerenciamento do SQL Server com o SSMS](https://msdn.microsoft.com/library/af68d59a-a04d-4f23-9967-ad4ee2e63381)|Instale e configure as Ferramentas de Gerenciamento do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[SQL Server PowerShell](../../database-engine/install-windows/install-sql-server-powershell.md)|Considerações sobre a instalação de componentes do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell.|  
  

## <a name="sql-server-configuration"></a>Configuração do SQL Server 
  
|Artigo|Descrição|  
|-----------|-----------------|  
|[Configurar o Firewall do Windows (SQL Server)](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)|Visão geral da configuração do firewall e de como configurar o Firewall do Windows para permitir acesso ao SQL Server.|  
|[Configurar o Firewall do Windows (SSAS)](https://docs.microsoft.com/analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access)|Defina as configurações de porta e firewall para permitir acesso ao [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou ao [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] no SharePoint.|  
|[Configurar um computador multihomed](../../sql-server/install/configure-a-multi-homed-computer-for-sql-server-access.md)|Configure o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e o Firewall do Windows com Segurança Avançada para fornecer conexões de rede a uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] em um ambiente multihomed.|  

 
## <a name="see-also"></a>Confira também  

[Atualizar [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]](../../database-engine/install-windows/upgrade-sql-server.md)   
[Desinstalar o [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]](../../sql-server/install/uninstall-sql-server.md)   
[Instalar o SSRS (SQL Server Reporting Services)](../../reporting-services/install-windows/install-reporting-services.md)
[Instalar o SSAS (SQL Server Analysis Services)](/analysis-services/instances/install-windows/install-analysis-services)
[Instalar [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] recursos de business intelligence](../../sql-server/install/install-sql-server-business-intelligence-features.md)   
[Soluções de alta disponibilidade &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)  
