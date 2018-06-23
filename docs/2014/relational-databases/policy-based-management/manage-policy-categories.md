---
title: Gerenciar categorias de política | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.dmf.policycategories.f1
ms.assetid: d188a819-731f-4029-98aa-780d3299a0ce
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2b0f69df39befb389deb159a18e0a76fe283170c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36009534"
---
# <a name="manage-policy-categories"></a>Gerenciar Categorias de Política
  Este tópico descreve como aplicar uma ou todas as políticas disponíveis em uma categoria a toda a instância do [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Neste tópico**  
  
-   **Antes de começar:**  
  
     [Limitações e restrições](#Restrictions)  
  
     [Segurança](#Security)  
  
-   **Para aplicar políticas de categoria a uma instância do SQL Server usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="Restrictions"></a> Limitações e restrições  
  
-   Ao usar o [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], se a caixa de seleção **Autorizar Assinaturas de Banco de Dados** não estiver selecionada, a categoria de política deve ser aplicada individualmente a cada parte relevante do servidor, como em um ou mais bancos de dados e tabelas.  
  
-   Se você especificar uma categoria de política que não existe, uma nova categoria de política será criada e a assinatura será designada para todos os bancos de dados quando você executar o procedimento armazenado. Se você desmarcar a assinatura designada para a nova categoria, a assinatura só se aplicará ao banco de dados que você especificou como *target_object*. Para obter mais informações sobre como alterar uma configuração de assinatura designada, veja [sp_syspolicy_update_policy_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-subscription-transact-sql).  
  
###  <a name="Security"></a> Segurança  
  
####  <a name="Permissions"></a> Permissões  
 Este procedimento armazenado é executado no contexto de seu proprietário atual.  
  
##  <a name="SSMSProcedure"></a> Usando o SQL Server Management Studio  
  
#### <a name="to-apply-category-policies-to-a-sql-server-instance"></a>Para aplicar políticas de categoria a uma instância do SQL Server  
  
1.  No **Pesquisador de Objetos**, clique no sinal de adição para expandir o servidor no qual você aplicará políticas de categoria.  
  
2.  Clique no sinal de adição para expandir a pasta **Gerenciamento** .  
  
3.  Clique com o botão direito do mouse em **Gerenciamento de Política** e selecione **Gerenciar Categorias**.  
  
     As seguintes informações estão disponíveis na caixa de diálogo **Gerenciar Categorias de Política** :  
  
     **Nome**  
     O nome da categoria de política.  
  
     **Autorizar Assinaturas de Banco de Dados**  
     Obriga que todos os bancos de dados na instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] imponham políticas na categoria de política.  
  
4.  Marque ou desmarque uma ou todas as caixas de seleção em **Autorizar Assinaturas de Banco de Dados** para aplicar essa categoria de política à instância do SQL Server.  
  
5.  Quando terminar, clique em **OK**.  
  
##  <a name="TsqlProcedure"></a> Usando o Transact-SQL  
  
#### <a name="to-apply-category-policies-to-a-sql-server-instance"></a>Para aplicar políticas de categoria a uma instância do SQL Server  
  
1.  No **Pesquisador de Objetos**, conecte-se a uma instância do [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Na barra Padrão, clique em **Nova Consulta**.  
  
3.  Copie e cole o exemplo a seguir na janela de consulta e clique em **Executar**.  
  
    ```  
    USE msdb;  
    GO  
    -- configures the specified database to subscribe to a policy category that is named 'Table Naming Policies'.  
    EXEC dbo.sp_syspolicy_add_policy_category_subscription @target_type = N'DATABASE'  
    , @target_object = N'AdventureWorks2012'  
    , @policy_category = N'Table Naming Policies';  
    GO  
    ```  
  
 Para obter mais informações, veja [sp_syspolicy_add_policy_category_subscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-add-policy-category-subscription-transact-sql).  
  
  