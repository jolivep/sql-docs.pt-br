---
title: Método createrecordset (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DataControl::CreateRecordset
- RDS.DataControl::CreateRecordset
- CreateRecordset
- RDSServer.DataFactory::CreateRecordset
- DataFactory::CreateRecordset
helpviewer_keywords:
- CreateRecordset method [RDS]
ms.assetid: 6840b1e5-c04d-4d3e-9dcc-42128c83492f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3c65f7d415864b169b683e0c9ab858506d31783b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67964510"
---
# <a name="createrecordset-method-rds"></a>Método CreateRecordset (RDS)
Cria um [conjunto de registros](../../../ado/reference/ado-api/recordset-object-ado.md)vazio e desconectado.  
  
> [!IMPORTANT]
>  A partir do Windows 8 e do Windows Server 2012, os componentes do servidor RDS não são mais incluídos no sistema operacional Windows (consulte Windows 8 e [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) para obter mais detalhes). Os componentes do cliente RDS serão removidos em uma versão futura do Windows. Evite usar esse recurso em desenvolvimentos novos e planeje modificar os aplicativos que atualmente o utilizam. Os aplicativos que usam o RDS devem migrar para o [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
object.CreateRecordset(ColumnInfos)  
```  
  
#### <a name="parameters"></a>parâmetros  
 *Objeto*  
 Uma variável de objeto que representa um [RDSServer. datafactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) ou [RDS. Objeto DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) .  
  
 *ColumnsInfos*  
 Uma matriz **variante** de atributos que define cada coluna no **conjunto de registros** criado. Cada definição de coluna contém uma matriz de quatro atributos necessários e um atributo opcional.  
  
|Atributo|DESCRIÇÃO|  
|---------------|-----------------|  
|Nome|Nome do cabeçalho da coluna.|  
|Type|Inteiro do tipo de dados.|  
|Tamanho|O número inteiro da largura em caracteres, independentemente do tipo de dados.|  
|Nulidade|Valor booliano.|  
|Escala (opcional)|Esse atributo opcional define a escala para campos numéricos. Se esse valor não for especificado, os valores numéricos serão truncados para uma escala de três. A precisão não é afetada, mas o número de dígitos após o ponto decimal será truncado para três.|  
  
 O conjunto de matrizes de coluna é então agrupado em uma matriz, que define o **conjunto de registros**.  
  
## <a name="remarks"></a>Comentários  
 O objeto comercial do lado do servidor pode preencher o **conjunto de registros** resultante com dados de um provedor de dados não OLE DB, como um arquivo do sistema operacional que contém Cotações de ações.  
  
 A tabela a seguir lista os valores de [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) com suporte pelo método **createrecordset** . O número listado é o número de referência usado para definir campos.  
  
 Cada um dos tipos de dados é de comprimento fixo ou variável. Os tipos de comprimento fixo devem ser definidos com um tamanho de-1, porque o tamanho é predeterminado e uma definição de tamanho ainda é necessária. Os tipos de dados de comprimento variável permitem um tamanho de 1 a 32767.  
  
 Para alguns dos tipos de dados variáveis, o tipo pode ser forçado para o tipo indicado na coluna de substituição. Você não verá as substituições até que o **conjunto de registros** seja criado e preenchido. Em seguida, você pode verificar o tipo de dados real, se necessário.  
  
|Comprimento|Constante|Número|Substituição|  
|------------|--------------|------------|------------------|  
|Correção|**adTinyInt**|16||  
|Correção|**adSmallInt**|2||  
|Correção|**adInteger**|3||  
|Correção|**adBigInt**|20||  
|Correção|**adUnsignedTinyInt**|17||  
|Correção|**adUnsignedSmallInt**|18||  
|Correção|**adUnsignedInt**|19||  
|Correção|**adUnsignedBigInt**|21||  
|Correção|**adSingle**|4||  
|Correção|**adDouble**|5||  
|Correção|**adCurrency**|6||  
|Correção|**adDecimal**|14||  
|Correção|**adNumeric**|131||  
|Correção|**adBoolean**|11||  
|Correção|**adError**|10||  
|Correção|**adGuid**|72||  
|Correção|**adDate**|7||  
|Correção|**adDBDate**|133||  
|Correção|**adDBTime**|134||  
|Correção|**adDBTimestamp**|135|7|  
|Variável|**adBSTR**|8|130|  
|Variável|**adChar**|129|200|  
|Variável|**adVarChar**|200||  
|Variável|**adLongVarChar**|201|200|  
|Variável|**adWChar**|130||  
|Variável|**adVarWChar**|202|130|  
|Variável|**adLongVarWChar**|203|130|  
|Variável|**adBinary**|128||  
|Variável|**adVarBinary**|204||  
|Variável|**adLongVarBinary**|205|204|  
  
## <a name="applies-to"></a>Aplica-se A  
  
|||  
|-|-|  
|[Objeto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[Objeto DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|  
  
## <a name="see-also"></a>Consulte Também  
 [Exemplo do método createrecordset (VB)](../../../ado/reference/ado-api/createrecordset-method-example-vb.md)   
 [Exemplo do método createrecordset (VBScript)](../../../ado/reference/rds-api/createrecordset-method-example-vbscript.md)   
 [Método CreateObject (RDS)](../../../ado/reference/rds-api/createobject-method-rds.md)



