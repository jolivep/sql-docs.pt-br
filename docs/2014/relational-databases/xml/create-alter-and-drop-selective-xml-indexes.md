---
title: Criar, alterar e remover índices XML seletivos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: c398f396-f630-4a2d-a264-f243c5346de1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a95fa1c010197d0107c757198d9db7eaf8d3c42e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62637594"
---
# <a name="create-alter-and-drop-selective-xml-indexes"></a>Criar, alterar e remover índices XML seletivos
  Descreve como criar um novo índice XML seletivo ou alterar ou remover um índice XML seletivo existente.  
  
 Para obter mais informações sobre índices XML seletivos, veja [Índices XML Seletivos &#40;SXI&#41;](selective-xml-indexes-sxi.md).  
  
##  <a name="create"></a> Criando um índice XML seletivo  
  
### <a name="how-to-create-a-selective-xml-index"></a>Como criar um índice XML seletivo  
 **Criar um índice XML seletivo usando Transact-SQL**  
 Crie um índice XML seletivo chamando a instrução CREATE SELECTIVE XML INDEX. Para obter mais informações, veja [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).  
  
 **Exemplo**  
  
 O exemplo a seguir mostra a sintaxe para criar um índice XML seletivo. Ele também mostra variações da sintaxe para descrever os caminhos a serem indexados, com dicas de otimização opcionais.  
  
```sql  
CREATE SELECTIVE XML INDEX sxi_index  
ON Tbl(xmlcol)  
  
FOR(  
    pathab   = '/a/b' as XQUERY 'node()'  
    pathabc  = '/a/b/c' as XQUERY 'xs:double',   
    pathdtext = '/a/b/d/text()' as XQUERY 'xs:string' MAXLENGTH(200) SINGLETON  
    pathabe = '/a/b/e' as SQL NVARCHAR(100)  
)  
```  
  
  
  
##  <a name="alter"></a> Alterando um índice XML seletivo  
  
### <a name="how-to-alter-a-selective-xml-index"></a>Como alterar um índice XML seletivo  
 **Alterar um índice XML seletivo usando Transact-SQL**  
 Altere um índice XML seletivo existente chamando a instrução ALTER INDEX. Para obter mais informações, veja [ALTER INDEX &#40;Índices XML Seletivos&#41;](../indexes/indexes.md).  
  
 **Exemplo**  
  
 O exemplo a seguir mostra uma instrução ALTER INDEX. Essa instrução adiciona o caminho `'/a/b/m'` à parte XQuery do índice e exclui o caminho `'/a/b/e'` da parte SQL do índice criado no exemplo no tópico [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql). O caminho a ser excluído é identificado pelo nome atribuído a ele quando foi criado.  
  
```sql  
ALTER INDEX sxi_index  
ON Tbl  
FOR   
(  
    ADD pathm = '/a/b/m' as XQUERY 'node()' ,  
    REMOVE pathabe  
)  
```  
  
  
  
##  <a name="drop"></a> Removendo um índice XML seletivo  
  
### <a name="how-to-drop-a-selective-xml-index"></a>Como remover um índice XML seletivo  
 **Remover um índice XML seletivo usando Transact-SQL**  
 Remova um índice XML seletivo chamando a instrução DROP INDEX. Para obter mais informações, veja [DROP INDEX &#40;Índices XML Seletivos&#41;](/sql/t-sql/statements/drop-index-selective-xml-indexes).  
  
 **Exemplo**  
  
 O exemplo a seguir mostra uma instrução DROP INDEX.  
  
```sql  
DROP INDEX sxi_index ON tbl  
```  
  
 
  
  
