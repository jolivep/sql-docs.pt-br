---
title: Propriedades da coluna (página geral) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.columnproperties.general.f1
ms.assetid: a745890b-994e-4c23-8028-5c83751e60c4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 741c8633a9b7eed9fcd253918c34a27119e51ee4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62854906"
---
# <a name="column-properties-general-page"></a>Propriedades da coluna (página Geral)
  Use esta página para exibir as propriedades da coluna selecionada.  
  
 As informações nesta página são somente leitura. Para modificar a coluna, feche a caixa de diálogo **Propriedades da Coluna** , expanda a tabela e as colunas no Pesquisador de Objetos, clique com o botão direito do mouse na coluna e, depois clique em **Design**.  
  
## <a name="options"></a>Opções  
 **Nome**  
 O nome da coluna.  
  
 **Tipo de dados**  
 O tipo de dados que a coluna pode conter. Se o tipo de dados for um tipo definido pelo usuário, o tipo de dados definido pelo usuário será exibido. Se o tipo de dados não for um tipo definido pelo usuário, então o tipo de dados de sistema será exibido. Para obter mais informações, veja [Tipos de dados &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).  
  
 **Tipo de sistema**  
 O tipo de dados que a coluna pode conter. Se o tipo de dados for um tipo de dados de sistema, então o tipo de dados de sistema será exibido. Se o tipo de dados for um tipo definido pelo usuário, o tipo de dados de sistema que corresponde ao tipo de dados definido pelo usuário será exibido.  
  
 **Chave primária**  
 Indica se a coluna é uma chave primária. Os valores possíveis são **True**e **False**.  
  
 **Permitir Nulos**  
 Indica se a coluna aceita valores nulos. Os valores possíveis são **True** e **False**.  
  
 **É computado**  
 Indica se o valor de coluna é o resultado de uma expressão computada.  
  
 **Texto computado**  
 Indica a instrução usada para computar o texto da coluna. Para obter mais informações, veja [Especificar colunas computadas em uma tabela](specify-computed-columns-in-a-table.md).  
  
 **Identidade**  
 Indica se a coluna é a coluna de identidade da tabela. Os valores possíveis são **True** e **False**.  
  
 **Semente de identidade**  
 Indica o valor de linha inicial para uma coluna de identidade.  
  
 **Incremento de identidade**  
 A propriedade **Incremento de Identidade** especifica o valor que o [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] adiciona ao maior valor existente de linha de identidade ao gerar um valor de identidade para uma linha que esteja sendo inserida.  
  
 **Associação padrão**  
 O padrão [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] associado à coluna. Essa opção estará em branco se nenhum padrão estiver associado.  
  
 **Esquema Padrão**  
 Identifica o esquema de banco de dados que possui o padrão associado à coluna referenciada. Essa opção estará em branco se nenhum padrão estiver associado.  
  
 **Régua**  
 Identifica a restrição de integridade de dados que está associada à coluna. Essa opção estará em branco se nenhuma regra estiver associada.  
  
 **Esquema de regra**  
 Exibe o esquema do banco de dados do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que possui a regra associada à coluna referenciada. Essa opção estará em branco se nenhuma regra estiver associada.  
  
 **Comprimento**  
 Indica o número máximo de caracteres ou bytes aceito pela coluna.  
  
 **Ordenação**  
 Exibe a ordenação atual para a coluna. Se estiver em branco, a propriedade de ordenação é herdada do objeto.  
  
 **Precisão numérica**  
 Indica o número máximo de dígitos em um tipo de dados numérico de precisão fixa.  
  
 **Escala numérica**  
 Indica o número de dígitos à direita da vírgula decimal em um tipo de dados numérico de precisão fixa.  
  
 **Namespace de esquema XML**  
 Define o tipo da coluna de XML por meio da validação da Linguagem de Definição de Esquema XML (XSD).  
  
 **Esquema de namespace de esquema XML**  
 O esquema do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que possui o Namespace de Esquema XML.  
  
> [!NOTE]  
>  Há vários significados comuns, mas diferentes, da palavra esquema. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usa o esquema para organizar os objetos de bancos de dados. É semelhante à propriedade. A XML usa o esquema para definir a organização de informações de XML em uma série de namespaces. É um modo de agrupar códigos XML relacionados.  
  
 **É esparso**  
 Indica se a coluna é uma coluna esparsa. Os valores possíveis são **True** e **False**. Para obter mais informações, veja [Usar colunas esparsas](use-sparse-columns.md).  
  
 **É conjunto de colunas**  
 Indica se a coluna é um conjunto de colunas. Os valores possíveis são **True** e **False**. Para obter mais informações, veja [Usar conjuntos de colunas](use-column-sets.md).  
  
 **Status de preenchimento ANSI**  
 Indica se o preenchimento ANSI está ativado ou desativado. Para obter mais informações, veja [SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql).  
  
 **Texto completo**  
 Especifica se a coluna participa de consultas de texto completo.  
  
 **Semântica estatística**  
 Indica se a pesquisa de semântica estatística está habilitada para a coluna. Para obter mais informações, veja [Pesquisa semântica &#40;SQL Server&#41;](../search/semantic-search-sql-server.md).  
  
 **Não para replicação**  
 Indica se a coluna está disponível para replicação. Os valores possíveis são **True** e **False**.  
  
  
