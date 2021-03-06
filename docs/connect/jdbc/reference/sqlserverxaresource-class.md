---
title: Classe SQLServerXAResource | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: df957b79-536f-4db7-b6ac-3d59343559fc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 282201b7ff3f5b2ebfe4d8a1224d4d1b39285c53
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67970084"
---
# <a name="sqlserverxaresource-class"></a>Classe SQLServerXAResource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Representa um XAResource para o gerenciamento de transações distribuídas XA.  
  
 **Pacote:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** java.lang.Object  
  
 **Implementa:** javax.transaction.xa.XAResource  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public class SQLServerXAResource  
```  
  
## <a name="remarks"></a>Remarks  
 As transações XA são implementadas no [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] usando o [!INCLUDE[msCoName](../../../includes/msconame_md.md)] DTC (Gerenciador de Transações Distribuídas). A classe SQLServerXAResource faz chamadas a uma dll estendida do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] denominada sqljdbc_xa.dll, que faz interface com o DTC. As chamadas XA que são recebidas pelo SQLServerXAResource (XA_START, XA_END, XA_PREPARE e assim por diante) são mapeadas para as chamadas correspondentes às funções do DTC.  
  
## <a name="see-also"></a>Consulte Também  
 [Membros SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Referência de API do JDBC Driver](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
