---
title: 使用設計工具建立 SharePoint 的網頁元件
description: 在這個逐步解說中，使用 Visual Studio 中的 SharePoint 視覺 Web 元件專案範本，以視覺化方式建立網頁元件。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 066ae0ab9c23ebb1d55f6c0480d7aeed4255fb4f
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217732"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>逐步解說：使用設計工具建立 SharePoint 的網頁元件

如果您建立 SharePoint 網站的 web 元件，則您的使用者可以使用瀏覽器直接修改該網站中頁面的內容、外觀和行為。 本逐步解說將示範如何使用 Visual Studio 中的 SharePoint **視覺 Web 元件** 專案範本，以視覺化方式建立網頁元件。

您將建立的 web 元件會顯示每月行事曆視圖，以及網站上每個行事曆清單的核取方塊。 使用者可以選取核取方塊，以指定要包含在每月行事曆視圖中的行事曆清單。

本逐步解說將說明下列工作：

- 使用 **視覺網頁元件** 專案範本建立網頁元件。
- 使用 Visual Studio 中的 Visual Web Developer designer 來設計網頁元件。
- 加入程式碼來處理網頁元件上的控制項事件。
- 測試 SharePoint 中的網頁元件。

    > [!NOTE]
    > 您的電腦可能會為使用者介面的某些元素顯示不同的名稱或位置，以在下列指示中 Visual Studio。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件

您需要下列元件才能完成這個逐步解說：

- 支援的 Windows 和 SharePoint 版本。

## <a name="create-a-web-part-project"></a>建立 web 元件專案

首先，使用 [ **視覺 Web 元件** ] 專案範本建立 web 元件專案。

1. 首先 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，使用 [以 **系統管理員身分執行** ] 選項。

2. 在功能表列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]。

     [新增專案]  對話方塊隨即出現。

