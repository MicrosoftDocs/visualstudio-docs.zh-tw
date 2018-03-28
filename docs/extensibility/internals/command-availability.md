---
title: 命令可用性 |Microsoft 文件
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ee0f746b87fcc83e9967ea65be08b8f4b04f2e3f
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="command-availability"></a>命令可用性

Visual Studio 內容會決定可用的命令。 根據目前的專案、 目前的編輯器，會載入 Vspackage 和整合式的開發環境 (IDE) 的其他層面，可以變更內容。

## <a name="command-contexts"></a>命令的內容

在下列的命令內容是最常見的。

-   **IDE**永遠都可以使用 IDE 所提供的命令。

-   **VSPackage** Vspackage 可以定義命令時要顯示或隱藏。

-   **專案**專案命令只會出現目前選取的專案。

-   **編輯器**一次只能有一個編輯器可以為作用中。 使用命令的使用中的編輯器。 與語言服務密切編輯器。 語言服務必須處理它編輯器相關聯的內容中的命令。

-   **檔案類型**編輯器可以載入多個檔案類型。 可用的命令可以變更根據檔案類型。

-   **使用中視窗**最後一個使用中的文件視窗的索引鍵繫結設定的使用者介面 (UI) 的內容。 不過，有一個索引鍵繫結資料表，類似於內部的 Web 瀏覽器工具視窗也可以設定 UI 內容。 多個索引標籤的文件視窗 （例如 HTML 編輯器） 如每個索引標籤會有不同的命令內容 GUID。 註冊工具視窗之後，它位於一律**檢視**功能表。

-   **UI 內容**UI 內容的值來識別<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>類別，例如<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>建立方案時，或<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>當偵錯工具在作用中。 多個 UI 內容可以在相同的時間。

## <a name="defining-custom-context-guids"></a>定義自訂內容的 Guid

如果未定義的 GUID 不適當的命令內容中，您可以定義一個 VSPackage 中，然後再將它設為作用中或非使用中，視需要控制命令的可見性程式。

1.  藉由呼叫註冊內容 Guid<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A>方法。

2.  取得內容 GUID 的狀態，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>方法。

3.  藉由呼叫開啟及關閉開啟內容 Guid<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A>方法。

    > [!CAUTION]
    > 請確定，VSPackage 不會影響任何現有的內容中的 Guid 因為其他 Vspackage 可能會取決於它們。

## <a name="see-also"></a>另請參閱

- [選取內容物件](../../extensibility/internals/selection-context-objects.md)
- [VSPackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)