---
title: 註冊服務 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, registering
ms.assetid: c4ebac40-0374-4dda-948e-06fdda0e9c81
caps.latest.revision: 8
manager: douge
ms.openlocfilehash: f56c73bbb09c659a76083e511d79d487402477ac
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491448"
---
# <a name="registering-services"></a>註冊服務
若要支援依需求載入，服務提供者必須註冊其全域服務與[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。  
  
 在開發期間，受管理的服務提供者註冊服務和服務覆寫將屬性新增至套件的原始程式碼，然後再建立的 封裝[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]IDE。 這會在產生的組件上執行 RegPkg.exe 公用程式，並註冊封裝，然後準備進行部署。 如需詳細資訊，請參閱 <<c0> [ 如何： 註冊服務](../misc/how-to-register-a-service.md)。  
  
 未受管理的服務提供者必須註冊它們所提供的服務[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]在服務區段或 service overrides 區段的系統登錄。 下列 .reg 檔案片段顯示可能會如何登錄 SVsTextManager 服務：  
  
```  
[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
@="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
"Name"="SVsTextManager"  
```  
  
 在上述範例中，版本號碼是版本[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，例如 7.1 或 8.0，機碼 {F5E7E71D-1401-11d1-883B-0000F87579D2} 是 SVsTextManager 服務預設值 {的服務識別元 (SID)F5e7e720-1401-11d1-883b-0000f87579d2} 是封裝之文字管理員 VSPackage，提供服務的 GUID。  
  
## <a name="remote-services-and-background-threads"></a>遠端服務和背景執行緒  
 無法自動從遠端使用您所提供的服務，或背景執行緒無法自動使用您所提供的服務。 若要將它們設為可用，您必須建立並註冊類型程式庫。  
  
 從使用 Visual Studio Library (VSL) 的 Unmanaged 程式碼，您可以透過這種方式註冊您的類型程式庫：  
  
```  
#define VSL_REGISTER_TYPE_LIB TRUE  
#include <VSLPackageDllEntryPoints.cpp>  
```  
  
 從 Managed 程式碼，您可以加入建置後步驟，如下所示：  
  
```  
regasm /tlb MyAssembly.dll  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用和提供服務](../extensibility/using-and-providing-services.md)   
 [服務的基本資訊](../extensibility/internals/service-essentials.md)