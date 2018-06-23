---
title: Medidas no relatório de validação cruzada | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- root mean square error [data mining]
- cross-validation [data mining]
- mean absolute error [data mining]
- log score [data mining]
- likelihood [data mining]
ms.assetid: a07b1665-7f72-4266-82a4-43a91ae2571d
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bedc8656248ced7c8f25b0868804e36ad410d642
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36020611"
---
# <a name="measures-in-the-cross-validation-report"></a>Medidas no relatório de validação cruzada
  Durante a validação cruzada, o [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] divide os dados em uma estrutura de mineração em várias seções cruzadas e, em seguida, iterativamente testa a estrutura e os modelos de mineração associados. Com base nesta análise, ele produz um conjunto de medidas de precisão padrão para a estrutura e cada modelo.  
  
 O relatório contém algumas informações básicas sobre o numero de dobras nos dados, e a quantidade de dados em cada dobra, e um conjunto de métricas gerais que descrevem a distribuição de dados. Comparando as métricas gerais para cada seção cruzada, você pode avaliar a confiabilidade da estrutura ou modelo.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] também exibe um conjunto de medidas detalhadas para modelos de mineração. Estas medidas dependem do tipo de modelo e do tipo de atributo que está sendo analisado: por exemplo, se é discreto ou contínuo.  
  
 Esta seção fornece uma lista das medidas que estão contidas no relatório **Validação Cruzada** e o que elas querem dizer. Para obter detalhes sobre como cada medida é calculada, consulte [Fórmulas de validação cruzada](cross-validation-formulas.md).  
  
## <a name="list-of-measures-in-the-cross-validation-report"></a>Lista de medidas no relatório de validação cruzada  
 A tabela a seguir lista as medidas que aparecem no relatório de validação cruzada. As medidas são agrupadas por *tipo de teste*, que é fornecido na coluna à esquerda da tabela a seguir. A coluna à direita lista o nome da medida como aparece no relatório e fornece uma explicação breve do que significa.  
  
|tipo de teste|Medidas e Descrições|  
|---------------|-------------------------------|  
|Clustering|Medidas que se aplicam a modelos de clustering:<br /><br /> **Probabilidade de caso**: essa medida geralmente indica a probabilidade é que um caso pertencer a um cluster específico. <br />                      Para validação cruzada, as contagens são somadas e, em seguida, divididas pelo número de casos; portanto, aqui a contagem é uma probabilidade de caso média.|  
|Classificação|Medidas que se aplicam a modelos de classificação:<br /><br /> **Verdadeiro positivo**/<br />                      **Verdadeiro negativo**/ **falso positivo**/ **falso positivo**: contagem de linhas ou valores na partição onde o estado previsto corresponde ao estado de destino, e a probabilidade de previsão é maior que o limite especificado. São excluídos casos que têm valores ausentes para o atributo de destino, que significa que as contagens de todos os valores pode não somar|  
||**Aprovado/reprovado**: contagem de linhas ou valores na partição onde o estado previsto corresponde ao estado de destino, e o valor de probabilidade de previsão é maior que 0.|  
|Probabilidade|Medidas de probabilidade aplicam-se a vários tipos de modelo:<br /><br /> **Comparação de precisão**: A taxa de probabilidade da previsão atual para a probabilidade marginal nos casos de teste. Linhas que têm valores ausentes para o atributo de destino são excluídas. Esta medida geralmente mostra quanto a probabilidade do resultado de destino aumenta quando o modelo é usado.<br /><br /> **Erro de raiz quadrada média**: a raiz quadrada do erro médio para todos os casos de partição, dividida pelo número de casos na partição, excluindo as linhas com valores ausentes para o atributo de destino. O RMSE é um avaliador popular para modelos preditivos. A contagem calcula a média dos resíduos para cada caso para render um único indicador de erro modelo.<br /><br /> **Pontuação de log**: O logaritmo da probabilidade real para cada caso, somado e, em seguida, dividido pelo número de linhas no conjunto de dados, exceto as linhas com valores ausentes para o atributo de destino. Como a probabilidade é representada como uma fração decimal, as pontuações de log são sempre números negativos. Um número mais próximo de 0 é uma pontuação melhor. Visto que contagens brutas podem ter distribuições muito irregulares ou distorcidas, uma contagem de log é semelhante a uma porcentagem.|  
|Estimativa|Medidas que se aplicam somente a modelos de estimativa, que preveem um atributo numérico contínuo:<br /><br /> **Erro de raiz quadrada média**: erro médio quando o valor previsto é comparado ao valor real. O RMSE é um avaliador popular para modelos preditivos. A contagem calcula a média dos resíduos para cada caso para render um único indicador de erro modelo.<br /><br /> **Erro de média absoluta**: erro médio quando os valores previstos são comparados aos valores reais, calculados como a média da soma absoluta dos erros. Erro de média absoluta é útil para entender como as previsões em geral estão próximas dos valores reais. Uma pontuação menor significa que as previsões foram mais precisas.<br /><br /> **Pontuação de log**: O logaritmo da probabilidade real para cada caso, somado e, em seguida, dividido pelo número de linhas no conjunto de dados, exceto as linhas com valores ausentes para o atributo de destino. Como a probabilidade é representada como uma fração decimal, as pontuações de log são sempre números negativos. Um número mais próximo de 0 é uma pontuação melhor. Visto que contagens brutas podem ter distribuições muito irregulares ou distorcidas, uma contagem de log é semelhante a uma porcentagem.|  
|Agregações|As medidas de agregação fornecem uma indicação da variação nos resultados para cada partição:<br /><br /> **Significa**: valores de média de partição para uma medida específica.<br /><br /> **Desvio padrão**: média do desvio da média para uma medida específica, em todas as partições em um modelo. Para validação cruzada, um valor mais alto para esta pontuação implica variação significativa entre as dobras.|  
  
## <a name="see-also"></a>Consulte também  
 [Teste e validação &#40;mineração de dados&#41;](testing-and-validation-data-mining.md)  
  
  