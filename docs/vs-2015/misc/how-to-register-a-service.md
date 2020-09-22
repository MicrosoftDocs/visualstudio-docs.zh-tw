---
title: 如何：註冊服務 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, registering
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: f41578f2522487f746a469933a2269a621390f3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838813"
---
# <a name="how-to-register-a-service"></a>如何：註冊服務
Managed Package Framework (MPF) 提供屬性以控制受管理服務的註冊。 RegPkg 公用程式使用這些屬性，向 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]註冊服務。  
  
## <a name="example"></a>範例  
 接下來的程式碼來自 [VSSDK 範例](../misc/vssdk-samples.md)。  
  
 [!code-csharp[VSSDKRegisterService#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#1)]
 [!code-vb[VSSDKRegisterService#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#1)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 會向 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 註冊 SMyGlobalService 服務。 如需和的詳細資訊 <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> ，請參閱 [註冊和取消註冊 vspackage](../extensibility/registering-and-unregistering-vspackages.md)。  
  
 若要註冊會取代另一個同名服務的服務，請使用 <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>而非 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>。  
  
## <a name="robust-programming"></a>穩固程式設計  
 若要更輕鬆地重新編譯服務提供者，而不需要變更服務用戶端，或反之亦然，您可以在個別組件模組中定義服務和其介面。 下列程式碼來自 Reference.Services (C#) 範例中的 IMyGlobalService.cs 檔案。  
  
 [!code-csharp[VSSDKRegisterService#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#2)]
 [!code-vb[VSSDKRegisterService#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#2)]  
  
 需要有 <xref:System.Runtime.InteropServices.ComVisibleAttribute>才能透過 Unmanaged 程式碼取得介面。  
  
> [!NOTE]
> 雖然您可以針對服務和介面使用相同的類型或 GUID，但是建議您使用不同的類型或 GUID，因為服務可以公開不同的介面。  
  
## <a name="see-also"></a>另請參閱  
 [註冊 Vspackage](../extensibility/internals/registering-vspackages.md)   
 [服務的基本資訊](../extensibility/internals/service-essentials.md)