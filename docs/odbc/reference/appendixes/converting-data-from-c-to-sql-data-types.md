---
title: Convertendo dados de C para tipos de dados SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], about converting
- converting data from c to SQL types [ODBC]
- data conversions from C to SQL types [ODBC], about converting
- data types [ODBC], C data types
- data types [ODBC], converting data
- SQL data types [ODBC], converting from C types
- data types [ODBC], SQL data types
- data conversions from C to SQL types [ODBC]
- C data types [ODBC], converting to SQL types
ms.assetid: ee0afe78-b58f-4d34-ad9b-616bb23653bd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: aca333a6f3006b1f12cf44d1670e38556027e476
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68019124"
---
# <a name="converting-data-from-c-to-sql-data-types"></a>Converter dados de C para tipos de dados SQL
Quando um aplicativo chama **SQLExecute** ou **SQLExecDirect**, o driver recupera os dados de todos os parâmetros associados ao **SQLBindParameter** de locais de armazenamento no aplicativo. Quando um aplicativo chama **SQLSetPos**, o driver recupera os dados para uma atualização ou adição de uma operação de colunas associadas a **SQLBindCol**. Para parâmetros de dados em execução, o aplicativo envia os dados de parâmetro com **SQLPutData**. Se necessário, o driver converte os dados do tipo de dados especificado pelo argumento *ValueType* em **SQLBindParameter** para o tipo de dados especificado pelo argumento *ParameterType* em **SQLBindParameter**e, em seguida, envia os dados para a fonte de dados.  
  
 A tabela a seguir mostra as conversões com suporte dos tipos de dados ODBC C para tipos de dados ODBC do SQL. Um círculo preenchido indica a conversão padrão para um tipo de dados SQL (o tipo de dados C do qual os dados serão convertidos quando o valor de *ValueType* ou o campo do descritor de SQL_DESC_CONCISE_TYPE for SQL_C_DEFAULT). Um círculo vazio indica uma conversão com suporte.  
  
 O formato dos dados convertidos não é afetado pela configuração de país do Windows®.  
  
 ![Conversões suportadas: tipos de dados ODBC C em SQL](../../../odbc/reference/appendixes/media/apd1b.gif "apd1b")  
  
 As tabelas nas seções a seguir descrevem como o driver ou a fonte de dados converte os dados enviados para a fonte de dados; os drivers são necessários para dar suporte a conversões de todos os tipos de dados ODBC C para os tipos de dados ODBC SQL para os quais dão suporte. Para um determinado tipo de dados ODBC C, a primeira coluna da tabela lista os valores de entrada legais do argumento *ParameterType* em **SQLBindParameter**. A segunda coluna lista os resultados de um teste que o driver executa para determinar se ele pode converter os dados. A terceira coluna lista o SQLSTATE retornado para cada resultado por **SQLExecDirect**, **SQLExecute**, **SQLBulkOperations**, **SQLSetPos**ou **SQLPutData**. Os dados serão enviados para a fonte de dados somente se SQL_SUCCESS for retornado.  
  
 Se o argumento *ParameterType* em **SQLBindParameter** contiver o identificador de um tipo de dados ODBC SQL que não é mostrado na tabela para um determinado tipo de dados C, **SQLBindParameter** retornará SQLSTATE 07006 (violação de atributo de tipo de dados restrito). Se o argumento *ParameterType* contiver um identificador específico de driver e o driver não oferecer suporte à conversão do tipo de dados ODBC C específico para esse tipo de dados SQL específico de driver, **SQLBINDPARAMETER** retornará SQLSTATE HYC00 (recurso opcional não implementado).  
  
 Se os argumentos *ParameterValuePtr* e *StrLen_or_IndPtr* especificados em **SQLBindParameter** forem ambos ponteiros nulos, essa função retornará SQLSTATE HY009 (uso inválido de ponteiro NULL). Embora não seja mostrada nas tabelas, um aplicativo define o valor do buffer de comprimento/indicador apontado pelo argumento *StrLen_or_IndPtr* de **SQLBindParameter** ou o valor do argumento *StrLen_or_IndPtr* de **SQLPutData** para SQL_NULL_DATA para especificar um valor de dados SQL nulo. (O argumento *StrLen_or_IndPtr* corresponde ao campo SQL_DESC_OCTET_LENGTH_PTR do APD.) O aplicativo define esses valores como SQL_NTS para especificar que o valor em \* *ParameterValuePtr* em **SQLBindParameter** ou \* *DataPtr* em **SQLPutData** (apontado pelo campo SQL_DESC_DATA_PTR do APD) é uma cadeia de caracteres terminada em nulo.  
  
 Os seguintes termos são usados nas tabelas:  
  
-   **Tamanho de bytes de dados** -número de bytes de dados SQL disponíveis para enviar para a fonte de dados, se os dados serão truncados antes de serem enviados para a fonte de dados. Para dados de cadeia de caracteres, isso não inclui espaço para o caractere de terminação nula.  
  
-   **Comprimento de byte de coluna** -número de bytes necessários para armazenar os dados na fonte de dados.  
  
-   **Comprimento de byte de caractere** – número máximo de bytes necessários para exibir dados no formato de caractere. Isso é conforme definido para cada tipo de dados SQL no [tamanho de exibição](../../../odbc/reference/appendixes/display-size.md), exceto que comprimento de byte de caractere está em bytes, enquanto o tamanho de exibição está em caracteres.  
  
-   **Número de dígitos** -número de caracteres usados para representar um número, incluindo o sinal de subtração, o ponto decimal e o expoente (se necessário).  
  
-   **Palavras em**   
     ***itálico*** -elementos da gramática SQL. Para obter a sintaxe dos elementos gramaticais, consulte o [Apêndice C: SQL Grammar](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 Esta seção contém os seguintes tópicos:  
  
-   [C para SQL: caractere](../../../odbc/reference/appendixes/c-to-sql-character.md)  
  
-   [C para SQL: numérico](../../../odbc/reference/appendixes/c-to-sql-numeric.md)  
  
-   [C para SQL: bit](../../../odbc/reference/appendixes/c-to-sql-bit.md)  
  
-   [C para SQL: binário](../../../odbc/reference/appendixes/c-to-sql-binary.md)  
  
-   [C para SQL: data](../../../odbc/reference/appendixes/c-to-sql-date.md)  
  
-   [C para SQL: GUID](../../../odbc/reference/appendixes/c-to-sql-guid.md)  
  
-   [C para SQL: hora](../../../odbc/reference/appendixes/c-to-sql-time.md)  
  
-   [C para SQL: carimbo de data/hora](../../../odbc/reference/appendixes/c-to-sql-timestamp.md)  
  
-   [C para SQL: intervalos de ano-mês](../../../odbc/reference/appendixes/c-to-sql-year-month-intervals.md)  
  
-   [C para SQL: intervalos de tempo-dia](../../../odbc/reference/appendixes/c-to-sql-day-time-intervals.md)  
  
-   [Exemplos de conversão de dados de C para SQL](../../../odbc/reference/appendixes/c-to-sql-data-conversion-examples.md)
