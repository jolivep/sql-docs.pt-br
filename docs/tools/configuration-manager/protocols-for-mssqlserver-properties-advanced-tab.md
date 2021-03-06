---
title: Protocolos para propriedades MSSQLSERVER (guia Avançado) | Microsoft Docs
ms.custom: ''
ms.date: 01/24/2019
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: abd5ca68-825f-4c07-b27c-3b3a79d03d74
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: e2cce3ddb17324e234395dcf764855dcffbc44ed
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68071980"
---
# <a name="protocols-for-mssqlserver-properties-advanced-tab"></a>Protocolos para propriedades de MSSQLSERVER (guia Avançado)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Use a guia **Avançado** na caixa de diálogo **Protocolos para Propriedades de MSSQLSERVER** para configurar a **Proteção Estendida para Autenticação** do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]. A**Proteção Estendida** é um recurso dos componentes de rede implementado pelo sistema operacional. A**Proteção Estendida** está disponível no Windows 7 e no Windows Server 2008 R2 e está incluída em service packs de sistemas operacionais anteriores. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] é mais seguro quando as conexões são efetuadas usando a **Proteção Estendida**. Alguns benefícios da **Proteção Estendida** exigem a seleção de **Forçar Criptografia** na guia **Sinalizadores** .

> [!IMPORTANT]  
> O Windows não habilita a **Proteção Estendida** por padrão. Para obter informações sobre como habilitar a **proteção estendida**, consulte o seguinte:
> - [ExtendedProtection de proteção \<estendida do Windows\>](https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/windowsauthentication/extendedprotection/)
> - [Visão geral sobre a Proteção Estendida para Autenticação](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/extended-protection-for-authentication-overview)

Para obter mais informações sobre como configurar outros serviços do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e uma descrição completa da **Proteção Estendida**, consulte informações mais recentes em [Microsoft.com](https://go.microsoft.com/fwlink/?LinkId=177752).

A**Proteção Estendida** tem suporte completo do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client a partir do [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]. Não há suporte para a **Proteção Estendida** para outros provedores de cliente do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] atualmente.

## <a name="options"></a>Opções

### <a name="extended-protection"></a>Proteção Estendida

Há três valores possíveis:  

- **Desativado**: significa que a **proteção estendida** está desabilitada. A instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aceitará conexões de qualquer cliente, independentemente de o cliente estar protegido ou não. A opção**Desativada** é compatível com sistemas operacionais mais antigos e sem patches, mas é menos segura. Só use essa configuração se souber que os sistemas operacionais cliente não têm suporte para proteção estendida.

- **Permitido**: significa que a **Proteção Estendida** é necessária para conexões de sistemas operacionais com suporte para a **Proteção Estendida**. As conexões de aplicativos cliente desprotegidos que estejam sendo executados em sistemas operacionais cliente protegidos são rejeitadas. A**Proteção Estendida** é ignorada para conexões de sistemas operacionais desprotegidos. Essa configuração é mais segura que **Desativada**, mas não é a configuração mais segura. Use essa configuração em ambientes mistos, onde alguns sistemas operacionais ou aplicativos dão suporte à **Proteção Estendida** e outros não.

- **Necessário**: significa que para uma conexão seja aceita, ele deve vir de um aplicativo protegido em um sistema operacional protegido. Essa configuração é a mais segura das três opções. Mas as conexões de sistemas operacionais que não dão suporte à **proteção estendida** não serão capazes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]se conectar ao.

### <a name="accepted-ntlm-spns"></a>SPNs NTLM aceitos

Uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pode ser identificada por mais de um SPN (nome da entidade de serviço) NTLM. Você lista os SPNs como uma série de cadeias de caracteres separadas por ponto e vírgula. Por exemplo, o valor **MSSQLSvc/HostName1.Contoso.com;MSSQLSvc/HostName2.Contoso.com** indica que os clientes que tentam se conectar aos SPNs **MSSQLSvc/HOST1.Contoso.com** ou **MSSQLSvc/HOST2.Contoso.com** são permitidos. Essa variável tem um tamanho máximo de 2.048 caracteres.

## <a name="see-also"></a>Consulte Também

[Proteção Estendida para Autenticação com o Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)

