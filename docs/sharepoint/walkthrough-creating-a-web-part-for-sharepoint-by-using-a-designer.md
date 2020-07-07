---
title: 使用設計工具建立 SharePoint 的 web 元件
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 732bd9fe3d34a768e0c6f71315f212c49bdf02af
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016383"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>逐步解說：使用設計工具建立 SharePoint 的 web 元件

如果您建立 SharePoint 網站的 web 元件，您的使用者可以使用瀏覽器直接修改該網站中頁面的內容、外觀和行為。 本逐步解說將示範如何使用 Visual Studio 中的 SharePoint**視覺 Web 元件**專案範本，以視覺化方式建立 web 元件。

您將建立的 web 元件會顯示每月行事曆視圖，以及網站上每個行事曆清單的核取方塊。 使用者可以藉由選取核取方塊，指定要包含在每月行事曆視圖中的行事曆清單。

本逐步解說將說明下列工作：

- 使用 [**視覺 Web 元件**] 專案範本建立 web 元件。
- 在 Visual Studio 中使用 Visual Web Developer designer 設計 web 元件。
- 加入程式碼來處理 web 元件上控制項的事件。
- 在 SharePoint 中測試 web 元件。

    > [!NOTE]
    > 在下列指示中，您的電腦可能會針對使用者介面的某些元素顯示不同的名稱或位置，Visual Studio。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件

您需要下列元件才能完成這個逐步解說：

- 支援的 Windows 和 SharePoint 版本。

## <a name="create-a-web-part-project"></a>建立 web 元件專案

首先，使用 [**視覺 Web 元件**] 專案範本來建立 web 元件專案。

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用 [**以系統管理員身分執行**] 選項啟動。

2. 在功能表列上 **，選擇 [** 檔案] [新增] [  >  **New**  >  **專案**]。

     [新增專案]  對話方塊隨即出現。

3. 在 [**新增專案**] 對話方塊的 [ **Visual c #** ] 或 [ **Visual Basic**] 底下，展開 [ **Office/SharePoint**]，然後選擇 [ **SharePoint 方案**] 類別。

4. 在範本清單中，選擇 [ **SharePoint 2013-視覺化網頁元件**] 範本，然後選擇 [**確定]** 按鈕。

     [ **SharePoint 自訂嚮導]** 隨即出現。 藉由使用此嚮導，您可以指定您將用來對專案進行的網站和方案的信任層級進行程式。

5. 在 [**此 SharePoint 方案的信任層級為何？** ] 區段中，選擇 [**部署為伺服器陣列方案**] 選項按鈕。

6. 選擇 [**完成]** 按鈕以接受預設的本機 SharePoint 網站。

## <a name="designing-the-web-part"></a>設計 web 元件

將控制項從 [**工具箱**] 加入至 Visual web Developer 設計工具的介面，以設計 web 元件。

1. 在 Visual Web Developer 設計工具上，選擇 [**設計**] 索引標籤以切換至設計檢視。

2. 在功能表列上，選擇 [**視圖**] [  >  **工具箱**]。

3. 在 [**工具箱**] 的 [**標準**] 節點中，選擇 [ **CheckBoxList** ] 控制項，然後執行下列其中一個步驟：

    - 開啟**CheckBoxList**控制項的快捷方式功能表，選擇 [**複製**]，在設計工具中開啟第一行的快捷方式功能表，然後選擇 [**貼**上]。

    - 從 [工具箱] 拖曳 [ **CheckBoxList** ] 控制項，並將控制項連接到設計**工具**中的第一行。

4. 重複上一個步驟，但將按鈕移至設計工具的下一行。

5. 在設計工具中，選擇 [ **Button1** ] 按鈕。

6. 在功能表列上，選擇 [**視圖**  >  **屬性視窗]**。

     [屬性]**** 視窗隨即開啟。

7. 在按鈕的 [ **Text** ] 屬性中，輸入**Update**。

## <a name="handling-the-events-of-controls-on-the-web-part"></a>處理 web 元件上控制項的事件

新增可讓使用者將行事曆新增至主要行事曆視圖的程式碼。

1. 請執行下列其中一組步驟：

   - 在設計工具中，按兩下 [**更新**] 按鈕。

   - 在 [**更新**] 按鈕的 [**屬性**] 視窗中，選擇 [**事件**] 按鈕。 在 [ **Click** ] 屬性中，輸入**Button1_Click**，然後選擇 enter 鍵。

     使用者控制項程式碼檔案會在程式碼編輯器中開啟，而 `Button1_Click` 事件處理常式隨即出現。 稍後，您會將程式碼加入至這個事件處理常式。

2. 將下列語句加入至使用者控制項程式碼檔案的頂端。

     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

3. 將下列程式程式碼新增至 `VisualWebPart1` 類別。 此程式碼會宣告每月行事曆視圖控制項。

     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]

