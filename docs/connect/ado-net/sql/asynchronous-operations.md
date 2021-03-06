---
title: Operações assíncronas
description: Descreve como executar operações de banco de dados assíncronas usando uma API que é modelada após o modelo assíncrono usado pelo .NET Framework.
ms.date: 09/30/2019
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 79cde936328476408fabb3df7a6bff8d983ace1c
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452327"
---
# <a name="asynchronous-operations"></a>Operações assíncronas

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Download ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Algumas operações de banco de dados, como execuções de comando, podem levar muito tempo para serem concluídas. Nesse caso, aplicativos de thread único devem bloquear outras operações e aguardar que o comando seja concluído antes que possam continuar suas próprias operações. Por outro lado, poder atribuir a operação demorada a um thread em segundo plano permite que o thread de primeiro plano permaneça ativo durante toda a operação. Em um aplicativo do Windows, por exemplo, delegar a operação de execução longa para um thread em segundo plano permite que o thread da interface do usuário permaneça responsivo enquanto a operação está em execução.  
  
O .NET fornece vários padrões de design assíncrono padrão que os desenvolvedores podem usar para aproveitar os threads em segundo plano e liberar a interface do usuário ou threads de alta prioridade para concluir outras operações em sua classe <xref:Microsoft.Data.SqlClient.SqlCommand>. Especificamente, os métodos <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteReader%2A> e <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A>, emparelhados com os métodos <xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>, <xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteReader%2A> e <xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A>, fornecem o suporte assíncrono.  
  
> [!NOTE]
>  A programação assíncrona é um recurso fundamental do .NET. Para obter mais informações sobre as diferentes técnicas assíncronas disponíveis para desenvolvedores, consulte [chamando métodos síncronos de forma](https://docs.microsoft.com/dotnet/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously)assíncrona.  
  
Embora o uso de técnicas assíncronas com recursos ADO.NET não adicione nenhuma consideração especial, é importante estar ciente dos benefícios e das armadilhas da criação de aplicativos multithread. Os exemplos a seguir nesta seção apontam vários problemas importantes que os desenvolvedores precisarão levar em conta ao criar aplicativos que incorporam a funcionalidade multithread.  
  
## <a name="in-this-section"></a>Nesta seção  
[Aplicativos do Windows usando retornos de chamada](windows-applications-callbacks.md)  
Fornece um exemplo que demonstra como executar um comando assíncrono com segurança, manipulando corretamente a interação com um formulário e seu conteúdo de um thread separado.  
  
[Aplicativos ASP.NET usando identificadores de espera](aspnet-apps-use-wait-handles.md)  
Fornece um exemplo que demonstra como executar vários comandos simultâneos de uma página do ASP.NET, usando identificadores de espera para gerenciar a operação na conclusão de todos os comandos.  
  
[Sondagem em aplicativos de console](poll-console-applications.md)  
Fornece um exemplo que demonstra o uso de sondagem para aguardar a conclusão de uma execução de comando assíncrono de um aplicativo de console. Essa técnica também é válida em uma biblioteca de classes ou outro aplicativo sem uma interface do usuário.  
  
## <a name="next-steps"></a>Próximas etapas
- [SQL Server e ADO.NET](index.md)
- [Chamando métodos síncronos de forma assíncrona](https://docs.microsoft.com/dotnet/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously)
