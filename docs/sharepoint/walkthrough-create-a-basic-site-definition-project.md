---
title: 逐步解說：建立基本網站定義專案 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 078fcc4d30613e4fe19b493150ce4570196b73ac
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608873"
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>逐步解說：建立基本網站定義專案
  本逐步解說會示範如何建立基本網站定義包含在其上的控制項的視覺 Web 組件。 為求清楚起見，您建立視覺 Web 組件會有只有少數的控制項。 不過，您可以建立更複雜的 SharePoint 網站定義包含更多的功能。

 本逐步解說將示範下列工作：

- 使用建立網站定義[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]專案範本。

- 在 SharePoint 中使用的網站定義，以建立 SharePoint 網站。

- 將視覺 Web 組件新增至解決方案。

- 加入新的視覺 Web 組件的自訂網站的 default.aspx 頁面。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

-   支援的 Microsoft Windows 和 SharePoint 版本。 如需詳細資訊，請參閱開發 SharePoint 方案的需求。

-   Visual Studio。

## <a name="create-a-site-definition-solution"></a>建立網站定義方案
 首先，建立在網站定義專案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

#### <a name="to-create-a-site-definition-project"></a>若要建立網站定義專案

1. 在功能表列上，選擇 [檔案] > [新增] > [專案]。 如果您的 IDE 設定為使用 Visual Basic 開發設定，在功能表列上，選擇**檔案** > **新專案**。

    [ **新增專案** ] 對話方塊隨即出現。

2. 依序展開**Visual C#** 節點或**Visual Basic**節點，展開**SharePoint**  節點，然後選擇**2010年**節點。

3. 在 **範本**清單中，選擇**SharePoint 2010 專案**範本。

4. 在 [**名稱**方塊中，輸入**TestSiteDef**，然後選擇 **[確定]** ] 按鈕。

    **SharePoint 自訂精靈**隨即出現。

5. 在 **指定偵錯的網站和安全性層級**頁面上，輸入您要偵錯網站定義，在 SharePoint 網站的 URL，或使用預設位置 (http://<em>系統名稱</em>/)。

6. 在 **此 SharePoint 方案的信任層級為何？** 區段中，選擇**部署為伺服陣列方案**選項按鈕。

    所有的網站定義專案必須部署為伺服陣列方案。 如需有關沙箱化方案與伺服器陣列方案的詳細資訊，請參閱[沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。

7. 選擇**完成** 按鈕。

    專案會出現在**方案總管 中**。

8. 在 **方案總管**，選擇專案節點，然後在功能表列上選擇 **專案** > **加入新項目**。

9. 之下**Visual C#** 或**Visual Basic**，展開**SharePoint**  節點，然後選擇**2010年**節點。

10. 中**範本**窗格中，選擇**網站定義**範本，讓**名稱**作為**SiteDefinition1**，然後選擇 [ **新增**] 按鈕。

## <a name="create-a-visual-web-part"></a>建立視覺 web 組件
 接下來，建立要顯示在網站定義的主頁面上的視覺 Web 組件。

#### <a name="to-create-a-visual-web-part"></a>若要建立視覺 web 組件

1.  在 [**方案總管**，選擇**顯示所有檔案**] 按鈕。

2.  選擇**SiteDefinition1**專案節點，然後在功能表列上選擇 **專案** > **加入新項目**。

     [新增項目] 對話方塊隨即出現。

3.  依序展開**Visual C#** 節點或**Visual Basic**節點，展開**SharePoint**  節點，然後選擇**2010年**節點。

4.  在範本清單中，選擇**視覺化網頁組件**範本，保留預設名稱 VisualWebPart1，，然後選擇**新增** 按鈕。

     *VisualWebPart1.ascx*檔案隨即開啟。

5.  在底部*VisualWebPart1.ascx*，新增下列標記來將三個控制項新增至表單： 文字方塊、 按鈕和標籤：

    ```aspx-csharp
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

6.  下*VisualWebPart1.ascx*，開啟*VisualWebPart1.ascx.cs*檔案 (如[!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]) 或*VisualWebPart1.ascx.vb* (如[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)])，然後新增下列程式碼：

     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

     這個程式碼加入 web 組件的按鈕按一下的功能。

## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>將視覺 web 組件新增至預設 ASPX 頁面
 接下來，新增網站定義的預設 ASPX 頁面的視覺 Web 組件。

#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>將視覺 web 組件新增至預設 ASPX 頁面

1.  開啟 default.aspx 頁面上，，然後加入下列這行程式`WebPartPages`標記：

    ```aspx-csharp
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>
    ```

     這一行會將名稱 MyWebPartControls 關聯 Web 組件和其程式碼。 *命名空間*參數必須符合用於命名空間*VisualWebPart1.ascx*程式碼檔案。

2.  在後`</asp:Content>`項目，取代整個`ContentPlaceHolderId="PlaceHolderMain"`區段和其內容與下列程式碼：

    ```aspx-csharp
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">
        <MyWebPartControls:VisualWebPart1 runat="server" />
    </asp:Content>
    ```

     此程式碼會建立您稍早建立的視覺 Web 組件的參考。

3.  在**方案總管 中**，開啟捷徑功能表**SiteDefinition1**節點，然後選擇**設定為啟動項目**。

## <a name="deploy-and-run-the-site-definition-solution"></a>部署和執行網站定義方案
 接下來，將專案部署到 SharePoint，然後再執行 專案。

#### <a name="to-deploy-and-run-the-site-definition"></a>若要部署和執行網站定義

-   在功能表列上選擇 **建置** > **部署 TestSiteDef**。

-   選擇 **F5** 鍵。

     Visual Studio 的程式碼編譯、 新增其功能、 套件的所有檔案至 SharePoint 方案 (WSP) 檔案，並會用於根據 WSP 檔案部署到 SharePoint 伺服器。 SharePoint 安裝檔案，，然後啟動功能。

## <a name="create-a-site-based-on-the-site-definition"></a>建立站台上的網站定義
 接下來，使用新的網站定義建立網站。

#### <a name="to-create-a-site-by-using-the-site-definition"></a>若要使用的網站定義建立站台

1.  在 SharePoint 網站上新的 SharePoint 網站頁面隨即出現。

2.  在 **標題和描述**區段中，輸入**我的新網站**標題和描述的網站。

3.  在 [**網址**區段中，輸入**mynewsite**中**URL 名稱**] 方塊中。

4.  在 [**樣板**區段中，選擇**SharePoint 自訂**] 索引標籤。

5.  在 **選取範本**清單中，選擇**SiteDefinition1**。

6.  將其他設定保留其預設值，，然後選擇 [**建立**] 按鈕。

     新的網站隨即出現。

## <a name="test-the-new-site"></a>測試新的站台
 接下來，測試新的站台，若要確認是否正常運作。

#### <a name="to-test-the-new-site"></a>若要測試新的站台

-   在預設 ASPX 頁面上，輸入一些文字，，然後選擇**變更標籤文字**文字方塊旁邊的按鈕。

     文字會出現在 [] 按鈕右邊的標籤。

## <a name="see-also"></a>另請參閱
- [如何：建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
