---
title: 命令可用性 |Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7dfe8a6b3e4c84fd97a159f6ac43e0de47536f0b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861810"
---
# <a name="command-availability"></a>命令可用性

Visual Studio 內容會決定哪些命令可供使用。 根據目前的專案、 目前的編輯器、 已載入，Vspackage 和整合式的開發環境 (IDE) 的其他層面，可以變更內容。

## <a name="command-contexts"></a>命令內容

下列的命令內容是最常見的：

- IDE:IDE 所提供的命令一律可用。

- VSPackage:Vspackage 可以定義命令時要顯示或隱藏。

- 專案:只會針對目前選取的專案，顯示專案命令。

- 編輯器：只有一個編輯器可以作用一次。 提供從作用中的編輯器命令。 與語言服務密切合作的編輯器。 語言服務必須處理其編輯器相關聯的內容中的命令。

- 檔案類型：編輯器可以載入多個檔案類型。 可用的命令可以根據檔案類型變更。

- 使用中視窗：最後一個使用中的文件視窗設定按鍵繫結的使用者介面 (UI) 內容。 不過，有一個索引鍵繫結資料表類似於內部網頁瀏覽器工具視窗也可以設定的 UI 內容。 針對多個索引標籤的文件視窗，例如 HTML 編輯器，每個索引標籤會有不同的命令內容的 GUID。 註冊工具視窗之後，其上都搭載**檢視**功能表。

- UI 內容：值來識別 UI 內容<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>類別，例如<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>建置解決方案時，或<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>當偵錯工具在作用中。 多個 UI 內容可同時處於作用中。

## <a name="define-custom-context-guids"></a>定義自訂內容的 Guid

如果未定義的 GUID 不適當的命令內容中，您可以定義在 VSPackage 中，並再進行程式設計，讓它成為作用中或非使用中，視需要控制可見性，您的命令：

1. 藉由呼叫註冊內容 Guid<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A>方法。

2. 取得 GUID 的內容的狀態，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>方法。

3. 藉由呼叫開啟內容的 Guid 和關閉<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A>方法。

> [!CAUTION]
> 請確定，VSPackage 不會影響任何現有內容的 Guid 因為其他 Vspackage 可能取決於它們。

## <a name="see-also"></a>另請參閱

- [選取內容物件](../../extensibility/internals/selection-context-objects.md)
- [Vspackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)