---
title: XMLNode 控制項
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f83d829ac5067d751cc035ac83c0fb3397178658
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927437"
---
# <a name="xmlnode-control"></a>XMLNode 控制項
  **重要**本主題有關 Microsoft Word 中設定的資訊是提供專門用於權益與使用個人和組織使用者位於外部皒玿璅其領域，或使用，或開發在執行的程式，第 2010 年 1 月 Microsoft 何時移除特定功能的實作之前由 Microsoft 所授權的 Microsoft Word 產品與自訂 XML 從 Microsoft Word。 有關 Microsoft Word 的這項資訊可能不會讀取或使用的個人或組織在美國或其區域使用，或開發在 2010 年 1 月 10 日之後由 Microsoft 所授權的 Microsoft Word 產品執行的程式;這些產品無法運作此日期之前的授權或購買，以在美國以外的使用授權的產品相同。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode>控制項是對應的 XML 節點物件，公開事件，並可以繫結至資料。 <xref:Microsoft.Office.Tools.Word.XMLNode>非重複的結構描述元素對應到 Microsoft Office Word 文件時，才建立控制項。 Visual Studio 建立的 XML 節點之後，您可以針對它進行程式設計直接而不必周遊 Word 物件模型。  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode>可刪除控制項只是藉由在 Word 中移除的項目對應。  
  
## <a name="bind-data-to-the-control"></a>將資料繫結至控制項  
 <xref:Microsoft.Office.Tools.Word.XMLNode>控制項支援簡單資料繫結。 XML 節點應該繫結至資料來源使用<xref:System.Windows.Forms.IBindableComponent.DataBindings%2A>屬性。 如果更新繫結資料集中的資料，則 <xref:Microsoft.Office.Tools.Word.XMLNode> 控制項會反映這些變更。  
  
## <a name="formatting"></a>格式化  
 格式設定套用至<xref:Microsoft.Office.Interop.Word.XMLNode>物件可以套用至<xref:Microsoft.Office.Tools.Word.XMLNode>控制項。 這包括字型、 底線樣式和字元的樣式。  
  
## <a name="events"></a>事件  
 下列事件適用於 <xref:Microsoft.Office.Tools.Word.XMLNode> 控制項：  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>  
  
## <a name="compare-events"></a>比較事件  
 您可以擷取的事件，當使用者將他或她的特定內容中的資料指標<xref:Microsoft.Office.Tools.Word.XMLNode>控制項。 例如，您可能會有<xref:Microsoft.Office.Tools.Word.XMLNode>控制項，名為`Customer`具有子系<xref:Microsoft.Office.Tools.Word.XMLNode>控制項，名為`Company`，和`Company`具有兩個子<xref:Microsoft.Office.Tools.Word.XMLNode>控制項名為`CompanyName`和`CompanyRegion`，如下所示：  
  
```xml  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 如果您想要顯示在 [動作] 窗格上的控制項只要將游標移到`Company`節點，它應該是否重要的資料指標放在`CompanyName`或是`CompanyRegion`的內容中兩者都是因為`Company`。 在此情況下，您可以撰寫程式碼<xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>事件的`Company`。  
  
 在大部分情況下，當游標進入<xref:Microsoft.Office.Tools.Word.XMLNode>控制項，同時<xref:Microsoft.Office.Tools.Word.XMLNode.Select>和<xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>引發事件。 下表顯示這些事件之間的差異。  
  
|選取事件|ContextEnter 事件|  
|------------------|------------------------|  
|發生於資料指標置於<xref:Microsoft.Office.Tools.Word.XMLNode>。|發生於資料指標置於<xref:Microsoft.Office.Tools.Word.XMLNode>或其中一個下階節點，從節點內容以外的區域。 換句話說，它只變更時引發的內容。|  
  
 比方說，當您移動之外的資料指標`Customer`成`CompanyName`，則<xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>事件`Customer`， `Company`，和`CompanyName`，就會引發。 如果您再移動的資料指標`CompanyName`要`CompanyRegion`，則只<xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>事件`CompanyRegion`因為這兩者的內容中，仍會引發`Company`和`Customer`。  
  
 相同的差異<xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>事件和<xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>事件。  
  
## <a name="see-also"></a>另請參閱  
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [使用擴充的物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNodes 控制項](../vsto/xmlnodes-control.md)   
 [如何：將 XMLNode 控制項加入 Word 文件](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [如何：將結構描述對應至 Visual Studio 中的 Word 文件](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
