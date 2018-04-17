---
title: 功能區概觀 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, multiple Ribbons
- Ribbon [Office development in Visual Studio], about Ribbon
- toolbars [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], multiple Ribbons
- toolbars [Office development in Visual Studio]
- custom Ribbon, multiple Ribbons
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dcd53d1b5d38ff144536f0dea62e441cb2b23072
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ribbon-overview"></a>功能區概觀
  功能區可組織相關的命令，以便輕鬆找到它們。 命令會顯示為功能區上的控制項。 控制項會組織成*群組*沿著在應用程式視窗的頂端邊緣的水平區域。 相關的群組會組織在索引標籤上。  
  
 在較舊版本的 Microsoft Office 系統中，使用功能表和工具列存取的大多數功能，現在可以使用功能區來存取。 如需詳細資訊，請參閱技術文件[2007 Microsoft Office system 使用者介面的開發人員概觀](http://go.microsoft.com/fwlink/?LinkID=70860)。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="customizing-the-microsoft-office-ribbon"></a>自訂 Microsoft Office 功能區  
 若要自訂功能區，請在 Office 專案中加入下列功能區項目之一：  
  
-   **功能區 （視覺化設計工具）**  
  
-   **功能區 (XML)**  
  
 例如，若要自訂 Excel 功能區，請將功能區項目加入 Excel VSTO 增益集專案。  
  
### <a name="ribbon-visual-designer-item"></a>功能區 (視覺化設計工具) 項目  
 **功能區 （視覺化設計工具）**項目提供進階的工具，可讓您更輕鬆地設計和開發自訂功能區。 使用**功能區 （視覺化設計工具）**以下列方式自訂功能區項目：  
  
-   在功能區加入自訂或內建索引標籤。  
  
-   將自訂群組加入自訂或內建的索引標籤。  
  
    > [!NOTE]  
    >  內建的索引標籤或群組是已位在 Microsoft Office 應用程式功能區的索引標籤。 例如，**資料** 索引標籤是在 Excel 中的內建索引標籤。 **連線**群組是內建群組上**資料** 索引標籤。  
  
-   將自訂控制項加入自訂群組。  
  
-   將自訂控制項加入 Backstage 檢視。  
  
 如需有關如何使用自訂功能區**功能區 （視覺化設計工具）**項目，請參閱[功能區設計工具](../vsto/ribbon-designer.md)。  
  
### <a name="ribbon-xml-item"></a>功能區 (XML) 項目  
 使用**功能區 (XML)**項目，如果您想要自訂功能區中不支援的方式**功能區 （視覺化設計工具）**項目。 使用**功能區 (XML)**以下列方式自訂功能區項目：  
  
-   新增*內建*群組，以自訂索引標籤或內建索引標籤。  
  
-   將內建控制項加入自訂群組。  
  
-   加入自訂程式碼來覆寫內建控制項的事件處理常式。  
  
-   自訂快速存取工具列。  
  
-   使用限定 ID 在 VSTO 增益集之間共用功能區自訂。  
  
 如需有關如何使用自訂功能區**功能區 (XML)**項目，請參閱[功能區 XML](../vsto/ribbon-xml.md)。  
  
## <a name="exporting-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>將功能區設計工具的功能區匯出至功能區 XML  
 如果您使用功能區設計工具中，建立功能區，然後決定您想要自訂功能區的方式，**功能區 （視覺化設計工具）**項目不支援，您可以將功能區匯出至 XML。  
  
 Visual Studio 會自動建立**功能區 (XML)**項目，並於其中填入功能區上的每個控制項具有項目和屬性的功能區 XML 檔案。  
  
 並非所有屬性都在**屬性**功能區設計工具 視窗會傳送到功能區 XML 檔案。  例如，Visual Studio 不會匯出的值**映像**或**文字**屬性。 這是因為您必須在已匯出專案的功能區程式碼檔中建立回呼方法，才能指派映像或設定控制項的文字。 Visual Studio 不會自動產生回呼方法作為匯出程序的一部分。  
  
 此外，任何未經變更的預設屬性值都不會出現在產生的功能區 XML 檔案中。  
  
 如需如何將功能區匯出至 XML 的詳細資訊，請參閱[How to： 將功能區設計工具功能區匯出至功能區 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)。  
  
### <a name="updating-the-code"></a>更新程式碼  
 新的功能區程式碼檔案加入至**方案總管 中**。 這個檔案包含功能區 XML 類別。 您必須在這個類別的 `Ribbon Callbacks` 區域中建立回呼方法以處理使用者動作，例如按一下某個按鈕。 從這些回呼方法的事件處理常式中移除您的程式碼，並修改程式碼以使用功能區擴充功能 (RibbonX) 程式設計模型。 如需詳細資訊，請參閱 [Ribbon XML](../vsto/ribbon-xml.md)。  
  
 您也必須將程式碼加入`ThisAddIn`， `ThisWorkbook`，或`ThisDocument`類別，覆寫 CreateRibbonExtensibilityObject 方法，並在功能區 XML 類別傳回 Office 應用程式。  
  
 如需詳細資訊，請參閱 [Ribbon XML](../vsto/ribbon-xml.md)。  
  
## <a name="adding-multiple-ribbon-items-to-a-project"></a>在專案中加入多個功能區項目  
 一個專案中可以加入多個功能區項目。 如果您想要執行下列兩項工作的其中之一，這會很有用：  
  
-   建立 Outlook 的功能區*偵測器*。 如需詳細資訊，請參閱[自訂 Outlook 功能區](../vsto/customizing-a-ribbon-for-outlook.md)。  
  
    > [!NOTE]  
    >  [偵測器] 是使用者執行特定工作時開啟的視窗，例如建立電子郵件訊息。  
  
-   選取要在執行階段顯示的功能區。  
  
### <a name="selecting-which-ribbons-to-display-at-run-time"></a>選取要在執行階段顯示的功能區  
 因為一個專案可以包含多個功能區，所以您可以選取要在執行階段顯示的功能區。  
  
 若要選取要顯示在執行階段的功能區，覆寫中的 CreateRibbonExtensibilityObject 方法`ThisAddin`， `ThisWorkbook`，或`ThisDocument`您的專案，並將您想要顯示在功能區的類別。 下列範例會檢查名為 `myCondition` 之欄位的值，並傳回適當的功能區。  
  
> [!NOTE]  
>  此範例中使用的語法會傳回使用所建立的功能區**功能區 （視覺化設計工具）**項目。 傳回功能區所建立的使用語法**功能區 (XML)**項目會有些許不同。 如需有關傳回**功能區 (XML)**項目，請參閱[功能區 XML](../vsto/ribbon-xml.md)。  
  
 加入下列程式碼：  
  
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]  
  
