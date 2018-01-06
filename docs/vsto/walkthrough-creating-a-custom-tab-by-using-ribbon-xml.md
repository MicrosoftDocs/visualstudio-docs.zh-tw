---
title: "逐步解說： 使用功能區 XML 建立自訂索引標籤 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: f6391a01-df1a-4a0f-bfbb-a9526c73b2b3
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8933345017cef96c17ed69a42dc3e095fcf7c7ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-custom-tab-by-using-ribbon-xml"></a>GetCustomUI
  本逐步解說示範如何建立自訂功能區索引標籤使用**功能區 (XML)**項目。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   將按鈕加入**增益集** 索引標籤。**增益集** 索引標籤是功能區 XML 檔案中定義的預設索引標籤。  
  
-   使用上的按鈕自動化 Microsoft Office Word**增益集** 索引標籤。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="creating-the-project"></a>建立專案  
 第一步是建立 Word VSTO 增益集專案。 您稍後將會自訂**增益集**這份文件 索引標籤。  
  
#### <a name="to-create-a-new-project"></a>建立新的專案  
  
1.  建立**Word 增益集**名稱專案**MyRibbonAddIn**。  
  
     如需詳細資訊，請參閱 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]開啟**ThisAddIn.cs**或**ThisAddIn.vb**程式碼檔案並將**MyRibbonAddIn**專案加入**方案總管 中**。  
  
## <a name="creating-the-vsto-add-ins-tab"></a>建立 VSTO 增益集索引標籤  
 若要建立**增益集**索引標籤上，新增**功能區 (XML)**至您的專案項目。 稍後在本逐步解說中，您將會加入一些按鈕到此索引標籤中。  
  
#### <a name="to-create-the-add-ins-tab"></a>建立增益集索引標籤  
  
1.  在 [專案]  功能表中，按一下 [加入新項目] 。  
  
2.  在**加入新項目**對話方塊中，選取**功能區 (XML)**。  
  
3.  將新功能區的名稱變更為 **MyRibbon**，然後按一下 [加入] 。  
  
     **MyRibbon.cs**或**MyRibbon.vb**檔案隨即在設計工具中開啟。 名為 XML 檔案**MyRibbon.xml**也會加入至您的專案。  
  
4.  在**方案總管] 中**，以滑鼠右鍵按一下**ThisAddin.cs**或**ThisAddin.vb**，然後按一下 [**檢視程式碼**。  
  
5.  將下列程式碼加入 **ThisAddin** 類別中。 此程式碼會覆寫 CreateRibbonExtensibilityObject 方法，而此功能區 XML 類別傳回 Office 應用程式。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  在**方案總管 中**，以滑鼠右鍵按一下**MyRibbonAddIn**專案，然後按一下**建置**。 確認專案建置無誤。  
  
## <a name="adding-buttons-to-the-add-ins-tab"></a>將按鈕加入增益集索引標籤中  
 此 VSTO 增益集的目標在讓使用者能夠重複使用的文字與特定資料表，加入使用中的文件。 若要提供使用者介面，加入至兩個按鈕**增益集**藉由修改功能區 XML 檔案 索引標籤。 稍後在本逐步解說中，您將定義按鈕的回呼方法。 如需功能區 XML 檔案的詳細資訊，請參閱[功能區 XML](../vsto/ribbon-xml.md)。  
  
#### <a name="to-add-buttons-to-the-add-ins-tab"></a>將按鈕加入增益集索引標籤中  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下**MyRibbon.xml** ，然後按一下 [**開啟**。  
  
2.  取代內容 **索引標籤**具有下列 XML 項目。 這段 XML 會變更預設控制項群組的標籤**內容**，並將兩個新的按鈕標籤**插入文字**和**插入表格**。  
  
    ```  
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
  
## <a name="automating-the-document-by-using-the-buttons"></a>使用按鈕自動化文件  
 您必須新增`onAction`的回呼方法**插入文字**和**插入表格**執行動作，當使用者按一下這些按鈕。 如需功能區控制項回呼方法的詳細資訊，請參閱[功能區 XML](../vsto/ribbon-xml.md)。  
  
#### <a name="to-add-callback-methods-for-the-buttons"></a>加入按鈕的回呼方法  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下**MyRibbon.cs**或**MyRibbon.vb**，然後按一下 [**開啟**。  
  
2.  將下列程式碼加入至頂端**MyRibbon.cs**或**MyRibbon.vb**檔案。 此程式碼會建立為 <xref:Microsoft.Office.Interop.Word> 命名空間建立別名。  
  
     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]  
  
3.  將下列方法加入 `MyRibbon` 類別中。 這是回呼方法，以便**插入文字**將字串加入至資料指標的目前位置在使用中文件的按鈕。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]  
  
4.  將下列方法加入 `MyRibbon` 類別中。 這是回呼方法，以便**插入表格**將資料表加入至資料指標的目前位置在使用中文件的按鈕。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]  
  
## <a name="testing-the-vsto-add-in"></a>測試 VSTO 增益集  
 當您執行專案、 Word 開啟和名為 [] 索引標籤**增益集**會出現在功能區上。 按一下**插入文字**和**插入表格**按鈕**增益集**測試的程式碼 索引標籤。  
  
#### <a name="to-test-your-vsto-add-in"></a>測試 VSTO 增益集  
  
1.  請按 F5 執行您的專案。  
  
2.  確認**增益集** 索引標籤會顯示在功能區上。  
  
3.  按一下 [增益集]  索引標籤。  
  
4.  確認**內容**群組會顯示在功能區上。  
  
5.  按一下**插入文字**按鈕**內容**群組。  
  
     這會在文件目前的游標位置上加入字串。  
  
6.  按一下**插入表格**按鈕**內容**群組。  
  
     這會在文件目前的游標位置上加入表格。  
  
## <a name="next-steps"></a>後續步驟  
 您可以透過下列主題，進一步了解自訂 Office UI 的方式：  
  
-   自訂不同 Office 應用程式的功能區。 如需支援自訂功能區的應用程式的詳細資訊，請參閱[功能區概觀](../vsto/ribbon-overview.md)。  
  
-   使用功能區設計工具自訂 Office 應用程式的功能區。 如需詳細資訊，請參閱 [Ribbon Designer](../vsto/ribbon-designer.md)。  
  
-   建立自訂執行窗格。 如需詳細資訊，請參閱 [Actions Pane Overview](../vsto/actions-pane-overview.md)。  
  
-   使用 Outlook 表單區域自訂 Microsoft Office Outlook 的 UI。 如需詳細資訊，請參閱[逐步解說： 設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)。  
  
## <a name="see-also"></a>請參閱  
 [功能區概觀](../vsto/ribbon-overview.md)   
 [功能區 XML](../vsto/ribbon-xml.md)   
 [逐步解說：使用功能區設計工具建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  