---
title: IDE 中的選取專案和貨幣 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: edff400420ca5f0c93e1df85fb9118eee6302d02
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723970"
---
# <a name="selection-and-currency-in-the-ide"></a>IDE 中的選取項目和貨幣
@No__t_0 的整合式開發環境（IDE）會使用*選取內容來*維護使用者目前選取之物件的相關資訊。 有了選取內容，Vspackage 可以透過兩種方式參與貨幣追蹤：

- 藉由將 Vspackage 的相關貨幣資訊傳播至 IDE。

- 藉由監視使用者目前在 IDE 中的作用中選取範圍。

## <a name="selection-context"></a>選取範圍內容
 @No__t_0 IDE 會在它自己的全域選取範圍內容物件中，以全域方式追蹤 IDE 貨幣。 下表顯示組成選取內容的元素。

|項目|描述|
|-------------|-----------------|
|目前階層|通常是目前的專案;Null 目前的階層表示整個方案是最新的。|
|目前的 ItemID|目前階層中選取的專案;當 [專案] 視窗中有多個選項時，可以有多個目前的專案。|
|目前的 `SelectionContainer`|保留一或多個屬性視窗應該顯示內容的物件。|

 此外，環境會維護兩個全域清單：

- 作用中 UI 命令識別碼的清單

- 目前使用中元素類型的清單。

### <a name="window-types-and-selection"></a>視窗類型和選取範圍
 @No__t_0 IDE 會將視窗組織成兩種一般類型：

- 階層-類型 windows

- 框架視窗，例如工具和文件視窗

  IDE 會以不同的方式追蹤每個視窗類型的貨幣。

  最常見的專案類型視窗是 IDE 所控制的 [方案瀏覽器]。 專案類型視窗會追蹤全域選取範圍內容的全域階層和 ItemID，而視窗會依賴使用者的選取專案來判斷目前的階層。 針對專案類型的 windows，環境會提供全域服務 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>，Vspackage 可以透過此監視 open 元素的目前值。 環境中的屬性流覽是由這個全域服務所驅動。

  另一方面，框架視窗會使用框架視窗內的 DocObject 來推送 SelectionCoNtext 值（階層/ItemID/SelectionContainer 三個）。 執行個體時提供 SQL Server 登入。 框架視窗會針對此目的使用服務 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>。 DocObject 只能推送選取容器的值，讓階層和 ItemID 的區域值保持不變，如同一般用於 MDI 子檔。

### <a name="events-and-currency"></a>活動和貨幣
 可能會發生兩種類型的事件，這會影響環境的貨幣概念：

- 傳播至全域層級並變更視窗框架選取內容的事件。 這類事件的範例包括開啟的 MDI 子視窗、開啟的全域工具視窗，或開啟的專案類型工具視窗。

- 變更視窗框架選取內容中追蹤之元素的事件。 範例包括變更 DocObject 內的選取範圍，或變更專案類型視窗中的選取範圍。

## <a name="see-also"></a>請參閱
- [選取內容物件](../../extensibility/internals/selection-context-objects.md)
- [使用者的意見反應](../../extensibility/internals/feedback-to-the-user.md)