### <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)|示範如何自訂 Microsoft Office 應用程式的功能區、 新增**功能區 （視覺化設計工具）**或**功能區 (XML)**項目加入 Office 專案。|  
|[功能區設計工具](../vsto/ribbon-designer.md)|說明如何使用功能區設計工具，在 Microsoft Office 應用程式的功能區中加入自訂的索引標籤、群組和控制項。|  
|[逐步解說：使用功能區設計工具建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|示範如何使用功能區設計工具建立自訂的功能區索引標籤。 您可以使用功能區設計工具，在自訂的索引標籤中加入和放置控制項。|  
|[功能區物件模型概觀](../vsto/ribbon-object-model-overview.md)|提供可在執行階段取得和設定功能區控制項屬性之強類型物件模型的概觀。|  
|[逐步解說：在執行階段更新功能區中的控制項](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|示範如何使用功能區物件模型，在功能區載入至 Office 應用程式之後，更新功能區上的控制項。|  
|[自訂 Outlook 的功能區](../vsto/customizing-a-ribbon-for-outlook.md)|提供自訂 Microsoft Office Outlook 功能區的指導。|  
|[自訂 InfoPath 的功能區](../vsto/customizing-a-ribbon-for-infopath.md)|提供自訂 Microsoft Office InfoPath 功能區的指導。|  
|[在執行階段存取功能區](../vsto/accessing-the-ribbon-at-run-time.md)|示範如何顯示、隱藏和修改功能區，並且讓使用者從自訂工作窗格、執行窗格或 Outlook 表單區域中的控制項執行程式碼。|  
|[如何：變更功能區索引標籤的位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|示範如何變更功能區上的索引標籤順序。|  
|[如何：自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)|示範如何在內建索引標籤中加入群組和控制項。|  
|[如何：將控制項新增至 Backstage 檢視](../vsto/how-to-add-controls-to-the-backstage-view.md)|示範如何將控制項加入至後按一下開啟功能表**檔案**。|  
|[如何：在功能區群組中新增對話方塊啟動器](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|示範在功能區的任一群組中加入對話方塊啟動程式。|  
|[如何：將功能區設計工具的功能區匯出至功能區 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|示範如何將設計工具的功能區匯出至功能區 XML，以使用進階方式自訂功能區。|  
|[功能區 XML](../vsto/ribbon-xml.md)|說明如何使用功能區 XML 自訂功能區。|  
|[逐步解說：使用功能區設計工具建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|示範如何建立自訂功能區索引標籤使用**功能區 (XML)**項目。|  
  
  