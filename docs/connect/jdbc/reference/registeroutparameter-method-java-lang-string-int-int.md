---
title: Método registerOutParameter para digitar e dimensionar | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.registerOutParameter (java.lang.String, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8bddc557-4526-4843-9804-05dc83c8832d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 134fcc223486971bb8249f1313c84ce969308626
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67975935"
---
# <a name="registeroutparameter-method-javalangstring-int-int"></a>Método registerOutParameter (java.lang.String, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Registra o parâmetro OUT com o nome especificado para a escala e o tipo de JDBC fornecidos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public void registerOutParameter(java.lang.String s,  
                                 int n,  
                                 int n1)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *s*  
  
 Uma **String** que contém o nome do parâmetro.  
  
 *sqlType*  
  
 Um código do tipo de JDBC, conforme definido em java.sql.Types.  
  
 *scale*  
  
 Um **int** que indica o número de dígitos a serem colocados à direita da vírgula decimal.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Esse método registerOutParameter é especificado pelo método registerOutParameter na interface java. Sql. CallableStatement.  
  
## <a name="see-also"></a>Consulte Também  
 [Método registerOutParameter &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [Membros SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
