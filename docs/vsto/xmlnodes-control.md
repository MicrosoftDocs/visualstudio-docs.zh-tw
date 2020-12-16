---
title: XMLNodes 控制項
description: 瞭解 XMLNodes 控制項只會在重複的架構元素對應到 Microsoft Word 檔時建立。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, events
- XMLNodes control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cd82b4bac36d648bee3f6735cf844691ef6d58b2
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527847"
---
# <a name="xmlnodes-control"></a>XMLNodes 控制項
  **重要** 本主題中有關 Microsoft Word 的資訊，只會提供給位於美國以外的個人和組織，或使用或正在開發的 microsoft word 產品（在2010年1月之前由 Microsoft 授權的 microsoft Word 產品），而 Microsoft 已從 Microsoft Word 移除與自訂 XML 相關的特定功能。 這項有關 Microsoft Word 的資訊，可能無法由美國的個人或組織、在2010年1月10日之後由 Microsoft 授權的 Microsoft Word 產品所使用的 microsoft word 產品或開發人員所使用;這些產品的行為不像在該日期之前授權的產品，或購買並授權在美國以外地區使用。

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 <xref:Microsoft.Office.Tools.Word.XMLNodes>控制項是對應之 XML 節點物件的集合，這些物件會公開事件。 <xref:Microsoft.Office.Tools.Word.XMLNodes>只有在重複的架構專案對應到 Microsoft Office Word 檔時，才會建立控制項。 如果重複的元素包含子項目，則每個子專案也會建立為 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項。

 在 Visual Studio 建立 XML 節點的集合之後，您可以直接對控制項進行程式設計，而不需要跨越 Word 物件模型。 <xref:Microsoft.Office.Tools.Word.XMLNodes>只能藉由移除檔中的專案對應來刪除控制項。

> [!NOTE]
> 如果您透過屬性存取控制項的子項目 <xref:Microsoft.Office.Tools.Word.XMLNodes> <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> ，則會傳回 <xref:Microsoft.Office.Interop.Word.XMLNode> 物件，而不是 <xref:Microsoft.Office.Tools.Word.XMLNode> 控制項。 如需詳細資訊，請參閱 [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)。

## <a name="bind-data-to-the-control"></a>將資料系結至控制項
 <xref:Microsoft.Office.Tools.Word.XMLNodes>控制項不支援資料系結。 這是因為控制項沒有複雜的資料系結 <xref:Microsoft.Office.Tools.Word.XMLNodes> 功能，而且簡單的資料系結無法表示重複的資料。

## <a name="formatting"></a>格式化
 可以套用至檔內文字的任何格式設定都可以套用至 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項。

## <a name="events"></a>事件
 控制項可用的事件 <xref:Microsoft.Office.Tools.Word.XMLNodes> 包括：

- <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>

## <a name="compare-events"></a>比較事件
 當使用者在特定控制項的內容中移動其資料指標時，您可以捕獲事件 <xref:Microsoft.Office.Tools.Word.XMLNodes> 。 例如，您可能會有一個 <xref:Microsoft.Office.Tools.Word.XMLNodes> 名為 `Customer` 的控制項，該控制項具有 <xref:Microsoft.Office.Tools.Word.XMLNodes> 名為的子控制項 `Company` ，而且 `Company` 具有兩個 <xref:Microsoft.Office.Tools.Word.XMLNodes> 名為的子控制項 `CompanyName` `CompanyRegion` ，如下所示：

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 如果您想要在每次資料指標移至節點時，于 [動作] 窗格上顯示控制項，則資料 `Company` 指標是否放置於或都不重要， `CompanyName` `CompanyRegion` 因為它們都在的內容中 `Company` 。 在此情況下，您可以在事件中撰寫程式碼 <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> `Company` 。

 在大部分的情況下，當游標進入 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項時， <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> 會引發和事件。 下表顯示這些事件之間的差異。

|選取事件|CoNtextEnter 事件|
|------------------|------------------------|
|當游標放在 <xref:Microsoft.Office.Tools.Word.XMLNodes> 集合的其中一個節點時發生。|當游標從節點內容以外的區域，放到 <xref:Microsoft.Office.Tools.Word.XMLNodes> 集合的其中一個節點或子代 (Descendant) 節點時發生。 換句話說，只有在內容變更時才會引發，而且可以針對多個嵌套 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項引發。|

 例如，當您將資料指標從外部移至 `Customer` 時 `CompanyName` ， <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> `Customer` `Company` 會引發、和的事件 `CompanyName` 。 如果您將資料指標從移 `CompanyName` 至 `CompanyRegion` ，則 <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> 只 `CompanyRegion` 會引發的事件，因為和的內容相同 `Company` `Customer` 。 您可以 `Company` 在檔中擁有多個節點。 如果您將游標從 `CompanyName` 一個節點移 `Company` 至另一個節點 `CompanyName` `Company` ，則內容相同，因此只 <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> 會引發事件。

 事件與事件之間存在相同的差異 <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> 。

## <a name="see-also"></a>另請參閱
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
- [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)
- [XMLNode 控制項](../vsto/xmlnode-control.md)
- [如何：將 XMLNodes 控制項加入至 Word 檔](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [如何：將架構對應至 Visual Studio 內的 Word 檔](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
