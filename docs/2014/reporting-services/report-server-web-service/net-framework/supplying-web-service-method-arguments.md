---
title: Fornecendo argumentos de método de serviço Web | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- methods [Reporting Services], arguments
- XML Web service [Reporting Services], methods
ms.assetid: f7b9ca05-fc4c-4b30-8e5d-172dd0f4a832
caps.latest.revision: 38
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: e5457181efd539029f4f3e0b35e0297491f9d835
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36118808"
---
# <a name="supplying-web-service-method-arguments"></a>Fornecendo argumentos de método de serviço Web
  Um método do serviço Web do servidor de relatório envia uma solicitação para o serviço em uma determinada URL usando o SOAP por meio do HTTP. O serviço recebe a solicitação, a processa e, em seguida, retorna uma resposta. Essas solicitações e respostas estão no formulário de documentos XML.  
  
## <a name="optional-parameters"></a>Parâmetros opcionais  
 Em alguns casos, um método de serviço Web pode ter parâmetros de entrada opcionais. Mesmo se um parâmetro de entrada para um método de serviço Web for opcional, você deverá incluí-lo e definir o valor do parâmetro como `null` (`Nothing` no [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]). A definição de um valor de parâmetro como `null` define o valor do elemento para aquele parâmetro na solicitação de SOAP como `null`.  
  
 O exemplo a seguir usa o método <xref:ReportService2010.ReportingService2010.CreateFolder%2A> para criar uma nova pasta nomeada como Vendas de Produto na pasta Vendas. Ao fornecer um valor `null` para as propriedades da pasta, nenhuma propriedade específica para o usuário será fornecida para a pasta:  
  
```  
// C#  
rs.CreateFolder("Product Sales", "/Sales", null);  
```  
  
## <a name="complex-data-types"></a>Tipos dados complexos  
 A classe principal do serviço Web Servidor de Relatórios é <xref:ReportService2010.ReportingService2010>, que você usa para invocar as operações SOAP ou os métodos Web da classe proxy. Para suportar essa classe e seus métodos, o [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] inclui tipos de dados complexos definidos pelo usuário que são específicos para os parâmetros de entrada e saída dos métodos de serviço Web. Esses tipos de dados complexos fazem parte da classe proxy gerada, que você pode usar quando estiver desenvolvendo soluções no ambiente do [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
 Quando você gera uma classe de proxy, os tipos de dados complexos que são definidos no arquivo WSDL são representados pelas classes de proxy, que incluem propriedades que correspondem a vários elementos SOAP dos tipos de dados complexos. As sequências desses tipos de dados se tornam matrizes de objetos que você pode enumerar através de seu código. Isso elimina a necessidade de trabalhar diretamente com as estruturas de XML enviadas nas mensagens de SOAP. O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] trata dessa tradução para você.  
  
## <a name="see-also"></a>Consulte também  
 [Criando aplicativos usando o serviço Web e o .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)   
 [Serviço Web do Servidor de Relatório](../report-server-web-service.md)   
 [Referência técnica &#40;SSRS&#41;](../../technical-reference-ssrs.md)  
  
  