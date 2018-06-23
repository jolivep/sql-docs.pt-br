---
title: 'Lição 6: Executar o aplicativo de esquema RDL (VB-C#) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2cd2386-2df8-4b69-ab81-9ad1a31f6d27
caps.latest.revision: 15
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 95ef194a66d6c5480f8a83cbd0b78547e79804e6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36120479"
---
# <a name="lesson-6-run-the-rdl-schema-application-vb-c"></a>Lição 6: Executar o aplicativo de esquema RDL (VB-C#)
  O [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oferece dois métodos para criar e executar um aplicativo de console com base no ambiente de desenvolvimento integrado (IDE):  
  
-   Iniciar (com Depuração)  
  
-   Iniciar sem Depuração  
  
### <a name="to-build-and-run-the-samplerdlschema-application"></a>Criar e executar o aplicativo SampleRDLSchema  
  
1.  Do **depurar** menu, clique em **Start Without Debugging**. Isso assegura que a janela de console permaneça aberta após o fim da execução do programa.  
  
     O aplicativo imprime a seguinte saída para o console:  
  
    ```  
    Loading Report Definition  
    Updating Report Definition  
    - Old Description: <Old Report Description>  
    - New Description: <New Report Description>  
    Publishing Report Definition  
    ```  
  
2.  Pressione qualquer tecla para fechar o console.  
  
    > [!NOTE]  
    >  Qualquer erro que ocorra será gravado no console.  
  
3.  Quando a execução do aplicativo de exemplo terminar, uma cópia atualizada do relatório será salva no servidor de relatório.  
  
## <a name="see-also"></a>Consulte também  
 [Atualizando relatórios por meio de Classes geradas a partir do esquema RDL &#40;Tutorial do SSRS&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [Linguagem RDL &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  