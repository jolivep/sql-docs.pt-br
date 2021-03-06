---
title: Trabalhando com tipos de dados (JDBC) | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b39f44d0-3710-4bc6-880c-35bd8c10a734
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f45b8fdf1fa0ef03bdb014ee3553d2e8bf23d29a
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69025699"
---
# <a name="working-with-data-types-jdbc"></a>Trabalhando com tipos de dados (JDBC)

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

A função primária do [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] é permitir que os desenvolvedores Java acessem dados contidos nos bancos de dados do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para realizar isso, o driver JDBC atua como mediador da conversão entre tipos de dados do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e tipos e objetos da linguagem Java.  
  
> [!NOTE]  
> Para acompanhar uma discussão detalhada dos tipos de dados do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e do driver JDBC, incluindo as suas diferenças e como eles são convertidos para tipos de dados da linguagem Java, veja [Entendendo os tipos de dados do JDBC Driver](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md).  
  
Para trabalhar com tipos de dados do SQL Server, o driver JDBC fornece métodos get\<Type> e set\<Type> para as classes [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) e [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), e fornece os métodos get\<Type> e update\<Type> para a classe [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md). Qual método você usa depende do tipo de dados com os quais você está trabalhando, e se você está usando conjuntos de resultados ou consultas.  
  
Os tópicos nesta seção descrevem como usar os tipos de dados do driver JDBC para acessar dados do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] em seus aplicativos Java.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Exemplo de tipos de dados básicos](../../connect/jdbc/basic-data-types-sample.md)|Descreve como usar métodos getter de conjunto de resultados para recuperar valores de tipo de dados básicos do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], além de como usar métodos de atualização de conjunto de resultados para atualizar esses valores.|  
|[Exemplo de tipo de dados SQLXML](../../connect/jdbc/sqlxml-data-type-sample.md)|Descreve como armazenar dados XML em um banco de dados relacional, como recuperar dados XML de um banco de dados, e como analisar dados XML com um tipo de dados **SQLXML** Java.|  
|[Exemplo de tipos de dados espaciais](../../connect/jdbc/spatial-data-types-sample.md)|Descreve como armazenar e recuperar dados com tipos de dataespaciais ' Geometry ' e ' geography [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ' de banco de dado com **geometria** e **geography** de tipo Java definidos pelo Microsoft JDBC Driver.|

## <a name="see-also"></a>Confira também

[Aplicativos de exemplo do JDBC Driver](../../connect/jdbc/sample-jdbc-driver-applications.md)  
