---
title: 逐步解說：建立基本網站定義專案 |Microsoft Docs
description: 在這個 SharePoint 逐步解說中，請參閱如何建立基本網站定義，其中包含具有一些控制項的視覺網頁元件。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 0411f027b105622d806e123bd80f38c4b05281ca
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913850"
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>逐步解說：建立基本網站定義專案
  本逐步解說將示範如何建立基本網站定義，其中包含有一些控制項的視覺網頁元件。 為了清楚起見，您所建立的視覺網頁元件只有幾個控制項。 不過，您可以建立更複雜的 SharePoint 網站定義，其中包含更多功能。

 本逐步解說將示範下列工作：

- 使用專案範本建立網站定義 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。

- 使用 SharePoint 中的網站定義建立 SharePoint 網站。

- 將視覺 Web 元件加入至方案。

- 藉由將新的視覺網頁元件新增至網站，來自訂網站的 default.aspx 頁面。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- 支援的 Microsoft Windows 和 SharePoint 版本。 如需詳細資訊，請參閱開發 SharePoint 方案的需求。

- Visual Studio。

## <a name="create-a-site-definition-solution"></a>建立網站定義解決方案
 首先，在中建立網站定義專案 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。

#### <a name="to-create-a-site-definition-project"></a>若要建立網站定義專案

1. 在功能表列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]。 如果您的 IDE 設定為使用 Visual Basic 開發設定，請在功能表列 **上選擇 [** 檔案  >  **新增專案**]。

    [新增專案]  對話方塊隨即出現。

2. 展開 [ **Visual c #** ] 節點或 [ **Visual Basic** ] 節點，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

3. 在 [ **範本** ] 清單中，選擇 [ **SharePoint 2010] 專案** 範本。

4. 在 [ **名稱** ] 方塊中，輸入 **TestSiteDef**，然後選擇 [ **確定]** 按鈕。

    [ **SharePoint 自訂] Wizard** 隨即出現。

5. 在 [ **指定偵錯工具的網站和安全性等級** ] 頁面上，輸入您要在其中偵測網站定義的 SHAREPOINT 網站 URL，或使用預設位置 (Http://<em>系統名稱</em>/) 。

6. 在 [ **此 SharePoint 方案的信任層級為何？** ] 區段中，選擇 [ **部署為伺服器陣列方案** ] 選項按鈕。

    所有網站定義專案都必須部署為伺服器陣列方案。 如需有關沙箱化方案與伺服器陣列方案的詳細資訊，請參閱 [沙箱化解決方案考慮](../sharepoint/sandboxed-solution-considerations.md)。

7. 選擇 [完成] 按鈕。

    專案隨即出現在 **方案總管** 中。

8. 在 **方案總管** 中，選擇專案節點，然後在功能表列上選擇 [**專案**  >  **加入新專案**]。

9. 在 [ **Visual c #** ] 或 [ **Visual Basic**] 下，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

10. 在 [ **範本** ] 窗格中，選擇 [ **網站定義** ] 範本，將 [ **名稱** ] 保留為 [ **SiteDefinition1**]，然後選擇 [ **新增** ] 按鈕。

## <a name="create-a-visual-web-part"></a>建立視覺網頁元件
 接下來，建立要出現在網站定義主頁面上的視覺化網頁元件。

#### <a name="to-create-a-visual-web-part"></a>若要建立視覺網頁元件

1. 在 **方案總管** 中，選擇 [ **顯示所有** 檔案] 按鈕。

2. 選擇 [ **SiteDefinition1** ] 專案節點，然後在功能表列上選擇 [**專案**  >  **加入新專案**]。

     [加入新項目]  對話方塊隨即出現。

3. 展開 [ **Visual c #** ] 節點或 [ **Visual Basic** ] 節點，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

4. 在範本清單中，選擇 [ **視覺網頁元件** ] 範本，保留預設名稱 VisualWebPart1，然後選擇 [ **加入** ] 按鈕。

     *VisualWebPart1 .ascx* 檔案隨即開啟。

5. 在 *VisualWebPart1* 的底部，新增下列標記，以將三個控制項新增至表單：文字方塊、按鈕和標籤：

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

6. 在 [ *VisualWebPart1*] 下，針對) 開啟) 或 (VisualWebPart1 的 *VisualWebPart1.ascx.cs* 檔 ([!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] ，然後 *VisualWebPart1.ascx.vb* [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 加入下列程式碼：

     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

     這段程式碼會為網頁元件的按鈕點擊加入功能。

## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>將視覺網頁元件新增至預設 ASPX 頁面
 接下來，將視覺網頁元件新增至網站定義的預設 ASPX 頁面。

#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>將視覺網頁元件加入至預設 ASPX 頁面

1. 開啟 default.aspx 頁面，然後在標記底下加入下列程式 `WebPartPages` 程式碼：

    ```aspx-csharp
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>
    ```

     這一行會將名稱 MyWebPartControls 與網頁元件及其程式碼產生關聯。 *Namespace* 參數符合 *VisualWebPart1 .ascx* 程式碼檔案中使用的命名空間。

2. 在 `</asp:Content>` 元素之後， `ContentPlaceHolderId="PlaceHolderMain"` 以下列程式碼取代整個區段及其內容：

    ```aspx-csharp
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">
        <MyWebPartControls:VisualWebPart1 runat="server" />
    </asp:Content>
    ```

     這段程式碼會建立您稍早建立之視覺 Web 元件的參考。

3. 在 **方案總管** 中，開啟 [ **SiteDefinition1** ] 節點的快捷方式功能表，然後選擇 [ **設定為啟始專案**]。

## <a name="deploy-and-run-the-site-definition-solution"></a>部署和執行網站定義解決方案
 接下來，將專案部署至 SharePoint，然後執行專案。

#### <a name="to-deploy-and-run-the-site-definition"></a>若要部署和執行網站定義

- 在功能表列上，選擇 [**建立**  >  **部署 TestSiteDef**]。

- 選擇 **F5** 鍵。

     Visual Studio 會編譯器代碼、加入其功能、將所有檔案封裝至 SharePoint 方案 (WSP) 檔，然後將 WSP 檔案部署到 SharePoint 伺服器。 SharePoint 接著會安裝檔案，然後啟動功能。

## <a name="create-a-site-based-on-the-site-definition"></a>根據網站定義建立網站
 接下來，使用新的網站定義建立網站。

#### <a name="to-create-a-site-by-using-the-site-definition"></a>使用網站定義建立網站

1. 在 SharePoint 網站上，[新的 SharePoint 網站] 頁面隨即出現。

2. 在 [ **標題與描述** ] 區段中，輸入 **新網站** 的標題和網站的描述。

3. 在 [網站 **位址**] 區段的 [ **URL 名稱**] 方塊中，輸入 **mynewsite** 。

4. 在 [ **範本** ] 區段中，選擇 [ **SharePoint 自訂** ] 索引標籤。

5. 在 [ **選取範本** ] 清單中，選擇 [ **SiteDefinition1**]。

6. 將其他設定保留為預設值，然後選擇 [ **建立** ] 按鈕。

     新網站隨即出現。

## <a name="test-the-new-site"></a>測試新網站
 接下來，測試新的網站，以確認它是否正常運作。

#### <a name="to-test-the-new-site"></a>若要測試新網站

- 在 [預設 ASPX] 頁面上輸入一些文字，然後選擇文字方塊旁的 [ **變更標籤文字** ] 按鈕。

     文字會出現在按鈕右邊的標籤中。

## <a name="see-also"></a>另請參閱
- [如何：建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
