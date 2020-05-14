---
title: 視覺工作室的交互模式 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac917aeb2530570b755e7f1e6fc6de00714a54b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698367"
---
# <a name="interaction-patterns-for-visual-studio"></a>適用於 Visual Studio 的互動模式
## <a name="overview"></a>概觀
 通常,設計模式是設計的核心,可用於特定情況,以解決具有類似約束集的問題。 功能和系統設計人員使用這些設計模式作為起點,然後可以根據具體情況進行調整。

 Visual Studio 具有一個常見交互模式庫,在構建新功能時應考慮這些模式。 我們的設計模式有兩個核心上下文:視覺工作室用戶端 (devenv) 和可視化工作室在線。 對於某些設計問題,有一種無處不在的模式,在所有情況下都效果很好。 但是,在許多情況下,對於在瀏覽器中顯示的 UI 和託管在用戶端應用程式上的 UI,解決方案可能有所不同。

### <a name="visual-studio-client-pattern-types"></a>視覺化工作室客戶端模式類型

|模式類型|描述|範例|
|------------------|-----------------|--------------|
|**應用程式級模式**|應用程式共有的進階模式,確定或顯示應用程式上下文,並在其中包含複合和控制模式|- 工具視窗<br />- 文件視窗|
|**複合模式**|跨應用程式模式的常見模式,或由不同配置中的多個控制元件組成的識別模式|- 查看切換<br />- 清單產生器<br />- 顯示資料<br />- 通知<br />- 驗證<br />- 選擇模型|
|**控制模式**|關於低級控制項預期如何操作的具體細節|- 樹狀圖<br />- 在格線控制器編輯|

## <a name="application-patterns"></a>應用程式模式
 在高級別上,Visual Studio 介面包含單個 IDE 中的多個視窗、對話框、命令和工具列。 Visual Studio 層次結構確定上下文並驅動功能表。 IDE 使用者介面中的關鍵整合點是文件視窗、工具視窗、專案、命令結構、文本編輯器、工具箱、屬性視窗和工具>選項。

 IDE 使用者介面中的每個關鍵整合點都有基本使用模式:

- [適用於 Visual Studio 的功能表和命令](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [適用於 Visual Studio 的應用程式模式](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [窗互](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [工具視窗](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [文件編輯器約定](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [對話方塊](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [專案](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>常見的控制模式
 控制模式主要涉及單個控件的可預期方式。 這是一致性最關鍵的一個領域。

 可視化工作室中最常見的控制項應遵循桌面 Windows 指南。 我們的指南僅包括我們需要通過 Visual Studio 特定交互來增強常見約定的領域,或者我們完全取代準則的位置,以便定製 Visual Studio 以滿足我們老練使用者的需求。

- [適用於 Visual Studio 的通用控制項模式](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [通用控制項](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [文字控制項](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [按鈕與超連結](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>複合模式
 使用者期望通過多種方式完成任務。 在可能的情況下,應設計要素以將這些模式用於交互和可視化設計。

 雖然 Visual Studio 中有許多複合模式,但有關一致性的一些最重要的模式是:

- [適用於 Visual Studio 的複合模式](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [物件 UI 和窺視](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [選擇模型](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [持久性和儲存設定](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [觸控輸入](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
