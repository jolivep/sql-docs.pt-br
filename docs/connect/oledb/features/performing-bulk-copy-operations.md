---
title: Executando operações de cópia em massa | Microsoft Docs
description: Executando operações de cópia em massa usando OLE DB driver para SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- bulk copy [OLE DB Driver for SQL Server]
- data access [OLE DB Driver for SQL Server], bulk copy operations
- OLE DB Driver for SQL Server, bulk copy operations
- MSOLEDBSQL, bulk copy operations
author: pmasl
ms.author: pelopes
ms.openlocfilehash: c6b1d33f4a0a768d33ebe9613c0c0cb97c5e77c3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67988985"
---
# <a name="performing-bulk-copy-operations"></a>Executando operações de cópia em massa
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  O recurso de cópia em massa do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] suporta a transferência de grandes quantidades de dados de ou para uma tabela ou exibição do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Os dados também podem ser transferidos com a especificação de uma instrução SELECT. É possível mover os dados entre o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e um arquivo de dados do sistema operacional, como um arquivo ASCII. O arquivo de dados pode ter diferentes formatos; o formato é definido para que a cópia em massa seja feita em um arquivo de formato. Como alternativa, os dados podem ser carregados para variáveis de programa e podem ser transferidos para o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] usando funções e métodos de cópia em massa.  
  
 Para obter um aplicativo de exemplo que demonstra esse recurso, consulte [copiar dados em &#40;massa&#41;usando o OLE DB IRowsetFastLoad](../../oledb/ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md).  
  
 Normalmente, um aplicativo usa o recurso de cópia em massa de uma destas maneiras:  
  
-   Faz cópia em massa a partir de uma tabela, exibição ou conjunto de resultados de uma instrução Transact-SQL para um arquivo de dados onde os dados são armazenados no mesmo formato que a tabela ou exibição.  
  
     Esse arquivo é chamado de arquivo de dados de modo nativo.  
  
-   Faz cópia em massa a partir de uma tabela, exibição ou conjunto de resultados de uma instrução Transact-SQL para um arquivo de dados onde os dados são armazenados em um formato diferente do formato da tabela ou exibição.  
  
     Nesse caso, um arquivo de formato separado é criado para definir as características (tipo de dados, posição, comprimento, terminador, e assim por diante) de cada coluna à medida que ela é armazenada no arquivo de dados. Se todas as colunas forem convertidas em um formato de caractere, o arquivo resultante será chamado de arquivo de dados do modo de caractere.  
  
-   Faz cópia em massa a partir de um arquivo de dados para uma tabela ou exibição.  
  
     Se necessário, um arquivo de formato é usado para determinar o layout do arquivo de dados.  
  
-   Faz o carregamento de dados para variáveis de programa e importa os dados para uma tabela ou exibição usando as funções de cópia em massa para executar a cópia em massa em uma linha de cada vez.  
  
 Os arquivos de dados usados pelas funções de cópia em massa não precisam ser criados por outro programa de cópia em massa. Qualquer outro sistema pode gerar um arquivo de dados e um arquivo de formato para executar a cópia em massa de definições; esses arquivos podem ser usados com um programa de cópia em massa do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] para importar dados para o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Por exemplo, você poderia exportar dados de uma planilha em um arquivo delimitado por tabulação, criar um arquivo de formato descrevendo o arquivo delimitado por tabulação e usar um programa de cópia em massa para importar rapidamente os dados para o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Os arquivos de dados gerados pela cópia em massa também podem ser importados para outros aplicativos. Por exemplo, você poderia usar as funções de cópia em massa para exportar dados de uma tabela ou exibição para um arquivo delimitado por tabulação que poderia, por sua vez, ser carregado para a planilha.  
  
 Os aplicativos de codificação para programadores que usam funções de cópia em massa deveriam seguir as regras gerais para garantir o bom desempenho dessas funções. Para obter mais informações sobre o suporte para operações de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]cópia em massa no, consulte [importação e &#40;exportação&#41;em massa de SQL Server de dados](../../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
## <a name="limitations-and-restrictions"></a>Limitações e Restrições  
 Um UDT (tipo definido pelo usuário) CLR deve ser associado como dados binários. Mesmo se um arquivo de formato especificar SQLCHAR como o tipo de dados para uma coluna UDT de destino, o utilitário BCP interpretará os dados como binários.  
  
 Não use SET FMTONLY OFF com operações de cópia em massa. SET FMTONLY OFF pode fazer sua operação de cópia em massa falhar ou gerar resultados inesperados.  
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server 
 O driver OLE DB para SQL Server implementa dois métodos para executar operações de cópia em massa [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] com um banco de dados. O primeiro método envolve o uso da interface [IRowsetFastLoad](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md) para operações de cópia em massa baseadas em memória; o segundo envolve o uso da interface [IBCPSession](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md) para operações de cópia em massa baseadas em arquivo.  
  
### <a name="using-memory-based-bulk-copy-operations"></a>Usando operações de cópia em massa baseadas em memória  
 O OLE DB Driver for SQL Server implementa a interface **IRowsetFastLoad** para expor o suporte a operações de cópia em massa baseadas em memória do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. A interface **IRowsetFastLoad** implementa os métodos [IRowsetFastLoad::Commit](../../oledb/ole-db-interfaces/irowsetfastload-commit-ole-db.md) e [IRowsetFastLoad::InsertRow](../../oledb/ole-db-interfaces/irowsetfastload-insertrow-ole-db.md).  
  
#### <a name="enabling-a-session-for-irowsetfastload"></a>Habilitando uma sessão para IRowsetFastLoad  
 O consumidor notifica o driver de OLE DB para SQL Server de sua necessidade de cópia em massa, definindo o driver de OLE DB para a propriedade de fonte de dados específica SQL Server SSPROP_ENABLEFASTLOAD como VARIANT_TRUE. Com a propriedade definida na fonte de dados, o consumidor cria um driver de OLE DB para SQL Server sessão. A nova sessão permite que o consumidor acesse a interface **IRowsetFastLoad**.  
  
> [!NOTE]  
>  Se a interface **IDataInitialize** for usada para inicializar a fonte de dados, será necessário definir a propriedade SSPROP_IRowsetFastLoad no parâmetro *rgPropertySets* do método **IOpenRowset::OpenRowset**; caso contrário, a chamada ao método **OpenRowset** retornará E_NOINTERFACE.  
  
 Habilitar uma sessão para cópia em massa restringe o driver de OLE DB para SQL Server suporte para interfaces na sessão. Uma sessão habilitada para cópia em massa expõe apenas as seguintes interfaces:  
  
-   **IDBSchemaRowset**  
  
-   **IGetDataSource**  
  
-   **IOpenRowset**  
  
-   **ISupportErrorInfo**  
  
-   **ITransactionJoin**  
  
 Para desabilitar a criação de conjuntos de linhas habilitados para cópia em massa e fazer com que a sessão do OLE DB Driver for SQL Server seja revertida para o processamento padrão, redefina SSPROP_ENABLEFASTLOAD como VARIANT_FALSE.  
  
#### <a name="irowsetfastload-rowsets"></a>Conjuntos de linhas IRowsetFastLoad  
 Os conjuntos de linhas de cópia em massa do OLE DB Driver for SQL Server são somente gravação, mas eles expõem interfaces que permitem que o consumidor determine a estrutura de uma tabela do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. As interfaces a seguir são expostas em um driver de OLE DB habilitado para cópia em massa para SQL Server conjunto de linhas:  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
-   **IColumnsRowset**  
  
-   **IConvertType**  
  
-   **IRowsetFastLoad**  
  
-   **IRowsetInfo**  
  
-   **ISupportErrorInfo**  
  
 As propriedades específicas do provedor SSPROP_FASTLOADOPTIONS, SSPROP_FASTLOADKEEPNULLS e SSPROP_FASTLOADKEEPIDENTITY controlam os comportamentos de um conjunto de linhas de cópia em massa do OLE DB Driver for SQL Server. As propriedades são especificadas no membro *rgProperties* de um membro de parâmetro **IOpenRowset** de *rgPropertySets*.  
  
|ID da propriedade|Descrição|  
|-----------------|-----------------|  
|SSPROP_FASTLOADKEEPIDENTITY|Coluna: Não<br /><br /> Leitura/gravação: leitura/gravação<br /><br /> Tipo: VT_BOOL<br /><br /> Padrão: VARIANT_FALSE<br /><br /> Descrição: Mantém valores de identidade fornecidos pelo consumidor.<br /><br /> VARIANT_FALSE: Valores para uma coluna de identidade na tabela [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] são gerados pelo [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Qualquer valor associado à coluna é ignorado pelo driver de OLE DB para SQL Server.<br /><br /> VARIANT_TRUE: O consumidor associa um acessador fornecendo um valor para uma coluna de identidade [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. A propriedade de identidade não está disponível em colunas que aceitam valores NULL e, portanto, o consumidor fornece um valor exclusivo em cada chamada a **IRowsetFastLoad::Insert**.|  
|SSPROP_FASTLOADKEEPNULLS|Coluna: Não<br /><br /> Leitura/gravação: leitura/gravação<br /><br /> Tipo: VT_BOOL<br /><br /> Padrão: VARIANT_FALSE<br /><br /> Descrição: Mantém valores NULL para colunas com uma restrição DEFAULT. Só afeta colunas [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que aceitam valores NULL e que têm uma restrição DEFAULT aplicada.<br /><br /> VARIANT_FALSE: o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] insere o valor padrão para a coluna quando o consumidor do OLE DB Driver for SQL Server insere uma linha que contém valores NULL para a coluna.<br /><br /> VARIANT_TRUE: o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] insere NULL para o valor da coluna quando o consumidor do OLE DB Driver for SQL Server insere uma linha que contém valores NULL para a coluna.|  
|SSPROP_FASTLOADOPTIONS|Coluna: Não<br /><br /> Leitura/gravação: leitura/gravação<br /><br /> Tipo: VT_BSTR<br /><br /> Padrão: nenhum<br /><br /> Descrição: essa propriedade é a mesma que a opção **-h** "*hint*[,...*n*]" do utilitário **bcp**. A cadeia de caracteres a seguir pode ser usada como opção na cópia em massa de dados para uma tabela.<br /><br /> **ORDER**(*column*[**ASC** &#124; **DESC**][,...*n*]): ordem de classificação dos dados no arquivo de dados. O desempenho da operação de cópia em massa é aprimorado se o arquivo de dados que está sendo carregado for classificado de acordo com o índice clusterizado na tabela.<br /><br /> **ROWS_PER_BATCH** = *bb*: número de linhas de dados por lote (como *bb*). O servidor otimiza o carregamento em massa de acordo com o valor *bb*. Por padrão, **ROWS_PER_BATCH** é desconhecido.<br /><br /> **KILOBYTES_PER_BATCH** = *cc*: o número de KB (quilobytes) de dados por lote (como cc). Por padrão, **KILOBYTES_PER_BATCH** é desconhecido.<br /><br /> **TABLOCK**: um bloqueio em nível de tabela é obtido enquanto durar a operação de cópia em massa. Essa opção melhora significativamente o desempenho porque manter um bloqueio apenas durante a operação de cópia em massa reduz a contenção de bloqueios na tabela. Uma tabela pode ser carregada simultaneamente por vários clientes se ela não tem índices e se **TABLOCK** está especificado. Por padrão, o comportamento de bloqueio é determinado pela opção de tabela **table lock on bulk load**.<br /><br /> **CHECK_CONSTRAINTS**: todas as restrições em *table_name* são verificadas durante a operação de cópia em massa. Por padrão, as restrições são ignoradas.<br /><br /> **FIRE_TRIGGER**: o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] usa o controle de versão de linha para gatilhos e armazena as versões de linha no repositório de versões em **tempdb**. Portanto, as otimizações de registro em massa estão disponíveis até mesmo quando os gatilhos estão habilitados. Antes de iniciar a importação em massa de um lote com um número grande de linhas com gatilhos habilitados, talvez você precise expandir o tamanho do **tempdb**.|  
  
### <a name="using-file-based-bulk-copy-operations"></a>Usando operações de cópia em massa baseadas em arquivo  
 O OLE DB Driver for SQL Server implementa a interface **IBCPSession** para expor o suporte para operações de cópia em massa baseadas em arquivo do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. A interface **IBCPSession** implementa os métodos [IBCPSession::BCPColFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md), [IBCPSession::BCPColumns](../../oledb/ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md), [IBCPSession::BCPControl](../../oledb/ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md), [IBCPSession::BCPDone](../../oledb/ole-db-interfaces/ibcpsession-bcpdone-ole-db.md), [IBCPSession::BCPExec](../../oledb/ole-db-interfaces/ibcpsession-bcpexec-ole-db.md), [IBCPSession::BCPInit](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md), [IBCPSession::BCPReadFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md) e [IBCPSession::BCPWriteFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md).  
  
  
## <a name="see-also"></a>Consulte Também  
 [Recursos do OLE DB Driver for SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)   
 [Propriedades de fonte de dados &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-properties-ole-db.md)   
 [Importação e exportação em massa de dados &#40;SQL Server&#41;](../../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)   
 [OLE DB &#40;IRowsetFastLoad&#41;](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md)   
 [OLE DB &#40;IBCPSession&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [Otimizando o desempenho da importação em massa](https://msdn.microsoft.com/library/ms190421\(SQL.105\).aspx)  

