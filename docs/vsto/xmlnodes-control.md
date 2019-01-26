---
title: XMLNodes 控制項
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
ms.openlocfilehash: 2944627b66459afd96646f2c9cf6c2e72bfdd837
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870333"
---
# <a name="xmlnodes-control"></a>XMLNodes 控制項
  **重要**本主題有關 Microsoft Word 中設定的資訊是提供專門用於權益與使用個人和組織使用者位於外部皒玿璅其領域，或使用，或開發在執行的程式，第 2010 年 1 月 Microsoft 何時移除特定功能的實作之前由 Microsoft 所授權的 Microsoft Word 產品與自訂 XML 從 Microsoft Word。 有關 Microsoft Word 的這項資訊可能不會讀取或使用的個人或組織在美國或其區域使用，或開發在 2010 年 1 月 10 日之後由 Microsoft 所授權的 Microsoft Word 產品執行的程式;這些產品無法運作此日期之前的授權或購買，以在美國以外的使用授權的產品相同。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNodes>控制項是可公開事件對應的 XML 節點物件的集合。 <xref:Microsoft.Office.Tools.Word.XMLNodes>重複的結構描述項目對應到 Microsoft Office Word 文件時，才建立控制項。 如果重複的項目包含子項目，每一個子項目也會建立為<xref:Microsoft.Office.Tools.Word.XMLNodes>控制項。  
  
 Visual Studio 會建立 XML 節點的集合之後，您可以直接而不必周遊 Word 物件模型程式對控制項。 <xref:Microsoft.Office.Tools.Word.XMLNodes>可刪除控制項只能由從文件中移除的項目對應。  
  
> [!NOTE]  
>  如果您存取的子元素<xref:Microsoft.Office.Tools.Word.XMLNodes>透過控制<xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A>屬性，它會傳回<xref:Microsoft.Office.Interop.Word.XMLNode>物件而非<xref:Microsoft.Office.Tools.Word.XMLNode>控制項。 如需詳細資訊，請參閱 <<c0> [ 主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)。  
  
## <a name="bind-data-to-the-control"></a>將資料繫結至控制項  
 <xref:Microsoft.Office.Tools.Word.XMLNodes>控制項不支援資料繫結。 這是因為<xref:Microsoft.Office.Tools.Word.XMLNodes>控制項並沒有複雜資料繫結功能，而且不能代表簡單資料繫結重複資料。  
  
## <a name="formatting"></a>格式化  
 可以套用至文件中的文字的任何格式設定可以套用至<xref:Microsoft.Office.Tools.Word.XMLNodes>控制項。  
  
## <a name="events"></a>事件  
 事件可供<xref:Microsoft.Office.Tools.Word.XMLNodes>顯示的項目：  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>  
  
## <a name="compare-events"></a>比較事件  
 您可以擷取的事件，當使用者將他或她的特定內容中的資料指標<xref:Microsoft.Office.Tools.Word.XMLNodes>控制項。 例如，您可能會有<xref:Microsoft.Office.Tools.Word.XMLNodes>控制項，名為`Customer`具有子系<xref:Microsoft.Office.Tools.Word.XMLNodes>控制項，名為`Company`，和`Company`具有兩個子<xref:Microsoft.Office.Tools.Word.XMLNodes>控制項名為`CompanyName`和`CompanyRegion`，如下所示：  
  
```xml  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 如果您想要顯示在 [動作] 窗格上的控制項只要將游標移到`Company`節點，它應該是否重要的資料指標放在`CompanyName`或是`CompanyRegion`的內容中兩者都是因為`Company`。 在此情況下，您可以撰寫程式碼<xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>事件的`Company`。  
  
 在大部分情況下，當游標進入<xref:Microsoft.Office.Tools.Word.XMLNodes>控制項，同時<xref:Microsoft.Office.Tools.Word.XMLNodes.Select>和<xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>引發事件。 下表顯示這些事件之間的差異。  
  
|選取 [事件]|ContextEnter 事件|  
|------------------|------------------------|  
|將游標放置於其中的節點時，就會發生<xref:Microsoft.Office.Tools.Word.XMLNodes>集合。|將游標放置於其中一個節點或子代節點時，就會發生<xref:Microsoft.Office.Tools.Word.XMLNodes>集合，從節點內容以外的區域。 換句話說，它只變更時引發的內容，並可能產生多個巢狀<xref:Microsoft.Office.Tools.Word.XMLNodes>控制項。|  
  
 比方說，當您移動之外的資料指標`Customer`成`CompanyName`，則<xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>事件`Customer`， `Company`，和`CompanyName`會引發。 如果您再移動的資料指標`CompanyName`要`CompanyRegion`，則<xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>事件，僅適用於`CompanyRegion`引發，因為內容是相同`Company`和`Customer`。 您可以有多個`Company`文件中的節點。 如果您將從游標`CompanyName`節點的其中一個`Company`要`CompanyName`另一個節點`Company`，內容是相同的因此只<xref:Microsoft.Office.Tools.Word.XMLNodes.Select>就會引發事件。  
  
 相同的差異<xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>事件和<xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>事件。  
  
## <a name="see-also"></a>另請參閱  
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [使用擴充的物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNode 控制項](../vsto/xmlnode-control.md)   
 [如何：XMLNodes 控制項加入 Word 文件](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [如何：將結構描述對應至 Visual Studio 中的 Word 文件](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
