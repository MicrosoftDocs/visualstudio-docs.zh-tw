---
title: 如何： 註冊服務 |Microsoft Docs
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
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
manager: douge
ms.openlocfilehash: a242a13893c7cd303adfe266c9609b7a71d251ba
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489108"
---
# <a name="how-to-register-a-service"></a>如何：註冊服務
Managed Package Framework (MPF) 提供屬性以控制受管理服務的註冊。 RegPkg 公用程式來註冊的服務會使用這些屬性[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。  
  
## <a name="example"></a>範例  
 後面的程式碼取自[VSSDK 範例](../misc/vssdk-samples.md)。  
  
 [!code-csharp[VSSDKRegisterService#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#1)]
 [!code-vb[VSSDKRegisterService#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#1)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>註冊 SMyGlobalService 服務與[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。 如需詳細資訊<xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute>並<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>，請參閱[註冊和取消註冊 Vspackage](../extensibility/registering-and-unregistering-vspackages.md)。  
  
 若要註冊以相同的名稱取代另一個服務的服務，請使用<xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>而不是<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>。  
  
## <a name="robust-programming"></a>穩固程式設計  
 若要更輕鬆地重新編譯服務提供者，而不需要變更服務用戶端，或反之亦然，您可以在個別組件模組中定義服務和其介面。 下列程式碼來自 Reference.Services (C#) 範例中的 IMyGlobalService.cs 檔案。  
  
 [!code-csharp[VSSDKRegisterService#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#2)]
 [!code-vb[VSSDKRegisterService#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#2)]  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> ，才可從 unmanaged 程式碼取得的介面。  
  
> [!NOTE]
>  雖然您可以針對服務和介面使用相同的類型或 GUID，但是建議您使用不同的類型或 GUID，因為服務可以公開不同的介面。  
  
## <a name="see-also"></a>另請參閱  
 [註冊 Vspackage](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd)   
 [服務的基本資訊](../extensibility/internals/service-essentials.md)