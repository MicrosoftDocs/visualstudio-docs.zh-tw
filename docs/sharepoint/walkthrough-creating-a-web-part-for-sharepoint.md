---
title: 逐步解說：建立 SharePoint 的網頁元件 |Microsoft Docs
description: 建立 SharePoint 的網頁元件。 Web 元件可讓使用者使用瀏覽器直接變更 SharePoint 網站頁面的內容、外觀和行為。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3e018085bd9900a9ee04f838b7c802afd2acc4fe
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217706"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint"></a>逐步解說：建立 SharePoint 的網頁元件

Web 組件可讓使用者使用瀏覽器直接修改 SharePoint 網站頁面的內容、外觀和行為。 本逐步解說將示範如何使用 Visual Studio 2010 中的 **Web 元件** 專案範本來建立網頁元件。

Web 元件會顯示資料方格中的員工。 使用者指定包含員工資料之檔案的位置。 使用者也可以篩選資料格，讓只有經理的員工出現在清單中。

本逐步解說將說明下列工作：

- 使用 Visual Studio **Web 元件** 專案範本建立網頁元件。

- 建立可由 Web 元件的使用者設定的屬性。 這個屬性會指定員工資料檔案的位置。

- 藉由將控制項加入至 Web 元件控制項集合，在 Web 元件中轉譯內容。

- 建立新的功能表項目（稱為 *動詞）* ，這會出現在轉譯的網頁元件的動詞功能表中。 動詞命令可讓使用者修改出現在 Web 元件中的資料。

- 測試 SharePoint 中的網頁元件。

    > [!NOTE]
    > 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件

- 支援的 Microsoft Windows 和 SharePoint 版本。

- Visual Studio 2017 或 Azure DevOps Services。

## <a name="create-an-empty-sharepoint-project"></a>建立空白的 SharePoint 專案

首先，建立空白的 SharePoint 專案。 稍後，您會使用 **Web 元件** 專案範本，將 web 元件加入至專案。

1. 首先 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，使用 [以 **系統管理員身分執行** ] 選項。

2. 在 [男性] 列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]。

3. 在 [ **新增專案** ] 對話方塊中，展開您要使用之語言底下的 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

4. 在 [ **範本** ] 窗格中，選擇 [ **SharePoint 2010 專案**]，然後選擇 [ **確定]** 按鈕。

     [ **SharePoint 自訂] Wizard** 隨即出現。 此嚮導可讓您選取要用來將專案和方案的信任層級進行偵測的網站。

5. 選擇 [ **部署為伺服器陣列方案** ] 選項按鈕，然後選擇 [ **完成]** 按鈕以接受預設的本機 SharePoint 網站。

## <a name="add-a-web-part-to-the-project"></a>將網頁元件新增至專案

將 **Web 元件** 專案加入至專案。 **Web 元件** 專案會加入 web 元件的程式碼檔案。 稍後，您會將程式碼加入至 Web 元件程式碼檔案，以轉譯網頁元件的內容。

1. 在功能表列上，選擇 [ **Project**  >  **加入新專案**]。

2. 在 [ **加入新專案** ] 對話方塊的 [ **已安裝的範本** ] 窗格中，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

3. 在 SharePoint 範本清單中，選擇 [ **Web 元件** ] 範本，然後選擇 [ **加入** ] 按鈕。

     **Web 元件** 專案隨即出現在 **方案總管** 中。

## <a name="rendering-content-in-the-web-part"></a>轉譯網頁元件中的內容

您可以藉由將控制項加入網頁元件類別的控制項集合，來指定要在 Web 元件中顯示哪些控制項。

1. 在 **方案總管** 中，以 c # (中的 Visual Basic) 或 *WebPart1* (開啟 *WebPart1。*

     Web 元件程式碼檔案會在程式碼編輯器中開啟。

2. 將下列指示詞加入至 Web 元件程式碼檔案的頂端。

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb" id="Snippet1":::

3. 將下列程式碼新增至 `WebPart1` 類別。 此程式碼會宣告下欄欄位：

   - 在 Web 元件中顯示員工的資料格。

   - 顯示在用來篩選資料方格之控制項上的文字。

   - 如果資料格無法顯示資料，則為顯示錯誤的標籤。

   - 字串，其中包含員工資料檔案的路徑。

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs" id="Snippet2":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb" id="Snippet2":::

