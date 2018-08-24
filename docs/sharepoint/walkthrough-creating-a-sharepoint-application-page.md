---
title: 逐步解說： 建立 SharePoint 應用程式頁面 |Microsoft Docs
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
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 52ff6b3431ac3f87c85eefcf728cfe4c4875f884
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42634783"
---
# <a name="walkthrough-create-a-sharepoint-application-page"></a>逐步解說： 建立 SharePoint 應用程式頁面
 
應用程式頁面是 ASP.NET 網頁的一種特殊的形式。 應用程式頁面包含與 SharePoint 主版頁面合併的內容。 如需詳細資訊，請參閱 <<c0> [ 建立適用於 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。

本逐步解說會示範如何建立應用程式頁面，並使用本機 SharePoint 網站來偵錯。 此頁面會顯示每位使用者已建立或修改所有網站伺服器陣列中的所有項目。

這個逐步解說將說明下列工作：

- 建立 SharePoint 專案。
- 應用程式頁面加入 SharePoint 專案。
- 將 ASP.NET 控制項加入至應用程式頁面。
- 加入 ASP.NET 控制項的程式碼。
- 測試應用程式頁面。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件

- 支援的 Windows 和 SharePoint 版本。

## <a name="create-a-sharepoint-project"></a>建立 SharePoint 專案

首先，建立**空的 SharePoint 專案**。 稍後，您會加入**應用程式頁面**項目加入這個專案。

1. 啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2. 開啟**新的專案**對話方塊方塊中，展開**Office/SharePoint**節點下的語言，您想要使用此項目，然後選擇**SharePoint 方案**節點。

3. 在  **Visual Studio 安裝的範本**窗格中，選擇**SharePoint 2010-空專案**範本。 將專案命名為**MySharePointProject**，然後選擇**確定**按鈕。

     **SharePoint 自訂精靈**隨即出現。 此精靈可讓您選取的網站，您將使用專案和方案的信任層級進行偵錯。

4. 選擇**部署為伺服陣列方案**選項按鈕，然後再選擇**完成** 按鈕，接受預設的本機 SharePoint 網站。

## <a name="create-an-application-page"></a>建立應用程式頁面

若要建立應用程式頁面上，新增**應用程式頁面**項目加入專案。

1. 在 **方案總管**，選擇**MySharePointProject**專案。

2. 在功能表列中，選擇 [專案] > [加入新項目]。

3. 在 **加入新項目**對話方塊方塊中，選擇**應用程式頁面 (僅限陣列方案**範本。

4. 將頁面命名**命名為 SearchItems**，然後選擇**新增** 按鈕。

     Visual Web Developer 設計工具會顯示在應用程式頁面**來源**檢視，您可以在這裡看到網頁的 HTML 項目。 在設計工具顯示的標記數個<xref:System.Web.UI.WebControls.Content>控制項。 每個控制項都會對應至<xref:System.Web.UI.WebControls.ContentPlaceHolder>預設應用程式的主版頁面中定義的控制項。

## <a name="design-the-layout-of-the-application-page"></a>設計應用程式頁面的版面配置

應用程式頁面項目可讓您使用設計工具將 ASP.NET 控制項新增至應用程式頁面。 這個設計工具是在 Visual Web Developer 中使用的相同設計工具。 新增標籤、 選項按鈕清單和資料表**來源**設計工具中，檢視，並且就像當設計任何標準 ASP.NET 頁面，然後設定屬性。

1. 在功能表列上選擇 **檢視** > **工具箱**。

2. 中的標準節點**工具箱**，執行下列步驟：

    - 開啟捷徑功能表**標籤**項目中，選擇**複製**，開啟下的那一行的捷徑功能表**PlaceHolderMain**內容控制項在設計工具中，然後選擇**貼上**。

    - 拖曳**標籤**項目從**工具箱**到主體**PlaceHolderMain**內容控制項。

3. 重複上述步驟以新增**DropDownList**項目並**表格**項目**PlaceHolderMain**內容控制項。

4. 在設計工具的值變更`Text`屬性的 label 控制項，以**顯示所有項目**。

5. 在設計工具中，將`<asp:DropDownList>`具有下列 XML 項目。

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handle-the-events-of-controls-on-the-page"></a>處理頁面上控制項的事件

處理應用程式頁面中的控制項，就如同任何 ASP.NET 頁面。 在此程序中，您將處理`SelectedIndexChanged`的下拉式清單的事件。

1. 在 **檢視**功能表上，選擇**程式碼**。

     應用程式頁面程式碼檔案會開啟在程式碼編輯器。

2. 將下列方法加入 `SearchItems` 類別中。 此程式碼會處理<xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged>事件的<xref:System.Web.UI.WebControls.DropDownList>所呼叫的方法，您將建立稍後在本逐步解說。

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. 應用程式頁面程式碼檔案頂端新增下列陳述式。

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. 將下列方法加入 `SearchItems` 類別中。 這個方法會逐一查看伺服器陣列上的所有站台，並搜尋目前使用者所建立或修改的項目。

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. 將下列方法加入 `SearchItems` 類別中。 這個方法會顯示在資料表中目前的使用者所建立或修改的項目。

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="test-the-application-page"></a>測試應用程式頁面

當您執行專案時，會開啟 SharePoint 網站和應用程式頁面隨即出現。

1. 在 **方案總管**，開啟 應用程式 頁面的捷徑功能表，然後選擇**設定為啟動項目**。

2. 選擇 **F5** 鍵。

     SharePoint 網站隨即開啟。

3. 在應用程式 頁面上，選擇**修改由我**選項。

     應用程式頁面重新整理，並顯示您的伺服器陣列上的所有網站中修改過的所有項目。

4. 在應用程式 頁面上，選擇**我所建立的**清單中。

     應用程式頁面重新整理，並顯示您已建立伺服器陣列上的所有站台的所有項目。

## <a name="next-steps"></a>後續步驟

如需有關 SharePoint 應用程式頁面的詳細資訊，請參閱 <<c0> [ 建立適用於 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。

您可以進一步了解如何使用 Visual Web 設計工具，從下列主題來設計 SharePoint 頁面內容：

- [建立 SharePoint web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)。

- [建立可重複使用的控制項，為 web 組件或應用程式頁面](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)。

## <a name="see-also"></a>另請參閱

[如何： 建立應用程式頁面](../sharepoint/how-to-create-an-application-page.md)  
[應用程式 _layouts 頁面類型](http://go.microsoft.com/fwlink/?LinkID=169274)
