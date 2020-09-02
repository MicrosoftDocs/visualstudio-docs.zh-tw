---
title: 下拉式列 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7db4296a8fa4146a52d167bce3d8b051aa3ca073
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204640"
---
# <a name="drop-down-bar"></a>下拉式功能表列
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

下拉式列會在程式碼視窗的頂端提供，並包含兩個下拉式清單。  
  
## <a name="drop-down-bar-interfaces"></a>下拉清單欄介面  
 例如，在中， [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] 下拉式列包含 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] 專案和專案成員函式的清單 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] ，如下列圖片所示。  
  
 ![下拉&#45;向下橫條](../extensibility/media/vsdropdown-bar.gif "vsDropdown_bar")  
下拉式列  
  
 在執行下拉式列時，有四個主要重要性的介面：  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     執行此介面來插入下拉式列的內容。 每個下拉式清單都可包含純文字或純文字 (粗體、底線或斜體) 、可以有視窗文字字型著色或以灰色呈現字型色彩，也可以選擇性地在下拉式專案旁邊提供小點陣圖。 與介面類別似 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> ，影像清單中會提供點陣圖影像。 每個下拉式清單都可以有不同的影像清單;不過，每個影像清單都必須包含相同高度的影像。 此外，使用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> 方法，您可以為每個組合提供工具提示。  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     呼叫這個介面可建立或終結程式碼視窗的下拉式清單。 這個介面也可以用來判斷是否已藉由呼叫方法，將下拉式列附加至程式碼視窗 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> 。 <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>的呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> 。  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     呼叫這個介面，即可直接與下拉式列進行通訊。 您可以使用這個介面來強制重新整理下拉式列內容，或變更其中一個清單方塊中的選取範圍。  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     如果您已 `ShowDropdownBarOption` 在語言服務登錄機碼中註冊，則您的程式碼視窗管理員必須監視此事件，以便與使用者喜好設定同步處理下拉式列是否應顯示。 如果您未在語言服務金鑰中註冊這個選項，則 [ **選項** ] 功能表上的 [顯示] 或 [隱藏] 下拉式列的選項已停用。  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>將下拉式清單附加至程式碼視窗  
 若要在建立時將下拉式清單附加至程式碼視窗，當呼叫方法時，語言服務應該附加至下拉式清單行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> 。 如果方法的呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> 指出下拉式列不存在，則呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A> 。 若要存取 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> 介面，請在 <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> 附加您的實作時，從傳回給您的指標呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 。  
  
## <a name="see-also"></a>另請參閱  
 [使用舊版 API 自訂程式碼視窗](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [舊版語言服務中對巡覽列的支援](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)
