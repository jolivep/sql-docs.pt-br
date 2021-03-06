---
title: Mapeando tipos de dados de origem e de destino (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- customizing data type mappings
- data types, mapping
- mapping, data types
- source data types
- target data types
ms.assetid: b362a075-16e7-423f-b63f-e1e9f02844a9
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: e0600778b938a7736ab1112f31bbe4828605cdaf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67907166"
---
# <a name="mapping-source-and-target-data-types-accesstosql"></a>Mapeando tipos de dados de origem e de destino (AccessToSQL)
Tipos de banco de dados [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] do Access são diferentes dos tipos de banco de dados Ao converter objetos de banco de dados [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] do Access em objetos, você deve especificar como mapear tipos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dado do Access para o. Você pode aceitar os mapeamentos de tipo de dados padrão ou pode personalizar os mapeamentos, conforme mostrado nos procedimentos a seguir.  
  
## <a name="default-mappings"></a>Mapeamentos padrão  
O SSMA tem um conjunto padrão de mapeamentos de tipo de dados. Para obter a lista de mapeamentos padrão, consulte [configurações do projeto (mapeamento de tipo)](https://msdn.microsoft.com/b87b9683-abed-4677-8c50-18bdba704655).  
  
## <a name="customizing-data-type-mappings"></a>Personalizando mapeamentos de tipo de dados  
Usando a caixa de diálogo **configurações do projeto** , você pode personalizar a forma como os tipos são mapeados para todos os bancos de dados e objetos de um projeto. Os mapeamentos de tipo para um projeto aplicam-se a todos os bancos de dados e objetos de banco que não têm mapeamentos de tipo personalizados.  
  
Você também pode personalizar o mapeamento de tipo de dados no nível de tabela ou banco de dado.  
  
O procedimento a seguir mostra como mapear os tipos de dados no nível de objeto do projeto, do banco de dado ou do.  
  
**Para mapear tipos de dados**  
  
1.  Para personalizar o mapeamento de tipo de dados para o projeto inteiro, abra a caixa de diálogo **configurações do projeto** :  
  
    1.  No menu **ferramentas** , selecione **configurações do projeto**.  
  
    2.  No painel esquerdo, selecione **mapeamento de tipo**.  
  
        O gráfico de mapeamento de tipo e os botões aparecem no painel direito.  
  
    Ou, para personalizar o mapeamento de tipo de dados no nível de tabela ou banco de dado, selecione o banco de dados ou a tabela no painel Gerenciador de metadados do Access:  
  
    1.  No painel Access Metadata Explorer, expanda **Access-metabase**e, em seguida, expanda **bancos de dados**.  
  
    2.  Selecione o banco de dados ou tabela para o qual você deseja personalizar o mapeamento de tipo de dado.  
  
    3.  No painel direito, clique em **mapeamento de tipo**.  
  
2.  Para adicionar um novo mapeamento, faça o seguinte:  
  
    1.  No painel mapeamento de tipo, clique em **Adicionar**.  
  
    2.  Na caixa de diálogo **novo mapeamento de tipo** , em **tipo de origem**, selecione o tipo de dados do Access a ser mapeado.  
  
    3.  Se o tipo exigir um comprimento, especifique os comprimentos mínimo e máximo de dados para o mapeamento, marcando as caixas **de seleção de** e **para** e, em seguida, inserindo os valores.  
  
        Isso permite que você personalize o mapeamento de dados para valores menores e maiores do mesmo tipo de dados.  
  
    4.  Em **tipo de destino**, selecione o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo de dados de destino.  
  
        Alguns tipos exigem um comprimento de tipo de dados de destino. Se for necessário, insira o novo comprimento dos dados na caixa **substituir por** e clique em **OK**.  
  
3.  Para editar um mapeamento de tipo de dados, faça o seguinte:  
  
    1.  No painel mapeamento de tipo, clique em **Editar**.  
  
    2.  Na caixa de diálogo **lista de mapeamento de tipos** , em tipo de **origem**, selecione o tipo de dados do Access a ser mapeado.  
  
    3.  Se o tipo exigir um comprimento, especifique os comprimentos mínimo e máximo de dados para o mapeamento, marcando as caixas **de seleção de** e **para** e, em seguida, inserindo os valores.  
  
        Isso permite que você personalize o mapeamento de dados para valores menores e maiores do mesmo tipo de dados.  
  
    4.  Em **tipo de destino**, selecione o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo de dados de destino.  
  
        Alguns tipos exigem um comprimento de tipo de dados de destino. Se for necessário, insira o novo comprimento dos dados na caixa **substituir por** e clique em **OK**.  
  
4.  Para remover um mapeamento de tipo de dados, faça o seguinte:  
  
    1.  No painel mapeamento de tipo, selecione a linha na lista mapeamento de tipo que contém o mapeamento de tipo de dados que você deseja remover.  
  
    2.  Clique em **Remover**.  
  
## <a name="next-steps"></a>Próximas etapas  
A próxima etapa no processo de migração é [converter objetos de banco de dados do Access em objetos SQL Server](converting-access-database-objects-accesstosql.md)  
  
## <a name="see-also"></a>Consulte Também  
[Migrando bancos de dados do Access para SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
