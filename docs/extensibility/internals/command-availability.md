---
title: 命令可用性 |微軟文件
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dca47d9ed9968c101e3b6b859b51c1cd8d7404db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709703"
---
# <a name="command-availability"></a>命令可用性

可視化工作室上下文確定哪些命令可用。 上下文可能會根據當前專案、當前編輯器、載入的 VS 包以及整合式開發環境 (IDE) 的其他方面而變化。

## <a name="command-contexts"></a>命令內容文

以下命令名稱文是最常見的:

- IDE:IDE 提供的命令始終可用。

- VSPackage:VS包可以定義何時顯示或隱藏命令。

- 專案:專案命令僅顯示當前選定的專案。

- 編輯器:一次只能有一個編輯器處於活動狀態。 活動編輯器的命令可用。 編輯器與語言服務密切合作。 語言服務必須在關聯的編輯器的上下文中處理其命令。

- 檔案類型:編輯器可以載入多種類型的檔案。 可用命令可能會根據文件類型更改。

- 活動視窗:最後一個活動文件視窗設置密鑰綁定的使用者介面 (UI) 上下文。 但是,具有類似於內部 Web 瀏覽器的鍵綁定表的工具視窗也可以設置 UI 上下文。 對於多選項卡文件視窗(如 HTML 編輯器),每個選項卡都具有不同的命令上下文 GUID。 註冊工具視窗后,它始終在 **「檢視」** 功能表上可用。

- UI 上下文:UI 上下<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>文由 類的值識別<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>,例如, 在<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>生成解決方案時或調試器處於活動狀態時。 多個 UI 上下文可以同時處於活動狀態。

## <a name="define-custom-context-guids"></a>定義自訂內容介面

如果尚未定義適當的命令上下文 GUID,則可以在 VSPackage 中定義一個,然後根據需要將其程式設計為活動或非活動,以控制命令的可見性:

1. 通過調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A>方法註冊上下文 GUID。

2. 通過調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>方法獲取上下文 GUID 的狀態。

3. 通過調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A>方法打開和關閉上下文 GUID。

> [!CAUTION]
> 請確保您的 VS 包不會影響任何現有上下文 GUID,因為其他 VS 包可能依賴於它們。

## <a name="see-also"></a>另請參閱

- [選擇內容物件](../../extensibility/internals/selection-context-objects.md)
- [VS 套件如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
