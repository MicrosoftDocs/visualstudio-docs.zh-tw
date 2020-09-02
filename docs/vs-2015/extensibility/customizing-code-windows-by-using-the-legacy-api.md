---
title: 使用舊版 API 自訂程式碼視窗 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f15c649b8d857d2e920bb957e5975d296749cb86
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62556112"
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>使用舊版 API 自訂程式碼視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

程式碼視窗是支援一或多個文字視圖的文件視窗物件。 程式碼視窗的確切功能取決於相關聯的語言服務。 在多重文件介面 (MDI) 模式中，程式碼視窗是 MDI 子框架。  
  
 程式碼視窗是由語言服務所控制，而每個語言服務都可以提供自己的程式碼視窗管理員。 這可讓語言服務將自己的裝飾新增至程式碼視窗，例如波浪線、顏色標示等等。 如需如何建立核心視窗的詳細資訊，請參閱 [使用舊版 API 將核心編輯器](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)具現化。  
  
 程式碼視窗是 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 具有文字視圖和物件中所放置之任何裝飾的物件。 當您在核心編輯器具現化期間建立程式碼視窗時，您的語言服務可以附加 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 至程式碼視窗，如下圖所示。  
  
 ![CodeWindow 圖形](../extensibility/media/vscodewindow.gif "vscodewindow")  
程式碼視窗  
  
 語言服務會執行程式碼視窗管理員，負責管理裝飾，例如下拉式清單。 程式碼視窗會 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> 在程式碼視窗初始化期間呼叫方法。 當進行這個呼叫時，語言服務可以將下拉式列或按鈕列 (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) 加入至程式碼視窗。  
  
## <a name="in-this-section"></a>本節內容  
 `Customizing Code Windows by Using the Legacy API`  
 說明如何使用舊版 API 自訂程式碼視窗。  
  
 [如何：在其他編輯器中裝載編輯器](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 說明如何在編輯器視窗內裝載第二個編輯器。  
  
 [如何：在編輯器失去焦點時引發事件](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 說明如何將檔視圖附加至檔資料物件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [使用舊版 API 將核心編輯器具現化](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [使用舊版 API 存取文字檢視](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
