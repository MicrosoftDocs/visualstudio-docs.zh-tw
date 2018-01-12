---
title: "逐步解說： 建立 SharePoint 應用程式頁面 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload: office
ms.openlocfilehash: 49407485bb408371b69b86bddac4957c4aa7cdcd
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-sharepoint-application-page"></a>逐步解說：建立 SharePoint 應用程式頁面
  應用程式頁面是一種特殊的形式的 ASP.NET 網頁。 應用程式頁面包含合併與 SharePoint 主版頁面的內容。 如需詳細資訊，請參閱[建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
 本逐步解說將示範如何建立應用程式頁面上，並使用本機 SharePoint 網站來偵錯。 此頁面會顯示每位使用者建立或修改在伺服器陣列上的所有站台的所有項目。  
  
 這個逐步解說將說明下列工作：  
  
-   建立 SharePoint 專案。  
  
-   將應用程式頁面加入 SharePoint 專案。  
  
-   將 ASP.NET 控制項加入至應用程式頁面。  
  
-   在 ASP.NET 控制項後面加入程式碼。  
  
-   測試應用程式頁面。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 Windows 版本和 SharePoint。 如需詳細資訊，請參閱[開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]或 Visual Studio Ultimate 或 Visual Studio Premium edition。  
  
## <a name="creating-a-sharepoint-project"></a>建立 SharePoint 專案  
 首先，建立**空白的 SharePoint 專案**。 稍後，您會加入**應用程式頁面**項目加入此專案。  
  
#### <a name="to-create-a-sharepoint-project"></a>若要建立 SharePoint 專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  開啟**新專案**對話方塊方塊中，展開  **Office/SharePoint**節點下的語言，您想要使用，然後選擇  **SharePoint 方案**節點。  
  
3.  在**Visual Studio 安裝的範本** 窗格中，選擇**SharePoint 2010-空專案**範本。 將專案命名**MySharePointProject**，然後選擇 [**確定**] 按鈕。  
  
     **SharePoint 自訂精靈**隨即出現。 此精靈可讓您選取的網站，您將用於偵錯專案和方案的信任層級。  
  
4.  選擇**部署為伺服陣列方案**選項按鈕，然後再選擇**完成** 按鈕，接受預設的本機 SharePoint 網站。  
  
## <a name="creating-an-application-page"></a>建立應用程式頁面  
 若要建立應用程式頁面上，新增**應用程式頁面**項目加入專案。  
  
#### <a name="to-create-an-application-page"></a>若要建立的應用程式頁面  
  
1.  在**方案總管 中**，選擇**MySharePointProject**專案。  
  
2.  在功能表列上選擇 **專案**，**加入新項目**。  
  
3.  在**加入新項目**對話方塊方塊中，選擇**應用程式頁面上 (僅限陣列方案**範本。  
  
4.  將頁面命名**SearchItems**，然後選擇 [**新增**] 按鈕。  
  
     Visual Web Developer 設計工具會顯示應用程式頁面中的**來源**檢視您可以在其中檢視網頁的 HTML 項目。 在設計工具顯示數個標記<xref:System.Web.UI.WebControls.Content>控制項。 每個控制項都對應到<xref:System.Web.UI.WebControls.ContentPlaceHolder>定義預設應用程式的主版頁面中的控制項。  
  
## <a name="designing-the-layout-of-the-application-page"></a>設計應用程式頁面上的配置  
 應用程式頁面項目可讓您使用應用程式頁面加入 ASP.NET 控制項的設計工具。 這個設計工具是在 Visual Web Developer 中使用相同的設計工具。 加入標籤、 圓鈕清單中，與資料表以**來源**的設計工具中，檢視和一樣，當您設計任何標準 ASP.NET 網頁，然後設定屬性。  
  
#### <a name="to-design-the-layout-of-the-application-page"></a>若要設計的應用程式頁面的版面配置  
  
1.  在功能表列上，依序選擇 [檢視] 和 [工具箱]。  
  
2.  中的標準節點**工具箱**，執行下列步驟：  
  
    -   開啟捷徑功能表**標籤**項目，選擇**複製**，開啟下的那一行的捷徑功能表**PlaceHolderMain**內容控制項在設計師中，然後按一下選擇**貼上**。  
  
    -   拖曳**標籤**項目從**工具箱**主體到**PlaceHolderMain**內容控制項。  
  
3.  重複上述步驟以新增**DropDownList**項目和**資料表**項目**PlaceHolderMain**內容控制項。  
  
4.  在設計工具中，變更的值`Text`的 label 控制項，以屬性**顯示所有項目**。  
  
5.  在設計工具中，將`<asp:DropDownList>`具有下列 XML 項目。  
  
    ```  
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"  
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">  
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>  
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>  
    </asp:DropDownList>  
    ```  
  
## <a name="handling-the-events-of-controls-on-the-page"></a>處理頁面上的控制項的事件  
 處理控制項的應用程式頁面中，就如同任何 ASP.NET 網頁。 在此程序，您將處理`SelectedIndexChanged`下拉式清單的事件。  
  
#### <a name="to-handle-the-events-of-controls-on-the-page"></a>若要處理的頁面上的控制項事件  
  
1.  在**檢視**功能表上，選擇**程式碼**。  
  
     應用程式頁面的程式碼檔隨即開啟 程式碼編輯器。  
  
2.  將下列方法加入 `SearchItems` 類別中。 此程式碼會處理<xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged>事件<xref:System.Web.UI.WebControls.DropDownList>所呼叫的方法，您將建立稍後在本逐步解說。  
  
     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]  
  
3.  應用程式頁面的程式碼檔案頂端加入下列陳述式。  
  
     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]  
  
4.  將下列方法加入 `SearchItems` 類別中。 這個方法會逐一查看所有站台伺服器陣列上，搜尋由目前的使用者建立或修改項目。  
  
     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]  
  
5.  將下列方法加入 `SearchItems` 類別中。 這個方法會顯示目前的使用者資料表中所建立或修改項目。  
  
     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]  
  
## <a name="testing-the-application-page"></a>測試應用程式頁面  
 當您執行專案時，開啟 SharePoint 網站和應用程式 頁面隨即出現。  
  
#### <a name="to-test-the-application-page"></a>若要測試應用程式頁面  
  
1.  在**方案總管 中**，開啟 應用程式 頁面的捷徑功能表，然後選擇**設定為啟動項目**。  
  
2.  選擇 F5 鍵。  
  
     開啟 SharePoint 網站。  
  
3.  在應用程式] 頁面上，選擇 [**修改由我**選項。  
  
     應用程式頁面重新整理，並顯示您已在伺服器陣列上的所有網站中修改的所有項目。  
  
4.  在應用程式] 頁面上，選擇 [**我所建立的**清單中。  
  
     應用程式頁面重新整理，並顯示您已在伺服器陣列上的所有站台建立的所有項目。  
  
## <a name="next-steps"></a>後續步驟  
 如需 SharePoint 應用程式頁面的詳細資訊，請參閱[建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
 您可以深入了解如何使用 Visual Web 設計工具，從下列主題來設計 SharePoint 網頁內容：  
  
-   [建立 SharePoint Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)。  
  
-   [為 Web 組件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)。  
  
## <a name="see-also"></a>請參閱  
 [如何： 建立應用程式頁面](../sharepoint/how-to-create-an-application-page.md)   
 [應用程式 _layouts 頁面中輸入](http://go.microsoft.com/fwlink/?LinkID=169274)  
  
  