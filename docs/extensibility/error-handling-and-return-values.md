---
title: "錯誤處理和傳回值 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a1c9aa444860de2e20f51247ac53d16ceaad2b48
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="error-handling-and-return-values"></a>錯誤處理和傳回值
Vspackage 和 COM 錯誤使用相同的架構。 `SetErrorInfo`和`GetErrorInfo`函式是 Win32 應用程式開發介面 (API) 的一部分。 整合式的開發環境 (IDE) 中任何 VSPackage 可以呼叫這些全域 Win32 Api，來記錄豐富的錯誤資訊時接收錯誤通知。 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]提供管理資訊時發生錯誤的 interop 組件。  
  
## <a name="interop-methods"></a>Interop 方法  
 為了方便起見，IDE 會提供一種方法， <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>，而不是呼叫 Win32 Api 使用。 在 managed 程式碼使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>。 當錯誤`HRESULT`抵達應該會顯示錯誤訊息的層級 (這通常是物件實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>命令處理常式)，IDE 使用另一種方法， <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>，以顯示適當的訊息方塊。 在 managed 程式碼使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>方法。  
  
 為 VSPackage 實施者 COM 物件通常實作`ISupportErrorInfo`。 `ISupportErrorInfo`介面可確保呼叫鏈結豐富的錯誤資訊可以垂直移動。 可能在跨處理序或跨執行緒使用的物件必須支援`ISupportErrorInfo`以確保，豐富的錯誤資訊會正確地封送處理回呼叫端。  
  
 Vspackage 與相關的而且會參與擴充 IDE，包括編輯器 factory、 編輯器、 階層、 並提供服務的所有物件應該都支援豐富的錯誤資訊。 雖然 IDE 不需要實作這些 VSPackage 物件`ISupportErrorInfo`，一律鼓勵。  
  
 IDE 會負責錯誤資訊回報並顯示給使用者的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]每當`HRESULT`傳播至 IDE。 IDE 也是一種機制建立`ErrorInfo`物件。  
  
## <a name="general-guidelines"></a>一般方針  
 您可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>方法設定和報表，則您的 VSPackage 實作以及內部錯誤。 不過，一般而言，遵循這些指導方針來處理您的 VSPackage 中的錯誤訊息：  
  
-   實作`ISupportErrorInfo`VSPackage COM 物件中。  
  
-   建立錯誤報告呼叫的機制<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法實作的物件中<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
-   可讓使用者透過顯示錯誤 IDE<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>方法。  
  
## <a name="error-information-in-the-ide"></a>在 IDE 中的資訊時發生錯誤  
 下列規則指出如何處理錯誤資訊[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]IDE:  
  
-   若要保證，過時的錯誤資訊不會報告給使用者，防禦策略函式呼叫一樣<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>方法應該先呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法。 傳入`null`清除快取的錯誤訊息，才能呼叫任何項目，可能會設定新的錯誤資訊。  
  
-   只允許直接不報告錯誤訊息的函式呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法如果它們將傳回錯誤`HRESULT`。 它是允許清除`ErrorInfo`函式，或在傳回的項目<xref:Microsoft.VisualStudio.VSConstants.S_OK>。 此規則唯一的例外狀況時，才能呼叫會傳回錯誤`HRESULT`接收合作對象可以明確地復原，或從放心忽略。  
  
-   明確地略過錯誤任何合作對象`HRESULT`必須呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法<xref:Microsoft.VisualStudio.VSConstants.S_OK>。 否則，`ErrorInfo`物件可能會不小心使用另一方會產生錯誤，而不需提供其本身時`ErrorInfo`。  
  
-   產生錯誤的所有方法`HRESULT`鼓勵呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法以提供豐富的錯誤資訊。 如果傳回`HRESULT`為特殊`FACILITY_ITF`錯誤，則此方法才能提供適當的`ErrorInfo`物件。 如果傳回的錯誤是標準的系統錯誤 (例如， <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>， <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>， <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>， <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>，等) 是傳回的錯誤碼而不需要明確地呼叫可接受的<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法。 做為防衛性程式碼撰寫策略，當原始錯誤`HRESULT`（包括系統錯誤），請務必呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法，不論是透過`ErrorInfo`描述更詳細地、 失敗或`null`。  
  
-   傳回引發另一個呼叫錯誤必須來自失敗的資訊傳遞的所有函式呼叫中`HRESULT`而不需修改`ErrorInfo`物件。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (元件 Automation)](http://msdn.microsoft.com/en-us/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](http://msdn.microsoft.com/en-us/03317526-8c4f-4173-bc10-110c8112676a)   
 [ISupportErrorInfo 介面](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)