---
title: STEquals (tipo de dados geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STEquals_TSQL
- STEquals (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STEquals method
ms.assetid: 0766ff37-0b9e-49bf-83c0-019f4354fe44
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: caa274b1571a9c0506acbe3f6d5d5d004588fede
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68042269"
---
# <a name="stequals-geography-data-type"></a>STEquals (tipo de dados geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retornará 1 se uma instância de **geography** representar o mesmo conjunto de pontos que outra instância de **geography**. Retornará 0 se isso não ocorrer.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
.STEquals ( other_geography )  
```  
  
## <a name="arguments"></a>Argumentos  
 *other_geography*  
 É outra instância de **geography** a ser comparada com a instância na qual `STEquals()` é invocado.  
  
## <a name="return-types"></a>Tipos de retorno  
 Tipo de retorno do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
 Tipo de retorno do CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Comentários  
 Esse método sempre retornará nulo se as SRIDs (IDs de referência espacial) das instâncias de **geography** não forem correspondentes.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir cria duas instâncias de `geography` com `STGeomFromText()` que são iguais, mas não superficialmente iguais, e usa `STEquals()` para testar a igualdade entre elas. As instâncias são iguais porque `LINESTRING` e `POINT` estão contidos no `POLYGON`.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('GEOMETRYCOLLECTION(POLYGON((-122.368 47.658, -122.338 47.649, -122.338 47.658, -122.368 47.658, -122.368 47.658)), LINESTRING(-122.360 47.656, -122.343 47.656), POINT (-122.35 47.656))', 4326);  
SET @h = geography::STGeomFromText('POLYGON((-122.368 47.658, -122.338 47.649, -122.338 47.658, -122.368 47.658, -122.368 47.658))', 4326);  
SELECT @g.STEquals(@h);  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Métodos OGC em instâncias geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
