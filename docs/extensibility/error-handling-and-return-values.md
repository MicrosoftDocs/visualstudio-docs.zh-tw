---
title: 錯誤處理和傳回值 |Microsoft Docs
description: 瞭解 Visual Studio SDK 如何提供 interop 元件，以便在收到錯誤通知時，記錄豐富的錯誤資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 530430852d621ea4aaf62bf2c86365609f26cf8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883359"
---
# <a name="error-handling-and-return-values"></a>錯誤處理和傳回值
Vspackage 和 COM 針對錯誤使用相同的架構。 和函式 `SetErrorInfo` `GetErrorInfo` 是 Win32 應用程式設計介面的一部分， (API) 。 整合式開發環境 (IDE) 中的任何 VSPackage 都可以呼叫這些全域 Win32 Api，以在收到錯誤通知時記錄豐富的錯誤資訊。 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]提供 interop 元件來管理錯誤資訊。

## <a name="interop-methods"></a>Interop 方法
 為了方便起見，IDE 會提供方法， <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 以使用而不是呼叫 Win32 api。 在 managed 程式碼中使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 。 當錯誤 `HRESULT` 抵達應顯示錯誤訊息的層級時 (這通常是執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 命令處理常式的物件) ，IDE 會使用另一個方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 來顯示適當的訊息方塊。 在 managed 程式碼中，請使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 方法。

 以 VSPackage 的實作者而言，您的 COM 物件通常會執行 `ISupportErrorInfo` 。 `ISupportErrorInfo`介面可確保豐富的錯誤資訊可以垂直向上移動至呼叫鏈。 可能跨進程或跨執行緒使用的物件必須支援 `ISupportErrorInfo` ，以確保將豐富的錯誤資訊正確地封送處理回呼叫端。

 所有與 Vspackage 相關的物件（包括編輯器 factory、編輯器、階層和提供的服務）都應該支援豐富的錯誤資訊。 雖然 IDE 不需要執行這些 VSPackage 物件 `ISupportErrorInfo` ，但一定是建議的。

 IDE 會負責報告錯誤資訊，並在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 每次傳播至 IDE 時向使用者顯示該資訊 `HRESULT` 。 IDE 也是建立物件的機制 `ErrorInfo` 。

## <a name="general-guidelines"></a>一般指導方針
 您也可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 方法來設定和報告 VSPackage 執行的內部錯誤。 不過，一般而言，請遵循下列指導方針來處理 VSPackage 中的錯誤訊息：

- `ISupportErrorInfo`在您的 VSPACKAGE COM 物件中執行。

- 建立錯誤報表機制， <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 以在執行的物件中呼叫方法 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 。

- 讓 IDE 透過方法向使用者顯示錯誤 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 。

## <a name="error-information-in-the-ide"></a>IDE 中的錯誤資訊
 下列規則指出如何處理 IDE 中的錯誤資訊 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ：

- 為了確保不會向使用者回報過時錯誤資訊的防禦策略，呼叫方法的函式 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 應該先呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 方法。 傳入 `null` 以清除快取的錯誤訊息，然後呼叫可能會設定新錯誤資訊的任何內容。

- 未直接報告錯誤訊息的函式，只有在傳回錯誤時才允許呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 方法 `HRESULT` 。 您可以對函式 `ErrorInfo` 或傳回時的專案清除 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 。 這項規則的唯一例外狀況是當呼叫傳回的錯誤是 `HRESULT` 接收方可以明確復原或安全地忽略的錯誤。

- 任何明確忽略錯誤的 `HRESULT` 合作物件都必須使用來呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 方法 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 。 否則， `ErrorInfo` 當另一個合作物件產生錯誤而未提供自己的錯誤時，可能會不小心使用此物件 `ErrorInfo` 。

- 我們鼓勵所有源自錯誤的方法 `HRESULT` 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 方法，以提供豐富的錯誤資訊。 如果傳回的 `HRESULT` 是特殊 `FACILITY_ITF` 錯誤，則需要方法才能提供適當的 `ErrorInfo` 物件。 如果傳回的錯誤是標準系統錯誤 (例如，、、 <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> 、等等 <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> 。 ) 可接受傳回錯誤碼，而不需要明確呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 方法。 作為防禦程式碼策略，當產生錯誤 `HRESULT` (包括系統錯誤) 時，請一律呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 方法，方法是以 `ErrorInfo` 更詳細的方式描述失敗，或 `null` 。

- 傳回另一個呼叫所產生之錯誤的所有函式，都必須傳遞在中從失敗呼叫所收到的資訊， `HRESULT` 而不需要修改 `ErrorInfo` 物件。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (元件自動化) ](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [ISupportErrorInfo 介面](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
