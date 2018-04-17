---
title: 逐步解說： 建立 sharepoint Web 組件，使用設計工具 |Microsoft 文件
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
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: edc9665882caae64e0548a00507022f32f3b2bd5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer"></a>逐步解說：使用設計工具建立 SharePoint 的 Web 組件

如果您建立 SharePoint 網站的 web 組件，您的使用者可以直接使用瀏覽器修改內容、 外觀和行為，該網站中的頁數。 本逐步解說會示範如何使用 SharePoint，以視覺化方式建立的 web 組件**視覺 Web 組件**Visual Studio 中的專案範本。

您將建立的 web 組件的網站上顯示每月的行事曆檢視並為每個行事曆清單 核取方塊。 使用者可以指定哪些行事曆列出要包含在每月的行事曆檢視中的核取方塊。

這個逐步解說將說明下列工作：

- 使用建立的 web 組件**視覺 Web 組件**專案範本。
- 使用 Visual Studio 中的 Visual Web Developer 設計工具設計的 web 組件。
- 加入程式碼來處理的 web 組件上的控制項事件。
- 在 SharePoint 中測試 web 組件。

    > [!NOTE]
    > 在下列指示您的電腦可能會顯示不同的名稱或位置 for Visual Studio 使用者介面的某些項目。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件

您需要下列元件才能完成此逐步解說：

- 支援的 Windows 版本和 SharePoint。 請參閱[開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。

## <a name="creating-a-web-part-project"></a>建立 web 組件專案

首先，建立使用的 web 組件專案**視覺 Web 組件**專案範本。

1. 啟動[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用**系統管理員身分執行**選項。

2. 在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。

     [ **新增專案** ] 對話方塊隨即出現。

3. 在**新專案**對話方塊之下**Visual C#**或**Visual Basic**，依序展開**Office/SharePoint**，然後選擇  **SharePoint 方案**類別目錄。

4. 在範本清單中，選擇  **SharePoint 2013-視覺 Web 組件**範本，然後選擇 **確定** 按鈕。

     **SharePoint 自訂精靈**隨即出現。 使用此精靈，您可以指定要用來偵錯專案和方案的信任層級的站台。

5. 在**此 SharePoint 方案的信任層級為何？**區段中，選擇**部署為伺服陣列方案**選項按鈕。

6. 選擇**完成** 按鈕，接受預設的本機 SharePoint 網站。

## <a name="designing-the-web-part"></a>設計網頁組件

將控制項從設計網頁組件**工具箱**Visual Web Developer 設計工具介面。

1. 在 Visual Web Developer 設計工具中，選擇 **設計**切換至 設計 檢視中的索引標籤。

2. 在功能表列上，依序選擇 [檢視] 和 [工具箱]。

3. 在**標準**節點**工具箱**，選擇**CheckBoxList**控制項，然後再執行下列步驟：

    - 開啟快顯功能表**CheckBoxList**控制項、 選擇 **複製**，在設計師中，開啟的第一行的捷徑功能表，然後選擇**貼上**。

    - 拖曳**CheckBoxList**控制項從**工具箱**，並將控制項連接至設計工具中的第一行。

4. 重複上述步驟，但將按鈕移至下一行的設計工具。

5. 在設計工具中，選擇 [ **Button1** ] 按鈕。

6. 在功能表列上選擇 [**檢視**，**屬性] 視窗**。

     **屬性**視窗隨即開啟。

7. 在**文字**按鈕的屬性中輸入**更新**。

## <a name="handling-the-events-of-controls-on-the-web-part"></a>處理 web 組件上的控制項的事件

加入程式碼，讓使用者新增至主要行事曆檢視行事曆。

1. 請執行下列其中一組步驟：

    - 在設計師中，按兩下**更新** 按鈕。

    - 在**屬性**視窗**更新**按鈕，選擇**事件** 按鈕。 在**按一下**屬性中，輸入**Button1_Click**，然後選擇 Enter 鍵。

     使用者控制項程式碼檔案會開啟在程式碼編輯器和`Button1_Click`事件處理常式隨即出現。 稍後，您會將程式碼加入此事件處理常式。

2. 加入使用者控制項程式碼檔案頂端加入下列陳述式。

     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

3. 加入下列一行程式碼`VisualWebPart1`類別。 此程式碼會宣告的每月的行事曆檢視控制項。

     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]

4. 取代`Page_Load`方法`VisualWebPart1`為下列程式碼的類別。 這個程式碼會執行下列工作：

    - 將每月的行事曆檢視加入至使用者控制項。

    - 新增站台上的核取方塊，為每個行事曆清單。

    - 行事曆 檢視中，指定每一種顯示的項目範本。

     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]

