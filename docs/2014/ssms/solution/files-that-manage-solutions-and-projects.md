---
title: Arquivos que gerenciam soluções e projetos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], files
- .ssmssln files
- .ssmsmobileproj files
- .ssmsasproj files
- .ssmssqlproj files
- .sqlsuo files
- files [SQL Server Management Studio], projects
ms.assetid: e19d2859-0b97-4727-ac27-c4c226d86b2f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6e8481c1cce3e43287c04678ddae10ac1b0703af
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63044306"
---
# <a name="files-that-manage-solutions-and-projects"></a>Arquivos que gerenciam soluções e projetos
  Este tópico descreve os tipos de arquivo que são específicos [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]para o. Por padrão, todas as soluções e seus projetos são criados em \Meus Documentos\SQL Server Management Studio Projects.  
  
## <a name="management-studio-solution-files"></a>Arquivos de solução do Management Studio  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]usa tipos de arquivo diferentes [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] do [!INCLUDE[msCoName](../../includes/msconame-md.md)] ou do Visual Studio. Isso significa que você não pode abrir uma solução [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] no [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ou não Visual Studio. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Os arquivos da solução permitem que o Gerenciador de Soluções exiba uma interface gráfica para gerenciar seus arquivos.  
  
|Extensão|Tipo de arquivo|DESCRIÇÃO|Criado por|  
|---------------|---------------|-----------------|----------------|  
|.ssmssln|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Objeto de solução|Fornece o ambiente com referências ao local em disco de projetos [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , itens de projeto e solução|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|  
  
## <a name="management-studio-project-files"></a>Arquivos de projeto do Management Studio  
 Da mesma forma que as soluções contêm arquivos que gerenciam os objetos da solução, os projetos contêm arquivos de projeto. O tipo de arquivo de projeto que o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] cria para um projeto depende do modelo usado para criar o projeto. A tabela a seguir descreve o tipo de arquivo criado para cada projeto.  
  
|Extensão|Modelo do projeto|  
|---------------|----------------------|  
|.ssmssqlproj|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Projeto de scripts|  
|.ssmsasproj|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Projeto de scripts|  
  
## <a name="location-of-solution-level-files"></a>Local dos arquivos do nível da solução  
 Por padrão, arquivos do nível da solução são criados no diretório físico do primeiro projeto criado com a solução. Você pode especificar um diretório para a solução criando uma solução, ou especificar o diretório ao criar um projeto novo.  
  
 Se você tiver uma estrutura de diretórios semelhante à estrutura lógica mostrada no Gerenciador de Soluções, os arquivos de projeto e solução serão mais fáceis de localizar e compartilhar com outros desenvolvedores em uma equipe.  
  
## <a name="see-also"></a>Consulte Também  
 [Gerenciar arquivos com codificação](manage-files-with-encoding.md)   
 [Arquivos diversos](miscellaneous-files.md)   
 [Gerenciador de Soluções](solution-explorer.md)   
 [Soluções &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md)   
 [Projetos &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md)   
 [Controle do código-fonte do Gerenciador de Soluções](../../database-engine/solution-explorer-source-control.md)  
  
  
