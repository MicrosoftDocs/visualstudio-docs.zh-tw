---
title: 功能區概觀
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c2d06098d1643f4c9b5e64206cdf94362a2c97b4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040142"
---
# <a name="ribbon-overview"></a>功能區概觀
  功能區是一種方式，使其更容易尋找到組織相關的命令。 命令會顯示為功能區上的控制項。 控制項分為*群組*沿著水平帶狀的應用程式視窗的頂端。 相關的群組會組織在索引標籤上。

 大部分的舊版 Microsoft Office system 中，使用功能表和工具列存取的功能現在可以存取使用功能區。 如需詳細資訊，請參閱技術文件[2007 Microsoft Office system 使用者介面的開發人員概觀](http://go.microsoft.com/fwlink/?LinkID=70860)。

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="customize-the-microsoft-office-ribbon"></a>自訂 Microsoft Office 功能區
 若要自訂功能區，請將其中一個下列功能區項目加入至 Office 專案中：

- **功能區 （視覺化設計工具）**

- **Ribbon (XML)**

  例如，若要自訂 Excel 功能區，請將功能區項目加入 Excel VSTO 增益集專案。

### <a name="ribbon-visual-designer-item"></a>功能區 （視覺化設計工具） 項目
 **功能區 （視覺化設計工具）** 項目提供進階的工具，可讓您更輕鬆地設計和開發自訂功能區。 使用**功能區 （視覺化設計工具）** 以下列方式自訂功能區項目：

- 加入功能區自訂或內建索引標籤。

- 將自訂群組加入自訂或內建的索引標籤。

  > [!NOTE]
  >  內建索引標籤或群組可以是現有的 Microsoft Office 應用程式功能區上的。 例如，**資料** 索引標籤是在 Excel 中的內建索引標籤。 **連線**群組上是內建群組**資料** 索引標籤。

- 將自訂控制項加入自訂群組。

- 將自訂控制項加入 Backstage 檢視。

  如需有關如何使用自訂功能區**功能區 （視覺化設計工具）** 項目，請參閱[功能區設計工具](../vsto/ribbon-designer.md)。

### <a name="ribbon-xml-item"></a>功能區 (XML) 項目
 使用**功能區 (XML)** 項目，如果您想要自訂功能區中不支援的方式**功能區 （視覺化設計工具）** 項目。 使用**功能區 (XML)** 以下列方式自訂功能區項目：

- 新增*內建*自訂索引標籤或內建索引標籤的群組。

- 將內建控制項加入自訂群組。

- 加入自訂程式碼來覆寫內建控制項的事件處理常式。

- 自訂快速存取工具列。

- 使用限定 ID 在 VSTO 增益集之間共用功能區自訂。

  如需有關如何使用自訂功能區**功能區 (XML)** 項目，請參閱[功能區 XML](../vsto/ribbon-xml.md)。

## <a name="export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>將功能區設計工具功能區匯出至功能區 XML
 如果您使用功能區設計工具中，建立功能區，然後決定您想要自訂功能區中的方法，**功能區 （視覺化設計工具）** 項目不支援，您可以將功能區匯出至 XML。

 Visual Studio 會自動建立**功能區 (XML)** 項目，並於其中填入在功能區上的每個控制項的功能區 XML 檔案項目和屬性。

 不是所有的內容中所**屬性**的功能區設計工具視窗都會傳送到功能區 XML 檔案。  例如，Visual Studio 不會匯出的值**映像**或是**文字**屬性。 這是因為您必須在已匯出專案的功能區程式碼檔中建立回呼方法，才能指派映像或設定控制項的文字。 Visual Studio 不會自動產生回呼方法作為匯出程序的一部分。

 此外，任何未經變更的預設屬性值都不會出現在產生的功能區 XML 檔案中。

 如需如何將功能區匯出到 XML 的詳細資訊，請參閱[How to:將功能區設計工具功能區匯出至功能區 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)。

### <a name="update-the-code"></a>更新程式碼
 新的功能區程式碼檔案加入至**方案總管 中**。 這個檔案包含功能區 XML 類別。 您必須在這個類別的 `Ribbon Callbacks` 區域中建立回呼方法以處理使用者動作，例如按一下某個按鈕。 從這些回呼方法的事件處理常式中移除您的程式碼，並修改程式碼以使用功能區擴充功能 (RibbonX) 程式設計模型。 如需詳細資訊，請參閱 [Ribbon XML](../vsto/ribbon-xml.md)。

 您也必須將程式碼加入會覆寫 `CreateRibbonExtensibilityObject` 方法，並將功能區 XML 類別傳回 Office 應用程式的 `ThisAddIn`、`ThisWorkbook` 或 `ThisDocument` 類別中。

 如需詳細資訊，請參閱 [Ribbon XML](../vsto/ribbon-xml.md)。

## <a name="add-multiple-ribbon-items-to-a-project"></a>將多個功能區項目加入至專案
 一個專案中可以加入多個功能區項目。 如果您想要執行下列兩項工作的其中之一，這會很有用：

- 建立 Outlook 功能區*偵測器*。 如需詳細資訊，請參閱 < [outlook 自訂功能區](../vsto/customizing-a-ribbon-for-outlook.md)。

    > [!NOTE]
    >  [偵測器] 是使用者執行特定工作時開啟的視窗，例如建立電子郵件訊息。

- 選取要顯示在執行階段的功能區。

### <a name="select-which-ribbons-to-display-at-runtime"></a>選取要在執行階段顯示哪個功能區
 因為專案可以包含多個功能區，您可以選取要顯示在執行階段的功能區。

 若要選取要顯示在執行階段的功能區，請覆寫`CreateRibbonExtensibilityObject`方法中的`ThisAddin`， `ThisWorkbook`，或`ThisDocument`的專案，然後傳回您想要顯示的功能區類別。 下列範例會檢查名為欄位的值`myCondition`，並傳回適當的功能區。

> [!NOTE]
>  在此範例中所用的語法會傳回一個功能區，利用所建立**功能區 （視覺化設計工具）** 項目。 傳回一個功能區，建立使用語法**功能區 (XML)** 項目會有些許不同。 如需有關傳回**功能區 (XML)** 項目，請參閱[功能區 XML](../vsto/ribbon-xml.md)。

 加入下列程式碼：

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.cs#1)]

### <a name="related-topics"></a>相關主題

|標題|說明|
|-----------|-----------------|
|[如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)|示範如何自訂 Microsoft Office 應用程式的功能區中，新增**功能區 （視覺化設計工具）** 或是**功能區 (XML)** 在 Office 專案的項目。|
|[功能區設計工具](../vsto/ribbon-designer.md)|說明如何使用功能區設計工具，以及在將自訂索引標籤、 群組和控制項新增至 Microsoft Office 應用程式的功能區。|
|[逐步解說：使用功能區設計工具建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|示範如何使用功能區設計工具建立自訂的功能區索引標籤。 您可以使用功能區設計工具，在自訂的索引標籤中加入和放置控制項。|
|[功能區物件模型概觀](../vsto/ribbon-object-model-overview.md)|提供可用來取得和設定功能區控制項的屬性，在執行階段的強類型的物件模型概觀。|
|[逐步解說：更新在執行階段的功能區上的控制項](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|示範如何使用功能區物件模型，在功能區載入至 Office 應用程式之後，更新功能區上的控制項。|
|[適用於 Outlook 自訂功能區](../vsto/customizing-a-ribbon-for-outlook.md)|提供自訂 Microsoft Office outlook 功能區的指引。|
|[自訂 infopath 的功能區](../vsto/customizing-a-ribbon-for-infopath.md)|提供自訂 Microsoft Office infopath 功能區的指引。|
|[在執行階段功能區的存取](../vsto/accessing-the-ribbon-at-run-time.md)|示範如何顯示、 隱藏，並修改功能區中，並讓使用者能夠從自訂工作窗格、 執行窗格或 Outlook 表單區域中的控制項執行程式碼。|
|[如何：變更功能區上的索引標籤的位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|示範如何變更功能區上的索引標籤的順序。|
|[如何：自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)|示範如何在內建索引標籤中加入群組和控制項。|
|[如何：將控制項加入至 Backstage 檢視](../vsto/how-to-add-controls-to-the-backstage-view.md)|示範如何將控制項新增至後按一下開啟功能表**檔案**。|
|[如何：在功能區群組中新增對話方塊啟動器](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|顯示功能區上的任何群組中加入對話方塊啟動程式。|
|[如何：將功能區設計工具功能區匯出至功能區 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|示範如何使用進階方式自訂功能區設計工具的功能區匯出至功能區 XML。|
|[Ribbon XML](../vsto/ribbon-xml.md)|說明如何使用功能區 XML 自訂功能區。|
|[逐步解說：使用功能區設計工具建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|示範如何藉由建立自訂功能區索引標籤**功能區 (XML)** 項目。|
