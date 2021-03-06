---
title: Gerenciar uma base de dados de conhecimento
ms.date: 06/04/2013
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 27f306f4-d67c-47f5-b35c-4260cc5d36e3
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 1fda81ac39233435dbcd0546e452878cc6767b33
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "75247146"
---
# <a name="manage-a-knowledge-base"></a>Gerenciar uma base de dados de conhecimento

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Este tópico descreve como executar funções de gerenciamento em uma base de dados de conhecimento no [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Você pode excluir uma base de dados de conhecimento, desbloqueá-la, descartar seu trabalho nela, renomeá-la e exibir suas propriedades.  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="Prerequisites"></a> Pré-requisitos  
 Para gerenciar uma base de dados de conhecimento, ela já deve ter sido criada e publicada (caso outra pessoa a tenha criado) ou fechada (se você a criou).  
  
###  <a name="Security"></a> Segurança  
  
####  <a name="Permissions"></a> Permissões  
 Você deve ter a função dqs_kb_editor ou dqs_administrator no banco de dados DQS_MAIN para abrir uma base de dados de conhecimento.  
  
##  <a name="Manage"></a>Gerenciar uma base de dados de conhecimento  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Execute o aplicativo Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Na tela inicial do [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , clique em **Abrir base de dados de conhecimento**.  
  
3.  Clique com o botão direito do mouse em uma base de dados de conhecimento na tabela de bases de dados de conhecimento.  
  
4.  No menu de contexto, você pode fazer o seguinte:  
  
    1.  **Abrir**: clique para abrir a base de dados de conhecimento na atividade selecionada no painel **selecionar atividade** .  
  
    2.  **Desbloquear**: você pode desbloquear a base de dados de conhecimento se você for o usuário que estava trabalhando na base de dados de conhecimento em uma das etapas de gerenciamento de domínio, descoberta de conhecimento e atividade de política de correspondência e o fechou. Se você descarregar a base de dados de conhecimento, outra pessoa poderá abri-la e trabalhar nela. Este comando não estará disponível se a base de dados de conhecimento não estiver no estado de uma atividade. Para obter mais informações, consulte [Open a Knowledge Base](../data-quality-services/open-a-knowledge-base.md).  
  
    3.  **Descartar trabalho**: clique quando a base de dados de conhecimento estiver em um estado em que está sendo trabalhado, conforme mostrado com uma entrada no campo Estado na tabela. Este comando não estará disponível se a base de dados de conhecimento não estiver no estado de uma atividade e se a base de dados de conhecimento estiver bloqueada. Para obter mais informações, consulte [Open a Knowledge Base](../data-quality-services/open-a-knowledge-base.md).  
  
    4.  **Renomear**: clique para tornar o campo base de dados de conhecimento da tabela editável para a base de dados de conhecimento na qual você clicou com o botão direito do mouse. Altere o nome e clique nessa base de dados de conhecimento e em outra no campo p0ara aceitar a alteração do nome.  
  
    5.  **Excluir**: clique para remover a base de dados de conhecimento do banco [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]de dados DQS_MAIN em.  
  
    6.  **Propriedades**: clique para exibir as propriedades do banco de dados em uma exibição somente leitura.  
  
        1.  **Base de dados de conhecimento**: a base de dados de conhecimento na qual esse banco de dados se baseia. Isso é opcional.  
  
        2.  **Estado**: indica se a base de dados de conhecimento está **em funcionamento** e se está em uma atividade de gerenciamento de conhecimento específica, conforme determinado quando ela foi fechada pela última vez. O estado pode ser **Em Serviço**, no qual a base de dados de conhecimento é aberta em uma sessão de gerenciamento de conhecimento, mas não em uma atividade específica, ou **Em Serviço** mais uma atividade de gerenciamento de conhecimento, na qual a base de dados de conhecimento é aberta em uma sessão de gerenciamento de conhecimento, e em uma atividade específica.  
  
        3.  **Está bloqueado**: **true** se a base de dados de conhecimento foi bloqueada, **false** se não  
  
        4.  **Contém conteúdo não publicado**: verdadeiro se a base de dados de conhecimento contiver conteúdo que não foi salvo pela publicação, falso se não  
  
        5.  **Bloqueado por**: o nome do usuário que fechou a base de dados de conhecimento, bloqueando-a  
  
        6.  **Data de bloqueio**: data quando bloqueada  
  
        7.  **Criado por**: o nome do usuário que criou a base de dados de conhecimento, com a rede à qual ele pertence  
  
        8.  **Data de criação**: data quando criada  
  
##  <a name="FollowUp"></a>Acompanhamento: depois de gerenciar uma base de dados de conhecimento  
 Depois que você gerenciar uma base de dados de conhecimento, a próxima etapa dependerá da ação executada na base de dados de conhecimento:  
  
-   Se você abriu a base de dados de conhecimento, continuará na atividade que selecionou.  
  
-   Se você a desbloqueou, ela estará disponível para outra pessoa abrir e trabalhar nela, no estado indicado.  
  
-   Se você descartou o trabalho nela, a base de dados de conhecimento estará disponível em seu último estado publicado.  
  
-   Se você a renomeou, precisará abrir a base de dados de conhecimento renomeada para trabalhar nela.  
  
-   Se você a excluiu, precisará selecionar outra base de dados de conhecimento para trabalhar ou criar uma nova.  
  
  
