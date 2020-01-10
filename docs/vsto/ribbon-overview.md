---
title: 功能區總覽
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
ms.openlocfilehash: 668517705caa7ba6baef0b85305bf4470bc3b26b
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985604"
---
# <a name="ribbon-overview"></a>功能區總覽
  功能區是組織相關命令以方便尋找的方式。 命令會顯示為功能區上的控制項。 控制項會組織成*群組*，沿著應用程式視窗上邊緣的水準帶狀。 相關的群組會組織在索引標籤上。

 大部分使用舊版 Microsoft Office 系統中的功能表和工具列存取的功能，現在都可以使用功能區來存取。 如需詳細資訊，請參閱技術文章[開發人員概述 2007 Microsoft Office 系統的使用者介面](/previous-versions/office/developer/office-2007/aa338198(v=office.12))。

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="customize-the-microsoft-office-ribbon"></a>自訂 Microsoft Office 功能區
 若要自訂功能區，請將下列其中一個功能區專案加入至您的 Office 專案：

- **功能區（視覺化設計工具）**

- **功能區（XML）**

  例如，若要自訂 Excel 功能區，請將功能區項目加入 Excel VSTO 增益集專案。

### <a name="ribbon-visual-designer-item"></a>功能區（視覺化設計工具）專案
 [**功能區（視覺化設計工具）** ] 專案提供的先進工具，可讓您更輕鬆地設計和開發自訂功能區。 使用 [**功能區（視覺化設計工具）** ] 專案，以下列方式自訂功能區：

- 將自訂或內建索引標籤加入至功能區。

- 將自訂群組加入自訂或內建的索引標籤。

  > [!NOTE]
  > 內建索引標籤或群組是已存在於 Microsoft Office 應用程式功能區上的索引標籤。 例如，[**資料**] 索引標籤是 Excel 中的內建索引標籤。 [**連接**] 群組是 [**資料**] 索引標籤上的內建群組。

- 將自訂控制項加入自訂群組。

- 將自訂控制項加入 Backstage 檢視。

  如需如何使用 [**功能區（視覺化設計工具）** ] 專案自訂功能區的詳細資訊，請參閱[功能區設計](../vsto/ribbon-designer.md)工具。

### <a name="ribbon-xml-item"></a>功能區（XML）專案
 如果您想要以 [**功能區（視覺化設計工具）** ] 專案不支援的方式自訂功能區，請使用 [**功能區（XML）** ] 專案。 使用 [**功能區（XML）** ] 專案，以下列方式自訂功能區：

- 將*內建*組加入自訂索引標籤或內建索引標籤。

- 將內建控制項加入自訂群組。

- 加入自訂程式碼來覆寫內建控制項的事件處理常式。

- 自訂快速存取工具列。

- 使用限定 ID 在 VSTO 增益集之間共用功能區自訂。

  如需如何使用 [**功能區（XML）** ] 專案自訂功能區的詳細資訊，請參閱[功能區 XML](../vsto/ribbon-xml.md)。

## <a name="export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>從功能區設計工具將功能區匯出至功能區 XML
 如果您使用功能區設計工具建立功能區，然後決定要以 [**功能區（視覺化設計工具）** ] 專案不支援的方式自訂功能區，您可以將功能區匯出至 XML。

 Visual Studio 會自動建立 [**功能區（XML）** ] 專案，並在功能區 XML 檔案中填入功能區上每個控制項的元素和屬性。

 並非所有位於功能區設計工具的 [**屬性**] 視窗中的屬性都會傳送到功能區 XML 檔案。  例如，Visual Studio 不會匯出**Image**或**Text**屬性的值。 這是因為您必須在已匯出專案的功能區程式碼檔中建立回呼方法，才能指派映像或設定控制項的文字。 Visual Studio 不會自動產生回呼方法作為匯出程序的一部分。

 此外，任何未經變更的預設屬性值都不會出現在產生的功能區 XML 檔案中。

 如需如何將功能區匯出至 XML 的詳細資訊，請參閱如何：將功能區設計工具的[功能區匯出至功能區 xml](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)。

### <a name="update-the-code"></a>更新程式碼
 新的功能區程式碼檔案會加入至**方案總管**。 這個檔案包含功能區 XML 類別。 您必須在這個類別的 `Ribbon Callbacks` 區域中建立回呼方法以處理使用者動作，例如按一下某個按鈕。 從這些回呼方法的事件處理常式中移除您的程式碼，並修改程式碼以使用功能區擴充功能 (RibbonX) 程式設計模型。 如需詳細資訊，請參閱 [Ribbon XML](../vsto/ribbon-xml.md)。

 您也必須將程式碼加入會覆寫 `CreateRibbonExtensibilityObject` 方法，並將功能區 XML 類別傳回 Office 應用程式的 `ThisAddIn`、`ThisWorkbook` 或 `ThisDocument` 類別中。

 如需詳細資訊，請參閱 [Ribbon XML](../vsto/ribbon-xml.md)。

