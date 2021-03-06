---
title: Classe SQLServerException | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: af5ef257-7cf6-4db3-b1ee-07d22d82bef1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 40474f747022c34994dba9f34dbed15f1791c2af
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67971151"
---
# <a name="sqlserverexception-class"></a>Classe SQLServerException
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Representa uma execução malsucedida ou incompleta de uma instrução SQL.  
  
 **Pacote:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** java.sql.SQLException  
  
 **Implementa:** java.io.Serializable  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public final class SQLServerException  
```  
  
## <a name="remarks"></a>Remarks  
 A classe SQLServerException manipula os códigos de estado do SQL 92 e do XOPEN. Eles podem ser trocados usando uma propriedade de conexão especificada pelo usuário. As exceções são gravadas em qualquer arquivo de log aberto que foi especificado.  
  
## <a name="see-also"></a>Consulte Também  
 [Membros SQLServerException](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [Referência de API do JDBC Driver](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
