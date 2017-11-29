---
title: xp_logininfo (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xp_logininfo_TSQL
- xp_logininfo
dev_langs: TSQL
helpviewer_keywords: xp_logininfo
ms.assetid: ee7162b5-e11f-4a0e-a09c-1878814dbbbd
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 76259a13734e0a62358ea46b70447da5fa3eb795
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xplogininfo-transact-sql"></a>xp_logininfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retorna informações sobre os usuários e grupos do Windows.  
  
||  
|-|  
|**Aplica-se a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] até a [versão atual](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
xp_logininfo [ [ @acctname = ] 'account_name' ]   
     [ , [ @option = ] 'all' | 'members' ]   
     [ , [ @privilege = ] variable_name OUTPUT]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@acctname =** ] **'***account_name***'**  
 É o nome de um usuário ou grupo do Windows que recebeu acesso ao [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *account_name* é **sysname**, com um padrão NULL. Se *account_name* não for especificado, todos os grupos e usuários do Windows que foram explicitamente concedida permissão de logon são relatados. *account_name* devem ser totalmente qualificados. Por exemplo, 'ADVWKS4\macraes' ou 'BUILTIN\Administrators'.  
  
 **'todos'** | **'members'**  
 Especifica se as informações sobre todos os caminhos de permissão para a conta ou sobre os membros do grupo do Windows devem ser relatadas. **@option**é **varchar (10)**, com um padrão NULL. A menos que **todos os** for especificado, somente o primeiro caminho de permissão é exibido.  
  
 [  **@privilege =** ] *variable_name*  
 É um parâmetro de saída que retorna o nível de privilégio da conta do Windows especificada. *variable_name* é **varchar (10)**, com um padrão de 'Not wanted'. O nível de privilégio retornado é **usuário**, **admin**, ou **nulo**.  
  
 OUTPUT  
 Quando especificado, coloca *variable_name* no parâmetro de saída.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 0 (êxito) ou 1 (falha)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**nome da conta**|**sysname**|Nome da conta do Windows completamente qualificada.|  
|**tipo**|**char (8)**|Tipo de conta do Windows. Os valores válidos são **usuário** ou **grupo**.|  
|**privilégio**|**char(9)**|Privilégio de acesso para o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Os valores válidos são **admin**, **usuário**, ou **nulo**.|  
|**nome de logon mapeado**|**sysname**|Contas de usuário que tem o privilégio de usuário, **mapeado nome de logon** mostra o nome de logon mapeado que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tenta usar ao efetuar logon nesta conta usando as regras mapeadas com o nome de domínio é adicionado antes dele.|  
|**caminho de permissão**|**sysname**|Associação de grupo que permitiu o acesso à conta.|  
  
## <a name="remarks"></a>Comentários  
 Se *account_name* for especificado, **xp_logininfo** relata o nível de privilégio mais alto do usuário do Windows especificado ou grupo. Se um usuário do Windows tiver acesso como administrador de sistema e como usuário de domínio, ele será relatado como um administrador de sistema. Se o usuário for membro de vários grupos do Windows com o mesmo nível de privilégio, somente o grupo ao qual o acesso ao [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] foi concedido primeiro será relatado.  
  
 Se *account_name* é um usuário do Windows ou grupo que não está associado a válido um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logon, um conjunto de resultados vazio será retornado. Se *account_name* não pode ser identificado como um usuário válido do Windows ou um grupo, uma mensagem de erro é retornada.  
  
 Se *account_name* e **todos os** são todos os caminhos de permissão do usuário do Windows ou grupo especificado, serão retornados. Se *account_name* é um membro de vários grupos, que receberam acesso a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], várias linhas serão retornadas. O **admin** privilégio linhas são retornadas antes do **usuário** linhas de privilégio, e dentro de um privilégio níveis linhas são retornadas na ordem na qual correspondente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logons foram criados.  
  
 Se *account_name* e **membros** são uma lista de membros do próximo nível do grupo especificado, será retornada. Se *account_name* é um grupo local, a lista pode incluir usuários locais, usuários de domínio e grupos. Se *account_name* é uma conta de domínio, a lista é composta de usuários do domínio. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve conectar-se ao controlador de domínio para recuperar informações de associação de grupo. Se o servidor não puder contatar o controlador de domínio, nenhuma informação será retornada.  
  
 **xp_logininfo** retorna apenas informações de grupos globais do Active Directory, não de grupos universais.  
  
## <a name="permissions"></a>Permissões  
 Requer a participação no **sysadmin** fixo de função de servidor ou associação no **pública** função de banco de dados fixa no **mestre** banco de dados com a permissão EXECUTE concedida.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir exibe informações sobre o grupo do Windows `BUILTIN\Administrators`.  
  
```  
EXEC xp_logininfo 'BUILTIN\Administrators';  
```  
  
## <a name="see-also"></a>Consulte também  
 [sp_denylogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Estendidos gerais procedimentos armazenados &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)  
  
  