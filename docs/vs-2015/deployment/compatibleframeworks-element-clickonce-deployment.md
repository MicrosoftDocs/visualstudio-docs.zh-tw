---
title: '&lt;Compatibleframeworks> &gt; 元素 (ClickOnce 部署) |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ef54062bd74c9395e187503dd12db1c0cd70d822
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675420"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;&gt;ClickOnce 部署 (的 compatibleframeworks> 元素) 
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

識別安裝及執行此應用程式所需的 .NET Framework 版本。  
  
> [!NOTE]
> [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14) `compatibleFrameworks` 當儲存已使用[MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)以憑證簽署的應用程式資訊清單時，MageUI.exe不支援元素。 您必須改用 [Mage.exe](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)。  
  
## <a name="syntax"></a>語法  
  
```  
<compatibleFrameworks  
      SupportUrl>   
   <framework  
      targetVersion  
      profile  
      supportedRuntime  
   />   
</ compatibleFrameworks>  
```  
  
## <a name="elements-and-attributes"></a>元素和屬性  
 針對以 `compatibleFrameworks` [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] 或更新版本提供的執行時間為目標的部署資訊清單，需要元素。 `compatibleFrameworks`元素包含一或多個專案 `framework` ，這些專案會指定此應用程式可以執行的 .NET Framework 版本。 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]執行時間會在此清單中第一個可用的應用程式上執行 `framework` 。  
  
 下表列出 `compatibleFrameworks` 元素支援的屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`S` `upportUrl`|選擇性。 指定可下載慣用相容 .NET Framework 版本的 URL。|  
  
## <a name="framework"></a>架構  
 必要。 下表列出 `framework` 元素支援的屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`targetVersion`|必要。 指定目標 .NET Framework 的版本號碼。|  
|`profile`|必要。 指定目標 .NET Framework 的設定檔。|  
|`supportedRuntime`|必要。 指定與目標 .NET Framework 相關聯之執行時間的版本號碼。|  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 下列程式碼範例顯示 `compatibleFrameworks` [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 部署資訊清單中的元素。 此部署可以在上執行 [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] 。 它也可以在上執行， [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] 因為它是的超集合 [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] 。  
  
```  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)
