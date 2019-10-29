---
title: 逐步解說：建立 SharePoint 應用程式頁面 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0eaf7bda4ac4ed67dae79b8dd83bb59ba6985343
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985020"
---
# <a name="walkthrough-create-a-sharepoint-application-page"></a>逐步解說：建立 SharePoint 應用程式頁面

應用程式頁面是一種特殊形式的 ASP.NET 網頁。 應用程式頁面包含與 SharePoint 主版頁面合併的內容。 如需詳細資訊，請參閱[建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。

本逐步解說會示範如何建立應用程式頁面，然後使用本機 SharePoint 網站來加以調試。 此頁面會顯示每個使用者在伺服器陣列的所有網站中建立或修改的所有專案。

這個逐步解說將說明下列工作：

- 建立 SharePoint 專案。
- 將應用程式頁面加入至 SharePoint 專案。
- 將 ASP.NET 控制項加入至應用程式頁面。
- 在 ASP.NET 控制項後面加入程式碼。
- 測試應用程式頁面。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>Prerequisites

- 支援的 Windows 和 SharePoint 版本。

## <a name="create-a-sharepoint-project"></a>建立 SharePoint 專案

首先，建立**空白的 SharePoint 專案**。 稍後，您將會在此專案中加入**應用程式頁面**專案。

1. 啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2. 開啟 [**新增專案**] 對話方塊，展開您要使用之語言下的 [ **Office/SharePoint** ] 節點，然後選擇 [ **SharePoint 方案**] 節點。

3. 在 [ **Visual Studio 安裝的範本**] 窗格中，選擇 [ **SharePoint 2010-空白專案**] 範本。 將專案命名為**MySharePointProject**，然後選擇 [**確定]** 按鈕。

     [ **SharePoint 自訂嚮導]** 隨即出現。 此嚮導可讓您選取要用來對專案進行的網站和方案的信任層級的建立。

4. 選擇 [**部署為數組方案**] 選項按鈕，然後選擇 [**完成]** 按鈕以接受預設的本機 SharePoint 網站。

## <a name="create-an-application-page"></a>建立應用程式頁面

若要建立應用程式頁面，請將**應用程式頁面**專案新增至專案。

1. 在**方案總管**中，選擇 [ **MySharePointProject** ] 專案。

2. 在功能表列中，選擇 [專案] > [加入新項目]。

3. 在 [**加入新專案**] 對話方塊中，選擇 [**應用程式] 頁面（[僅限陣列方案**] 範本。

4. 將頁面命名為**SearchItems**，然後選擇 [**新增**] 按鈕。

     Visual Web Developer 設計工具會在 [**來源**] 視圖中顯示應用程式頁面，您可以在其中看到頁面的 HTML 元素。 設計工具會顯示數個 <xref:System.Web.UI.WebControls.Content> 控制項的標記。 每個控制項都會對應到預設應用程式主版頁面中定義的 <xref:System.Web.UI.WebControls.ContentPlaceHolder> 控制項。

## <a name="design-the-layout-of-the-application-page"></a>設計應用程式頁面的版面配置

應用程式頁面專案可讓您使用設計工具，將 ASP.NET 控制項加入至應用程式頁面。 這個設計工具是在 Visual Web Developer 中使用的設計工具。 將標籤、選項按鈕清單和資料表加入至設計工具的**來源**視圖，然後設定屬性，就像設計任何標準 ASP.NET 網頁一樣。

1. 在功能表列上，選擇 [檢視] > [工具箱]。

2. 在 [**工具箱**] 的 [標準] 節點中，執行下列其中一個步驟：

    - 開啟 [**標籤**] 專案的快捷方式功能表，選擇 [**複製**]，開啟設計工具中**PlaceHolderMain**內容控制項底下行的快捷方式功能表，然後選擇 [**貼**上]。

    - 將 [**標籤**] 專案從 [**工具箱**] 拖曳至**PlaceHolderMain**內容控制項的主體。

3. 重複上一個步驟，將**DropDownList**專案和**資料表**專案加入至**PlaceHolderMain**內容控制項。

4. 在設計工具上，將 [標籤] 控制項的 [`Text`] 屬性值變更為 [**顯示所有專案**]。

5. 在設計工具上，將 `<asp:DropDownList>` 元素取代為下列 XML。

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handle-the-events-of-controls-on-the-page"></a>處理頁面上控制項的事件

處理應用程式頁面中的控制項，就像任何 ASP.NET 網頁一樣。 在這個程式中，您將處理下拉式清單的 `SelectedIndexChanged` 事件。

1. 在 [ **View** ] 功能表上，選擇 [程式**代碼**]。

     應用程式頁面程式碼檔案隨即在程式碼編輯器中開啟。

2. 將下列方法加入 `SearchItems` 類別。 這個程式碼會藉由呼叫稍後將在本逐步解說中建立的方法，來處理 <xref:System.Web.UI.WebControls.DropDownList> 的 <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> 事件。

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. 將下列語句新增至應用程式頁面程式碼檔案的頂端。

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. 將下列方法加入 `SearchItems` 類別。 這個方法會逐一查看伺服器陣列上的所有網站，並搜尋目前使用者所建立或修改的專案。

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. 將下列方法加入 `SearchItems` 類別。 這個方法會顯示資料表中目前使用者所建立或修改的專案。

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="test-the-application-page"></a>測試應用程式頁面

當您執行專案時，SharePoint 網站隨即開啟，而且 [應用程式] 頁面隨即出現。

1. 在**方案總管**中，開啟應用程式頁面的快捷方式功能表，然後選擇 [**設定為啟始專案**]。

2. 選擇 **F5** 鍵。

     SharePoint 網站隨即開啟。

3. 在 [應用程式] 頁面上，選擇 [**由我修改**] 選項。

     [應用程式] 頁面會重新整理，並顯示您在伺服器陣列上所有網站中修改的所有專案。

4. 在 [應用程式] 頁面上，挑選清單中的 [**由我建立**]。

     [應用程式] 頁面會重新整理，並顯示您在伺服器陣列上所有網站中建立的所有專案。

## <a name="next-steps"></a>後續步驟

如需 SharePoint 應用程式頁面的詳細資訊，請參閱[建立 sharepoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。

您可以從下列主題深入瞭解如何使用 Visual Web 設計工具來設計 SharePoint 網頁內容：

- [建立 SharePoint 的 web 元件](../sharepoint/creating-web-parts-for-sharepoint.md)。

- [為 web 元件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)。

## <a name="see-also"></a>請參閱

[如何：建立應用程式頁面](../sharepoint/how-to-create-an-application-page.md)
[應用程式 _layouts 頁面類型](/previous-versions/office/aa979604(v=office.14))
