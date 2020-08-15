---
title: 逐步解說：建立 SharePoint 的 Web 元件 |Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7fe560ae0c639ec8c400719738ea1f52b5315a9a
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2020
ms.locfileid: "88247647"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint"></a>逐步解說：建立 SharePoint 的 web 元件

Web 組件可讓使用者使用瀏覽器直接修改 SharePoint 網站頁面的內容、外觀和行為。 本逐步解說會示範如何使用 Visual Studio 2010 中的 **Web 元件** 專案範本來建立 web 元件。

Web 元件會在資料方格中顯示員工。 使用者會指定包含員工資料之檔案的位置。 使用者也可以篩選資料方格，讓經理的員工只能出現在清單中。

本逐步解說將說明下列工作：

- 使用 Visual Studio **Web 元件** 專案範本建立 Web 元件。

- 建立可由 Web 元件的使用者設定的屬性。 這個屬性會指定員工資料檔案的位置。

- 藉由將控制項加入至 Web 元件控制項集合，在 Web 元件中轉譯內容。

- 建立新的功能表項目，稱為 *動詞，* 它會出現在轉譯的 Web 元件的動詞功能表中。 動詞可讓使用者修改 Web 元件中顯示的資料。

- 在 SharePoint 中測試 Web 元件。

    > [!NOTE]
    > 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>先決條件

- 支援的 Microsoft Windows 和 SharePoint 版本。

- Visual Studio 2017 或 Azure DevOps Services。

## <a name="create-an-empty-sharepoint-project"></a>建立空白的 SharePoint 專案

首先，建立空白的 SharePoint 專案。 稍後，您會使用 **Web 元件** 專案範本，將 web 元件新增至專案。

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用 [**以系統管理員身分執行**] 選項啟動。

2. 在 [男] 列上 **，選擇 [** 檔案] [  >  **新增**  >  **專案**]。

3. 在 [ **新增專案** ] 對話方塊中，展開您要使用之語言下的 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

4. 在 [ **範本** ] 窗格中，選擇 [ **SharePoint 2010 專案**]，然後選擇 [ **確定]** 按鈕。

     [ **SharePoint 自訂嚮導]** 隨即出現。 此嚮導可讓您選取要用來對專案進行的網站和方案的信任層級的建立。

5. 選擇 [ **部署為數組方案** ] 選項按鈕，然後選擇 [ **完成]** 按鈕以接受預設的本機 SharePoint 網站。

## <a name="add-a-web-part-to-the-project"></a>將 web 元件新增至專案

將 **Web 元件** 專案新增至專案。 **Web 元件**專案會加入 web 元件程式碼檔案。 稍後，您會將程式碼新增至 Web 元件程式碼檔案，以呈現 Web 元件的內容。

1. 在功能表列上，選擇 [**專案**] [  >  **加入新專案**]。

2. 在 [ **加入新專案** ] 對話方塊的 [ **已安裝的範本** ] 窗格中，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

3. 在 SharePoint 範本清單中，選擇 [ **Web 元件** ] 範本，然後選擇 [ **新增** ] 按鈕。

     **Web 元件**專案會出現在**方案總管**中。

## <a name="rendering-content-in-the-web-part"></a>呈現 web 元件中的內容

您可以藉由將控制項新增至 Web 元件類別的 controls 集合，指定要在 Web 元件中顯示的控制項。

1. 在**方案總管**中，以 c # (中的 Visual Basic) 或*WebPart1.cs* ) 開啟*WebPart1 (。*

     Web 元件程式碼檔案會在程式碼編輯器中開啟。

