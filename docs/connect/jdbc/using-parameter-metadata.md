---
title: Como usar metadados de parâmetro | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: db2c1957-91c6-4989-a07b-9f8be6d2033a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 80ff8cebcc4141e8363c25f83821cb4924e6c46a
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69026082"
---
# <a name="using-parameter-metadata"></a>Como usar metadados de parâmetro

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Para consultar um objeto [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) ou [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) sobre os parâmetros que eles contêm, o [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] implementa a classe [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md). Esta classe contém diversos campos e métodos que retornam informações como um único valor.

Para criar um objeto SQLServerParameterMetaData, você pode usar os métodos [getParameterMetaData](../../connect/jdbc/reference/getparametermetadata-method-sqlserverpreparedstatement.md) das classes SQLServerPreparedStatement e SQLServerCallableStatement.

No exemplo a seguir, uma conexão aberta com o [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] banco de dados de exemplo é passada para a função, o método getParameterMetaData da classe SQLServerCallableStatement é usado para retornar um objeto SQLServerParameterMetaData e, em seguida, vários os métodos do objeto SQLServerParameterMetaData são usados para exibir informações sobre o tipo e o modo dos parâmetros contidos no procedimento armazenado HumanResources. uspUpdateEmployeeHireInfo.

[!code[JDBC#UsingParamMetaData1](../../connect/jdbc/codesnippet/Java/using-parameter-metadata_1.java)]  

> [!NOTE]  
> Há algumas limitações ao usar a classe SQLServerParameterMetaData com instruções preparadas.
>
> **Com o Microsoft JDBC Driver 6.0 (ou superior) para SQL Server**: ao usar o SQL Server 2008 ou 2008 R2, o driver JDBC dá suporte para as instruções SELECT, DELETE, INSERT e UPDATE, uma vez que essas instruções não contêm subconsultas e/ou junções.

Consultas de mesclagem também não têm suporte para a classe SQLServerParameterMetaData ao usar o SQL Server 2008 ou 2008 R2. Para o SQL Server 2012 e metadados de parâmetro de versões anteriores com consultas complexas que têm suporte.

Não há suporte para a recuperação de metadados de parâmetro para colunas criptografadas. **Com o Microsoft JDBC Driver 4.1 ou 4.2 para SQL Server**: o driver JDBC dá suporte para as instruções SELECIONAR, EXCLUIR, INSERIR e ATUALIZAR, uma vez que essas instruções não contêm subconsultas e/ou junções. As consultas de MESCLAgem também não são suportadas para a classe SQLServerParameterMetaData.
