---
title: 逐步解說：使用設計工具建立 SharePoint Web 組件 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 4a22d814ce50dea1ee67ed3bf1f071839e60a797
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56607015"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>逐步解說：使用設計工具建立 SharePoint web 組件

如果您建立 SharePoint 網站的 web 組件時，您的使用者可以直接使用瀏覽器修改內容、 外觀及行為，該網站中的頁數。 本逐步解說會示範如何使用 SharePoint，以視覺化方式建立的 web 組件**視覺化網頁組件**Visual Studio 中的專案範本。

您將建立的 web 組件的網站上顯示月份的行事曆檢視並為每個行事曆清單 核取方塊。 使用者可以指定的行事曆清單包含每月的行事曆檢視中，選取核取方塊。

這個逐步解說將說明下列工作：

- 使用建立 web 組件**視覺化網頁組件**專案範本。
- 在 Visual Studio 中使用 Visual Web Developer 設計工具設計 web 組件。
- 加入程式碼來處理 web 組件上控制項的事件。
- 在 SharePoint 中測試 web 組件。

    > [!NOTE]
    > 您的電腦可能會顯示不同的名稱或位置的使用者介面的一些項目適用於 Visual Studio，在下列指示。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件

您需要下列元件才能完成此逐步解說：

- 支援的 Windows 和 SharePoint 版本。

## <a name="create-a-web-part-project"></a>建立網頁組件專案

首先，使用建立網頁組件專案**視覺化網頁組件**專案範本。

1. 開始[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]利用**系統管理員身分執行**選項。

2. 在功能表列上，選擇 [檔案] > [新增] > [專案]。

     [ **新增專案** ] 對話方塊隨即出現。

3. 在**新的專案**對話方塊中，在**Visual C#** 或**Visual Basic**，展開**Office/SharePoint**，然後選擇  **SharePoint 方案**類別目錄。

4. 在範本清單中，選擇**SharePoint 2013-視覺 Web 組件**範本，然後選擇**確定** 按鈕。

     **SharePoint 自訂精靈**隨即出現。 使用此精靈，您可以指定您將使用專案和方案的信任層級進行偵錯的網站。

5. 在 **此 SharePoint 方案的信任層級為何？** 區段中，選擇**部署為伺服陣列方案**選項按鈕。

6. 選擇**完成** 按鈕，接受預設的本機 SharePoint 網站。

## <a name="designing-the-web-part"></a>設計 web 組件

加入從控制項來設計 web 組件**工具箱**Visual Web Developer 設計工具的介面。

1. 在 Visual Web Developer 設計工具中，選擇**設計**索引標籤，切換至 [設計] 檢視。

2. 在功能表列上，選擇 [檢視] > [工具箱]。

3. 在 **標準**節點**工具箱**，選擇**CheckBoxList**控制項，並執行下列步驟：

    - 開啟捷徑功能表**CheckBoxList**控制項中，選擇**複製**，在設計師中，開啟的第一行的捷徑功能表，然後選擇**貼上**。

    - 拖曳**CheckBoxList**控制從**工具箱**，並將控制項連接至設計工具中的第一行。

4. 重複上一個步驟中，但將 Button 移至設計工具的下一行。

5. 在設計工具中，選擇**Button1**  按鈕。

6. 在功能表列上選擇 [**檢視** > **屬性] 視窗**。

     **屬性**視窗隨即開啟。

7. 在 **文字**屬性的按鈕，輸入**更新**。

## <a name="handling-the-events-of-controls-on-the-web-part"></a>處理 web 組件上控制項的事件

加入程式碼，可讓使用者將行事曆新增至主要行事曆檢視。

1. 請執行下列其中一組步驟：

   - 在設計工具中，按兩下**更新** 按鈕。

   - 在 [**屬性**視窗**更新**按鈕，並選擇**事件**] 按鈕。 在 **按一下 **  屬性中，輸入**Button1_Click**，然後選擇 Enter 鍵。

     使用者控制項程式碼檔案會在 「 程式碼編輯器 」 中開啟和`Button1_Click`事件處理常式隨即出現。 稍後，您會將程式碼加入這個事件處理常式。

