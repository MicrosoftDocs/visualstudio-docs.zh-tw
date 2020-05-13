---
title: IDE 中的選擇和貨幣 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f580b7c8e1651dcbcd053476ae756399a0ac3482
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705574"
---
# <a name="selection-and-currency-in-the-ide"></a>IDE 中的選取項目和貨幣
整合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]式開發環境 (IDE) 使用選擇*上下文*維護使用者當前選擇的物件的資訊。 使用選擇上下文,VSPackages 可透過兩種方式參與貨幣追蹤:

- 通過將有關 VSPackages 的貨幣資訊傳播到 IDE。

- 通過監視使用者當前在 IDE 中的活動選擇。

## <a name="selection-context"></a>選擇內容
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 全域追蹤其自己的全域選擇上下文物件中的 IDE 貨幣。 下表顯示了構成選擇上下文的元素。

|元素|描述|
|-------------|-----------------|
|目前層次結構|通常是當前專案;NULL 電流層次結構表示整個解決方案是最新的。|
|目前項目 ID|當前層次結構中的選定項;當項目視窗中有多個選擇時,可以有多個當前項。|
|目前`SelectionContainer`|保存屬性視窗應為其顯示屬性的一個或多個物件。|

 此外,環境維護兩個全域清單:

- 使用 UI 命令識別碼清單

- 目前活動元素類型的清單。

### <a name="window-types-and-selection"></a>視窗型態與選擇
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 將視窗組織成兩種常規類型:

- 層次結構類型視窗

- 框架視窗,如工具和文件視窗

  IDE 對這些窗口類型的不同跟蹤貨幣。

  最常見的項目類型視窗是 IDE 控制的解決方案資源管理員。 項目類型視窗追蹤全域選擇上下文的全域層次結構和 ItemID,該視窗依賴於使用者的選擇來確定當前層次結構。 對於項目類型視窗,環境提供全域服務<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>,VS包可以通過該服務監視打開元素的當前值。 環境中的屬性流覽由此全域服務驅動。

  另一方面,框架視窗使用框架視窗中的 DocObject 推送選擇上下文值(層次結構/ItemID/選擇容器三重奏)。 . 框架視窗為此使用服務<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>。 DocObject 只能推送選擇容器的值,從而使層次結構和 ItemID 的本地值保持不變,這是 MDI 子文檔的典型值。

### <a name="events-and-currency"></a>事件和貨幣
 可能發生兩種類型的事件,這些事件會影響環境的貨幣概念:

- 傳播到全域級別並更改視窗框架選擇上下文的事件。 此類事件的範例包括正在打開的 MDI 子視窗、正在打開的全域工具視窗或正在打開的項目類型工具視窗。

- 更改視窗框架選擇上下文中追蹤的元素的事件。 範例包括在 DocObject 中更改選擇或在專案類型視窗中更改選擇。

## <a name="see-also"></a>另請參閱
- [選取項目內容物件](../../extensibility/internals/selection-context-objects.md)
- [使用者的意見反應](../../extensibility/internals/feedback-to-the-user.md)
