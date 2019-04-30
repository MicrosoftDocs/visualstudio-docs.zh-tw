---
title: 逐步解說：建立 SharePoint Web 組件 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 622dfafbe16efee1e953fbc42bfa3b94cfa3cc58
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965267"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint"></a>逐步解說：建立 SharePoint web 組件

Web 組件可讓使用者能夠直接使用瀏覽器，以修改內容、 外觀及行為的 SharePoint 網站頁面。 本逐步解說會示範如何使用建立 Web 組件**Web 組件**Visual Studio 2010 中的項目範本。

Web 組件會顯示資料格線中的員工。 使用者指定的檔案，其中包含員工資料的位置。 使用者也可以使身為經理的員工出現在清單中只篩選資料格。

這個逐步解說將說明下列工作：

- 使用 Visual Studio 中建立 Web 組件**Web 組件**項目範本。

- 建立屬性，可以設定 Web 組件的使用者。 此屬性指定員工的資料檔案的位置。

- 呈現網頁組件的內容，將控制項加入至網頁組件控制項集合。

- 建立新的功能表項目，稱為*動詞*出現在轉譯的 Web 組件動詞命令功能表。 動詞命令可讓使用者修改所顯示 Web 組件中的資料。

- 在 SharePoint 中測試 Web 組件。

    > [!NOTE]
    > 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件

- 支援的 Microsoft Windows 和 SharePoint 版本。

- Visual Studio 2017 或 Azure 的 DevOps 服務。

## <a name="create-an-empty-sharepoint-project"></a>建立空的 SharePoint 專案

首先，建立空的 SharePoint 專案。 稍後，您會將網頁組件加入專案使用**Web 組件**項目範本。

1. 開始[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]利用**系統管理員身分執行**選項。

2. 在功能表列中，選擇**檔案** > **新增** > **專案**。

3. 在 **新的專案**對話方塊方塊中，展開**SharePoint**節點下的語言，您想要使用此項目，然後選擇  **2010年**節點。

4. 在 [**範本**] 窗格中，選擇**SharePoint 2010 專案**，然後選擇 [ **[確定]** ] 按鈕。

     **SharePoint 自訂精靈**隨即出現。 此精靈可讓您選取的網站，您將使用專案和方案的信任層級進行偵錯。

5. 選擇**部署為伺服陣列方案**選項按鈕，然後再選擇**完成** 按鈕，接受預設的本機 SharePoint 網站。

## <a name="add-a-web-part-to-the-project"></a>將 web 組件加入至專案

新增**Web 組件**項目加入專案。 **Web 組件**項目加入網頁組件的程式碼檔案。 稍後，您會在 Web 組件的程式碼檔案，來呈現網頁組件的內容中加入程式碼。

1. 在功能表列中，選擇 [專案] > [加入新項目]。

2. 中**加入新項目**對話方塊中，於**已安裝的範本**窗格中，展開**SharePoint** ] 節點，然後選擇 [ **2010年**節點。

3. 在 SharePoint 範本清單中，選擇**Web 組件**範本，然後選擇**新增** 按鈕。

     **Web 組件**項目出現在**方案總管 中**。

## <a name="rendering-content-in-the-web-part"></a>呈現在 web 組件的內容

您可以指定您想要將它們新增至網頁組件類別的 controls 集合出現在 網頁組件中的控制項。

1. 在 **方案總管**，開啟*WebPart1.vb* （在 Visual Basic) 或*WebPart1.cs* （在 C# 中)。

     Web 組件程式碼檔案會在 「 程式碼編輯器 」 中開啟。

