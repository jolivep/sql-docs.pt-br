---
title: Diretrizes e limitações do carregamento em massa de XML (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XML Bulk Load [SQLXML], about XML Bulk Load
- bulk load [SQLXML], about bulk load
ms.assetid: c5885d14-c7c1-47b3-a389-455e99a7ece1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 329fb8df41df5d97cfcc3750c2850d03278d3739
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66013440"
---
# <a name="guidelines-and-limitations-of-xml-bulk-load-sqlxml-40"></a>Diretrizes e limitações de Carregamento em Massa de XML (SQLXML 4.0)
  Ao usar o Carregamento em Massa de XML, você deve estar familiarizado com as diretrizes e limitações a seguir:  
  
-   Não há suporte a esquemas embutidos.  
  
     Se houver um esquema embutido no documento XML de origem, o Carregamento em Massa de XML ignorará esse esquema. Você especifica o esquema de mapeamento para o Carregamento em Massa de XML que é externo aos dados XML. Você não pode especificar o esquema de mapeamento em um nó usando o atributo **xmlns = "x:Schema"** .  
  
-   Um documento XML é verificado para que esteja bem formado, mas ele não é validado.  
  
     O carregamento em massa de XML verifica o documento XML para determinar se ele está bem formado, ou seja, para garantir que o XML esteja em conformidade com os requisitos de sintaxe da recomendação XML 1,0 do World Wide Web Consortium. Se o documento não estiver bem formado, o Carregamento em Massa de XML cancelará o processamento e retornará um erro. A única exceção é quando o documento é um fragmento (por exemplo, o documento não tem nenhum elemento raiz), caso em que o Carregamento em Massa de XML carregará o documento.  
  
     O Carregamento em Massa de XML não valida o documento com relação a qualquer esquema DTD ou de Dados XML definido ou referenciado no arquivo de dados XML. Além disso, o Carregamento em Massa de XML não valida o arquivo de dados XML com base no esquema de mapeamento fornecido.  
  
-   Quaisquer informações de prólogo XML são ignoradas.  
  
     O carregamento em massa de XML ignora todas as informações antes e \<depois do elemento de> raiz no documento XML. Por exemplo, o Carregamento em Massa de XML ignora qualquer declaração XML, definições de DTD internas, referências de DTD externas, comentários e assim por diante.  
  
-   Se você tiver um esquema de mapeamento que define um relacionamento de chave primária/chave estrangeira entre duas tabelas (como entre Customer e CustOrder), a tabela com a chave primária deverá ser descrita primeiro no esquema. A tabela com a coluna de chave estrangeira deve aparecer depois no esquema. O motivo disso é que a ordem na qual as tabelas são identificadas no esquema é a ordem usada para carregá-las no banco de dados. Por exemplo, o seguinte esquema XDR produzirá um erro quando ele for usado no carregamento em massa XML, pois o ** \<elemento Order>** é descrito antes do ** \<elemento Customer>** . A coluna CustomerID em CustOrder é uma coluna de chave estrangeira que se refere à coluna de chave primária CustomerID na tabela Cust.  
  
    ```  
    <?xml version="1.0" ?>  
    <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
            xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
            xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
        <ElementType name="Order" sql:relation="CustOrder" >  
          <AttributeType name="OrderID" />  
          <AttributeType name="CustomerID" />  
          <attribute type="OrderID" />  
          <attribute type="CustomerID" />  
        </ElementType>  
  
       <ElementType name="CustomerID" dt:type="int" />  
       <ElementType name="CompanyName" dt:type="string" />  
       <ElementType name="City" dt:type="string" />  
  
       <ElementType name="root" sql:is-constant="1">  
          <element type="Customers" />  
       </ElementType>  
       <ElementType name="Customers" sql:relation="Cust"   
                         sql:overflow-field="OverflowColumn"  >  
          <element type="CustomerID" sql:field="CustomerID" />  
          <element type="CompanyName" sql:field="CompanyName" />  
          <element type="City" sql:field="City" />  
          <element type="Order" >   
               <sql:relationship  
                   key-relation="Cust"  
                    key="CustomerID"  
                    foreign-key="CustomerID"  
                    foreign-relation="CustOrder" />  
          </element>  
       </ElementType>  
    </Schema>  
    ```  
  
-   Se o esquema não especificar colunas de estouro usando a anotação `sql:overflow-field`, o Carregamento em Massa de XML ignorará todos os dados presentes no documento XML porém não descritos no esquema de mapeamento.  
  
     O Carregamento em Massa de XML aplica o esquema de mapeamento que você especifica sempre que encontra marcas conhecidas no fluxo de dados XML. Ele ignora dados presentes no documento XML mas não descritos no esquema. Por exemplo, suponha que você tenha um esquema de mapeamento que descreve um elemento de ** \<>do cliente** . O arquivo de dados XML tem ** \<** uma marca raiz>de usuários (que não está descrita no esquema) que inclui todos os elementos de ** \<>do cliente** :  
  
    ```  
    <AllCustomers>  
      <Customer>...</Customer>  
      <Customer>...</Customer>  
       ...  
    </AllCustomers>  
    ```  
  
     Nesse caso, o carregamento em massa de XML ignora o elemento ** \<>de usuários** e começa o mapeamento no elemento>do ** \<cliente** . O Carregamento em Massa de XML ignora os elementos não descritos no esquema mas presentes no documento XML.  
  
     Considere outro arquivo de dados de origem XML ** \<** que contenha elementos de ordem>. Esses elementos não são descritos no esquema de mapeamento:  
  
    ```  
    <AllCustomers>  
      <Customer>...</Customer>  
        <Order> ... </Order>  
        <Order> ... </Order>  
         ...  
      <Customer>...</Customer>  
        <Order> ... </Order>  
        <Order> ... </Order>  
         ...  
      ...  
    </AllCustomers>  
    ```  
  
     O carregamento em massa de XML ** \<** ignora esses elementos de>de ordem. Mas se você usar a `sql:overflow-field`anotação no esquema para identificar uma coluna como uma coluna de estouro, a carga em massa de XML armazenará todos os dados não consumidos nesta coluna.  
  
-   As referências de entidade e seções CDATA são traduzidas para os respectivos equivalentes de cadeia de caracteres antes de serem armazenadas no banco de dados.  
  
     Neste exemplo, uma seção CDATA encapsula o valor do elemento ** \<City>** . O carregamento em massa de XML extrai o valor da cadeia de caracteres ("NY") antes de inserir o elemento de ** \<>de cidade** no banco de dados.  
  
    ```  
    <City><![CDATA[NY]]> </City>  
    ```  
  
     O Carregamento em Massa de XML não preserva as referências de entidade.  
  
-   Se o esquema de mapeamento especificar o valor padrão de um atributo e os dados de origem XML não contiverem esse atributo, o Carregamento em Massa de XML usará o valor padrão.  
  
     O seguinte esquema XDR de exemplo atribui um valor padrão ao atributo **HireDate** :  
  
    ```  
    <?xml version="1.0" ?>  
    <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
            xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
            xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
       <ElementType name="root" sql:is-constant="1">  
          <element type="Customers" />  
       </ElementType>  
  
       <ElementType name="Customers" sql:relation="Cust3" >  
          <AttributeType name="CustomerID" dt:type="int"  />  
          <AttributeType name="HireDate"  default="2000-01-01" />  
          <AttributeType name="Salary"   />  
  
          <attribute type="CustomerID" sql:field="CustomerID" />  
          <attribute type="HireDate"   sql:field="HireDate"  />  
          <attribute type="Salary"     sql:field="Salary"    />  
       </ElementType>  
    </Schema>  
    ```  
  
     Nesses dados XML, o atributo **HireDate** está ausente do segundo ** \<elemento>do cliente** . Quando o carregamento em massa de XML ** \<** insere o segundo elemento de clientes>no banco de dados, ele usa o valor padrão especificado no esquema.  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1" HireDate="1999-01-01" Salary="10000" />  
      <Customers CustomerID="2" Salary="10000" />  
    </ROOT>  
    ```  
  
-   Não há suporte à anotação `sql:url-encode`:  
  
     Você não pode especificar uma URL na entrada de dados XML e esperar que o Carregamento em Massa leia os dados desse local.  
  
     São criadas as tabelas identificadas no esquema de mapeamento (o banco de dados precisa existir). Se uma ou mais das tabelas já existir no banco de dados, a propriedade SGDropTables determinará se essas tabelas preexistentes devem ser descartadas e recriadas.  
  
-   Se você especificar a propriedade SchemaGen (por exemplo, SchemaGen = true), as tabelas identificadas no esquema de mapeamento serão criadas. Mas o SchemaGen não cria nenhuma restrição (como as restrições PRIMARY KEY/FOREIGN KEY) nessas tabelas com uma exceção: se os nós XML que constituem a chave primária em uma relação forem definidos como tendo um tipo XML de ID (ou seja, `type="xsd:ID"` para xsd) e a propriedade SGUseID estiver definida como true para SchemaGen, não somente as chaves primárias serão criadas a partir dos nós de tipo de ID, mas as relações de chave primária/chave estrangeira serão criadas a partir do mapeamento de relações de esquema.  
  
-   SchemaGen não usa facetas e extensões de esquema XSD para gerar o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] esquema relacional.  
  
-   Se você especificar a propriedade SchemaGen (por exemplo, SchemaGen = true) no carregamento em massa, somente as tabelas (e não as exibições do nome compartilhado) especificadas serão atualizadas.  
  
-   O SchemaGen fornece apenas a funcionalidade básica para gerar o esquema relacional do XSD anotado. O usuário deve modificar as tabelas geradas manualmente, se necessário.  
  
-   Quando houver mais de uma relação entre as tabelas, SchemaGen tentará criar uma única relação que inclui todas as chaves envolvidas entre as duas tabelas. Essa limitação pode causar um erro [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
-   Quando você está carregando em massa os dados XML em um banco de dados, é necessário haver pelo menos um atributo ou elemento filho no esquema de mapeamento que esteja mapeado para uma coluna de banco de dados.  
  
-   Se você estiver inserindo valores de data usando o XML Bulk Load, eles deverão ser especificados no formato (-)CCYY-MM-DD((+-)TZ). Esse é o formato de XSD padrão para a data.  
  
-   Alguns sinalizadores de propriedade não são compatíveis com outros. Por exemplo, o carregamento em massa não aceita `Ignoreduplicatekeys=true` junto com `Keepidentity=false`. Quando `Keepidentity=false`, o carregamento em massa espera o servidor gerar os valores de chave. As tabelas devem ter uma restrição `IDENTITY` na chave. O servidor não gerará chaves duplicadas, o que significa que não há necessidade de `Ignoreduplicatekeys` ser definido como `true`. 
  `Ignoreduplicatekeys` deve ser definido como `true` somente ao enviar valores de chave primária dos dados de entrada para uma tabela que tem linhas e se houver um possível conflito dos valores de chave primária.  
  
  
