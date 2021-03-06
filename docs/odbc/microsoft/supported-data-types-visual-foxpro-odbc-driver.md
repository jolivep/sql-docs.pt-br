---
title: Tipos de dados com suporte (driver ODBC do Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], data types
- FoxPro ODBC driver [ODBC], data types
- data types [ODBC], Visual FoxPro ODBC driver
ms.assetid: ab529cc6-d157-4b35-b6f9-6ffd09af098c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e2d23ddc5fdd00db45aee235e96f13a8cf08082a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68080778"
---
# <a name="supported-data-types-visual-foxpro-odbc-driver"></a>Tipos de dados com suporte (Driver ODBC do Visual FoxPro)
A lista de tipos de dados com suporte pelo driver é apresentada por meio da API ODBC e do Microsoft Query.  
  
## <a name="data-types-in-c-applications"></a>Tipos de dados em aplicativos C  
 Você pode obter uma lista de tipos de dados com suporte pelo driver ODBC do Visual FoxPro usando a função [SQLGetTypeInfo](../../odbc/microsoft/sqlgettypeinfo-visual-foxpro-odbc-driver.md) em aplicativos C ou C++.  
  
## <a name="data-types-in-applications-using-microsoft-query"></a>Tipos de dados em aplicativos usando o Microsoft Query  
 Se seu aplicativo usar o Microsoft Query para criar uma nova tabela em uma fonte de dados do Visual FoxPro, o Microsoft Query exibirá a caixa de diálogo **nova definição de tabela** . Em **Descrição do campo**, a caixa **tipo** lista os tipos de dados de [campo do Visual FoxPro](../../odbc/microsoft/visual-foxpro-field-data-types.md), representados por caracteres únicos.
