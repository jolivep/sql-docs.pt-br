---
title: Alocar um identificador de ambiente | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-communication
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, environment handles
- ODBC applications, connections
- handles [SQL Server Native Client]
- environment handles [SQLNCLI]
ms.assetid: 15c1b428-ea6d-4672-894c-f0e289e2da3f
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1f7f5442bc8cb3a6e5443d25e196b0e4567bba3c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="allocating-an-environment-handle"></a>Alocando um identificador de ambiente
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Antes que um aplicativo possa chamar qualquer função ODBC, ele deve inicializar o ambiente de ODBC e alocar um identificador de ambiente. Trata-se do identificador de contexto global e do espaço reservado para os demais identificadores no ODBC. Você pode fazer isso chamando **SQLAllocHandle** com o *HandleType* parâmetro definido como SQL_HANDLE_ENV e *InputHandle* definido como SQL_NULL_HANDLE.  
  
 Depois de alocar o identificador de ambiente, o aplicativo deve definir atributos de ambiente para indicar qual versão das chamadas de função ODBC será usada. Para usar o ODBC 3. *x* chamar funções, [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md) com o *atributo* parâmetro definido como SQL_ATTR_ODBC_VERSION e *ValuePtr* definido como SQL_OV_ ODBC3.  
  
## <a name="see-also"></a>Consulte também  
 [Comunicação com o SQL Server &#40; ODBC &#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  