---
title: Dados do FILESTREAM
description: Descreve como trabalhar com dados de valor grande armazenados no SQL Server 2008 com o atributo FILESTREAM.
ms.date: 08/15/2019
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 83e793fac40a8e41850f2a45e138dd125130c13e
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452212"
---
# <a name="filestream-data"></a>Dados do FILESTREAM

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Download ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

O atributo de armazenamento FILESTREAM é para dados binários (BLOB) armazenados em uma coluna varbinary (max). Antes do FILESTREAM, o armazenamento de dados binários exigia tratamento especial. Dados não estruturados, como documentos de texto, imagens e vídeos, geralmente são armazenados fora do banco de dados, o que dificulta o gerenciamento.

> [!NOTE]
> Você deve instalar o .NET Framework 3,5 SP1 (ou posterior) ou o .NET Core para trabalhar com dados FILESTREAM usando o SqlClient.

A especificação do atributo FILESTREAM em uma coluna varbinary(max) faz com que o SQL Server armazene os dados no sistema de arquivos NTFS local em vez de no arquivo de banco de dados. Embora eles sejam armazenados separadamente, você pode usar as mesmas instruções Transact-SQL, que são compatíveis para trabalhar usando dados varbinary(max) que estão armazenados no banco de dados.

## <a name="sqlclient-support-for-filestream"></a>Suporte a SqlClient para FILESTREAM

O provedor de dados Microsoft SqlClient para SQL Server, <xref:Microsoft.Data.SqlClient>, dá suporte à leitura e à gravação em dados FILESTREAM usando a classe <xref:Microsoft.Data.SqlTypes.SqlFileStream> definida no namespace <xref:System.Data.SqlTypes>. o `SqlFileStream` herda da classe <xref:System.IO.Stream>, que fornece métodos para leitura e gravação em fluxos de dados. A leitura de um fluxo transfere dados do fluxo para uma estrutura de dados, como uma matriz de bytes. A gravação transfere os dados da estrutura de dados para um fluxo.

### <a name="creating-the-sql-server-table"></a>Criando a tabela de SQL Server

As instruções Transact-SQL a seguir criam uma tabela denominada employees e insere uma linha de dados. Depois de habilitar o armazenamento de FILESTREAM, você pode usar essa tabela em conjunto com os exemplos de código a seguir. Os links para os recursos nos Manuais Online do SQL Server estão localizados no final deste tópico.

```sql
CREATE TABLE employees
(
  EmployeeId INT  NOT NULL  PRIMARY KEY,
  Photo VARBINARY(MAX) FILESTREAM  NULL,
  RowGuid UNIQUEIDENTIFIER  NOT NULL  ROWGUIDCOL
  UNIQUE DEFAULT NEWID()
)
GO
Insert into employees
Values(1, 0x00, default)
GO
```

### <a name="example-reading-overwriting-and-inserting-filestream-data"></a>Exemplo: lendo, substituindo e inserindo dados FILESTREAM

O exemplo a seguir demonstra como ler dados de um FILESTREAM. O código obtém o caminho lógico para o arquivo, definindo o `FileAccess` como `Read` e o `FileOptions` como `SequentialScan`. Em seguida, o código lê os bytes do-SqlFileStream para o buffer. Em seguida, os bytes são gravados na janela do console.

O exemplo também demonstra como gravar dados em um FILESTREAM no qual todos os dados existentes são substituídos. O código obtém o caminho lógico para o arquivo e cria o `SqlFileStream`, definindo o `FileAccess` como `Write` e o `FileOptions` como `SequentialScan`. Um único byte é gravado no `SqlFileStream`, substituindo todos os dados no arquivo.

O exemplo também demonstra como gravar dados em um FILESTREAM usando o método Seek para acrescentar dados ao final do arquivo. O código obtém o caminho lógico para o arquivo e cria o `SqlFileStream`, definindo o `FileAccess` como `ReadWrite` e o `FileOptions` como `SequentialScan`. O código usa o método Seek para buscar até o final do arquivo, acrescentando um único byte ao arquivo existente.

```csharp
using System;
using Microsoft.Data.SqlClient;
using System.Data.SqlTypes;
using System.Data;
using System.IO;

namespace FileStreamTest
{
    class Program
    {
        static void Main(string[] args)
        {
            SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder("server=(local);integrated security=true;database=myDB");
            ReadFileStream(builder);
            OverwriteFileStream(builder);
            InsertFileStream(builder);

            Console.WriteLine("Done");
        }

        private static void ReadFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for the file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        // Create the SqlFileStream
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Read, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Read the contents as bytes and write them to the console
                            for (long index = 0; index < fileStream.Length; index++)
                            {
                                Console.WriteLine(fileStream.ReadByte());
                            }
                        }
                    }
                }
                tran.Commit();
            }
        }

        private static void OverwriteFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();

                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        // Create the SqlFileStream
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Write a single byte to the file. This will
                            // replace any data in the file.
                            fileStream.WriteByte(0x01);
                        }
                    }
                }
                tran.Commit();
            }
        }

        private static void InsertFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();

                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.ReadWrite, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Seek to the end of the file
                            fileStream.Seek(0, SeekOrigin.End);

                            // Append a single byte
                            fileStream.WriteByte(0x01);
                        }
                    }
                }
                tran.Commit();
            }

        }
    }
}
```

Para obter outro exemplo, confira [Como armazenar e buscar dados binários em uma coluna de fluxo de arquivos](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).

## <a name="resources-in-sql-server-books-online"></a>Recursos no Manuais Online do SQL Server

A documentação completa do FILESTREAM está localizada nas seguintes seções dos Manuais Online do SQL Server.

|Tópico|Descrição|
|-----------|-----------------|
|[FILESTREAM (SQL Server)](../../../relational-databases/blob/filestream-sql-server.md)|Descreve quando usar o armazenamento FILESTREAM e como ele integra o SQL Server Mecanismo de Banco de Dados com um sistema de arquivos NTFS.|
|[Criar aplicativos clientes para dados FILESTREAM](../../../relational-databases/blob/create-client-applications-for-filestream-data.md)|Descreve as funções de API do Windows para trabalhar com dados FILESTREAM.|
|[FILESTREAM e outros recursos do SQL Server](../../../relational-databases/blob/filestream-compatibility-with-other-sql-server-features.md)|Fornece considerações, diretrizes e limitações para usar dados FILESTREAM com outros recursos do SQL Server.|

## <a name="next-steps"></a>Próximas etapas
- [Tipos de dados do SQL Server e do ADO.NET](sql-server-data-types.md)
- [Dados binários e de valor grande do SQL Server](sql-server-binary-large-value-data.md)
