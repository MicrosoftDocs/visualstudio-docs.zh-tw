---
title: 錯誤處理與返回值 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30b6b9bff9056360f9ea840f47b1488f05bee872
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711927"
---
# <a name="error-handling-and-return-values"></a>錯誤處理與傳回值
VS 包和 COM 使用相同的體系結構來處理錯誤。 和`SetErrorInfo``GetErrorInfo`函數是 Win32 應用程式程式設計介面 (API) 的一部分。 集成開發環境 (IDE) 中的任何 VSPackage 都可以調用這些全域 Win32 API,以在收到錯誤通知時記錄豐富的錯誤資訊。 提供[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]用於管理錯誤資訊的互通程式集。

## <a name="interop-methods"></a>互通方法
 為方便起見,IDE 提供了一種方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, 使用 而不是調用 Win32 API。 在託管代碼使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>中。 當錯誤`HRESULT`到達應顯示錯誤消息的級別(這通常是<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>實現 命令處理程式的物件)時,IDE 使用另<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>一種方法 ,顯示相應的消息框。 在託管代碼中使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>方法。

 為 VSPackage 的擁有者,COM 物件通常`ISupportErrorInfo`。 該`ISupportErrorInfo`介面可確保豐富的錯誤資訊可以垂直向上移動呼叫鏈。 跨進程或跨線程使用的物件必須支援`ISupportErrorInfo`,以確保將豐富的錯誤資訊正確封送回調用方。

 與 VSPackages 相關且涉及擴展 IDE 的所有物件(包括編輯器工廠、編輯器、層次結構和提供的服務)都應支援豐富的錯誤資訊。 雖然 IDE 不需要這些 VSPackage`ISupportErrorInfo`物件來實現 ,但始終鼓勵它。

 IDE 負責報告錯誤資訊,並在將錯誤資訊傳播到[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]IDE 時`HRESULT`將其顯示給使用者。 IDE 也是`ErrorInfo`創建 對象的機制。

## <a name="general-guidelines"></a>一般方針
 也可以使用和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A><xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>方法設置和報告 VSPackage 實現內部的錯誤。 但是,通常,請遵循以下準則來處理 VSPackage 中的錯誤訊息:

- 在`ISupportErrorInfo`VSPackage COM 物件中實現。

- 創建錯誤報告機制,在實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A><xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>的物件中調用 方法。

- 讓 IDE<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>通過方法 向使用者顯示錯誤。

## <a name="error-information-in-the-ide"></a>IDE 中的錯誤資訊
 以下規則指示如何處理 IDE[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中的錯誤資訊:

- 作為一種防禦策略,以確保陳舊的錯誤資訊不報告給用戶,調用方法的<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>函數應首先調<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>用 方法。 在調用`null`任何可能設置新錯誤資訊的任何內容之前,先轉接以清除緩存的錯誤消息。

- 不直接報告錯誤消息的函數只有在返回錯誤<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>`HRESULT`時才允許調用 方法。 允許清除函數的條目`ErrorInfo`上或<xref:Microsoft.VisualStudio.VSConstants.S_OK>返回 時。 此規則的唯一例外是呼叫返回接收方可以顯式恢復`HRESULT`或安全地忽略的錯誤。

- 顯式忽略錯誤的`HRESULT`任何一方都必須使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>調用<xref:Microsoft.VisualStudio.VSConstants.S_OK>方法。 否則,當`ErrorInfo`另一方在未提供自己的`ErrorInfo`錯誤的情況下生成錯誤時,可能會意外使用該物件。

- 鼓勵所有產生錯誤`HRESULT`的方法調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>該方法 以提供豐富的錯誤資訊。 如果返回`HRESULT`的是特殊`FACILITY_ITF`錯誤,則需要該方法來提供正確的`ErrorInfo`物件。 如果傳回的錯誤是標準系統錯誤<xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>(<xref:Microsoft.VisualStudio.VSConstants.E_ABORT>例如<xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>, <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>、 、 、 、 等), 則無需顯式呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法即可傳回錯誤程式碼。 作為防禦性編碼策略,當產生`HRESULT`錯誤(包括系統錯誤)時,始終調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法,以更詳細`ErrorInfo`地 描述故障`null`,或 。

- 傳回由另一個調用引起的錯誤的所有函數都必須傳遞從 中的失敗調用接收`HRESULT``ErrorInfo`的資訊, 而無需修改物件。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [設定錯誤資訊(元件自動化)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [ISupportErrorInfo 介面](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
