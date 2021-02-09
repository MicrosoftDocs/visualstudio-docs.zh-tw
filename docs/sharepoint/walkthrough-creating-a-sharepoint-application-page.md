---
title: 逐步解說：建立 SharePoint 應用程式頁面 |Microsoft Docs
description: 在這個逐步解說中， (特殊形式的 ASP.NET 網頁來建立應用程式頁面) 然後使用本機 SharePoint 網站進行調試。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: def9407d309e5f673d0a7a2cdc3710fae557be50
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847839"
---
# <a name="walkthrough-create-a-sharepoint-application-page"></a>逐步解說：建立 SharePoint 應用程式頁面

應用程式頁面是 ASP.NET 網頁的特殊形式。 應用程式頁面包含與 SharePoint 主版頁面合併的內容。 如需詳細資訊，請參閱 [建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。

本逐步解說將示範如何建立應用程式頁面，然後使用本機 SharePoint 網站來進行調試。 此頁面會顯示每個使用者在伺服器陣列的所有網站中建立或修改的所有專案。

本逐步解說將說明下列工作：

- 建立 SharePoint 專案。
- 將應用程式頁面加入至 SharePoint 專案。
- 將 ASP.NET 控制項加入至應用程式頁面。
- 加入 ASP.NET 控制項背後的程式碼。
- 測試應用程式頁面。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件

- 支援的 Windows 和 SharePoint 版本。

## <a name="create-a-sharepoint-project"></a>建立 SharePoint 專案

首先，建立 **空白的 SharePoint 專案**。 稍後，您會將 **應用程式頁面** 專案加入至此專案。

1. 啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2. 開啟 [ **新增專案** ] 對話方塊，展開您要使用之語言底下的 [ **Office/SharePoint** ] 節點，然後選擇 [ **SharePoint 方案** ] 節點。

3. 在 [ **Visual Studio 安裝的範本** ] 窗格中，選擇 [ **SharePoint 2010-空白專案** ] 範本。 將專案命名為 **MySharePointProject**，然後選擇 [ **確定]** 按鈕。

     [ **SharePoint 自訂] Wizard** 隨即出現。 此嚮導可讓您選取要用來將專案和方案的信任層級進行偵測的網站。

4. 選擇 [ **部署為伺服器陣列方案** ] 選項按鈕，然後選擇 [ **完成]** 按鈕以接受預設的本機 SharePoint 網站。

## <a name="create-an-application-page"></a>建立應用程式頁面

若要建立應用程式頁面，請將 **應用程式頁面** 專案加入至專案。

1. 在 **方案總管** 中，選擇 [ **MySharePointProject** ] 專案。

2. 在功能表列上，選擇 [ **Project**  >  **加入新專案**]。

3. 在 [ **加入新專案** ] 對話方塊中，選擇 [ **應用程式頁面 (伺服器陣列方案** ] 範本。

4. 將頁面命名為 **SearchItems**，然後選擇 [ **加入** ] 按鈕。

     Visual Web Developer designer 會在 **來源** 視圖中顯示應用程式頁面，您可以在其中看到頁面的 HTML 元素。 設計工具會顯示數個控制項的標記 <xref:System.Web.UI.WebControls.Content> 。 每個控制項都會對應至在 <xref:System.Web.UI.WebControls.ContentPlaceHolder> 預設應用程式主版頁面中定義的控制項。

## <a name="design-the-layout-of-the-application-page"></a>設計應用程式頁面的版面配置

應用程式頁面專案可讓您使用設計工具將 ASP.NET 控制項新增至應用程式頁面。 這個設計工具是 Visual Web Developer 中使用的設計工具。 將標籤、選項按鈕清單和資料表加入至設計工具的 **來源** 視圖，然後設定屬性，就像設計任何標準 ASP.NET 網頁一樣。

1. 在功能表列上，選擇 [ **View**  >  **工具箱**]。

2. 在 [ **工具箱**] 的 [標準] 節點中，執行下列其中一個步驟：

    - 開啟 **標籤** 專案的快捷方式功能表，選擇 [ **複製**]，在設計工具中的 **PlaceHolderMain** 內容控制項下，開啟該行的快捷方式功能表，然後選擇 [ **貼** 上]。

    - 將 [ **標籤** ] 專案從 [ **工具箱** ] 拖曳至 **PlaceHolderMain** 內容控制項的主體。

3. 重複上述步驟，將 **DropDownList** 專案和 **資料表** 專案加入至 **PlaceHolderMain** 內容控制項。

4. 在設計工具上，將 [ `Text` 標籤] 控制項的屬性值變更為 **顯示所有專案**。

5. 在設計工具上， `<asp:DropDownList>` 以下列 XML 取代元素。

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handle-the-events-of-controls-on-the-page"></a>處理頁面上控制項的事件

處理應用程式頁面中的控制項，就像任何 ASP.NET 網頁一樣。 在這個程式中，您將會處理 `SelectedIndexChanged` 下拉式清單的事件。

1. 在 [ **View** ] 功能表上，選擇 [程式 **代碼**]。

     應用程式頁面程式碼檔案會在程式碼編輯器中開啟。

2. 將下列方法新增至 `SearchItems` 類別。 這段程式碼 <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> <xref:System.Web.UI.WebControls.DropDownList> 會藉由呼叫您稍後將在本逐步解說中建立的方法，來處理的事件。

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. 將下列語句加入至應用程式頁面程式碼檔案的頂端。

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. 將下列方法新增至 `SearchItems` 類別。 這個方法會逐一查看伺服器陣列上的所有網站，並搜尋目前使用者所建立或修改的專案。

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. 將下列方法新增至 `SearchItems` 類別。 這個方法會顯示資料表中目前使用者所建立或修改的專案。

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="test-the-application-page"></a>測試應用程式頁面

當您執行專案時，會開啟 SharePoint 網站並顯示應用程式頁面。

1. 在 **方案總管** 中，開啟 [應用程式] 頁面的快捷方式功能表，然後選擇 [ **設定為啟始專案**]。

2. 選擇 **F5** 鍵。

     SharePoint 網站隨即開啟。

3. 在 [應用程式] 頁面上，選擇 [ **由我修改** ] 選項。

     [應用程式] 頁面會重新整理，並顯示您在伺服器陣列的所有網站中修改過的所有專案。

4. 在 [應用程式] 頁面上，從清單中選擇 [ **我建立的** ]。

     [應用程式] 頁面會重新整理，並顯示您在伺服器陣列上的所有網站中建立的所有專案。

## <a name="next-steps"></a>下一步

如需 SharePoint 應用程式頁面的詳細資訊，請參閱 [建立 sharepoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。

您可以使用下列主題中的 Visual Web Designer，進一步瞭解如何設計 SharePoint 頁面內容：

- [建立 SharePoint 的網頁元件](../sharepoint/creating-web-parts-for-sharepoint.md)。

- [為 web 元件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)。

## <a name="see-also"></a>另請參閱

[如何：建立應用程式頁面](../sharepoint/how-to-create-an-application-page.md) 
[應用程式 _Layouts 頁面類型](/previous-versions/office/aa979604(v=office.14))