3. 在 [ **新增專案** ] 對話方塊的 [ **Visual c #** ] 或 [ **Visual Basic**] 底下，展開 [ **Office/SharePoint**]，然後選擇 [ **SharePoint 方案** ] 類別。

4. 在範本清單中，選擇 [ **SharePoint 2013-視覺 Web 元件** ] 範本，然後選擇 [ **確定]** 按鈕。

     [ **SharePoint 自訂] Wizard** 隨即出現。 您可以使用此嚮導來指定用來偵測專案的網站和方案的信任層級。

5. 在 [ **此 SharePoint 方案的信任層級為何？** ] 區段中，選擇 [ **部署為伺服器陣列方案** ] 選項按鈕。

6. 選擇 [ **完成]** 按鈕以接受預設的本機 SharePoint 網站。

## <a name="designing-the-web-part"></a>設計網頁元件

從 [ **工具箱** ] 將控制項加入至 Visual web Developer designer 的介面，以設計網頁元件。

1. 在 Visual Web Developer designer 上，選擇 [ **設計** ] 索引標籤以切換至設計檢視。

2. 在功能表列上，選擇 [ **View**  >  **工具箱**]。

3. 在 [**工具箱**] 的 [**標準**] 節點中，選擇 [ **CheckBoxList** ] 控制項，然後執行下列其中一個步驟：

    - 開啟 **CheckBoxList** 控制項的快捷方式功能表，選擇 [ **複製**]，開啟設計工具中第一行的快捷方式功能表，然後選擇 [ **貼** 上]。

    - 從 [工具箱] 拖曳 [ **CheckBoxList** ] 控制項，然後將控制項連接到設計 **工具** 中的第一行。

4. 重複上述步驟，但將按鈕移至設計工具的下一行。

5. 在設計工具中，選擇 [ **Button1** ] 按鈕。

6. 在功能表列上，選擇 [**視圖**  >  **屬性視窗]**。

     [屬性] 視窗隨即開啟。

7. 在按鈕的 [ **Text** ] 屬性中，輸入 **Update**。

## <a name="handling-the-events-of-controls-on-the-web-part"></a>處理網頁元件上的控制項事件

加入可讓使用者將行事曆新增至主要行事曆視圖的程式碼。

1. 請執行下列其中一組步驟：

   - 在設計工具中，按兩下 [ **更新** ] 按鈕。

   - 在 [**更新**] 按鈕的 [**屬性**] 視窗中，選擇 [**事件**] 按鈕。 在 [ **按一下** ] 屬性中，輸入 **Button1_Click**，然後選擇 enter 鍵。

     使用者控制項程式碼檔案會在程式碼編輯器中開啟，而 `Button1_Click` 事件處理常式會隨即出現。 稍後，您會將程式碼新增至此事件處理常式。

2. 將下列語句加入至使用者控制項程式碼檔案的頂端。

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet1":::

3. 將下列程式程式碼加入至 `VisualWebPart1` 類別。 此程式碼會宣告每月行事曆視圖控制項。

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet2":::

4. `Page_Load` `VisualWebPart1` 以下列程式碼取代類別的方法。 此程式碼會執行下列工作：

   - 將每月行事曆視圖加入使用者控制項。

   - 針對網站上的每個行事曆清單新增核取方塊。

   - 針對出現在行事曆視圖中的每個專案類型，指定範本。

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet3":::

5. `Button1_Click` `VisualWebPart1` 以下列程式碼取代類別的方法。 此程式碼會將每個所選行事曆的專案新增至主要行事曆視圖。

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet4":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet4":::

## <a name="test-the-web-part"></a>測試網頁元件

當您執行專案時，會開啟 SharePoint 網站。 網頁元件會自動加入至 SharePoint 中的 Web 元件庫。 若要測試此專案，您將執行下列工作：

- 將事件加入至兩個不同的行事曆清單中。
- 將 web 元件加入至 web 元件頁面。
- 指定要包含在每月行事曆視圖中的清單。

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>將事件加入至網站上的行事曆清單

1. 在 Visual Studio 中，選擇 **F5** 鍵。

     SharePoint 網站隨即開啟，而 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 快速啟動列會出現在頁面上。

2. 在快速啟動列的 [ **清單**] 底下，選擇 [行事 **曆** ] 連結。

     [行事 **曆** ] 頁面隨即出現。

     如果快速啟動列上沒有任何 [行事曆] 連結，請選擇 [ **網站內容** ] 連結。 如果 [網站內容] 頁面未顯示行事曆專案，請建立一個行事 **曆** 專案。

3. 在 [行事曆] 頁面上，選擇 [日]，然後選擇所選取日期的 [ **加入** ] 連結，以新增事件。

4. 在 [ **標題** ] 方塊中，于 **預設行事曆中輸入事件**，然後選擇 [ **儲存** ] 按鈕。

5. 選擇 [ **網站內容** ] 連結，然後選擇 [ **新增應用程式** ] 磚。

6. 在 [ **建立** ] 頁面上，選擇行事 **曆** 類型、為行事曆命名，然後選擇 [ **建立** ] 按鈕。

7. 將事件加入至新行事曆、將事件事件命名為 **自訂日曆**，然後選擇 [ **儲存** ] 按鈕。

### <a name="to-add-the-web-part-to-a-web-part-page"></a>將網頁元件新增至網頁元件頁面

1. 在 [ **網站內容** ] 頁面上，開啟 [ **網站頁面** ] 資料夾。

2. 在功能區上，選擇 [檔案] 索引標籤，開啟 [**新增****檔**] 功能表，然後選擇 [**網頁元件頁面**] 命令。

3. 在 [ **新增網頁元件** ] 頁面上，將頁面命名為 **SampleWebPartPage .aspx**，然後選擇 [ **建立** ] 按鈕。

     [網頁元件] 頁面隨即出現。

4. 在 [網頁元件] 頁面的上方區域中，選擇 [ **插入** ] 索引標籤，然後選擇 [ **web 元件** ] 按鈕。

5. 選擇 [ **自訂** ] 資料夾，選擇 [ **VisualWebPart1** ] 網頁元件，然後選擇 [ **加入** ] 按鈕。

     網頁元件會出現在頁面上。 網頁元件上會出現下列控制項：

    - 每月行事曆視圖。

    - [ **更新** ] 按鈕。

    - [行事 **曆** ] 核取方塊。

    - [ **自訂行事曆** ] 核取方塊。

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>指定要包含在每月行事曆視圖中的清單

在 web 元件中，指定您想要包含在每月行事曆視圖的行事曆，然後選擇 [ **更新** ] 按鈕。

您所指定所有行事曆中的事件都會出現在每月行事曆視圖中。

## <a name="see-also"></a>另請參閱

[建立 SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) 
 的網頁元件[如何：建立 SharePoint web 元件](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
[逐步解說：建立 SharePoint 的網頁元件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
