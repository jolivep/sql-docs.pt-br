---
title: SQLColAttributes (driver do Paradox) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLColAttributes
ms.assetid: bbeef024-d470-4d28-b61b-26997ef41007
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9b7d5967108d605d6b7426dcd662507a49037108
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68132659"
---
# <a name="sqlcolattributes-paradox-driver"></a>SQLColAttributes (Driver do Paradox)
> [!NOTE]  
>  Este tópico fornece informações específicas do driver do Paradox. Para obter informações gerais sobre essa função, consulte o tópico apropriado em [referência da API do ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Atributo|Comentários|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Para dados LONGVARBINARY, SQL_COLUMN_DISPLAY_SIZE é o comprimento máximo da coluna, não o comprimento máximo da coluna vezes 2.|  
|SQL_OWNER_NAME|Uma cadeia de caracteres vazia ("") é retornada nesta coluna porque não há suporte para o nome do proprietário.|  
|SQL_QUALIFIER_NAME|O caminho para um diretório é retornado.|  
|SQL_COLUMN_SEARCHABLE|As colunas LONGVARBINARY e LONGVARCHAR são relatadas como SQL_UNSEARCHABLE.<br /><br /> Os tipos de dados Binary e Character de comprimento fixo e variável são pesquisáveis, mesmo que LONGVARBINARY e LONGVARCHAR não estejam.|  
  
> [!NOTE]  
>  O acima não é uma lista completa dos atributos retornados por **SQLColAttributes**.
