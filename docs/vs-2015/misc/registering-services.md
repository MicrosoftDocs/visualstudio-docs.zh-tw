---
title: 註冊服務 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, registering
ms.assetid: c4ebac40-0374-4dda-948e-06fdda0e9c81
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: 64f2afa6e853978e919e466f91475bed1e8d698c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942012"
---
# <a name="registering-services"></a>註冊服務
若要支援依需求載入，服務提供者必須向 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]註冊其全域服務。  
  
 在開發期間，將屬性加入封裝的原始程式碼，然後在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE 中建置封裝，受管理服務提供者即會註冊服務和服務覆寫。 這會在產生的組件上執行 RegPkg.exe 公用程式，並註冊封裝，然後準備進行部署。 如需詳細資訊，請參閱[如何：註冊服務](../misc/how-to-register-a-service.md)。  
  
 未受管理的服務提供者必須在系統登錄的 [services] 區段或 [service overrides] 區段中，向 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 註冊它們所提供的服務。 下列 .reg 檔案片段顯示可能會如何登錄 SVsTextManager 服務：  
  
```  
[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
@="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
"Name"="SVsTextManager"  
```  
  
 在上述範例中，版本號碼是 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]版本 (如 7.1 或 8.0)、機碼 {F5E7E71D-1401-11d1-883B-0000F87579D2} 是 SVsTextManager 服務的服務識別項 (SID)，而預設值 {F5E7E720-1401-11d1-883B-0000F87579D2} 是提供該服務之文字管理員 VSPackage 的封裝 GUID。  
  
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