4. 將下列程式碼新增至 `WebPart1` 類別。 此程式碼會將名為的自訂屬性加入 `DataFilePath` 至網頁元件。 自訂屬性是使用者可以在 SharePoint 中設定的屬性。 這個屬性會取得並設定用來填入資料方格的 XML 資料檔案位置。

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs" id="Snippet3":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb" id="Snippet3":::

5. 以下列程式碼取代 `CreateChildControls` 方法。 此程式碼會執行下列工作：

   - 加入您在上一個步驟中宣告的資料格和標籤。

   - 將資料格系結至包含員工資料的 XML 檔案。

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs" id="Snippet4":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb" id="Snippet4":::

6. 將下列方法新增至 `WebPart1` 類別。 此程式碼會執行下列工作：

   - 建立顯示在所轉譯網頁元件的網頁元件動詞功能表中的動詞命令。

   - 處理當使用者選擇動詞命令功能表中的動詞命令時所引發的事件。 此程式碼會篩選出現在資料方格中的員工清單。

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs" id="Snippet5":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb" id="Snippet5":::

## <a name="test-the-web-part"></a>測試網頁元件

當您執行專案時，會開啟 SharePoint 網站。 網頁元件會自動加入至 SharePoint 中的 Web 元件庫。 您可以將網頁元件新增至任何網頁元件頁面。

1. 將下列 XML 貼到 [記事本] 檔案中。 這個 XML 檔案包含將會出現在網頁元件中的範例資料。

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

2. 在 [記事本] 的功能表列上，**選擇 [** 檔案  >  **另存** 新檔]。

3. 在 [ **另存** 新檔] 對話方塊的 [ **存檔類型** ] 清單中，選擇 [ **所有** 檔案]。

4. 在 [ **檔案名** ] 方塊中，輸入 **data.xml**。

5. 使用 [ **流覽資料夾]** 按鈕選擇任何資料夾，然後選擇 [ **儲存** ] 按鈕。

6. 在 Visual Studio 中，選擇 **F5** 鍵。

     SharePoint 網站隨即開啟。

7. 在 [ **網站動作** ] 功能表上，選擇 [ **更多選項**]。

8. 在 [ **建立** ] 頁面中，選擇 [ **Web 元件] 頁面** 類型，然後選擇 [ **建立** ] 按鈕。

9. 在 [ **新增網頁元件** ] 頁面上，將頁面命名為 **SampleWebPartPage .aspx**，然後選擇 [ **建立** ] 按鈕。

     [網頁元件] 頁面隨即出現。

10. 在 [網頁元件] 頁面上選取任何區域。

11. 選擇頁面頂端的 [ **插入** ] 索引標籤，然後選擇 [ **Web 元件** ] 按鈕。

12. 在 [ **類別目錄** ] 窗格中，選擇 [ **自訂** ] 資料夾，選擇 [ **WebPart1** ] 網頁元件，然後選擇 [ **加入** ] 按鈕。

     網頁元件會出現在頁面上。

## <a name="test-the-custom-property"></a>測試自訂屬性

若要填入出現在 Web 元件中的資料格，請指定 XML 檔案的路徑，其中包含每個員工的相關資料。

1. 選擇出現在 Web 元件右邊的箭號，然後從出現的功能表中選擇 [ **編輯網頁元件** ]。

     包含 Web 元件屬性的窗格會顯示在頁面的右側。

2. 在窗格中，展開 [**其他**] 節點，輸入您稍早建立之 XML 檔案的路徑，選擇 [套用] 按鈕，然後選擇 [**確定]** **按鈕。**

     確認員工清單出現在 Web 元件中。

## <a name="test-the-web-part-verb"></a>測試網頁元件動詞

選取出現在 [網頁元件] 動詞功能表中的專案，以顯示和隱藏非管理員的員工。

1. 選擇出現在 Web 元件右邊的箭號，然後從出現的功能表中選擇 [ **僅顯示管理員** ]。

     只有經理的員工才會出現在網頁元件中。

2. 再次選擇箭號，然後從出現的功能表中選擇 [ **顯示所有員工** ]。

     所有員工都會出現在 Web 元件中。

## <a name="see-also"></a>另請參閱

[建立 SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) 
 的網頁元件[如何：建立 SharePoint web 元件](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
[如何：使用設計](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) 
 工具建立 SharePoint web 元件[逐步解說：使用設計工具建立 SharePoint 的網頁元件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
