---
title: Conectar-se ao SQL Server (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: ceb77a97-d6d5-4a92-90a6-342e97d12b54
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 006a90ca082861aea4fecbe6934947afa2020335
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68006664"
---
# <a name="connect-to-sql-server-accesstosql"></a>Conectar-se ao SQL Server (AccessToSQL)
Use a caixa de diálogo **conectar a SQL Server** para se conectar à instância [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] do que você deseja migrar para o. Para acessar a caixa de diálogo **conectar a SQL Server** , no menu **arquivo** , clique em **conectar-se a SQL Server**.  
  
## <a name="options"></a>Opções  
**Nome do servidor**  
Insira ou selecione a instância do SQL Server à qual se conectar. Por padrão, a instância conectada ao mais recentemente é exibida.  
  
-   Se você estiver se conectando à instância padrão no computador local, poderá inserir **localhost** ou um ponto (**.**).  
  
-   Se você estiver se conectando à instância padrão em outro computador, insira o nome do computador.  
  
-   Se você estiver se conectando a uma instância nomeada em outro computador, insira o nome do computador, uma barra invertida e o nome da instância, como *meuservidor*\\*MyInstance*.  
  
**Porta do servidor**  
Se sua instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] não estiver configurada para aceitar conexões na porta padrão (1433), insira o número da porta. Caso contrário, deixe esse valor em branco.  
  
**Backup de banco de dados**  
Especifique o banco de dados para o qual os objetos e a migração são migrados. Essa opção não está disponível ao reconectar-se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ao.  
  
**Autenticação**  
Selecione o método de autenticação que é usado para se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]conectar ao. Para usar sua conta atual do Windows, selecione Autenticação do Windows. Para especificar um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logon e uma senha, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] selecione autenticação.  
  
**Nome de usuário**  
Se você estiver usando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a autenticação do, insira o logon para essa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]instância do. Se você estiver usando a autenticação do Windows, essa opção não estará disponível.  
  
**Senha**  
Se você estiver usando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a autenticação do, insira a senha para o logon nessa instância [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]do. Se você estiver usando a autenticação do Windows, essa opção não estará disponível.  
  
**Criptografar conexão**  
Se você quiser se conectar com segurança ao SQL Server, faça uso da conexão criptografar marcando a caixa de seleção **criptografar conexão** .  
  
**Confiar no certificado do servidor**  
Se você quiser usar essa opção, marque a caixa de seleção **certificado de servidor confiável** .  
  
> [!NOTE]  
> Para habilitar o **certificado de servidor confiável**, "criptografar" deve ser definido como **true**.  
  
