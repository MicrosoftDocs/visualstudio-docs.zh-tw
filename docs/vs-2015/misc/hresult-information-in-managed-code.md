---
title: 在 Managed 程式碼的 HRESULT 資訊 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 08d14f1155838e53321224280a69e7a76bf07b52
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911846"
---
# <a name="hresult-information-in-managed-code"></a>在 Managed 程式碼的 HRESULT 資訊
遇到 HRESULT 傳回值時，Managed 程式碼與 COM 之間的互動可能會造成問題。  
  
 在 COM 介面中，HRESULT 傳回值可以扮演下列角色：  
  
- 提供錯誤資訊 (例如，<xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>)。  
  
- 提供一般程式行為的狀態資訊。  
  
  COM 呼叫 Managed 程式碼時，HRESULT 可能導致這些問題：  
  
- 傳回 HRESULT 值小於零的 COM 函式 (失敗碼) 會產生例外狀況。  
  
- 無法區分定期傳回兩個以上不同成功碼 (例如，<xref:Microsoft.VisualStudio.VSConstants.S_OK> 或 <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>) 的 COM 方法。  
  
  因為許多 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] COM 函式都傳回小於零的 HRESULT 值或傳回不同的成功碼，所以已撰寫 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Interop 組件，來保留方法簽章。 所有 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Interop 方法的類型都是 `int` 。 在未進行修改且未產生例外狀況的情況下，HRESULT 值會通過 Interop 層。  
  
  因為 COM 函式會將 HRESULT 傳回給可呼叫它的 Managed 方法，所以呼叫中方法必須檢查 HRESULT，並在必要時擲回例外狀況。  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>處理從 COM 傳回給 Managed 程式碼的 HRESULT  
 當您透過 Managed 程式碼呼叫 COM 介面時，請檢查 HRESULT 值，並視需要擲回例外狀況。 <xref:Microsoft.VisualStudio.ErrorHandler> 類別包含會擲回 COM 例外狀況的 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 方法 (視傳遞給它的 HRESULT 值而定)。  
  
 根據預設，<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 只要傳遞的 HRESULT 值小於零就會擲回例外狀況。 如果這類 HRESULT 是可接受值，而且不應該擲回任何例外狀況，則在測試值之後，應該會將其他 HRESULT 的值傳遞給 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>。 如果正在測試的 HRESULT 符合明確傳遞給 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 的任何 HRESULT 值，則不會擲回任何例外狀況。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants>類別包含常數常見 hresults，例如<xref:Microsoft.VisualStudio.VSConstants.S_OK>並<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>，和[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]HRESULT，比方說，<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>和<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>。 <xref:Microsoft.VisualStudio.VSConstants> 也提供 <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> 和 <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> 方法，而這些方法會對應至 COM 中的 SUCCEEDED 和 FAILED 巨集。  
  
 例如，請考慮下列的函式呼叫，其中，<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> 是可接受的傳回值，但任何其他小於零的 HRESULT 都代表發生錯誤。  
  
 [!code-csharp[VSSDKHRESULTInformation#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]  
  
 如果有多個可接受的傳回值，則在 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 呼叫中只能將其他 HRESULT 值附加至清單。  
  
 [!code-csharp[VSSDKHRESULTInformation#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>透過 Managed 程式碼將 HRESULT 傳回給 COM  
 如果未發生例外狀況，則 Managed 程式碼會將 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 傳回給已呼叫它的 COM 函式。 COM Interop 支援透過 Managed 程式碼進行強類型處理的常見例外狀況。 例如，收到無法接受 `null` 引數的方法會擲回 <xref:System.ArgumentNullException>  
  
 如果您不確定會擲回哪個例外狀況，但知道您想要傳回給 COM 的 HRESULT，則可以使用 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 方法擲回適當的例外狀況。 這甚至適用於非標準錯誤 (例如，<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>)。 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 會嘗試將傳遞給它的 HRESULT 對應至強類型例外狀況。 如果失敗，則會改為擲回一般 COM 例外狀況。 最後結果是您透過 Managed 程式碼傳遞給 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 的 HRESULT 會傳回給呼叫它的 COM 函式。  
  
> [!NOTE]
>  例外狀況會危害效能並用來指出異常程式狀況。 經常發生的狀況應該透過內嵌方式處理，而不是擲回例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [Managed 的 Vspackage](../misc/managed-vspackages.md)   
 [與 Unmanaged 程式碼互通](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)   
 [如何： 對應 Hresult 和例外狀況](http://msdn.microsoft.com/library/610b364b-2761-429d-9c4a-afbc3e66f1b9)   
 [建置 COM 元件的互通性](http://msdn.microsoft.com/en-us/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [Managed VSPackages](../misc/managed-vspackages.md)