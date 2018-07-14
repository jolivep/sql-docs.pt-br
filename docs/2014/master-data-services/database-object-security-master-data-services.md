---
title: Segurança de objeto de banco de dados (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database [Master Data Services], object security
- security [Master Data Services], database objects
ms.assetid: dd5ba503-7607-45d9-ad0d-909faaade179
caps.latest.revision: 8
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 5195df44c591f4c605cfd33aa6bb9934c7d54908
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37163497"
---
# <a name="database-object-security-master-data-services"></a>Segurança de objeto de banco de dados (Master Data Services)
  No banco de dados [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , os dados são armazenados em várias tabelas de banco de dados e estão visíveis em exibições. As informações que você pode ter protegido no aplicativo Web do [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] são visíveis aos usuários com acesso ao banco de dados do [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 Especificamente, as informações sobre salários de funcionários podem estar contidas em um modelo de Funcionário, ou as informações financeiras da empresa podem estar em um modelo de Conta. Você pode negar o acesso de um usuário a esses modelos na interface do usuário do [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , mas os usuários com acesso ao banco de dados poderão exibir esses dados.  
  
 Você pode conceder permissões a objetos de banco de dados para disponibilizar dados específicos aos usuários. Para obter mais informações sobre como conceder permissões, consulte [Permissões de objeto GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql). Para obter mais informações sobre como proteger o SQL Server, consulte [Protegendo o SQL Server](../relational-databases/security/securing-sql-server.md).  
  
 As seguintes tarefas exigem o acesso ao banco de dados [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] :  
  
-   [Preparação de dados](#Staging)  
  
-   [Validando dados em relação a regras de negócio](#rules)  
  
-   [Exclusão de versões](#Versions)  
  
-   [Aplicação imediata de permissões de membro de hierarquia](#Hierarchy)  
  
-   [Alterando a conta de administrador do sistema](#SysAdmin)  
  
-   [Definição de configurações do sistema](#SysSettings)  
  
##  <a name="Staging"></a> Preparação de dados  
 Na tabela a seguir, cada protegível tem "name" como parte do nome. Isso indica o nome da tabela de preparo que é especificada quando uma entidade é criada. Para obter mais informações, consulte [importação de dados &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)  
  
|Ação|Protegíveis|Permissões|  
|------------|----------------|-----------------|  
|Carregue membros folha e seus atributos na tabela de preparo.|stg.name_Leaf|Obrigatória: INSERT<br /><br /> Opcional: SELECT e UPDATE|  
|Carregar os dados da tabela de preparo de Folha nas tabelas adequadas do banco de dados do MDS.|stg.udp_name_Leaf|Execute|  
|Carregar membros consolidados e seus atributos na tabela de preparo.|stg.name_Consolidated|Obrigatória: INSERT<br /><br /> Opcional: SELECT e UPDATE|  
|Carregar os dados da tabela de preparo de Consolidados nas tabelas adequadas do banco de dados do MDS.|stg.udp_name_Consolidated|Execute|  
|Carregar relações entre membros folha e consolidados em uma hierarquia explícita na tabela de preparo.|stg.name_Relationship|Obrigatória: INSERT<br /><br /> Opcional: SELECT e UPDATE|  
|Carregar os dados da tabela de preparo Relação nas tabelas adequadas do banco de dados do MDS.|stg.udp_name_Relationship|Execute|  
|Exibir erros ocorridos quando os dados das tabelas de preparo estavam sendo inseridos nas tabelas do banco de dados do MDS.|stg.udp_name_Relationship|SELECT|  
  
 Para obter mais informações, consulte [Importação de dados &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
##  <a name="rules"></a> Validando dados em relação a regras de negócio  
  
|Ação|Protegível|Permissões|  
|------------|---------------|-----------------|  
|Validar uma versão de dados em relação às regras de negócio|mdm.udpValidateModel|Execute|  
  
 Para obter mais informações, consulte [Procedimento armazenado de validação &#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md).  
  
##  <a name="Versions"></a> Exclusão de versões  
  
|Ação|Protegíveis|Permissões|  
|------------|----------------|-----------------|  
|Determinar a ID da versão que deseja excluir|mdm.viw_SYSTEM_SCHEMA_VERSION|SELECT|  
|Excluir uma versão de um modelo|mdm.udpVersionDelete|Execute|  
  
 Para obter mais informações, consulte [Excluir uma versão &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-version-master-data-services.md).  
  
##  <a name="Hierarchy"></a> Aplicação imediata de permissões de membro de hierarquia  
  
|Ação|Protegíveis|Permissões|  
|------------|----------------|-----------------|  
|Aplicação imediata de permissões de membro|mdm.udpSecurityMemberProcessRebuildModel|Execute|  
  
 Para obter mais informações, consulte [Aplicar permissões de membros imediatamente &#40;Master Data Services&#41;](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md).  
  
##  <a name="SysAdmin"></a> Alterando a conta de administrador do sistema  
  
|Ação|Protegíveis|Permissões|  
|------------|----------------|-----------------|  
|Determinar a SID do novo administrador|mdm.tblUser|SELECT|  
|Alterar a conta de administrador do sistema|mdm.udpSecuritySetAdministrator|Execute|  
  
 Para obter mais informações, consulte [alterar a conta de administrador do sistema &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md).  
  
##  <a name="SysSettings"></a> Definição de configurações do sistema  
 Há configurações de sistema que você pode ajustar para controlar o comportamento no [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Você poderá ajustar essas configurações no [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] ou, se tiver acesso UPDATE, diretamente na tabela de banco de dados mdm.tblSystemSetting. Para obter mais informações, veja [Configurações do sistema &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).  
  
## <a name="see-also"></a>Consulte também  
 [Segurança &#40;Master Data Services&#41;](../../2014/master-data-services/security-master-data-services.md)  
  
  