## <a name="add-multiple-ribbon-items-to-a-project"></a>將多個功能區專案加入至專案
 一個專案中可以加入多個功能區項目。 如果您想要執行下列兩項工作的其中之一，這會很有用：

- 建立 Outlook*檢查*器的功能區。 如需詳細資訊，請參閱[自訂 Outlook 的功能區](../vsto/customizing-a-ribbon-for-outlook.md)。

    > [!NOTE]
    > [偵測器] 是使用者執行特定工作時開啟的視窗，例如建立電子郵件訊息。

- 選取要在執行時間顯示的功能區。

### <a name="select-which-ribbons-to-display-at-run-time"></a>選取要在執行時間顯示的功能區
 因為專案可以包含一個以上的功能區，所以您可以選取要在執行時間顯示的功能區。

 若要選取要在執行時間顯示的功能區，請覆寫專案的 [`ThisAddin`]、[`ThisWorkbook`] 或 [`ThisDocument`] 類別中的 `CreateRibbonExtensibilityObject` 方法，然後傳回您要顯示的功能區。 下列範例會檢查名為 `myCondition` 之欄位的值，並傳回適當的功能區。

> [!NOTE]
> 這個範例中使用的語法會傳回使用 [**功能區（視覺化設計工具）** ] 專案所建立的功能區。 傳回使用 **[功能區（XML）** ] 專案所建立之功能區的語法稍有不同。 如需傳回 **[功能區（XML）** ] 專案的詳細資訊，請參閱[功能區 XML](../vsto/ribbon-xml.md)。

 加入下列程式碼：

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.cs#1)]

### <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)|示範如何自訂 Microsoft Office 應用程式的功能區，將 [**功能區（視覺化設計工具）** ] 或 **[功能區（XML）** ] 專案加入 Office 專案。|
|[功能區設計工具](../vsto/ribbon-designer.md)|描述如何使用功能區設計工具，將自訂索引標籤、群組和控制項加入至 Microsoft Office 應用程式的功能區。|
|[逐步解說：使用功能區設計工具建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|示範如何使用功能區設計工具建立自訂的功能區索引標籤。 您可以使用功能區設計工具，在自訂的索引標籤中加入和放置控制項。|
|[功能區物件模型總覽](../vsto/ribbon-object-model-overview.md)|提供可在執行階段取得和設定功能區控制項屬性之強類型物件模型的概觀。|
|[逐步解說：在執行時間更新功能區上的控制項](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|示範如何使用功能區物件模型，在功能區載入至 Office 應用程式之後，更新功能區上的控制項。|
|[自訂 Outlook 的功能區](../vsto/customizing-a-ribbon-for-outlook.md)|提供在 Microsoft Office Outlook 中自訂功能區的指引。|
|[自訂 InfoPath 的功能區](../vsto/customizing-a-ribbon-for-infopath.md)|提供在 Microsoft Office InfoPath 中自訂功能區的指引。|
|[在執行時間存取功能區](../vsto/accessing-the-ribbon-at-run-time.md)|示範如何顯示、隱藏和修改功能區，以及讓使用者從自訂工作窗格、執行窗格或 Outlook 表單區域中的控制項執行程式碼。|
|[如何：變更功能區上索引標籤的位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|顯示如何變更功能區上的索引標籤順序。|
|[如何：自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)|示範如何在內建索引標籤中加入群組和控制項。|
|[如何：將控制項加入至 Backstage 檢視](../vsto/how-to-add-controls-to-the-backstage-view.md)|顯示如何將控制項加入至按一下檔案時**開啟的功能表。**|
|[如何：在功能區群組中加入對話方塊啟動程式](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|顯示如何將對話方塊啟動器加入至功能區上的任何群組。|
|[如何：從功能區設計工具將功能區匯出至功能區 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|示範如何從設計工具將功能區匯出至功能區 XML，以在 advanced 的方式自訂功能區。|
|[功能區 XML](../vsto/ribbon-xml.md)|說明如何使用功能區 XML 自訂功能區。|
|[逐步解說：使用功能區設計工具建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|示範如何使用 [**功能區（XML）** ] 專案建立自訂功能區索引標籤。|
