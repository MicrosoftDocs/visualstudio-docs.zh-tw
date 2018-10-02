---
title: 在 Managed 程式碼的 HRESULT 資訊 |Microsoft Docs
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
- VSPackages, HRESULT information
- HRESULT, managed VSPackages
ms.assetid: 0795ee94-17a8-4327-bf57-27cd5e312a4c
caps.latest.revision: 29
manager: douge
ms.openlocfilehash: c87fc618f1c80b60bbd2f95537dc70a83eb2bdc7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485299"
---
# <a name="hresult-information-in-managed-code"></a>在 Managed 程式碼的 HRESULT 資訊
遇到 HRESULT 傳回值時，Managed 程式碼與 COM 之間的互動可能會造成問題。  
  
 在 COM 介面中，HRESULT 傳回值可以扮演下列角色：  
  
-   提供錯誤資訊 (例如<xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>)。  
  
-   提供一般程式行為的狀態資訊。  
  
 COM 呼叫 Managed 程式碼時，HRESULT 可能導致這些問題：  
  
-   傳回 HRESULT 值小於零的 COM 函式 (失敗碼) 會產生例外狀況。  
  
-   定期傳回兩個以上不同成功碼，例如，COM 方法<xref:Microsoft.VisualStudio.VSConstants.S_OK>或<xref:Microsoft.VisualStudio.VSConstants.S_FALSE>，無法辨別。  
  
 因為許多[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]COM 函式都傳回的 HRESULT 值小於零或傳回不同成功碼[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]保留方法簽章已寫入 interop 組件。 所有[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]interop 方法屬於`int`型別。 在未進行修改且未產生例外狀況的情況下，HRESULT 值會通過 Interop 層。  
  
 因為 COM 函式會將 HRESULT 傳回給可呼叫它的 Managed 方法，所以呼叫中方法必須檢查 HRESULT，並在必要時擲回例外狀況。  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>處理從 COM 傳回給 Managed 程式碼的 HRESULT  
 當您透過 Managed 程式碼呼叫 COM 介面時，請檢查 HRESULT 值，並視需要擲回例外狀況。 <xref:Microsoft.VisualStudio.ErrorHandler>類別包含<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>方法，就會擲回 COM 例外狀況的 HRESULT 值而定，傳遞給它。  
  
 根據預設，<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>傳遞的值小於零的 HRESULT 時擲回例外狀況。 在這類 Hresult 是可接受的值，應該擲回任何例外狀況的情況下，其他 HRESULT 的值應該傳遞至<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>則在測試值之後。 如果正在測試的 HRESULT 符合明確傳遞至任何 HRESULT 值<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>，會擲回任何例外狀況。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants>類別包含常數常見 hresults，例如<xref:Microsoft.VisualStudio.VSConstants.S_OK>並<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>，和[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]HRESULT，比方說，<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>和<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>。 <xref:Microsoft.VisualStudio.VSConstants> 也會提供<xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A>和<xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>方法，這會對應到在 COM 中的 SUCCEEDED 和 FAILED 巨集  
  
 例如，請考慮下列的函式呼叫，在其中<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>是可接受的傳回值，但任何其他的 HRESULT 錯誤小於零代表。  
  
 [!code-csharp[VSSDKHRESULTInformation#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]  
  
 如果有多個可接受的傳回值，其他的 HRESULT 值只是附加至清單的呼叫中<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>。  
  
 [!code-csharp[VSSDKHRESULTInformation#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>透過 Managed 程式碼將 HRESULT 傳回給 COM  
 如果沒有發生例外狀況，管理程式碼傳回<xref:Microsoft.VisualStudio.VSConstants.S_OK>COM 函式呼叫它。 COM Interop 支援透過 Managed 程式碼進行強類型處理的常見例外狀況。 例如，收到無法接受的方法`null`引數會擲回<xref:System.ArgumentNullException>。  
  
 如果您不確定哪個例外狀況擲回，但您知道 HRESULT 您想要傳回至 COM，您可以使用<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>方法會擲回適當的例外狀況。 這甚至適用於非標準的錯誤，例如<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>。 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 嘗試將對應的 HRESULT 會傳遞給它設為強類型例外狀況。 如果失敗，則會改為擲回一般 COM 例外狀況。 最後結果是，HRESULT 您傳遞給<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>從 managed 程式碼傳回給呼叫它的 COM 函式。  
  
> [!NOTE]
>  例外狀況會危害效能並用來指出異常程式狀況。 經常發生的狀況應該透過內嵌方式處理，而不是擲回例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [Managed 的 Vspackage](../misc/managed-vspackages.md)   
 [與 Unmanaged 程式碼互通](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)   
 [如何： 對應 Hresult 和例外狀況](http://msdn.microsoft.com/library/610b364b-2761-429d-9c4a-afbc3e66f1b9)   
 [建置 COM 元件的互通性](http://msdn.microsoft.com/en-us/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [Managed VSPackages](../misc/managed-vspackages.md)