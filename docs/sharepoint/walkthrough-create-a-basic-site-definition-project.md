---
title: "逐步解說： 建立基本網站定義專案 |Microsoft 文件"
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
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
ms.assetid: b0df5b0e-5fa0-43d8-a339-6d92f1276764
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a792ab750decf1a14b589116d886c847b3ddd478
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>逐步解說：建立基本網站定義專案
  本逐步解說將示範如何建立基本網站定義包含在其上某些控制項的視覺 Web 組件。 為了清楚起見，您建立視覺 Web 組件有只有少數的控制項。 不過，您可以建立更複雜的 SharePoint 網站定義，包括更多的功能。  
  
 本逐步解說將示範下列工作：  
  
-   使用建立網站定義[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]專案範本。  
  
-   在 SharePoint 中使用的站台定義，以建立 SharePoint 網站。  
  
-   將視覺 Web 組件加入至方案。  
  
-   加入新的視覺 Web 組件的自訂網站的 default.aspx 頁面。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 Microsoft Windows 和 SharePoint 版本。 如需詳細資訊，請參閱開發 SharePoint 方案的需求。  
  
-   Visual Studio。  
  
## <a name="creating-a-site-definition-solution"></a>建立網站定義方案  
 首先，在其中建立網站定義專案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
#### <a name="to-create-a-site-definition-project"></a>若要建立網站定義專案  
  
1.  在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。 如果您的 IDE 設定為使用 Visual Basic 開發設定，在功能表列上，選擇**檔案**，**新專案**。  
  
     [ **新增專案** ] 對話方塊隨即出現。  
  
2.  展開**Visual C#**節點或**Visual Basic** ] 節點，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010年**節點。  
  
3.  在**範本**清單中，選擇**SharePoint 2010 專案**範本。  
  
4.  在**名稱**方塊中，輸入**TestSiteDef**，然後選擇 [**確定**] 按鈕。  
  
     **SharePoint 自訂精靈**隨即出現。  
  
