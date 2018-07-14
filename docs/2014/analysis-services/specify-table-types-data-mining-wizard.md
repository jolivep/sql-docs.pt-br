---
title: Especificar tipos de tabela (Assistente de mineração de dados) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.specifytabletypes.f1
ms.assetid: 8209a707-faef-4ffc-8991-6c13bb350753
caps.latest.revision: 22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7c753554dcab61c10bacaf4c118d1781ba3d157b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159067"
---
# <a name="specify-table-types-data-mining-wizard"></a>Especificar tipos de tabelas (Assistente de Mineração de Dados)
  Use a página **Especificar Tipos de Tabelas** para identificar as tabelas a serem usadas para definir a estrutura de mineração. Se uma tabela não for selecionada, ela não será usada para definir a estrutura de mineração.  
  
> [!NOTE]  
>  Você pode adicionar tabelas mais tarde na guia **Estrutura de Mineração** do **Designer de Data Mining**.  
  
 **Para obter mais informações:** [Tabelas Aninhadas &#40;Analysis Services – Data mining&#41;](data-mining/nested-tables-analysis-services-data-mining.md), [Assistente de Data Mining &#40;Analysis Services – Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md) e [Criar uma estrutura de mineração relacional](data-mining/create-a-relational-mining-structure.md)  
  
## <a name="options"></a>Opções  
 **Tabelas**  
 Exibe as tabelas na exibição da fonte de dados selecionada na página **Selecionar Exibição da Fonte de Dados** do assistente.  
  
 **Caso**  
 Selecione uma tabela a ser usada como a tabela de casos.  
  
 **Aninhados**  
 Selecione as tabelas a serem usadas como tabelas aninhadas.  
  
> [!NOTE]  
>  Essas tabelas devem ter uma relação de muitos para um com a tabela de casos e não uma relação de um para muitos. Você deve especificar essa relação na exibição da fonte de dados para poder selecionar a tabela como aninhada.  
  
## <a name="see-also"></a>Consulte também  
 [Ajuda F1 do Assistente de mineração de dados &#40;Analysis Services - mineração de dados&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [Selecionar exibição da fonte de dados &#40;Assistente de mineração de dados&#41;](select-data-source-view-data-mining-wizard.md)   
 [Especificar os dados de treinamento &#40;Assistente de mineração de dados&#41;](specify-the-training-data-data-mining-wizard.md)  
  
  