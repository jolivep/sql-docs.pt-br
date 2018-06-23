---
title: Visão geral do Master Data Services | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Master Data Services, overview
- Master Data Services
ms.assetid: 8a4c28b1-6061-4850-80b6-132438b8c156
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 6ba63353b1a5fba1e5853f641cc6217002f0c805
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36121099"
---
# <a name="master-data-services-overview"></a>Visão geral do Master Data Services
  No [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], o modelo é o contêiner de nível mais alto na estrutura de dados mestres. Você cria um modelo para gerenciar grupos de dados semelhantes, por exemplo, para gerenciar dados de produtos online. Um modelo contém uma ou mais entidades, que por sua vez contêm membros que são os registros de dados.  
  
|||  
|-|-|  
|![Máquina Virtual do Azure](../../2014/master-data-services/media/azure-virtual-machine.png "Máquina Virtual do Azure")|Você deseja experimentar o SQL Server 2016 ? Inscreva-se no Microsoft Azure e acesse **[Aqui](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)** para criar uma Máquina Virtual com o SQL Server 2016 já instalado. Quando terminar, você pode excluir a Máquina Virtual.|  
  
 Por exemplo, o seu modelo de produto online pode conter entidades como produto, cor e estilo. A entidade de cor pode conter membros para as cores vermelho, prata e preto.  
  
 ![Modelo de produto com a entidade de cor](../../2014/master-data-services/media/mds-colorentity-productmodel.png "modelo de produto com a entidade de cor")  
  
 Modelos também contêm atributos que são definidos em entidades. Um atributo contém valores que ajudam a descrever os membros da entidade. Há atributos de forma livre e atributos baseados em domínio.  Um atributo baseado em domínio contém valores que são preenchidos por membros de uma entidade e podem ser usados como valores de atributo para outras entidades.  
  
 Por exemplo, a entidade de produto poderia ter atributos de forma livre para custo e peso. Além disso, há um atributo baseado em domínio para a cor que contém valores que são preenchidos pelos membros da entidade de cor. Essa lista mestra de cores é usada como valores de atributo para a entidade Produto.  
  
 ![Entidade de produto com o atributo de cor com base em domínio](../../2014/master-data-services/media/mds-productentity-colorattribute.png "entidade de produto com o atributo de cor com base em domínio")  
  
 As hierarquias derivadas são provenientes das relações entre entidades em um modelo. Estas são relações de atributo baseado em domínio. No modelo de produto, por exemplo, você pode ter uma hierarquia derivada de cor proveniente da relação entre as entidades de cor e produto.  
  
 ![](../../2014/master-data-services/media/mds-derivedhierarchy.png)  
  
 Depois de definir uma estrutura básica para seus dados, você pode iniciar a adição de registros de dados (membros) usando o recurso de importação. Você carrega dados em tabelas de preparo, valida os dados usando regras de negócio e carrega os dados nas tabelas MDS.  Você também pode usar as regras de negócio para definir valores de atributo.  
  
 A tabela a seguir descreve as tarefas principais [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Salvo indicação em contrário, todos os procedimentos a seguir exigem que você seja um administrador de modelo. Para obter mais informações, veja [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
> [!NOTE]  
>  Talvez você queira concluir as tarefas a seguir em um ambiente de teste e usar os dados de exemplo fornecidos quando instalar o [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Para obter mais informações, consulte [Implantando modelos &#40;Master Data Services&#41;](../../2014/master-data-services/deploying-models-master-data-services.md).  
  
|Ação|Detalhes|Tópicos relacionados|  
|------------|-------------|--------------------|  
|Criar um modelo|Ao ser criado, um modelo é considerado como VERSION_1.|[Modelos &#40;Master Data Services&#41;](../../2014/master-data-services/models-master-data-services.md)<br /><br /> [Criar um modelo de &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-master-data-services.md)|  
|Criar entidades|Crie quantas entidades forem necessárias para conter seus membros.|[Entidades &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md)<br /><br /> [Criar uma entidade &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md)|  
|Crie entidades para usar como atributos com base em domínio|Para criar um atributo com base em domínio, primeiro crie a entidade para preencher a lista de valores de atributo.|[Atributos baseados em domínio &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md)<br /><br /> [Criar um atributo baseado em domínio &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)|  
|Crie atributos para suas entidades|Crie atributos para descrever membros. Atributos de Nome e Código são incluídos automaticamente em cada entidade e não podem ser removidos. Talvez você queira criar outros atributos de forma livre para conter texto, datas, números ou arquivos.|[Atributos &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)<br /><br /> [Criar um atributo de texto &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)<br /><br /> [Criar um atributo numérico &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-numeric-attribute-master-data-services.md)<br /><br /> [Criar um atributo de data &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-date-attribute-master-data-services.md)<br /><br /> [Criar um atributo de Link &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-link-attribute-master-data-services.md)<br /><br /> [Criar um atributo de arquivo &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)|  
|Crie grupos de atributos|Se você tiver mais de quatro ou cinco atributos para uma entidade, talvez queira criar grupos de atributos. Esses grupos são as guias exibidas acima da grade no **Gerenciador** , que facilitam a navegação agrupando atributos em guias individuais. \<INSERIR IMAGEM &GT;|[Grupos de atributos &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md)<br /><br /> [Criar um grupo de atributos &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)|  
|Importar registros de dados (membros) para entidades de suporte|Importe os dados para suas entidades de suporte usando o processo de preparo.<br /><br /> Para o modelo de Produto, isso poderia significar a importação de cores ou tamanhos.<br /><br /> Também é possível criar membros manualmente.<br /><br /> Observação: os usuários podem criar membros no [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] se tiverem no mínimo uma permissão de **Atualização** no objeto modelo de folha de uma entidade e acesso à área funcional do **Gerenciador** .|[Importação de dados &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)<br /><br /> [Carregar ou atualizar membros no Master Data Services por meio do processo de preparo](/sql/2014/master-data-services/add-update-and-delete-data-master-data-services)<br /><br /> [Criar um membro folha &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-leaf-member-master-data-services.md)|  
|Criar regras de negócio para garantir a qualidade dos dados|Crie e publique regras de negócio para garantir a exatidão de seus dados. Você pode usar regras de negócio para:<br /><br /> Definir valores de atributo padrão.<br /><br /> Alterar valores de atributo.<br /><br /> Enviar notificações de email quando os dados não passam na validação de regras de negócio.|[Regras de negócio &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)<br /><br /> [Criar e publicar uma regra de negócio &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)<br /><br /> [Notificações &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md)<br /><br /> [Configurar notificações por Email &#40;Master Data Services&#41;](../../2014/master-data-services/configure-email-notifications-master-data-services.md)<br /><br /> [Configurar regras de negócio para enviar notificações &#40;Master Data Services&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)|  
|Importar registros de dados (membros) para suas entidades primárias. Aplicar regras de negócios|Importe os dados para suas entidades primárias usando o processo de preparo. Ao concluir, valide a versão. Isso aplica regras de negócio a todos os membros da versão do modelo.<br /><br /> Em seguida, você poderá trabalhar na correção de eventuais problemas de validação de regra de negócio.|[Validação &#40;Master Data Services&#41;](../../2014/master-data-services/validation-master-data-services.md)<br /><br /> [Validar uma versão em relação a regras de negócios &#40;Master Data Services&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)<br /><br /> [Procedimento armazenado de validação &#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md)|  
|Criar hierarquias derivadas|Hierarquias derivadas podem ser atualizadas conforme suas necessidades comerciais mudarem, garantindo que todos os membros sejam levados em conta no nível apropriado.|[Hierarquias derivadas &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)<br /><br /> [Criar uma hierarquia derivada &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md)|  
|Se necessário, crie hierarquias explícitas|Se quiser criar hierarquias que não sejam fundamentadas em nível e incluam membros de uma única entidade, você pode criar hierarquias explícitas.|[Hierarquias explícitas &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)<br /><br /> [Criar uma hierarquia explícita &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)|  
|Se necessário, crie coleções|Se quiser exibir diferentes agrupamentos de membros para fins de relatório ou análise e não precisar de uma hierarquia completa, crie uma coleção.<br /><br /> Observação: os usuários podem criar coleções no [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] se tiverem no mínimo uma permissão de **Atualização** no objeto modelo de coleção e acesso à área funcional do **Gerenciador** .|[Coleções &#40;Master Data Services&#41;](../../2014/master-data-services/collections-master-data-services.md)<br /><br /> [Criar uma coleção &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-collection-master-data-services.md)|  
|Criar metadados definidos pelo usuário|Para descrever seus objetos de modelo, adicione metadados definidos pelo usuário ao seu modelo. Os metadados podem incluir o proprietário de um objeto ou a origem dos dados.|[Metadados &#40;Master Data Services&#41;](../../2014/master-data-services/metadata-master-data-services.md)<br /><br /> [Adicionar metadados &#40;Master Data Services&#41;](../../2014/master-data-services/add-metadata-master-data-services.md)|  
|Bloquear uma versão do seu modelo e atribuir um sinalizador de versão|Bloqueie uma versão do seu modelo para impedir alterações nos membros, exceto por administradores. Quando os dados da versão tiverem sido validados com êxito de acordo com as regras de negócio, você poderá confirmar a versão, o que impedirá alterações nos membros por qualquer usuário.<br /><br /> Crie e atribua um sinalizador de versão ao modelo. Os sinalizadores ajudam os usuários e sistemas de assinatura a identificar qual versão de um modelo usar.|[Versões &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)<br /><br /> [Bloquear uma versão &#40;Master Data Services&#41;](../../2014/master-data-services/lock-a-version-master-data-services.md)<br /><br /> [Criar um sinalizador de versão &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md)|  
|Criar exibições de assinatura|Para que seus sistemas de assinatura utilizem seus dados mestre, crie exibições de assinatura, que geram exibições padrão no banco de dados do [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|[Exportando dados &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md)<br /><br /> [Criar uma exibição de assinatura &#40;Master Data Services&#41;](create-a-subscription-view-to-export-data-master-data-services.md)|  
|Configurar permissões de usuário e de grupo|Não é possível copiar permissões de usuário e de grupo de um ambiente de teste para um ambiente de produção. Entretanto, o ambiente de teste pode ser usado para determinar a segurança a ser usada subsequentemente na produção.|[Segurança &#40;Master Data Services&#41;](../../2014/master-data-services/security-master-data-services.md)<br /><br /> [Adicionar um grupo &#40;Master Data Services&#41;](../../2014/master-data-services/add-a-group-master-data-services.md)<br /><br /> [Adicionar um usuário &#40;Master Data Services&#41;](../../2014/master-data-services/add-a-user-master-data-services.md)|  
  
 Quando estiver pronto, você poderá implantar o seu modelo, com ou sem os respectivos dados, no ambiente de produção. Para obter mais informações, consulte [Implantando modelos &#40;Master Data Services&#41;](../../2014/master-data-services/deploying-models-master-data-services.md).  
  
  