5.  在**指定偵錯的網站和安全性層級**頁面上，輸入您要偵錯網站定義中，在 SharePoint 網站的 URL，或使用預設位置 (http://*系統名稱*/)。  
  
6.  在**此 SharePoint 方案的信任層級為何？**區段中，選擇**部署為伺服陣列方案**選項按鈕。  
  
     所有站台定義專案必須部署為陣列方案中。 如需有關沙箱化方案和伺服器陣列方案的詳細資訊，請參閱[沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。  
  
7.  選擇**完成** 按鈕。  
  
     專案會出現在**方案總管 中**。  
  
8.  在**方案總管] 中**，選擇專案節點，然後在功能表列上選擇 [**專案**，**加入新項目**。  
  
9. 之下**Visual C#**或**Visual Basic**，依序展開**SharePoint** ] 節點，然後選擇 [ **2010年**節點。  
  
10. 在**範本** 窗格中，選擇**網站定義**範本，將保留**名稱**做為**SiteDefinition1**，然後選擇  **新增** 按鈕。  
  
## <a name="create-a-visual-web-part"></a>建立視覺 Web 組件  
 接下來，建立要顯示在 站台定義的主頁面上的視覺 Web 組件。  
  
#### <a name="to-create-a-visual-web-part"></a>若要建立視覺 Web 組件  
  
1.  在**方案總管 中**，選擇**顯示所有檔案** 按鈕。  
  
2.  選擇**SiteDefinition1**專案節點，，然後在功能表列上選擇**專案**，**加入新項目**。  
  
     [新增項目] 對話方塊隨即出現。  
  
3.  展開**Visual C#**節點或**Visual Basic** ] 節點，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010年**節點。  
  
4.  在範本清單中，選擇 **視覺 Web 組件**範本中，保留預設名稱 VisualWebPart1，，然後選擇 **新增** 按鈕。  
  
     VisualWebPart1.ascx 檔案隨即開啟。  
  
5.  在 VisualWebPart1.ascx 下方，加入下列三個控制項加入表單的標記： 文字方塊、 按鈕和標籤：  
  
    ```  
    <table>  
      <tr>  
        <td>  
          <asp:TextBox runat="server" ID="tbName"></asp:TextBox>  
        </td>  
        <td>  
          <asp:Button runat="server" ID="btnSubmit" Text = "Change Label Text" OnClick="btnSubmit_Click"></asp:Button>  
        </td>  
        <td>  
          <asp:Label runat="server" ID="lblName"></asp:Label>  
        </td>  
      </tr>  
    </table>  
    ```  
  
6.  下 VisualWebPart1.ascx，開啟 VisualWebPart1.ascx.cs 檔案 (如[!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]) 或 VisualWebPart1.ascx.vb (如[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)])，然後加入下列程式碼：  
  
     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
     這個程式碼加入 web 組件的按一下按鈕的功能。  
  
## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>將視覺 Web 組件加入至預設 ASPX 頁面  
 接下來，將視覺 Web 組件加入至站台定義預設 ASPX 頁面。  
  
#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>將視覺 Web 組件新增至預設 ASPX 頁面  
  
1.  開啟 default.aspx 頁面上，，然後加入下列這行程式`WebPartPages`標記：  
  
    ```  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     這一行會將名稱 MyWebPartControls 與 Web 組件和其程式碼產生關聯。 *命名空間*參數必須符合 VisualWebPart1.ascx 程式碼檔案中使用的命名空間。  
  
2.  之後`</asp:Content>`項目，取代整個`ContentPlaceHolderId="PlaceHolderMain"`區段和其內容與下列程式碼：  
  
    ```  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     此程式碼會建立您稍早建立的視覺 Web 組件的參考。  
  
3.  在**方案總管 中**，開啟捷徑功能表**SiteDefinition1**  節點，然後選擇 **設定為啟動項目**。  
  
## <a name="deploy-and-run-the-site-definition-solution"></a>部署和執行網站定義方案  
 接下來，將專案部署到 SharePoint，，，然後執行專案。  
  
#### <a name="to-deploy-and-run-the-site-definition"></a>若要部署和執行網站定義  
  
-   在功能表列上選擇 **建置**，**部署 TestSiteDef**。  
  
-   選擇 F5 鍵。  
  
     Visual Studio 的程式碼編譯、 增加其功能、 SharePoint 方案 (WSP) 檔，將封裝的所有檔案，並將用於根據 WSP 檔案部署到 SharePoint 伺服器。 SharePoint 中安裝檔案，然後啟動 功能。  
  
## <a name="create-a-site-based-on-the-site-definition"></a>建立站台定義為基礎的站台  
 接下來，建立使用新的站台定義的網站。  
  
#### <a name="to-create-a-site-by-using-the-site-definition"></a>若要建立站台使用站台定義  
  
1.  在 SharePoint 網站上新的 SharePoint 網站頁面隨即出現。  
  
2.  在**標題和描述**區段中，輸入**My New Site**標題和描述的網站。  
  
3.  在**網站位址**區段中，輸入**mynewsite**中**URL 名稱**方塊。  
  
4.  在**範本**區段中，選擇**SharePoint 自訂** 索引標籤。  
  
5.  在**選取範本**清單中，選擇**SiteDefinition1**。  
  
6.  保留其預設值，其他設定，然後選擇 [**建立**] 按鈕。  
  
     此時會出現新的站台。  
  
## <a name="test-the-new-site"></a>測試新的站台  
 接著，測試新的站台，若要確認是否正常運作。  
  
#### <a name="to-test-the-new-site"></a>若要測試新的站台  
  
-   在預設 ASPX 頁面上，輸入一些文字，，然後選擇**變更標籤文字**文字方塊旁邊的按鈕。  
  
     文字會出現在按鈕右邊的標籤。  
  
## <a name="see-also"></a>請參閱  
 [如何： 建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)   
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  