5. 取代`Button1_Click`方法`VisualWebPart1`為下列程式碼的類別。 此程式碼會從每個選取的行事曆項目加入主要行事曆檢視。

     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]

## <a name="testing-the-web-part"></a>測試 web 組件

當您執行專案時，會開啟 SharePoint 網站。 Web 組件會自動加入至 sharepoint 網頁組件庫。 若要測試此專案，您會執行下列工作：

- 將事件加入至每兩個不同的行事曆清單。
- 將 web 組件加入至網頁組件。
- 指定要包含在每月的行事曆檢視清單。

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>若要將事件新增至站台上的行事曆清單

1. 在 Visual Studio 中，選擇 F5 鍵。

     SharePoint 網站隨即開啟，而[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]快速啟動 列會出現在頁面上。

2. 在 [快速啟動] 工具列上底下**列出**，選擇**行事曆**連結。

     **行事曆**頁面隨即出現。

     如果您沒有行事曆] 連結出現在 [快速啟動] 列上，選擇 [**網站內容**連結。 如果沒有顯示 [站台內容] 頁面**行事曆**項目，請建立一個。

3. 在行事曆 頁面上，選擇一天、，然後選擇**新增**中選取的日期，若要加入事件的連結。

4. 在**標題**方塊中，輸入**中預設的行事曆事件**，然後選擇 [**儲存**] 按鈕。

5. 選擇**網站內容**連結，，然後選擇 **新增應用程式**磚。

6. 在**建立**頁面上，選擇**行事曆**類型、 命名行事曆，然後選擇**建立** 按鈕。

7. 中，將事件加入至新的行事曆事件**中自訂行事曆事件**，然後選擇 [**儲存**] 按鈕。

### <a name="to-add-the-web-part-to-a-web-part-page"></a>若要將 web 組件加入至網頁組件

1. 在**網站內容**頁面上，開啟**網站頁面**資料夾。

2. 在功能區中，選擇 **檔案**索引標籤上，開啟**新文件**功能表，然後選擇  **Web 組件頁面**命令。

3. 上**新增 Web 組件頁面**頁面上，將頁面**SampleWebPartPage.aspx**，然後選擇 [**建立**] 按鈕。

     Web 組件頁面隨即出現。

4. 在 網頁組件的最上層區域中，選擇 **插入**索引標籤，然後選擇  **Web 組件** 按鈕。

5. 選擇**自訂**資料夾中，選擇**VisualWebPart1** web 組件，，然後選擇 [**新增**] 按鈕。

     Web 組件會出現在頁面上。 下列控制項顯示 web 組件上：

    - 每月的行事曆檢視。

    - **更新** 按鈕。

    - A**行事曆**核取方塊。

    - A**自訂行事曆**核取方塊。

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>若要指定列出要包含在每月的行事曆檢視

在 web 組件中，指定您想要納入每月的行事曆檢視，然後選擇 [行事曆**更新**] 按鈕。

從您指定的所有行事曆事件會出現在每月的行事曆檢視。

## <a name="see-also"></a>另請參閱

[建立 SharePoint 的 Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)  
[如何：建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part.md)  
[如何：使用設計工具建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)  
[逐步解說：建立 SharePoint 的 Web 組件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
