---
title: "下拉式清單列 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7058c0b93cd0ff4afb2a13b625cd7ef034b03699
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="drop-down-bar"></a>下拉式清單列
在下拉式清單列提供程式碼視窗頂端，並包含兩個下拉式清單。  
  
## <a name="drop-down-bar-interfaces"></a>下拉式清單列介面  
 在[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]，例如，下拉式清單列包含清單[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]項目和[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]項目成員函式，如下列圖片所示。  
  
 ![卸除 &#45; 向下列](../extensibility/media/vsdropdown_bar.gif "vsDropdown_bar")  
下拉式清單列  
  
 當實作下拉式清單列時，有四個最重要的一點介面：  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     實作這個介面可插入下拉式清單列的內容。 每個下拉式清單的組合可以包含純文字或美觀的文字 (粗體、 底線、 或斜體)，可以有視窗文字的字型色彩或灰色的字型著色、，而且可以選擇性地提供下拉式清單項目旁邊的小型點陣圖。 類似於<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>介面，點陣圖影像提供影像清單中。 每個下拉式清單的組合都可以擁有不同的影像清單。不過，每個映像清單必須包含具有相同高度的映像。 此外，使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A>方法，您可以為每個組合提供工具提示。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     呼叫這個介面可建立或終結程式碼視窗的下拉式清單列。 此介面也可用來判斷是否在下拉式清單列已附加至程式碼視窗藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A>方法。 呼叫<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>如<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>從<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     呼叫這個介面可直接與下拉式清單列通訊。 您可以使用這個介面，以強制重新整理的下拉式清單列內容，或變更其中一個清單方塊中的選取項目。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     如果您註冊了`ShowDropdownBarOption`在您的語言服務登錄機碼，然後您的程式碼視窗管理員必須監視同步處理是否應該顯示在下拉式清單列有關的使用者喜好設定與此事件。 如果您沒有註冊的語言服務金鑰，這個選項，則上已停用的選項，以顯示或隱藏的下拉式清單列**選項**功能表。  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>附加至程式碼視窗的下拉式清單列  
 若要在建立時，請將下拉式清單列附加至程式碼視窗中，語言服務應該附加至下拉式清單列時<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>方法呼叫。 如果呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A>方法表示下拉式清單列沒有已不存在，然後呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>。 若要存取<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>介面，請呼叫<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>從<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>傳回指標給您時您<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>實作已附加。  
  
## <a name="see-also"></a>請參閱  
 [使用舊版 API 的自訂程式碼視窗](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [舊版語言服務中對巡覽列的支援](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)