---
title: Exibir a definição da tabela | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- showing table properties
- displaying table properties
- tables [SQL Server], properties
- viewing table properties
ms.assetid: 1865fb7c-f480-4100-9007-df5364cd002a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 308281ed30b7f0a56acbe397c0294932afeae121
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68211758"
---
# <a name="view-the-table-definition"></a>Exibir a definição da tabela
  Você pode exibir as propriedades de uma tabela no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Neste tópico**  
  
-   **Antes de começar:**  
  
     [Segurança](#Security)  
  
-   **Para exibir as propriedades da tabela usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="Security"></a> Segurança  
  
####  <a name="Permissions"></a> Permissões  
 Você poderá ver as propriedades de uma tabela somente se for proprietário da tabela ou tiver permissões concedidas para essa tabela.  
  
##  <a name="SSMSProcedure"></a> Usando o SQL Server Management Studio  
  
#### <a name="to-show-table-properties-in-the-properties-window"></a>Para mostrar as propriedades da tabela na janela Propriedades  
  
1.  No Pesquisador de Objetos, selecione a tabela da qual deseja exibir as propriedades.  
  
2.  Clique com o botão direito do mouse na tabela e escolha **Propriedades** no menu de atalho. Para obter mais informações, consulte [Table Properties](table-properties-ssms.md).  
  
##  <a name="TsqlProcedure"></a> Usando o Transact-SQL  
  
#### <a name="to-show-table-properties"></a>Para exibir as propriedades da tabela  
  
1.  No **Pesquisador de Objetos**, conecte-se a uma instância do [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Na barra Padrão, clique em **Nova Consulta**.  
  
3.  Copie e cole o exemplo a seguir na janela de consulta e clique em **Executar**. O exemplo retorna todas as colunas da exibição de catálogo `sys.tables` do objeto especificado.  
  
    ```  
    SELECT * FROM sys.tables  
    WHERE object_id = 1973582069;  
  
    ```  
  
 Para obter mais informações, consulte [sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql).  
  
###  <a name="TsqlExample"></a>  
