---
title: 錯誤處理和傳回值 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1b45a903e9982ec4bbc6c567601e43d6156397d2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940108"
---
# <a name="error-handling-and-return-values"></a>錯誤處理和傳回值
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vspackage 和 COM 錯誤使用相同的架構。 `SetErrorInfo`和`GetErrorInfo`函式是 Win32 應用程式開發介面 (API) 的一部分。 整合式的開發環境 (IDE) 中的任何 VSPackage 可以呼叫這些全域 Win32 Api 來記錄豐富的錯誤資訊時接收錯誤通知。 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]提供 interop 組件，以管理資訊時發生錯誤。  
  
## <a name="interop-methods"></a>Interop 方法  
 為了方便起見，IDE 會提供一種方法， <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>，若要使用而不是呼叫 Win32 Api。 在 managed 程式碼使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>。 錯誤時`HRESULT`抵達時，應該會顯示錯誤訊息層級 (這通常是物件實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>命令處理常式)，IDE 會使用另一種方法， <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>，用來顯示適當的訊息方塊。 在 managed 程式碼使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>方法。  
  
 為 VSPackage 實施者，將 COM 物件通常實作`ISupportErrorInfo`。 `ISupportErrorInfo`介面可確保呼叫鏈結豐富的錯誤資訊可以垂直移動。 可能會使用跨處理序或跨執行緒的物件都必須支援`ISupportErrorInfo`以確保，豐富的錯誤資訊會正確地封送處理回呼叫端。  
  
 與相關的 Vspackage，且會參與擴充 IDE，包括編輯器 factory、 編輯器、 階層、 並提供服務的所有物件應該都支援豐富的錯誤資訊。 雖然 IDE 不需要實作這些 VSPackage 物件`ISupportErrorInfo`，一律建議。  
  
 IDE 會負責報告錯誤的資訊並顯示給使用者，是[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]每當`HRESULT`傳播到 IDE。 IDE 也是建立機制`ErrorInfo`物件。  
  
## <a name="general-guidelines"></a>一般方針  
 您可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>方法來設定和報告您 VSPackage 實作內部的錯誤。 不過，一般而言，遵循這些指導方針來處理在 VSPackage 中的錯誤訊息：  
  
-   實作`ISupportErrorInfo`VSPackage COM 物件中。  
  
-   建立錯誤報告機制，會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法中實作的物件<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
-   讓 IDE 透過向使用者顯示錯誤<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>方法。  
  
## <a name="error-information-in-the-ide"></a>在 IDE 中的錯誤資訊  
 下列規則指出如何處理中的錯誤資訊[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]IDE:  
  
-   防禦性策略，以確保過時錯誤資訊給使用者，不會報告的函式呼叫一樣<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>方法應該先呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法。 傳入`null`清除快取的錯誤訊息，才能呼叫任何項目，可能會設定新的錯誤資訊。  
  
-   無法直接報告錯誤訊息的函式只可呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法，如果它們將傳回錯誤`HRESULT`。 允許清除`ErrorInfo`函式，或傳回的項目<xref:Microsoft.VisualStudio.VSConstants.S_OK>。 此規則唯一的例外狀況時，才能呼叫若傳回錯誤`HRESULT`接收的合作對象可以明確地復原，或從放心地忽略。  
  
-   明確地忽略錯誤的任何一方`HRESULT`必須呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法<xref:Microsoft.VisualStudio.VSConstants.S_OK>。 否則，請`ErrorInfo`物件可能會不小心使用另一方會產生錯誤，而不需提供其本身時`ErrorInfo`。  
  
-   產生錯誤的所有方法`HRESULT`建議呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法，以提供豐富的錯誤資訊。 如果傳回`HRESULT`是一種特殊`FACILITY_ITF`error，則此方法，才能提供適當`ErrorInfo`物件。 如果傳回的錯誤是標準的系統錯誤 (例如<xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>， <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>， <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>， <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>，等等。) 是可接受傳回的錯誤碼，而不需要明確呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法。 防禦性程式碼撰寫策略，當原始錯誤`HRESULT`（包括系統錯誤），請務必呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法，不論是透過`ErrorInfo`描述更詳細地、 失敗或`null`。  
  
-   呼叫中的所有函式會傳回錯誤源自另一個呼叫必須來自失敗的資訊傳遞`HRESULT`而不需修改`ErrorInfo`物件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo （元件自動化）](http://msdn.microsoft.com/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](http://msdn.microsoft.com/03317526-8c4f-4173-bc10-110c8112676a)   
 [ISupportErrorInfo 介面](http://msdn.microsoft.com/42d33066-36b4-4a5b-aa5d-46682e560f32)
