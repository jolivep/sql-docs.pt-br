---
title: Resolvedores baseados em Microsoft COM | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- COM-based resolvers [SQL Server replication]
- custom resolvers [SQL Server replication]
ms.assetid: a6637e4b-4e6b-40aa-bee6-39d98cc507c8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8fb5a27e9087044b1049106ca5abd071db74af9f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63240208"
---
# <a name="microsoft-com-based-resolvers"></a>Microsoft COM-Based Resolvers
  Todos os resolvedores baseados em COM fornecidos com [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tratam de conflitos de atualização e, quando indicado, tratam de conflitos de inserção e exclusão. Todos eles tratam de rastreamento de colunas; a maioria também trata de rastreamento de linhas. Estes e todos os outros resolvedores baseados em COM declaram os tipos de conflito que eles podem tratar e o Merge Agent usa o resolvedor padrão para todos os outros tipos de conflito.  
  
 Os resolvedores são instalados durante o processo de instalação para [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Execute o procedimento armazenado **sp_enumcustomresolvers** para exibir todos os resolvedores de conflito registrados em um computador. Executar o procedimento exibe a descrição e o GUID (identificador global exclusivo) para cada resolvedor em um conjunto de resultados separado.  
  
 Para especificar um resolvedor, consulte [Specify a Merge Article Resolver](../publish/specify-a-merge-article-resolver.md).  
  
 A tabela a seguir descreve os atributos dos resolvedores específicos.  
  
|Nome|Entrada Requerida|DESCRIÇÃO|Comentários|  
|----------|--------------------|-----------------|--------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Resolvedor de conflitos aditivo|Nome da coluna que será somada. Deve ter um tipo de dado aritmético (como **int**, **smallint**, **numeric**e assim por diante).|O vencedor de conflito é determinado a partir do valor de prioridade. Valores de coluna especificados são definidos pela soma dos valores de coluna de origem e de destino. Se um for definido como NULL, eles serão definidos pelo valor da outra coluna.|Oferece suporte apenas a conflitos de atualização e rastreamento de coluna.|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Resolvedor de conflitos de média|Nome da coluna a ser calculada pela média. Deve ter um tipo de dado aritmético (como **int**, **smallint**, **numeric**e assim por diante).|O vencedor de conflito é determinado a partir do valor de prioridade. Os valores de coluna resultantes são definidos pela média dos valores de coluna de origem e de destino. Se um for definido como NULL, eles serão definidos pelo valor da outra coluna.|Oferece suporte apenas a conflitos de atualização e rastreamento de coluna.|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Resolvedor de conflitos de DateTime (WINS anterior)|Nome da coluna a ser usada para determinar o vencedor de conflito. Deve ter um tipo de dados **datetime** .|A coluna com o valor de **datetime** mais antigo determina o vencedor de conflito. Se um for definido como NULL, a linha que contém o outro será a vencedora.|Fornece suporte a conflitos de atualização, linha e rastreamento de coluna. Os valores de coluna são comparados diretamente e não é feito um ajuste para fusos de horário diferentes.|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Resolvedor de conflitos de DateTime (WINS posterior)|Nome da coluna a ser usada para determinar o vencedor de conflito. Deve ter tipo de dados **datetime** .|A coluna com o valor de **datetime** mais recente determina o vencedor de conflito. Se um for definido como NULL, a linha que contém o outro será a vencedora.|Fornece suporte a conflitos de atualização, linha e rastreamento de coluna.|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Resolvedor de conflitos máximo|Nome da coluna a ser usada para determinar o vencedor de conflito. Deve ter um tipo de dado aritmético (como **int**, **smallint**, **numeric**e assim por diante).|A coluna com o valor numérico maior determina o vencedor de conflito. Se um for definido como NULL, a linha que contém o outro será a vencedora.|Oferece suporte a rastreamento de linha e coluna.|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Resolvedor de conflitos mínimo|Nome da coluna a ser usada para determinar o vencedor de conflito. Deve ter um tipo de dado aritmético (como **int**, **smallint**, **numeric**e assim por diante).|A coluna com o valor numérico menor determina o vencedor de conflito. Se um for definido como NULL, a linha que contém o outro será a vencedora.|Fornece suporte a conflitos de atualização, rastreamento de linha e coluna.|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Resolvedor de conflitos de texto de mesclagem|Nome da coluna de texto e delimitador, por exemplo, `@resolver_info = '[col1][===]'`.|O vencedor de conflito é determinado a partir do valor de prioridade. As colunas de texto em conflito são definidas com o valor de mesclagem, consistindo do prefixo comum seguido pela parte exclusiva do Publicador, depois pelo delimitador e finalmente pela parte exclusiva do Assinante.|Oferece suporte apenas a conflitos de atualização e rastreamento de coluna.|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Resolvedor de conflitos do assinante sempre WINS|Nenhuma entrada.|O Assinante, independentemente de ser a fonte ou destino, é o vencedor.|Oferece suporte a todos os tipos de conflito.|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Resolvedor de coluna de prioridade|Nome da coluna a ser usada para determinar o vencedor de conflito. Deve ter um tipo de dado aritmético (como **int**, **smallint**, **numeric**e assim por diante).|A coluna com o valor numérico maior determina o vencedor de conflito. Se um for definido como NULL, a linha que contém o outro será a vencedora.|Fornece suporte a conflitos de atualização, rastreamento de linha e coluna.|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Resolvedor de conflitos somente upload|Nenhuma entrada.|As alterações carregadas no Publicador são aceitas; não são baixadas alterações no Assinante.|Oferece suporte a todos os tipos de conflito.|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Resolvedor de conflitos somente download|Nenhuma entrada.|As alterações carregadas no Publicador são rejeitadas; são baixadas alterações no Assinante.|Oferece suporte a todos os tipos de conflito.|  
|Resolvedor de Procedimento Armazenado do[!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQL Server|Nome do procedimento armazenado que o resolvedor deverá chamar para tratar do conflito.|A resolução de conflito depende da lógica no procedimento armazenado que você especifica.|Oferece suporte a conflitos de atualização. Para obter mais informações, consulte [implementar um resolvedor de conflitos personalizado para um artigo de mesclagem](../implement-a-custom-conflict-resolver-for-a-merge-article.md)|  
  
## <a name="see-also"></a>Consulte Também  
 [Detecção e resolução de conflito de replicação de mesclagem avançada](advanced-merge-replication-conflict-detection-and-resolution.md)   
 [&#41;&#40;Transact-SQL de sp_enumcustomresolvers](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)  
  
  
