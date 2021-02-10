---
title: 伺服器總管：擴充 SharePoint 連接節點
titleSuffix: ''
description: 在這個逐步解說中，請參閱如何在伺服器總管中，從 [SharePoint 連接] 節點的延伸模組呼叫 SharePoint 用戶端物件模型。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a095e9d1e8fc48500bceac06732150a3067e2dd2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937676"
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>逐步解說：在伺服器總管擴充功能中呼叫 SharePoint 用戶端物件模型
  本逐步解說示範如何在 **伺服器總管** 中，從 [ **sharepoint 連接**] 節點的延伸模組呼叫 sharepoint 用戶端物件模型。 如需有關如何使用 SharePoint 用戶端物件模型的詳細資訊，請參閱 [呼叫 sharepoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。

 本逐步解說將示範下列工作：

- [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]以下列方式建立延伸 **伺服器總管** 的 **SharePoint 連接** 節點擴充：

  - 延伸模組會在 **伺服器總管** 的每個 SharePoint 網站節點下新增 [ **Web 元件庫**] 節點。 這個新節點包含子節點，代表網站上網頁元件庫中的每個 Web 元件。

  - 此延伸模組會定義代表 Web 元件實例的新節點類型。 這個新的節點類型是 [新增 **網頁元件庫** ] 節點下的子節點基礎。 [新增網頁元件] 節點類型會在 [ **屬性** ] 視窗中顯示節點所代表之 Web 元件的相關資訊。

- 建立 Visual Studio 擴充功能 (VSIX) 套件以部署擴充功能。

- 調試和測試擴充功能。

> [!NOTE]
> 您在此逐步解說中建立的擴充功能，與您在逐步解說：擴充伺服器總管中建立的擴充功能類似， [可顯示網頁元件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。 該逐步解說會使用 SharePoint 伺服器物件模型，但本逐步解說會使用用戶端物件模型來完成相同的工作。

## <a name="prerequisites"></a>必要條件
 您需要在開發電腦上執行下列元件，才能完成此逐步解說：

- 支援的 Windows、SharePoint 和 Visual Studio 版本。

- Visual Studio SDK。 本逐步解說會使用 SDK 中的 **Vsix 專案** 範本來建立 vsix 封裝，以部署擴充功能。 如需詳細資訊，請參閱 [Visual Studio 中的擴充 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。

下列概念的知識很有説明，但並非必要，無法完成此逐步解說：

- 使用 SharePoint 用戶端物件模型。 如需詳細資訊，請參閱 [Managed 用戶端物件模型](/previous-versions/office/developer/sharepoint-2010/ee537247(v=office.14))。

- SharePoint 中的 Web 元件。 如需詳細資訊，請參閱 [Web 組件總覽](/previous-versions/office/ms432401(v=office.14))。

## <a name="create-the-projects"></a>建立專案
 若要完成這個逐步解說，您必須建立兩個專案：

- 建立 VSIX 封裝以部署 **伺服器總管** 擴充功能的 vsix 專案。

- 實 **伺服器總管** 擴充的類別庫專案。

  藉由建立專案來開始逐步解說。

#### <a name="to-create-the-vsix-project"></a>建立 VSIX 專案

1. 啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2. 在功能表列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]。

3. 在 [ **新增專案** ] 對話方塊中，展開 [ **Visual c #** ] 或 [ **Visual Basic** 節點]， **然後選擇 [** 擴充性]。

    > [!NOTE]
    > 只有當您安裝 Visual Studio SDK 時，才能使用擴充 **性節點。** 如需詳細資訊，請參閱本主題稍早的必要條件一節。

4. 在對話方塊的頂端，選擇 .NET Framework 版本清單中的 **.NET Framework 4.5** 。

     SharePoint 工具延伸模組需要此 .NET Framework 版本的功能。

5. 選擇 [ **VSIX 專案** ] 範本。

6. 在 [ **名稱** ] 方塊中，輸入 **WebPartNode**，然後選擇 [ **確定]** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將 **WebPartNode** 專案新增至 **方案總管**。

#### <a name="to-create-the-extension-project"></a>建立延伸模組專案

1. 在 **方案總管** 中，開啟方案節點的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增專案**]。

2. 在 [  **新增專案** ] 對話方塊中，展開 [ **Visual c #** ] 或 [ **Visual Basic** 節點]，然後選擇 [ **Windows**]。

3. 在對話方塊的頂端，選擇 .NET Framework 版本清單中的 **.NET Framework 4.5** 。

4. 在專案範本清單中，選擇 [ **類別庫**]。

5. 在 [ **名稱** ] 方塊中，輸入 **WebPartNodeExtension**，然後選擇 [ **確定]** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將 **WebPartNodeExtension** 專案加入至方案，並開啟預設的 Class1 程式碼檔案。

6. 從專案中刪除 Class1 程式碼檔案。

## <a name="configure-the-extension-project"></a>設定擴充功能專案
 撰寫程式碼以建立擴充功能之前，您必須先將程式碼檔和元件參考加入至您的專案，而且必須更新預設的命名空間。

#### <a name="to-configure-the-project"></a>若要設定專案

1. 在 **WebPartNodeExtension** 專案中，加入名為 SiteNodeExtension 和 WebPartNodeTypeProvider 的兩個程式碼檔案。

2. 開啟 WebPartNodeExtension 專案的快捷方式功能表，然後選擇 [ **加入參考**]。

3. 在 [ **參考管理員-WebPartNodeExtension** ] 對話方塊中，選擇 [ **架構** ] 節點，然後選取 [ComponentModel] 和 [system.object] 元件的核取方塊。

4. 選擇 [ **擴充** 功能] 節點，選取下列每個元件的核取方塊，然後選擇 [ **確定]** 按鈕：

    - Microsoft. 用戶端

    - （執行時間）

    - VisualStudio SharePoint

5. 開啟 **WebPartNodeExtension** 專案的快捷方式功能表，然後選擇 [ **屬性**]。

     [專案設計工具] 隨即開啟。

6. 選擇 [應用程式] 索引標籤。

7. 在 [ **預設命名空間** ] 方塊中 (c # ) 或 **根命名空間** box (Visual Basic) ，請輸入 **ServerExplorer. SharePointConnections. WebPartNode**。

## <a name="create-icons-for-the-new-nodes"></a>建立新節點的圖示
 為 **伺服器總管** 擴充功能建立兩個圖示： [新的 **網頁元件庫** ] 節點的圖示，以及 [ **網頁元件庫** ] 節點下的每個子 Web 元件節點的另一個圖示。 稍後在此逐步解說中，您將撰寫程式碼，以將這些圖示與節點產生關聯。

#### <a name="to-create-icons-for-the-nodes"></a>建立節點的圖示

1. 在 WebPartNodeExtension 專案的 [ **專案設計** 工具] 中，選擇 [ **資源** ] 索引標籤。

2. 選擇 [ **此專案不包含預設資源檔] 連結。按一下這裡以建立一個。**

     Visual Studio 會建立資源檔，並在設計工具中開啟它。

3. 在設計工具的頂端，選擇 [ **新增資源** ] 功能表命令上的箭號，然後選擇 [ **加入新的圖示**]。

4. 針對新的圖示名稱輸入 **WebPartsNode** ，然後選擇 **[新增] 按鈕。**

     新的圖示會在 **影像編輯器** 中開啟。

5. 編輯16x16 版本的圖示，使其具有可輕易辨識的設計。

6. 開啟32版圖示的快捷方式功能表，然後選擇 [ **刪除映射類型**]。

7. 重複步驟3到7，將第二個圖示新增至專案資源，並將此圖示命名為 **web** 專案。

8. 在 [**方案總管**] 的 [ **WebPartNodeExtension** ] 專案的 [**資源**] 資料夾中，選擇 [ *WebPartsNode*]。

9. 在 [ **屬性** ] 視窗中，開啟 [ **組建動作** ] 清單，然後選擇 [ **內嵌資源**]。

10. 針對 [ *WebPart*] 重複最後兩個步驟。

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>將 web 元件庫節點新增至伺服器總管
 建立類別，以將新的 **網頁元件庫** 節點加入至每個 SharePoint 網站節點。 若要加入新的節點，類別會實作為 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 介面。 當您想要在 **伺服器總管** 中擴充現有節點的行為（例如，將新的子節點新增至節點）時，請執行這個介面。

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>將 web 元件庫節點新增至伺服器總管

1. 將下列程式碼貼入 **WebPartNodeExtension** 專案的 **SiteNodeExtension** 程式碼檔案中。

    > [!NOTE]
    > 加入此程式碼之後，專案會有一些編譯錯誤。 當您在後續步驟中新增程式碼時，這些錯誤就會消失。

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>定義代表網頁元件的節點類型
 建立類別，以定義代表 Web 元件的新節點類型。 Visual Studio 使用這個新的節點類型，在 [ **網頁元件庫** ] 節點下顯示子節點。 每個子節點都代表 SharePoint 網站上的單一網頁元件。

 若要定義新的節點類型，類別會實作為 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 介面。 當您想要在 **伺服器總管** 中定義新的節點類型時，請執行這個介面。

#### <a name="to-define-the-web-part-node-type"></a>若要定義 web 元件節點類型

1. 將下列程式碼貼入 **WebPartNodeExtension** 專案的 **WebPartNodeTypeProvider** 程式碼檔案中。

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]

## <a name="checkpoint"></a>Checkpoint
 在本逐步解說的這個階段中， **Web 元件庫** 節點的所有程式碼現在都位於專案中。 建立 **WebPartNodeExtension** 專案，以確定它會進行編譯而不會發生錯誤。

#### <a name="to-build-the-project"></a>建置專案

1. 在 **方案總管** 中，開啟 **WebPartNodeExtension** 專案的快捷方式功能表，然後選擇 [ **組建**]。

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>建立 VSIX 套件以部署擴充功能
 若要部署擴充功能，請在您的方案中使用 VSIX 專案來建立 VSIX 套件。 首先，請修改專案中包含的 extension.vsixmanifest 檔案，以設定 VSIX 套件。 然後藉由建立解決方案來建立 VSIX 套件。

#### <a name="to-configure-the-vsix-package"></a>設定 VSIX 封裝

1. 在 **方案總管** 的 **WebPartNode** 專案中，于資訊清單編輯器中開啟 **extension.vsixmanifest** 檔案。

     Extension.vsixmanifest 檔案是所有 VSIX 封裝所需的 extension.vsixmanifest 檔案基礎。 如需此檔案的詳細資訊，請參閱 [VSIX 延伸架構1.0 參考](/previous-versions/dd393700(v=vs.110))。

2. 在 [ **產品名稱** ] 方塊中，輸入 **伺服器總管的 [網頁元件庫] 節點**。

3. 在 [ **作者** ] 方塊中，輸入 **Contoso**。

4. 在 [ **描述** ] 方塊中，輸入 **伺服器總管中的 [SharePoint 連接] 節點加入自訂網頁元件庫節點**。

5. 在編輯器的 [ **資產** ] 索引標籤上，選擇 [ **新增** ] 按鈕。

6. 在 [ **加入新資產** ] 對話方塊的 [ **類型** ] 清單中，選擇 [ **VisualStudio. [microsoft.visualstudio.mefcomponent]**]。

    > [!NOTE]
    > 此值對應至 `MefComponent` extension.vsixmanifest 檔案中的元素。 這個元素會指定 VSIX 封裝中的擴充元件名稱。 如需詳細資訊，請參閱 [[Microsoft.visualstudio.mefcomponent] 元素 (VSX 架構) ](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))。

7. 在 [ **來源** ] 清單中，選擇 [ **目前方案中的專案**]。

8. 在 [ **專案** ] 清單中，選擇 [ **WebPartNodeExtension**]，然後選擇 [ **確定]** 按鈕。

9. 在功能表列上，選擇 [**組建**  >  **組建方案**]，然後確定方案會進行編譯而不會發生錯誤。

10. 請確定 WebPartNode 專案的組建輸出檔案夾現在包含 WebPartNode .vsix 檔案。

     根據預設，組建輸出檔案夾為。包含您專案檔之資料夾下的 \bin\Debug 資料夾。

## <a name="test-the-extension"></a>測試擴充功能
 您現在已準備好在 **伺服器總管** 中測試 [新的 **Web 元件庫**] 節點。 首先，開始在 Visual Studio 的實驗性實例中，對擴充功能專案進行 debug 錯。 然後，在 Visual Studio 的實驗實例中使用新的 **Web 組件** 節點。

#### <a name="to-start-debugging-the-extension"></a>開始進行擴充功能的調試

1. 使用系統管理認證重新開機 Visual Studio，然後開啟 **WebPartNode** 方案。

2. 在 WebPartNodeExtension 專案中，開啟 **SiteNodeExtension** 程式碼檔案，然後將中斷點加入至和方法中的第一行程式碼 `NodeChildrenRequested` `CreateWebPartNodes` 。

3. 選擇 **F5** 鍵以開始進行調試。

     Visual Studio 將擴充功能安裝到伺服器 Explorer\1.0 的%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web 元件庫節點延伸，並啟動 Visual Studio 的實驗實例。 您將在 Visual Studio 的這個實例中測試專案專案。

#### <a name="to-test-the-extension"></a>測試擴充功能

1. 在 Visual Studio 的實驗實例中，選擇功能表列上的 [ **View**]  >  **伺服器總管**。

2. 確認您要用於測試的 SharePoint 網站出現在 **伺服器總管** 的 [ **sharepoint 連接**] 節點底下。 如果未列出，請依照下列步驟執行：

    1. 開啟 [ **SharePoint 連接**] 的快捷方式功能表，然後選擇 [ **加入連接**]。

    2. 在 [ **加入 Sharepoint 連接** ] 對話方塊中，輸入您要連接之 SharePoint 網站的 URL，然後選擇 [ **確定]** 按鈕。

         若要在開發電腦上指定 SharePoint 網站，請輸入 **http://localhost** 。

3. 展開 [網站連線] 節點， (顯示您的網站 URL) ，然後展開 [子網站] 節點 (例如 [ **小組網站**) ]。

4. 確認 Visual Studio 的另一個實例中的程式碼會在您稍早在此方法中設定的中斷點上停止 `NodeChildrenRequested` ，然後選擇 **F5** 鍵繼續進行專案的偵錯工具。

5. 在 Visual Studio 的實驗實例中，展開 [ **網頁元件庫** ] 節點，此節點會出現在最上層網站節點下。

6. 確認 Visual Studio 的另一個實例中的程式碼會在您稍早在此方法中設定的中斷點上停止 `CreateWebPartNodes` ，然後選擇 **F5** 鍵繼續進行專案的偵錯工具。

7. 在 Visual Studio 的實驗實例中，確認連線網站上的所有 Web 組件都出現在 **伺服器總管** 的 [**網頁元件庫**] 節點底下。

8. 開啟網頁元件的快捷方式功能表，然後選擇 [ **屬性**]。

9. 在 [ **屬性** ] 視窗中，確認已顯示網頁元件的詳細資料。

10. 在 **伺服器總管** 中，開啟相同網頁元件的快捷方式功能表，然後選擇 [ **顯示訊息**]。

     在出現的訊息方塊中，選擇 [ **確定]** 按鈕。

## <a name="uninstall-the-extension-from-visual-studio"></a>從 Visual Studio 卸載擴充功能
 完成擴充功能的測試之後，請從 Visual Studio 將其卸載。

#### <a name="to-uninstall-the-extension"></a>安裝擴充功能

1. 在 Visual Studio 的實驗實例中，選擇功能表列上的 [**工具**  >  **擴充功能和更新**]。

     [擴充功能和更新] 對話方塊隨即開啟。

2. 在擴充功能清單中，選擇 [ **Web 元件庫] 節點以進行伺服器總管**，然後選擇 [ **卸載** ] 按鈕。

3. 在出現的對話方塊中，選擇 [ **是** ] 按鈕。

4. 選擇 [ **立即重新開機** ] 按鈕以完成卸載。

     專案專案也會一併卸載。

5. 關閉 Visual Studio 的兩個實例 (實驗實例，以及開啟 WebPartNode 方案) 的 Visual Studio 實例。

## <a name="see-also"></a>另請參閱
- [呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [擴充伺服器總管中的 [SharePoint 連接] 節點](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [逐步解說：擴充伺服器總管以顯示 web 元件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [圖示影像編輯器](/cpp/windows/image-editor-for-icons)
- [建立圖示或其他影像 &#40;圖示的影像編輯器&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)