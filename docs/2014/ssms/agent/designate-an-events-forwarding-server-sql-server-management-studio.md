---
title: Designar um servidor (SQL Server Management Studio) de encaminhamento de eventos | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- event forwarding servers [SQL Server]
- events [SQL Server], forwarding
- alerts [SQL Server], forwarded events
ms.assetid: 81dfcbe4-3000-4e77-99de-bf85fef63a12
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 36b795f0f4ecb1c594073a98da7dfc03bf5bed3c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37220766"
---
# <a name="designate-an-events-forwarding-server-sql-server-management-studio"></a>Designate an Events Forwarding Server (SQL Server Management Studio)
  Este tópico descreve como designar um servidor para o qual o [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] encaminhe eventos no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Observe que o encaminhamento de eventos se aplica a eventos encaminhados entre servidores, não a eventos encaminhados entre instâncias do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hospedadas em um único computador. Note também que, para receber eventos encaminhados, o servidor de gerenciamento de alertas deve ser uma instância padrão do SQL Server.  
  
 **Neste tópico**  
  
-   **Antes de começar:**  
  
     [Segurança](#Security)  
  
-   **Para designar um servidor de encaminhamento de eventos, usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="Security"></a> Segurança  
  
####  <a name="Permissions"></a> Permissões  
 Exige associação à função de servidor fixa **sysadmin** .  
  
##  <a name="SSMSProcedure"></a> Usando o SQL Server Management Studio  
  
#### <a name="to-designate-an-events-forwarding-server"></a>Para designar um servidor de encaminhamento de eventos  
  
1.  No **Pesquisador de Objetos** , clique no sinal de adição para expandir o servidor do qual você deseja encaminhar eventos para outro servidor.  
  
2.  Clique com o botão direito do mouse em **SQL Server Agent** e selecione **Propriedades**.  
  
3.  Na caixa de diálogo **Propriedades do SQL Server Agent –***server_name*, em **Selecionar uma página**, selecione **Avançado**.  
  
4.  Em **Encaminhamento de evento do SQL Server**, marque a caixa de seleção **Encaminhar eventos para um servidor diferente** .  
  
5.  Na lista **Servidor** , selecione um servidor e, em **Eventos**, selecione um destes procedimentos:  
  
    -   Selecione **Eventos sem tratamento** para encaminhar apenas os eventos que não foram manipulados por alertas locais.  
  
    -   Selecione **Todos os eventos** para encaminhar todos os eventos, independentemente de terem sido manipulados por alertas locais.  
  
6.  Na lista **Se a severidade do evento for esta ou acima** , clique no nível de severidade em que os eventos devem ser encaminhados para o servidor selecionado.  
  
7.  Quando terminar, clique em **OK**.  
  
  