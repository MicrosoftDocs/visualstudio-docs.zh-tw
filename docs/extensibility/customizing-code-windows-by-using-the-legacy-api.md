---
title: 使用舊版 API 來自訂程式碼的 Windows |Microsoft Docs
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
ms.openlocfilehash: 454d58a48abafe9b23f8a812e5d40b9fc6477b50
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499350"
---
# <a name="customize-code-windows-by-using-the-legacy-api"></a>使用舊版 API 來自訂程式碼視窗
程式碼視窗會支援一或多個文字檢視的文件視窗物件。 程式碼視窗的確切的功能取決於相關聯的語言服務。 在多重文件介面 (MDI) 模式中，程式碼視窗會是 MDI 子框架。  
  
 程式碼視窗所控制的語言服務，而且每個語言服務可以提供它自己的程式碼視窗管理員。 這可讓語言服務，讓它自己的裝飾加入程式碼視窗中，例如波浪線、 顏色標示、 等等。 如需如何建立核心視窗的詳細資訊，請參閱[具現化核心編輯器使用舊版 API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)。  
  
 程式碼視窗是<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>具有文字檢視和任何位置所在之物件中的裝飾物件。 當您建立的程式碼視窗您具現化的核心編輯器時，您的語言服務可以將附加<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>程式碼 視窗中，以做為顯示在下圖中。  
  
 ![CodeWindow 圖形](../extensibility/media/vscodewindow.gif "vscodewindow")  
程式碼視窗  
  
 語言服務會實作程式碼視窗管理員，並負責管理裝飾，如下拉式清單列。 程式碼視窗呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>程式碼視窗初始化期間的方法。 下拉式清單列或按鈕列，這個呼叫時，可以新增語言服務 (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) 到程式碼視窗。  
  
## <a name="in-this-section"></a>本節內容  
 `Customizing Code Windows by Using the Legacy API`  
 說明如何自訂使用舊版 API 的程式碼視窗。  
  
 [如何： 裝載在其他編輯器中的編輯器](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 說明如何裝載在編輯器視窗內的第二個編輯器。  
  
 [如何： 引發事件當編輯器失去焦點時](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 說明如何將文件檢視附加至文件資料物件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [使用舊版 API 具現化核心編輯器](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [使用舊版 API 存取 theText 檢視](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)