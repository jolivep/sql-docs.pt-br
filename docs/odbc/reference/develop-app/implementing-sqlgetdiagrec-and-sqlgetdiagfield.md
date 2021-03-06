---
title: Implementando SQLGetDiagRec e SQLGetDiagField | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], and SQLGetDiagRec
- SQLGetDiagRec function [ODBC], and SQLGetDiagField
- diagnostic information [ODBC], SqlGetDiagRec
- retrieving diagnostic information [ODBC]
ms.assetid: 11ba1857-b533-4517-8131-a2a8a0154a0a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a4b602d5ff4a94d2888395e6a62f03553fb50f98
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68216372"
---
# <a name="implementing-sqlgetdiagrec-and-sqlgetdiagfield"></a>Implementar SQLGetDiagRec e SQLGetDiagField
**SQLGetDiagRec** e **SQLGetDiagField** são implementados pelo Gerenciador de driver e por cada driver. O Gerenciador de driver e cada driver mantêm registros de diagnóstico para cada ambiente, conexão, instrução e identificador de descritor e liberam esses registros somente quando outra função é chamada com esse identificador ou o identificador é liberado.  
  
 Embora o Gerenciador de driver e cada driver devam determinar o primeiro registro de status de acordo com as classificações em [sequência de registros de status](../../../odbc/reference/develop-app/sequence-of-status-records.md), o Gerenciador de driver determina a sequência final de registros.  
  
 **SQLGetDiagRec** e **SQLGetDiagField** não postam registros de diagnóstico sobre si mesmos.  
  
 Esta seção contém os seguintes tópicos:  
  
-   [Regras de tratamento de diagnóstico](../../../odbc/reference/develop-app/diagnostic-handling-rules.md)  
  
-   [Função do Gerenciador do Driver](../../../odbc/reference/develop-app/role-of-the-driver-manager.md)  
  
-   [Função do driver](../../../odbc/reference/develop-app/role-of-the-driver.md)
