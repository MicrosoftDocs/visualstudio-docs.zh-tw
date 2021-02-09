---
title: 逐步解說：使用功能區 XML 建立自訂索引標籤
description: 瞭解如何將按鈕新增至 [Add-Ins] 索引標籤，並使用功能區 (XML) 將 Microsoft Word 自動化。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- customizing the Ribbon, tabscustom Ribbon, tabs
- Ribbon [Office development in Visual Studio], XML
- XML [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Custom tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 569a3bea98095afebb243c521db02410879b0b59
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920361"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>逐步解說：使用功能區 XML 建立自訂索引標籤
  本逐步解說示範如何使用 **功能區 (XML)** 專案來建立自訂功能區索引標籤。

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 本逐步解說將說明下列工作：

- 將按鈕加入 [ **增益集** ] 索引標籤。[ **增益集** ] 索引標籤是在功能區 XML 檔案中定義的預設索引標籤。

- 使用 [ **增益集** ] 索引標籤上的按鈕自動化 Microsoft Office Word。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>建立專案
 第一步是建立 Word VSTO 增益集專案。 您稍後將自訂此檔的 [ **增益集** ] 索引標籤。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 建立名稱為 **MyRibbonAddIn** 的 **Word 增益集** 專案。

     如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 開啟 **ThisAddIn.cs** 或 **ThisAddIn .vb** 程式碼檔，並將 **MyRibbonAddIn** 專案新增至 **方案總管**。

## <a name="create-the-vsto-add-ins-tab"></a>[建立 VSTO 增益集] 索引標籤
 若要建立 [ **增益集** ] 索引標籤，請將 **功能區 (XML)** 專案加入至您的專案。 稍後在本逐步解說中，您將會加入一些按鈕到此索引標籤中。

### <a name="to-create-the-add-ins-tab"></a>若要建立增益集索引標籤

1. 在 [專案] 功能表上，按一下 [加入新項目]。

2. 在 [ **加入新專案** ] 對話方塊中，選取 [ **功能區 (XML)**。

3. 將新功能區的名稱變更為 **MyRibbon**，然後按一下 [加入] 。

     **MyRibbon.cs** 或 **myribbon.vb .vb** 檔案會在設計工具中開啟。 名為 **MyRibbon.xml** 的 XML 檔案也會加入至您的專案。

4. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **ThisAddin.cs** ] 或 [ **ThisAddin**]，然後按一下 [ **視圖程式碼**]。

5. 將下列程式碼加入 **ThisAddin** 類別中。 此程式碼會覆寫 `CreateRibbonExtensibilityObject` 方法，並將功能區 XML 類別傳回 Office 應用程式。

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6. 在 **方案總管** 中，以滑鼠右鍵按一下 **MyRibbonAddIn** 專案，然後按一下 [ **建立**]。 確認專案建置無誤。

## <a name="add-buttons-to-the-add-ins-tab"></a>將按鈕加入 [增益集] 索引標籤
 此 VSTO 增益集的目標在讓使用者能夠重複使用的文字與特定資料表，加入使用中的文件。 若要提供使用者介面，請修改功能區 XML 檔案，將兩個按鈕加入 [ **增益集** ] 索引標籤。 稍後在本逐步解說中，您將定義按鈕的回呼方法。 如需功能區 XML 檔案的詳細資訊，請參閱 [功能區 xml](../vsto/ribbon-xml.md)。

### <a name="to-add-buttons-to-the-add-ins-tab"></a>將按鈕加入 [增益集] 索引標籤

1. 在 **方案總管** 中，以滑鼠右鍵按一下 **MyRibbon.xml** ，然後按一下 [ **開啟**]。

2. 以下列 XML 取代 **tab** 元素的內容。 這個 XML 會將預設控制項群組的標籤變更為 [ **內容**]，並加入兩個新的按鈕，內含標籤 **插入文字** 和 **插入資料表**。

    ```xml
    <tab idMso="TabAddIns">
        <group id="ContentGroup" label="Content">
            <button id="textButton" label="Insert Text"
                 screentip="Text" onAction="OnTextButton"
                 supertip="Inserts text at the cursor location."/>
            <button id="tableButton" label="Insert Table"
                 screentip="Table" onAction="OnTableButton"
                 supertip="Inserts a table at the cursor location."/>
        </group>
    </tab>
    ```

## <a name="automate-the-document-by-using-the-buttons"></a>使用按鈕將檔自動化
 您必須加入 `onAction` [ **插入文字** ] 和 [ **插入表格** ] 按鈕的回呼方法，以便在使用者按一下動作時執行動作。 如需功能區控制項回呼方法的詳細資訊，請參閱 [功能區 XML](../vsto/ribbon-xml.md)。

### <a name="to-add-callback-methods-for-the-buttons"></a>加入按鈕的回呼方法

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **MyRibbon.cs** ] 或 [ **myribbon.vb**]，然後按一下 [ **開啟**]。

2. 將下列程式碼新增至 **MyRibbon.cs** 或 **myribbon.vb .vb** 檔案的頂端。 此程式碼會建立為 <xref:Microsoft.Office.Interop.Word> 命名空間建立別名。

     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]

3. 將下列方法新增至 `MyRibbon` 類別。 這是 [ **插入文字** ] 按鈕的回呼方法，會在目前游標位置的活動文檔中加入字串。

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]

4. 將下列方法新增至 `MyRibbon` 類別。 這是 [ **插入資料表** ] 按鈕的回呼方法，會在目前的資料指標位置，將資料表加入至使用中的檔。

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]

## <a name="testing-the-vsto-add-in"></a>測試 VSTO 增益集
 當您執行專案時，Word 會開啟，而且功能區上會出現名稱為 [ **增益集** ] 的索引標籤。 按一下 [**增益集**] 索引標籤上的 [**插入文字**] 及 [**插入表格**] 按鈕來測試程式碼。

### <a name="to-test-your-vsto-add-in"></a>測試 VSTO 增益集

1. 按 **F5** 執行您的專案。

2. 確認 [ **增益集** ] 索引標籤顯示在功能區上。

3. 按一下 [增益集]  索引標籤。

4. 確認可在功能區上看見 **內容** 群組。

5. 按一下 [**內容**] 群組中的 [**插入文字**] 按鈕。

     這會在文件目前的游標位置上加入字串。

6. 按一下 [**內容**] 群組中的 [**插入資料表**] 按鈕。

     這會在文件目前的游標位置上加入表格。

## <a name="next-steps"></a>下一步
 您可以透過下列主題，進一步了解自訂 Office UI 的方式：

- 自訂其他 Office 應用程式的功能區。 如需支援自訂功能區之應用程式的詳細資訊，請參閱 [功能區總覽](../vsto/ribbon-overview.md)。

- 使用功能區設計工具自訂 Office 應用程式的功能區。 如需詳細資訊，請參閱 [Ribbon Designer](../vsto/ribbon-designer.md)。

- 建立自訂執行窗格。 如需詳細資訊，請參閱執行 [窗格總覽](../vsto/actions-pane-overview.md)。

- 使用 Outlook 表單區域自訂 Microsoft Office Outlook 的 UI。 如需詳細資訊，請參閱 [逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)。

## <a name="see-also"></a>另請參閱
- [功能區總覽](../vsto/ribbon-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [逐步解說：使用功能區設計工具建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