2. 加入使用者控制項程式碼檔案頂端新增下列陳述式。

     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

3. 新增下列一行程式碼`VisualWebPart1`類別。 此程式碼會宣告每月的行事曆檢視控制項。

     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]

4. 取代`Page_Load`方法的`VisualWebPart1`為下列程式碼的類別。 這個程式碼會執行下列工作：

   - 將月份的行事曆檢視加入至使用者控制項。

   - 新增站台上的核取方塊，為每個行事曆清單。

   - 行事曆檢視中指定每一種顯示項目的範本。

     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]

5. 取代`Button1_Click`方法的`VisualWebPart1`為下列程式碼的類別。 此程式碼會將各個選定行事曆項目，加入主要行事曆檢視。

     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]

## <a name="test-the-web-part"></a>測試 web 組件

當您執行專案時，會開啟 SharePoint 網站。 Web 組件會自動加入至 sharepoint 網頁組件庫。 若要測試此專案，您會執行下列工作：

- 加入兩個不同的行事曆清單的每個事件。
- 將網頁組件新增至網頁組件中。
- 指定要包含在月份行事曆檢視中的清單。

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>若要將事件新增至站台上的行事曆清單

1. 在 Visual Studio 中，選擇**F5**索引鍵。

     SharePoint 網站隨即開啟，而[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]快速啟動 列會出現在頁面上。

2. 在 [快速啟動] 工具列上底下**列出**，選擇**行事曆**連結。

     **行事曆**頁面隨即出現。

     如果您沒有行事曆連結出現在 [快速啟動] 列上，選擇**站台內容**連結。 如果未顯示 [站台內容] 頁面**行事曆**項目，請建立一個。

3. 在行事曆 頁面上，選擇一天、，然後選擇**新增**中選取的日期，若要加入事件的連結。

4. 在**標題**方塊中，輸入 **「 預設行事曆中的事件**，然後選擇**儲存** 按鈕。

5. 選擇**站台內容**連結，然後再選擇**新增應用程式**圖格。

6. 在上**Create**頁面上，選擇**行事曆**類型，命名行事曆，然後選擇**建立** 按鈕。

7. 加入新的行事曆事件中，事件**自訂行事曆中的事件**，然後選擇**儲存** 按鈕。

### <a name="to-add-the-web-part-to-a-web-part-page"></a>若要將網頁組件新增至網頁組件

1. 在 **站台內容**頁面上，開啟**網站頁面**資料夾。

2. 在功能區中，選擇 **檔案**索引標籤上，開啟**新文件**功能表，然後選擇 **網頁組件頁面**命令。

3. 上**新的網頁組件**頁面上，將頁面命名**SampleWebPartPage.aspx**，然後選擇**建立** 按鈕。

     網頁組件頁面隨即出現。

4. 在 [網頁組件頁面的上方區域中，選擇**插入**索引標籤，然後選擇**Web 組件**] 按鈕。

5. 選擇**自訂**資料夾中，選擇**VisualWebPart1**網頁組件，，然後選擇**新增** 按鈕。

     Web 組件會出現在頁面上。 下列控制項會出現在 web 組件：

    - 每月的行事曆檢視。

    - **更新** 按鈕。

    - A**行事曆**核取方塊。

    - A**自訂行事曆**核取方塊。

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>若要指定列出要納入月份行事曆檢視

在 web 組件中，指定您想要納入月份行事曆檢視中，然後選擇的行事曆**更新** 按鈕。

您指定的所有行事曆中的事件會顯示每月的行事曆檢視。

## <a name="see-also"></a>另請參閱

[建立 SharePoint web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)
[How to:建立 SharePoint web 組件](../sharepoint/how-to-create-a-sharepoint-web-part.md)
[逐步解說：建立 SharePoint web 組件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