2. 將下列指示詞新增至 Web 元件程式碼檔案的頂端。

     [!code-csharp[SP_WebPart#1](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#1)]

3. 將下列程式碼新增至 `WebPart1` 類別。 此程式碼會宣告下欄欄位：

   - 用來在 Web 元件中顯示員工的資料格。

   - 出現在控制項上的文字，用來篩選資料方格。

   - 標籤，如果資料格無法顯示資料，則會顯示錯誤。

   - 字串，其中包含員工資料檔案的路徑。

     [!code-csharp[SP_WebPart#2](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#2)]

4. 將下列程式碼新增至 `WebPart1` 類別。 此程式碼會將名為的自訂屬性新增 `DataFilePath` 至 Web 元件。 自訂屬性是可由使用者在 SharePoint 中設定的屬性。 這個屬性會取得和設定用來填入資料方格之 XML 資料檔的位置。

     [!code-csharp[SP_WebPart#3](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#3)]

5. 以下列程式碼取代 `CreateChildControls` 方法。 此程式碼會執行下列工作：

   - 加入您在上一個步驟中所宣告的資料格和標籤。

   - 將資料格系結至包含員工資料的 XML 檔案。

     [!code-csharp[SP_WebPart#4](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#4)]

6. 將下列方法新增至 `WebPart1` 類別。 此程式碼會執行下列工作：

   - 建立會出現在所呈現 Web 元件之 Web 元件動詞功能表中的動詞。

   - 處理當使用者選擇動詞命令功能表中的動詞命令時所引發的事件。 這段程式碼會篩選出現在資料方格中的員工清單。

     [!code-csharp[SP_WebPart#5](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#5)]

## <a name="test-the-web-part"></a>測試 web 元件

當您執行專案時，SharePoint 網站隨即開啟。 網頁元件會自動加入至 SharePoint 中的 Web 元件庫。 您可以將網頁元件新增至任何 Web 元件頁面。

1. 將下列 XML 貼入 [記事本] 檔案。 這個 XML 檔案包含將會出現在 Web 元件中的範例資料。

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

2. 在 [記事本] 的功能表列上，**選擇 [檔案] [**  >  **另存**新檔]。

3. 在 [ **另存** 新檔] 對話方塊的 [ **存檔類型** ] 清單中，選擇 [ **所有**檔案]。

4. 在 [ **檔案名** ] 方塊中，輸入 **data.xml**。

5. 使用 [ **流覽資料夾]** 按鈕選擇任何資料夾，然後選擇 [ **儲存** ] 按鈕。

6. 在 Visual Studio 中，選擇 **F5** 鍵。

     SharePoint 網站隨即開啟。

7. 在 [ **網站動作** ] 功能表上，選擇 [ **更多選項**]。

8. 在 [ **建立** ] 頁面中，選擇 [ **Web 元件] 頁面** 類型，然後選擇 [ **建立** ] 按鈕。

9. 在 [ **新增網頁元件** ] 頁面中，將頁面命名為 **SampleWebPartPage**，然後選擇 [ **建立** ] 按鈕。

     [網頁元件] 頁面隨即出現。

10. 在 [網頁元件] 頁面上選取任何區域。

11. 在頁面頂端，選擇 [ **插入** ] 索引標籤，然後選擇 [ **Web 元件** ] 按鈕。

12. 在 [ **類別** ] 窗格中，選擇 [ **自訂** ] 資料夾，選擇 [ **WebPart1** ] 網頁元件，然後選擇 [ **新增** ] 按鈕。

     網頁元件會顯示在頁面上。

## <a name="test-the-custom-property"></a>測試自訂屬性

若要填入出現在 Web 元件中的資料格，請指定包含每個員工相關資料的 XML 檔案路徑。

1. 選擇出現在 Web 元件右側的箭號，然後從出現的功能表中選擇 [ **編輯網頁元件** ]。

     包含 Web 元件屬性的窗格會出現在頁面的右側。

2. 在窗格中，展開 [**其他**] 節點，輸入您稍早建立之 XML 檔案的路徑，選擇 [套用] 按鈕，然後選擇 [**確定]** **按鈕。**

     確認員工清單出現在 Web 元件中。

## <a name="test-the-web-part-verb"></a>測試 web 元件動詞

藉由選取出現在 Web 元件動詞功能表中的專案，顯示和隱藏非管理員的員工。

1. 選擇出現在 Web 元件右側的箭號，然後從出現的功能表中選擇 [ **僅顯示經理** ]。

     只有經理的員工才會出現在 Web 元件中。

2. 再次選擇箭號，然後從出現的功能表中選擇 [ **顯示所有員工** ]。

     所有員工都會出現在 Web 元件中。

## <a name="see-also"></a>另請參閱

[建立 SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) 
 的 web 元件[如何：建立 SharePoint web 元件](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
[如何：使用設計](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) 
 工具建立 SharePoint web 元件[逐步解說：使用設計工具建立 SharePoint 的 web 元件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
