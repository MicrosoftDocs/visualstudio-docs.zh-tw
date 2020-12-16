---
title: XMLNode 控制項
description: 瞭解 XMLNode 控制項是一個對應的 XML 節點物件，它會公開事件並可系結至資料。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 58f9c5db883f55c00236bc202797dcf2ec3003f6
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528337"
---
# <a name="xmlnode-control"></a>XMLNode 控制項
  **重要** 本主題中有關 Microsoft Word 的資訊，只會提供給位於美國以外的個人和組織，或使用或正在開發的 microsoft word 產品（在2010年1月之前由 Microsoft 授權的 microsoft Word 產品），而 Microsoft 已從 Microsoft Word 移除與自訂 XML 相關的特定功能。 這項有關 Microsoft Word 的資訊，可能無法由美國的個人或組織、在2010年1月10日之後由 Microsoft 授權的 Microsoft Word 產品所使用的 microsoft word 產品或開發人員所使用;這些產品的行為不像在該日期之前授權的產品，或購買並授權在美國以外地區使用。

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 <xref:Microsoft.Office.Tools.Word.XMLNode>控制項是一個對應的 XML 節點物件，它會公開事件並可系結至資料。 <xref:Microsoft.Office.Tools.Word.XMLNode>只有當非重複的架構元素對應到 Microsoft Office Word 檔時，才會建立控制項。 Visual Studio 建立 XML 節點之後，您可以直接對其進行程式設計，而不需要跨越 Word 物件模型。

 <xref:Microsoft.Office.Tools.Word.XMLNode>只能藉由移除 Word 中的元素對應來刪除控制項。

## <a name="bind-data-to-the-control"></a>將資料系結至控制項
 <xref:Microsoft.Office.Tools.Word.XMLNode>控制項支援簡單的資料系結。 XML 節點應使用屬性系結至資料來源 <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> 。 如果更新繫結資料集中的資料，則 <xref:Microsoft.Office.Tools.Word.XMLNode> 控制項會反映這些變更。

## <a name="formatting"></a>格式化
 可以套用至物件的格式 <xref:Microsoft.Office.Interop.Word.XMLNode> 可以套用至 <xref:Microsoft.Office.Tools.Word.XMLNode> 控制項。 這包括字型、底線樣式和字元樣式。

## <a name="events"></a>事件
 下列事件適用於 <xref:Microsoft.Office.Tools.Word.XMLNode> 控制項：

- <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>

## <a name="compare-events"></a>比較事件
 當使用者在特定控制項的內容中移動其資料指標時，您可以捕獲事件 <xref:Microsoft.Office.Tools.Word.XMLNode> 。 例如，您可能會有一個 <xref:Microsoft.Office.Tools.Word.XMLNode> 名為 `Customer` 的控制項，該控制項具有 <xref:Microsoft.Office.Tools.Word.XMLNode> 名為的子控制項 `Company` ，而且 `Company` 具有兩個 <xref:Microsoft.Office.Tools.Word.XMLNode> 名為的子控制項 `CompanyName` `CompanyRegion` ，如下所示：

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 如果您想要在每次資料指標移至節點時，于 [動作] 窗格上顯示控制項，則資料 `Company` 指標是否放置於或都不重要， `CompanyName` `CompanyRegion` 因為它們都在的內容中 `Company` 。 在此情況下，您可以在事件中撰寫程式碼 <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> `Company` 。

 在大部分的情況下，當游標進入 <xref:Microsoft.Office.Tools.Word.XMLNode> 控制項時， <xref:Microsoft.Office.Tools.Word.XMLNode.Select> <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> 會引發和事件。 下表顯示這些事件之間的差異。

|選取事件|CoNtextEnter 事件|
|------------------|------------------------|
|發生于將游標置於內時 <xref:Microsoft.Office.Tools.Word.XMLNode> 。|當游標從節點內容以外的區域，放到 <xref:Microsoft.Office.Tools.Word.XMLNode> 或其中一個子代節點時發生。 換句話說，只有在內容變更時才會引發。|

 例如，當您將資料指標從外部移至 `Customer` 時 `CompanyName` ， <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> `Customer` `Company` 會引發、和的事件 `CompanyName` 。 如果您接著將資料指標從移 `CompanyName` 至 `CompanyRegion` ，則只會引發的 <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> 事件， `CompanyRegion` 因為您仍在和的內容 `Company` 中 `Customer` 。

 事件和事件之間存在相同的差異 <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> 。

## <a name="see-also"></a>另請參閱
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
- [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)
- [XMLNodes 控制項](../vsto/xmlnodes-control.md)
- [如何：將 XMLNode 控制項新增至 Word 檔](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [如何：將架構對應至 Visual Studio 內的 Word 檔](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
