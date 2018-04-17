---
title: XMLNode 控制項 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: b21f6f4e84672d195b6147f73c513c1995200a03
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="xmlnode-control"></a>XMLNode 控制項
  **重要**本主題有關 Microsoft Word 中設定的資訊是呈現專用的效益和使用個人和組織使用者位於美國和其領域之外或人員使用，或開發在執行的程式，已由 Microsoft 授權年 1 月 2010、 Microsoft 實作的特定功能中移除時之前的 Microsoft Word 產品與自訂 XML 從 Microsoft Word。 不能讀取或由個人或組織在美國或其領域人員使用，或是在開發已由 Microsoft 授權，2010 年 1 月 10 日之後的 Microsoft Word 產品執行的程式中使用這項資訊有關 Microsoft Word;這些產品無法運作此日期之前的授權或購買與授權在美國以外的產品相同。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode>控制項是可公開事件及可以繫結至資料的對應的 XML 節點物件。 <xref:Microsoft.Office.Tools.Word.XMLNode>非重複結構描述元素會對應到 Microsoft Office Word 文件時，才建立控制項。 Visual Studio 建立的 XML 節點之後，您可以針對它程式直接而不必周遊 Word 物件模型。  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode>可以刪除只是藉由在 Word 中移除的項目對應的控制項。  
  
## <a name="binding-data-to-the-control"></a>將資料繫結至控制項  
 <xref:Microsoft.Office.Tools.Word.XMLNode>控制項支援簡單資料繫結。 XML 節點應該繫結至資料來源使用<xref:System.Windows.Forms.IBindableComponent.DataBindings%2A>屬性。 如果更新繫結資料集中，<xref:Microsoft.Office.Tools.Word.XMLNode>控制項會反映這些變更。  
  
## <a name="formatting"></a>格式化  
 格式設定套用至<xref:Microsoft.Office.Interop.Word.XMLNode>物件可以套用至<xref:Microsoft.Office.Tools.Word.XMLNode>控制項。 這包括字型、 底線樣式和字元樣式。  
  
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
  
## <a name="comparing-events"></a>比較事件  
 您可以擷取的事件，當使用者將他或她的特定內容中的資料指標<xref:Microsoft.Office.Tools.Word.XMLNode>控制項。 例如，您可能會有<xref:Microsoft.Office.Tools.Word.XMLNode>控制項，名為`Customer`具有子系<xref:Microsoft.Office.Tools.Word.XMLNode>控制項，名為`Company`，和`Company`有兩個子<xref:Microsoft.Office.Tools.Word.XMLNode>控制項名為`CompanyName`和`CompanyRegion`，如下所示：  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 如果您想要顯示在 動作 窗格上的控制項只要將游標移到`Company` 節點，則應該是否將重要的資料指標會放在`CompanyName`或`CompanyRegion`兩者的內容中都因為`Company`。 在此情況下，您可以撰寫程式碼<xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>事件`Company`。  
  
 在大部分情況下，當游標進入<xref:Microsoft.Office.Tools.Word.XMLNode>控制兩者<xref:Microsoft.Office.Tools.Word.XMLNode.Select>和<xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>引發事件。 下表顯示這些事件之間的差異。  
  
|選取事件|ContextEnter 事件|  
|------------------|------------------------|  
|將游標放置於時，就會發生<xref:Microsoft.Office.Tools.Word.XMLNode>。|將游標放置於時，就會發生<xref:Microsoft.Office.Tools.Word.XMLNode>或其中一個下階的節點，從區域節點的內容之外。 換句話說，會引發此事件僅當內容變更時。|  
  
 例如，當您移動游標從外部`Customer`到`CompanyName`、<xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>事件`Customer`， `Company`，和`CompanyName`，就會引發。 如果您再移動的資料指標`CompanyName`至`CompanyRegion`，則只<xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>事件`CompanyRegion`因為您仍在兩者的內容就會引發`Company`和`Customer`。  
  
 相同的差異<xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>事件和<xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>事件。  
  
## <a name="see-also"></a>另請參閱  
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNodes 控制項](../vsto/xmlnodes-control.md)   
 [如何： 將 XMLNode 控制項加入 Word 文件](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [如何： 將結構描述對應至 Visual Studio 內的 Word 文件](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  