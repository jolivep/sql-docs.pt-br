---
title: Contagem de uso | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- usage counts [ODBC]
- file usage counts [ODBC]
- installing ODBC components [ODBC], usage counts
- subkeys [ODBC], usage counts
ms.assetid: 0678aee9-8256-463c-89dd-77b1a0dfdd60
author: MightyPen
ms.author: genemi
ms.openlocfilehash: edf9976dd3e5d890b46919808e896a8e81a0cd93
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093788"
---
# <a name="usage-counting"></a>Contagem de uso
> [!NOTE]  
>  A partir do Windows XP e do Windows Server 2003, o ODBC está incluído no sistema operacional Windows. Você só deve instalar explicitamente o ODBC em versões anteriores do Windows.  
  
 Dois tipos de contagens de uso são mantidos no registro para cada componente: uma contagem de uso de componentes e uma ou mais contagens de uso de arquivo opcional. A contagem de uso do componente ajuda a DLL do instalador a manter entradas do registro. Ele é armazenado no valor UsageCount nas subchaves ODBC Core, Driver e Translator. Para obter o formato do valor de UsageCount e mais informações sobre essas subchaves, consulte [entradas de registro para componentes ODBC](../../../odbc/reference/install/registry-entries-for-odbc-components.md).  
  
 Quando um componente é instalado pela primeira vez, a DLL do instalador cria uma subchave para ele e define os dados para o valor UsageCount nessa subchave como 1. Quando o componente é instalado novamente, a DLL do instalador incrementa a contagem de uso. Quando o componente é removido, a DLL do instalador decrementa a contagem de uso. Se a contagem de uso cair em 0, a DLL do instalador removerá a subchave do componente.  
  
> [!CAUTION]  
>  Um aplicativo não deve remover fisicamente os arquivos do Gerenciador de driver quando a contagem de uso do componente e a contagem de uso do arquivo atingem zero.  
  
 As contagens de uso de arquivo ajudam a determinar quando um arquivo deve realmente ser copiado ou excluído em vez de incrementar ou decrementar a contagem de uso. Isso é importante porque os componentes ODBC e, portanto, os arquivos nos componentes ODBC, são compartilhados e podem ser instalados ou removidos por uma variedade de aplicativos. O aplicativo pode excluir arquivos de driver e tradutor se a contagem de uso do componente e a contagem de uso do arquivo chegarem a zero. No entanto, os arquivos do Gerenciador de driver não devem ser excluídos quando a contagem de uso do componente e a contagem de uso do arquivo tiverem atingido zero, pois esses arquivos podem ser usados por outros aplicativos que não incrementaram a contagem de uso do arquivo.  
  
> [!NOTE]  
>  As contagens de uso de arquivo são opcionais no Microsoft®NT®/Windows2000.  
  
 As contagens de uso de arquivo são mantidas pelo programa de instalação depois de chamar **SQLInstallDriverManager**, **SQLInstallDriverEx**, **SQLInstallTranslatorEx**, **SQLRemoveDriverManager**, **SQLRemoveDriver**ou **SQLRemoveTranslator**.  
  
 Quando um componente é instalado pela primeira vez, o programa de instalação ou a DLL do instalador cria um valor na seguinte chave para cada arquivo no componente que ainda não está no sistema:  
  
> [!NOTE]  
>  HKEY_LOCAL_MACHINE  
>   
>  ANTIVÍRUS  
>   
>  Microsoft  
>   
>  Windows  
>   
>  CurrentVersion  
>   
>  SharedDlls  
  
 Ele define os dados para esses valores como 1 e copia o arquivo para o sistema. Quando o componente é instalado novamente, o programa de instalação ou a DLL do instalador incrementa as contagens de uso. Quando o componente é removido, o programa de instalação ou a DLL do instalador decrementa as contagens de uso. Se qualquer contagem de uso for para 0, o programa de instalação ou a DLL do instalador removerá o valor do arquivo e, se o componente for um driver ou um tradutor, excluirá o arquivo. Os arquivos do Gerenciador de driver não devem ser excluídos.  
  
 O formato do valor da contagem de uso do arquivo é mostrado na tabela a seguir.  
  
|Nome|Tipo de dados|data|  
|----------|---------------|----------|  
|*caminho completo*|REG_DWORD|*contagem*|  
  
 Por exemplo, suponha que um driver para o Informix use os arquivos Infrmx32. dll e Infrmx32. hlp e suponha que esse driver tenha sido instalado duas vezes. Os valores na subchave SharedDlls do driver Informix seriam os seguintes:  
  
```  
C:\WINDOWS\SYSTEM32\INFRMX32.DLL : REG_DWORD : 0x2  
C:\WINDOWS\SYSTEM32\INFRMX32.HLP : REG_DWORD : 0x2  
```
