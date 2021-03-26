---
title: IDE 中的選取專案和貨幣 |Microsoft Docs
description: 瞭解 Vspackage 如何參與貨幣追蹤。 Visual Studio IDE 會使用選取內容來維護目前所選物件的相關資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0fb65a63b99f625f8d32af8436db753a0f17322e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080901"
---
# <a name="selection-and-currency-in-the-ide"></a>IDE 中的選取項目和貨幣
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式開發環境 (IDE) 使用選取內容來維護使用者目前選取之物件的相關資訊。 透過選取內容，Vspackage 可以透過兩種方式參與貨幣追蹤：

- 將 Vspackage 的相關貨幣資訊傳播至 IDE。

- 藉由監視使用者目前在 IDE 內的作用中選取專案。

## <a name="selection-context"></a>選取內容
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Ide 會在其專屬的全域選取內容物件中，全域追蹤 ide 的貨幣。 下表顯示組成選取內容的元素。

|元素|描述|
|-------------|-----------------|
|目前的階層|通常是目前的專案;Null 目前階層表示整個方案都是最新的。|
|目前的 ItemID|目前階層中選取的專案;當專案視窗中有多個選取專案時，可能會有多個目前的專案。|
|當前 `SelectionContainer`|保留一或多個屬性視窗應顯示內容的物件。|

 此外，環境還會維護兩個全域清單：

- 作用中 UI 命令識別碼的清單

- 目前作用中的元素類型清單。

### <a name="window-types-and-selection"></a>視窗類型和選取範圍
 IDE 會將 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 視窗組織成兩種一般類型：

- 階層-類型視窗

- 框架視窗，例如工具和文件視窗

  IDE 會針對每個視窗類型追蹤不同的貨幣。

  最常見的專案類型視窗是 [solution explorer]，IDE 會將它控制項。 專案類型視窗會追蹤全域選取內容的全域階層和 ItemID，而視窗則會依賴使用者的選取專案來決定目前的階層。 若為專案類型的視窗，環境會提供全域服務 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> ，vspackage 可以透過此服務監視 open 元素目前的值。 環境中的屬性流覽是由此全域服務所驅動。

  另一方面，框架視窗會使用框架視窗內的 DocObject，將 SelectionCoNtext 值推 (階層/ItemID/SelectionContainer 三個) 。 . 框架視窗會將服務用於 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 此用途。 DocObject 只能推送選取專案容器的值，讓階層和 ItemID 的區域值保持不變，如同一般適用于 MDI 子檔。

### <a name="events-and-currency"></a>事件和貨幣
 可能會發生兩種類型的事件，這會影響環境的貨幣概念：

- 傳播至全域層級並變更視窗框架選取內容的事件。 這類事件的範例包括開啟的 MDI 子視窗、開啟的全域工具視窗，或開啟的專案類型工具視窗。

- 變更在視窗框架選取內容中追蹤之元素的事件。 範例包括在 DocObject 中變更選取範圍，或變更專案類型視窗中的選取範圍。

## <a name="see-also"></a>另請參閱
- [選取項目內容物件](../../extensibility/internals/selection-context-objects.md)
- [使用者的意見反應](../../extensibility/internals/feedback-to-the-user.md)
