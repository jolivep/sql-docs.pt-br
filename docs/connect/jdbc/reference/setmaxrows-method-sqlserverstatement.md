---
title: Método setMaxRows (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setMaxRows
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cccc0667-589b-4655-8ea8-14ae8b2eb9dc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1ff4ab9e1db2415c92d42012d45b04c57ac30b67
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67973974"
---
# <a name="setmaxrows-method-sqlserverstatement"></a>Método setMaxRows (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Define o limite para o número máximo de linhas que qualquer objeto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) pode conter como o número fornecido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public final void setMaxRows(int max)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *max*  
  
 Um **int** que indica o número máximo de linhas ou 0 se não houver limite.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Esse método setMaxRows é especificado pelo método setMaxRows na interface java. Sql. Statement.  
  
 Esse método setMaxRows não tem nenhum efeito para cursores roláveis dinâmicos. O aplicativo deve usar sintaxe de SQL SELECT TOP N para limitar o número de linhas retornado de conjuntos de resultados potencialmente grandes.  
  
 Quando o método setMaxRows é chamado, o [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] executa a instrução SQL SET ROWCOUNT quando executa a consulta do aplicativo. Isso leva o driver JDBC a limitar o número máximo de linhas afetado por todas as instruções [!INCLUDE[tsql](../../../includes/tsql-md.md)] executadas por essa consulta, e não apenas o número de linhas retornado por essa consulta. Se o aplicativo precisar definir somente um limite no objeto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) de nível superior, deve usar a sintaxe SQL SELECT TOP N na consulta em vez do método setMaxRows.  
  
 Para saber mais sobre a instrução SQL SET ROWCOUNT, consulte o tópico "[SET ROWCOUNT (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=139522)" nos Manuais Online do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Consulte Também  
 [Membros SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
