---
title: Método setSendStringParametersAsUnicode (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setSendStringParametersAsUnicode
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 49198d63-76cb-4843-8d04-e49b1fbb6916
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fe32325caccebd0e85204bbbc11b7a0cbe4eefca
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67972988"
---
# <a name="setsendstringparametersasunicode-method-sqlserverdatasource"></a>Método setSendStringParametersAsUnicode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Define um valor **booliano** que indica se o envio de parâmetros de cadeia de caracteres ao servidor no formato UNICODE está habilitado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public void setSendStringParametersAsUnicode(boolean sendStringParametersAsUnicode)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *sendStringParametersAsUnicode*  
  
 **true** se os parâmetros da cadeia de caracteres são enviados ao servidor no formato UNICODE. Caso contrário, **false**.  
  
## <a name="remarks"></a>Remarks  
 Se a propriedade sendStringParametersAsUnicode for definida como **true**, que é o valor padrão, os parâmetros de cadeia de caracteres serão enviados ao servidor no formato UNICODE. Se a propriedade sendStringParametersAsUnicode for definida como **false**, os parâmetros de cadeia de caracteres serão enviados ao servidor em um formato ASCII/MBCS, e não em UNICODE. Se sendStringParametersAsUnicode não for definida, [getSendStringParametersAsUnicode](../../../connect/jdbc/reference/getsendstringparametersasunicode-method-sqlserverdatasource.md) retornará o valor padrão, **true**.  
  
 Para obter mais informações sobre a propriedade de conexão sendStringParametersAsUnicode, consulte [definindo as propriedades de conexão](../../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Membros de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