4. `Page_Load` `VisualWebPart1` 使用下列程式碼取代類別的方法。 此程式碼會執行下列工作：

   - 將每月行事曆視圖加入至使用者控制項。

   - 在網站上新增每個行事曆清單的核取方塊。

   - 針對出現在行事曆視圖中的每個專案類型，指定一個範本。

     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]

5. `Button1_Click` `VisualWebPart1` 使用下列程式碼取代類別的方法。 此程式碼會將每個所選行事曆的專案新增至主要行事曆視圖。

     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]

## <a name="test-the-web-part"></a>測試 web 元件

當您執行專案時，SharePoint 網站隨即開啟。 網頁元件會自動加入至 SharePoint 中的 Web 元件庫。 若要測試此專案，您將執行下列工作：

- 將事件新增至兩個個別行事曆清單中的每一個。
- 將網頁元件新增至 web 元件頁面。
- 指定要包含在每月行事曆視圖中的清單。

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>將事件新增至網站上的行事曆清單

1. 在 Visual Studio 中，選擇**F5**鍵。

     SharePoint 網站隨即開啟，而且 [ [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 快速啟動] 列會出現在頁面上。

2. 在 [快速啟動] 列的 [**清單**] 底下，選擇 [行事**曆**] 連結。

     [行事**曆**] 頁面隨即出現。

     如果 [快速啟動] 列上沒有出現行事曆連結，請選擇 [**網站內容**] 連結。 如果 [網站內容] 頁面未顯示行事**曆**專案，請建立一個。

3. 在 [行事曆] 頁面上，選擇 [日]，然後選擇所選日期的 [**加入**] 連結來加入事件。

4. 在 [**標題**] 方塊中，輸入**預設行事曆中**的 [事件]，然後選擇 [**儲存**] 按鈕。

5. 選擇 [**網站內容**] 連結，然後選擇 [**新增應用程式**] 磚。

6. 在 [**建立**] 頁面上，選擇行事**曆**類型、為行事曆命名，然後選擇 [**建立**] 按鈕。

7. 將事件新增至新的行事曆，在**自訂行事曆中**為事件事件命名，然後選擇 [**儲存**] 按鈕。

### <a name="to-add-the-web-part-to-a-web-part-page"></a>若要將 web 元件加入至 web 元件頁面

1. 在 [**網站內容**] 頁面上，開啟 [**網站頁面**] 資料夾。

2. 在功能區上，選擇 [**檔案] 索引**標籤，開啟 [**新增**檔] 功能表，然後選擇 [**網頁元件頁面**] 命令。

3. 在 [**新增網頁元件**] 頁面上，將頁面命名為**SampleWebPartPage**，然後選擇 [**建立**] 按鈕。

     [網頁元件] 頁面隨即出現。

4. 在 [網頁元件] 頁面的頂端區域中，選擇 [**插入**] 索引標籤，然後選擇 [ **web 元件**] 按鈕。

5. 選擇 [**自訂**] 資料夾，選擇 [ **visualwebpartproject1.visualwebpart1.visualwebpart1** ] 網頁元件，然後選擇 [**新增**] 按鈕。

     網頁元件會顯示在頁面上。 下列控制項會出現在 web 元件上：

    - 每月行事曆視圖。

    - [**更新**] 按鈕。

    - 行事**曆**核取方塊。

    - **自訂行事曆**核取方塊。

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>若要指定要包含在每月日曆視圖中的清單

在 web 元件中，指定您想要包含在每月行事曆視圖中的行事曆，然後選擇 [**更新**] 按鈕。

您所指定之所有行事曆中的事件都會出現在每月行事曆視圖中。

## <a name="see-also"></a>另請參閱

[建立 SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) 
 的 web 元件[如何：建立 SharePoint web 元件](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
[逐步解說：建立 SharePoint 的 web 元件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
