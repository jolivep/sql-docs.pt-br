---
title: Especificar eventos e colunas de dados para um arquivo de rastreamento (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- adding events
- traces [SQL Server], data columns
- deleting events
- removing events
- traces [SQL Server], events
ms.assetid: 7da715a3-2f03-4063-b6a4-20fd7b44e675
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 4ed34a9e051435e7f6e990b445cf0ffd88383f09
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68059687"
---
# <a name="specify-events-and-data-columns-for-a-trace-file-sql-server-profiler"></a>Especificar eventos e colunas de dados para um arquivo de rastreamento (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Este tópico descreve como especificar classes de evento e colunas de dados para rastreamentos usando o [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-specify-events-and-data-columns-for-a-trace"></a>Para especificar eventos e colunas de dados para um rastreamento  
  
1.  Na caixa de diálogo **Propriedades do Rastreamento** ou **Propriedades do Modelo de Rastreamento** , clique na guia **Seleção de Eventos** .  
  
     A guia **Seleção de Eventos** contém um controle de grade. O controle de grade é uma tabela que contém cada uma das classes de evento rastreáveis. A tabela contém uma linha para cada classe de evento. As classes de evento podem diferir ligeiramente, dependendo do tipo e versão de servidor com o qual você está conectado. As classes de evento são identificadas na coluna **Events**da grade e são agrupadas por categoria de evento. As colunas restantes listam as colunas de dados que podem ser retornadas para cada classe de evento.  
  
2.  Na guia **Seleção de Eventos**, use o controle da grade para adicionar ou remover eventos e colunas de dados do arquivo de rastreamento.  
  
3.  Para remover eventos do rastreamento, desmarque a caixa de seleção na coluna **Eventos** para cada classe de evento.  
  
4.  Para incluir eventos em um rastreamento, marque a caixa de seleção na coluna **Eventos** para cada classe de evento ou marque uma coluna de dados que corresponda a um evento.  
  
> [!IMPORTANT]  
>  Se o rastreamento precisar ser correlacionado com os dados do Monitor do Sistema ou do Monitor de Desempenho, as colunas **Start Time** e **End Time** devem ser incluídas no rastreamento.  
  
 Quando uma classe de evento é incluída, todas as colunas de dados associadas a ela também serão incluídas no rastreamento, se você tiver marcado a caixa correspondente a um evento. Caso tenha marcado a caixa para uma coluna em particular, somente essa coluna será incluída no rastreamento.  
  
1.  Para remover colunas de dados de uma classe de evento, desmarque as caixas de seleção da coluna de dados na linha de classe de evento ou clique com o botão direito do mouse no cabeçalho de coluna e selecione a opção **Desmarcar seleção de coluna** .  
  
2.  Outra alternativa é aplicar filtros ao rastreamento. Para obter mais informações, veja [Filtrar eventos em um rastreamento &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)  
  
## <a name="see-also"></a>Consulte Também  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
