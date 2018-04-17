---
title: 逐步解說： 建立 SharePoint Web 組件 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e0659c354980eb302beb903d0107024882c6b160
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-web-part-for-sharepoint"></a>逐步解說：建立 SharePoint 的 Web 組件

Web 組件可讓使用者直接使用瀏覽器中修改內容、 外觀和行為的 SharePoint 網站頁面。 本逐步解說會示範如何建立使用 Web 組件**Web 組件**Visual Studio 2010 中的項目範本。

Web 組件會顯示在資料方格中的員工。 使用者指定包含員工資料檔案的位置。 使用者也可以篩選資料格，讓清單只顯示員工經理。

這個逐步解說將說明下列工作：

- 使用 Visual Studio 中建立 Web 組件**Web 組件**項目範本。

- 建立屬性可以設定 Web 組件的使用者。 此屬性指定員工的資料檔案的位置。

- 呈現 Web 組件中的內容控制項加入網頁組件控制項集合。

- 建立新的功能表項目，稱為*動詞命令、*出現在轉譯的 Web 組件的動詞命令功能表中。 動詞命令可讓使用者修改 Web 組件中出現的資料。

- 在 SharePoint 中測試 Web 組件。

    > [!NOTE]
    > 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件

- 支援的 Microsoft Windows 和 SharePoint 版本。 如需詳細資訊，請參閱[開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。

- Visual Studio 2017 或版本的 Visual Studio Application Lifecycle Management (ALM)。

## <a name="creating-an-empty-sharepoint-project"></a>建立空白的 SharePoint 專案

首先，建立空白的 SharePoint 專案。 稍後，您會將 Web 組件加入專案使用**Web 組件**項目範本。

1. 啟動[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用**系統管理員身分執行**選項。

2. 在功能表列中，選擇 **檔案**，**新增**，**專案**。

3. 在**新專案**對話方塊方塊中，展開  **SharePoint**節點下的語言，您想要使用，然後選擇  **2010年**節點。

4. 在**範本** 窗格中，選擇**SharePoint 2010 專案**，然後選擇 **確定** 按鈕。

     **SharePoint 自訂精靈**隨即出現。 此精靈可讓您選取的網站，您將用於偵錯專案和方案的信任層級。

5. 選擇**部署為伺服陣列方案**選項按鈕，然後再選擇**完成** 按鈕，接受預設的本機 SharePoint 網站。

## <a name="adding-a-web-part-to-the-project"></a>將 Web 組件加入至專案

新增**Web 組件**項目加入專案。 **Web 組件**項目加入 Web 組件的程式碼檔案。 更新版本中，您會將程式碼加入至 Web 組件程式碼檔案，以呈現 Web 組件的內容。

1. 在功能表列上選擇 **專案**，**加入新項目**。

2. 在**加入新項目**對話方塊中，於**已安裝的範本** 窗格中，展開**SharePoint**  節點，然後選擇  **2010年**節點。

3. 在 SharePoint 範本清單中選擇**Web 組件**範本，然後選擇 [**新增**] 按鈕。

     **Web 組件**項目出現在**方案總管 中**。

## <a name="rendering-content-in-the-web-part"></a>呈現 Web 組件中的內容

您可以指定您想要出現在 Web 組件中加入 Web 組件類別的控制項集合的控制項。

1. 在**方案總管 中**，開啟 WebPart1.vb （在 Visual Basic) 或 WebPart1.cs （在 C# 中)。

     Web 組件程式碼檔案會開啟程式碼編輯器中。

2. Web 組件程式碼檔案頂端加入下列陳述式。

     [!code-csharp[SP_WebPart#1](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#1)]

3. 將下列程式碼加入 `WebPart1` 類別。 此程式碼會宣告下列欄位：

    - 若要顯示 Web 組件中的員工資料方格。

    - 用於篩選的資料格的控制項顯示的文字。

    - 會顯示錯誤，如果資料格無法顯示資料標籤。

    - 字串，包含員工資料檔案的路徑。

     [!code-csharp[SP_WebPart#2](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#2)]

4. 將下列程式碼加入 `WebPart1` 類別。 這個程式碼加入自訂屬性，名為`DataFilePath`Web 組件。 自訂屬性是可以在 SharePoint 中設定使用者的屬性。 這個屬性取得並設定用來填入資料格的 XML 資料檔案的位置。

     [!code-csharp[SP_WebPart#3](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#3)]

5. 以下列程式碼取代 `CreateChildControls` 方法。 這個程式碼會執行下列工作：

    - 上一個步驟中加入的資料格和您所宣告的標籤。

    - 將資料格繫結至 XML 檔案包含員工資料。

     [!code-csharp[SP_WebPart#4](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#4)]

6. 將下列方法加入 `WebPart1` 類別中。 這個程式碼會執行下列工作：

    - 呈現的 Web 組件的 Web 組件動詞命令功能表中建立會顯示的動詞命令。

    - 處理當使用者選擇動詞命令功能表中的動詞命令時所引發的事件。 此程式碼會篩選出現在資料方格中的員工清單。

     [!code-csharp[SP_WebPart#5](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#5)]

## <a name="testing-the-web-part"></a>測試 Web 組件

當您執行專案時，會開啟 SharePoint 網站。 Web 組件會自動加入至 sharepoint 網頁組件庫。 您可以將 Web 組件加入任何 Web 組件頁面。

1. 將下列 XML 貼到 [記事本] 檔案。 這個 XML 檔案包含會在 Web 組件中的範例資料。

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
        <employees xmlns="http://schemas.microsoft.com/vsto/samples">
           <employee>
               <name>David Hamilton</name>
               <hireDate>2001-05-11</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Karina Leal</name>
               <hireDate>1999-04-01</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Nancy Davolio</name>
               <hireDate>1992-05-01</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Steven Buchanan</name>
               <hireDate>1955-03-04</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Suyama Michael</name>
               <hireDate>1963-07-02</hireDate>
               <title>Sales Associate</title>
           </employee>
        </employees>
    ```

2. 在 記事本 功能表列上選擇 **檔案**，**存**。

3. 在**另存新檔**對話方塊中，於**存檔類型**清單中，選擇**所有檔案**。

4. 在**檔案名稱**方塊中，輸入**data.xml**。

5. 選擇任何資料夾使用**瀏覽資料夾**按鈕，然後再選擇**儲存** 按鈕。

6. 在 Visual Studio 中，選擇  **F5**索引鍵。

     開啟 SharePoint 網站。

7. 在**網站動作**功能表上，選擇**更多選項**。

8. 在**建立**頁面上，選擇**Web 組件頁面**類型，然後選擇**建立** 按鈕。

9. 在**新增 Web 組件頁面**頁面上，將頁面**SampleWebPartPage.aspx**，然後選擇 [**建立**] 按鈕。

     Web 組件頁面隨即出現。

10. 選取 Web 組件頁面上的任何區域。

11. 在頁面頂端，選擇 **插入**索引標籤，然後選擇  **Web 組件** 按鈕。

12. 在**類別** 窗格中，選擇**自訂**資料夾中，選擇**WebPart1** Web 組件，然後選擇 **新增** 按鈕。

     Web 組件會出現在頁面上。

## <a name="testing-the-custom-property"></a>測試的自訂屬性

若要填入資料格出現在 Web 組件中，指定包含每位員工的相關資料的 XML 檔案的路徑。

1. 選擇出現在 Web 組件中，右邊的箭號，然後選擇**編輯網頁組件**從出現的功能表。

     包含 Web 組件屬性 窗格會顯示在頁面的右邊。

2. 在窗格中，展開 [**其他**節點，輸入您稍早建立的 XML 檔案的路徑，選擇**套用**按鈕，然後再選擇**確定**] 按鈕。

     確認 Web 組件中出現的員工清單。

## <a name="testing-the-web-part-verb"></a>測試的 Web 組件動詞命令

顯示和隱藏按一下出現在 Web 組件動詞命令功能表中項目不是管理員的員工。

1. 選擇出現在 Web 組件中，右邊的箭號，然後選擇**只顯示經理**從出現的功能表。

     只有是經理的員工會出現在 Web 組件。

2. 再次選擇箭號，然後選擇 **顯示所有員工**從出現的功能表。

     所有員工會都出現在 Web 組件。

## <a name="see-also"></a>另請參閱

[建立 SharePoint 的 Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)  
[如何：建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part.md)  
[如何：使用設計工具建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)  
[逐步解說：使用設計工具建立 SharePoint 的 Web 組件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)