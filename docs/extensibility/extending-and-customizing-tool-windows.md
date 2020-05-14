---
title: 擴展和自定義工具視窗 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 76c094ec73a69baa46a5e8313dd26febd57e5887
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711809"
---
# <a name="extend-and-customize-tool-windows"></a>擴充並自訂工具視窗
Visual Studio 提供了幾種不同類型的視窗,例如工具視窗、文檔視窗和對話框視窗。 其他視窗(如 **"屬性**"視窗 **、"輸出"** 視窗和**工作列表**視窗)是工具視窗的類型。

## <a name="tool-windows"></a>工具視窗
 可視化工作室工具視窗通常是不基於檔的唯讀視窗。 在這種情況下，它們與文件視窗不同，而文件視窗會以讀寫模式顯示檔案。 [工具箱] ****、 **方案總管**、[屬性] **** 視窗和 [網頁瀏覽器] **** 是工具視窗範例。

 要瞭解如何建立工具視窗,請參閱[新增工具視窗](../extensibility/adding-a-tool-window.md)。

 要向 Visual Studio 註冊工具視窗,請參閱[註冊工具視窗](../extensibility/registering-a-tool-window.md)。

 工具視窗預設是單一執行個體，這表示一次只能開啟工具視窗的一個執行個體。 單一執行個體工具視窗在開啟之後，除非關閉 IDE，否則仍然會持續開啟。 關閉單實例工具視窗時,只有其可見性會更改。 您也可以建立多執行個體工具視窗，這樣即可同時開啟視窗的多個執行個體。 關於詳細資訊[,請參閱建立多實體工具視窗](../extensibility/creating-a-multi-instance-tool-window.md)。

 工具視窗可以是*動態*的,這意味著每當應用相關的 UI 上下文時,它們都是可見的。 使用自動顯示可以減少 IDE 中視窗的雜亂。 有關詳細資訊,請參閱[開啟動態工具視窗](../extensibility/opening-a-dynamic-tool-window.md)。

 在文件框架中，可以停駐、浮動或標籤工具視窗。 工具視窗框架是由 IDE 所提供，並可用來控制大小、位置、停駐狀態和其他持續性屬性。 工具視窗窗格會顯示內容。 只有在第一次開啟工具視窗時，才會套用預設大小和位置；之後，就會持續保存工具視窗狀態。

 工具視窗窗格可以裝載 WPF 使用者控制項，並支援工具列。 您可以覆寫 <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> 屬性來傳回所裝載控制項的控制代碼。

 您可以將許多不同的功能添加到工具視窗。 例如, 您可以加入工具列:[將工具列加入工具視窗](../extensibility/adding-a-toolbar-to-a-tool-window.md)或快捷選單:[在工具視窗中加入快捷選單](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md)。 您可以新增搜尋控制項,允許您在工具視窗搜尋專案:[將搜尋到工具視窗](../extensibility/adding-search-to-a-tool-window.md)。

 您可以訂閱工具視窗事件:[訂閱事件](../extensibility/subscribing-to-an-event.md)。

## <a name="extend-existing-tool-windows"></a>延伸現有工具視窗
 您可以將有關工具視窗的資訊添加到新的 **「選項」** 頁和「**屬性**」 頁上的新設定,寫入**工作清單**和**輸出**視窗。 關於詳細資訊,請參閱[擴充屬性、工作清單、輸出和選項視窗](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)。

## <a name="modal-dialog-boxes"></a>模態對話框
 在 Visual Studio 擴充中,應透過派生<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>模式對話方塊來 創建它們,這允許您控制它們和 UI 的其餘部分。 關於詳細資訊,請參閱[建立及管理模式對話框](../extensibility/creating-and-managing-modal-dialog-boxes.md)。

## <a name="see-also"></a>另請參閱
- [使用工具視窗建立延伸](../extensibility/creating-an-extension-with-a-tool-window.md)
- [延伸項目](../extensibility/extending-projects.md)
- [擴充解決方案](../extensibility/extending-solutions.md)
