---
title: 使用舊版 API 自訂程式碼視窗 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8284985003415ef3e723fe735e64481c3666180a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>使用舊版 API 的自訂程式碼視窗
程式碼視窗會支援一或多個文字檢視文件視窗物件。 程式碼視窗的確切的功能取決於相關聯的語言服務。 在多重文件介面 (MDI) 模式中，程式碼視窗會是 MDI 子框架。  
  
 語言服務所控制的程式碼視窗，而且每個語言服務可以提供自己的程式碼視窗管理員。 這會讓它自己的裝飾加入程式碼視窗中，例如波浪線、 顏色標示，以及更多語言服務。 如需如何建立核心視窗的詳細資訊，請參閱[具現化核心編輯器使用舊版 API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)。  
  
 程式碼 視窗<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>物件，其文字檢視和任何設置物件中的裝飾。 當您建立程式碼視窗的核心您具現化編輯器時，語言服務可以連接<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>至程式碼視窗中，為顯示在下圖。  
  
 ![CodeWindow 圖形](../extensibility/media/vscodewindow.gif "vscodewindow")  
程式碼視窗  
  
 語言服務實作的程式碼視窗管理員，並負責管理裝飾，如下拉式清單列。 程式碼視窗呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>程式碼視窗初始化期間的方法。 下拉式清單列或一個按鈕列，進行這個呼叫時，可以新增語言服務 (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) 到程式碼視窗。  
  
## <a name="in-this-section"></a>本節內容  
 `Customizing Code Windows by Using the Legacy API`  
 說明如何自訂程式碼視窗使用舊版 API。  
  
 [How to： 裝載在其他編輯器中的編輯器](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 說明如何裝載在編輯器視窗內的第二個編輯器。  
  
 [如何： 引發事件，當編輯器失去焦點時](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 說明如何將文件檢視附加至文件資料物件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [執行個體化使用舊版 API 的核心編輯器](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [使用舊版 API 存取 theText 檢視](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)