---
title: Criar um projeto de qualidade de dados
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.dqproject.newdqproject.f1
helpviewer_keywords:
- create,data quality project
- data quality project,create
ms.assetid: 19c52d2b-d28e-4449-ab59-5fe0dc326cd9
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 99b869f153e6dacac799f8630283dbaf8d27660b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "75245493"
---
# <a name="create-a-data-quality-project"></a>Criar um projeto de qualidade de dados

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Este tópico descreve como criar um projeto de qualidade de dados usando o [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Um projeto de qualidade de dados é usado para executar a atividade de limpeza ou correspondência no [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="Prerequisites"></a> Pré-requisitos  
 Você deve ter uma base de dados de conhecimento relevante para usar no projeto de qualidade de dados para a atividade de limpeza ou correspondência.  
  
###  <a name="Security"></a> Segurança  
  
####  <a name="Permissions"></a> Permissões  
 Você deve ter a função dqs_kb_editor ou dqs_kb_operator no banco de dados DQS_MAIN para criar um projeto de qualidade de dados.  
  
##  <a name="Create"></a>Criar um projeto de qualidade de dados  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Execute o aplicativo Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Na tela inicial do [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , clique em **Novo projeto de qualidade de dados**.  
  
3.  Na tela **Novo Projeto de Qualidade de Dados** :  
  
    1.  Na caixa **Nome** , digite um nome para o novo projeto de qualidade de dados.  
  
    2.  (Opcional) Na caixa **Descrição** , digite uma descrição para o novo projeto de qualidade de dados.  
  
    3.  Na lista **Usar base de dados de conhecimento** , clique para selecionar uma base de dados de conhecimento a ser usada no projeto de qualidade de dados. A área **Detalhes da base de dados de conhecimento: <Knowledge_Base_Name>** do lado direito exibe os nomes de domínio disponíveis na base de dados de conhecimento selecionada.  
  
    4.  Na área **Selecionar Atividade** , clique em uma atividade que você deseja executar usando este projeto de qualidade de dados:  
  
        -   **Limpeza**: Selecione essa atividade para limpar os dados de origem.  
  
        -   **Correspondência**: Selecione esta atividade para executar a correspondência. Esta atividade só estará disponível se a base de dados de conhecimento selecionada para o projeto de qualidade de dados contiver uma política de correspondência.  
  
4.  Clique em **Criar** para criar um projeto de qualidade de dados.  
  
##  <a name="FollowUp"></a>Acompanhamento: depois de criar um projeto de qualidade de dados  
 Depois que você criar um projeto de qualidade de dados, verá um assistente que deverá ser usado para executar a atividade selecionada: limpeza ou correspondência. Para obter mais informações sobre a limpeza e correspondência de atividades, consulte [Limpeza de dados](../data-quality-services/data-cleansing.md) e [Correspondência de dados](../data-quality-services/data-matching.md).  
  
  