2. Web 組件程式碼檔案頂端新增下列陳述式。

     [!code-csharp[SP_WebPart#1](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#1)]

3. 將下列程式碼加入 `WebPart1` 類別。 此程式碼會宣告下列欄位：

   - 資料格，以顯示 Web 組件中的員工。

   - 用來篩選資料格的控制項顯示的文字。

   - 會顯示錯誤，如果資料格無法顯示資料標籤。

   - 字串，包含員工資料檔案的路徑。

     [!code-csharp[SP_WebPart#2](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#2)]

4. 將下列程式碼加入 `WebPart1` 類別。 這個程式碼加入自訂屬性，名為`DataFilePath`Web 組件。 自訂屬性是可以由使用者在 SharePoint 中設定的屬性。 這個屬性會取得並設定用來填入資料格的 XML 資料檔的位置。

     [!code-csharp[SP_WebPart#3](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#3)]

5. 以下列程式碼取代 `CreateChildControls` 方法。 這個程式碼會執行下列工作：

   - 上一個步驟中，新增您所宣告的標籤與資料格。

   - 將資料格繫結至 XML 檔案，其中包含員工資料。

     [!code-csharp[SP_WebPart#4](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#4)]

6. 將下列方法加入 `WebPart1` 類別。 這個程式碼會執行下列工作：

   - 會出現的動詞命令建立 Web 組件動詞命令的功能表中呈現的網頁組件。

   - 處理當使用者選擇動詞命令功能表中的動詞命令時所引發的事件。 此程式碼來篩選出現在資料格中的員工清單。

     [!code-csharp[SP_WebPart#5](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#5)]

## <a name="test-the-web-part"></a>測試 web 組件

當您執行專案時，會開啟 SharePoint 網站。 Web 組件會自動加入至 sharepoint 網頁組件庫。 您可以將網頁組件，加入任何 Web 組件頁面。

1. 將下列 XML 程式碼貼到 [記事本] 檔案。 此 XML 檔案包含會出現在 網頁組件的範例資料。

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

2. 在記事本中，在功能表列上選擇**檔案** > **另存新檔**。

3. 在**另存新檔**對話方塊中，於**將儲存為類型**清單中，選擇**所有檔案**。

4. 在 **檔名**方塊中，輸入**data.xml**。

5. 使用選擇的任何資料夾**瀏覽資料夾**按鈕，然後再選擇**儲存** 按鈕。

6. 在 Visual Studio 中，選擇**F5**索引鍵。

     SharePoint 網站隨即開啟。

7. 在上**站台動作**功能表上，選擇**更多選項**。

8. 在 [**建立**頁面上，選擇**網頁組件頁面**類型，然後選擇**建立**] 按鈕。

9. 中**新的網頁組件**頁面上，將頁面**SampleWebPartPage.aspx**，然後選擇**建立** 按鈕。

     Web 組件頁面隨即出現。

10. 選取 [網頁組件] 頁面上的任何區域。

11. 在頁面頂端，選擇**插入**索引標籤，然後選擇**Web 組件** 按鈕。

12. 中**類別** 窗格中，選擇**自訂**資料夾中，選擇**WebPart1** Web 組件，然後選擇**新增**按鈕。

     Web 組件會出現在頁面上。

## <a name="test-the-custom-property"></a>測試的自訂屬性

若要填入資料格出現在 網頁組件中，指定包含每一位員工的相關資料的 XML 檔案的路徑。

1. 選擇出現在 網頁組件中，右邊的箭號，然後選擇**編輯網頁組件**從出現的功能表。

     其中包含 Web 組件的屬性會出現一個頁面的右邊。

2. 在窗格中，依序展開**其他**節點，輸入您稍早建立的 XML 檔案的路徑，並選擇**套用**按鈕，然後再選擇**確定** 按鈕。

     請確認員工清單隨即出現在 Web 組件。

## <a name="test-the-web-part-verb"></a>測試 web 組件動詞命令

顯示和隱藏按一下出現在 Web 組件動詞命令功能表中的項目不是經理的員工。

1. 選擇出現在 網頁組件中，右邊的箭號，然後選擇**只顯示經理**從出現的功能表。

     只有身為經理的員工出現在 網頁組件。

2. 再次選擇箭號，然後選擇**顯示所有員工**從出現的功能表。

     所有的員工出現在 網頁組件。

## <a name="see-also"></a>另請參閱

[建立 SharePoint web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)
[How to:建立 SharePoint web 組件](../sharepoint/how-to-create-a-sharepoint-web-part.md)
[How to:使用設計工具建立 SharePoint web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)
[逐步解說：使用設計工具建立 SharePoint web 組件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
