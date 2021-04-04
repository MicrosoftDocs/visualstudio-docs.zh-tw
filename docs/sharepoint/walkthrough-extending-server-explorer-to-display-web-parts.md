---
title: 逐步解說：擴充伺服器總管以顯示 Web 組件 |Microsoft Docs
titleSuffix: ''
description: 在這個逐步解說中，擴充伺服器總管，使其在每個連線的 SharePoint 網站上顯示網頁元件庫。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 276315b7f470777da30fda33b15bac995deb07fd
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217667"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>逐步解說：擴充伺服器總管以顯示 web 元件
  在 Visual Studio 中，您可以使用 **伺服器總管** 的 [ **sharepoint 連接**] 節點來查看 sharepoint 網站上的元件。 不過， **伺服器總管** 預設不會顯示某些元件。 在這個逐步解說中，您將延伸 **伺服器總管** ，使其在每個連線的 SharePoint 網站上顯示網頁元件庫。

 本逐步解說將示範下列工作：

- 建立可透過下列方式擴充 **伺服器總管** 的 Visual Studio 延伸模組：

  - 延伸模組會在 **伺服器總管** 的每個 SharePoint 網站節點下新增 [ **Web 元件庫**] 節點。 這個新節點包含子節點，代表網站上網頁元件庫中的每個 Web 元件。

  - 此延伸模組會定義代表 Web 元件實例的新節點類型。 這個新的節點類型是 [新增 **網頁元件庫** ] 節點下的子節點基礎。 [新增網頁元件] 節點類型會在 [ **屬性** ] 視窗中顯示其所代表之 Web 元件的資訊。 節點類型也包含自訂快捷方式功能表項目，可讓您做為執行與網頁元件相關之其他工作的起點。

- 建立兩個擴充元件呼叫的自訂 SharePoint 命令。 SharePoint 命令是可由擴充元件呼叫的方法，以在適用于 SharePoint 的伺服器物件模型中使用 Api。 在這個逐步解說中，您會建立命令，以從開發電腦上的本機 SharePoint 網站取得網頁元件資訊。 如需詳細資訊，請參閱 [呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。

- 建立 Visual Studio 擴充功能 (VSIX) 套件以部署擴充功能。

- 調試和測試擴充功能。

> [!NOTE]
> 如需本逐步解說中使用用戶端物件模型（而不是其伺服器物件模型）的替代版本，請參閱 [逐步解說：在伺服器總管擴充功能中呼叫 sharepoint 用戶端物件模型](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)。

## <a name="prerequisites"></a>必要條件
 您需要在開發電腦上執行下列元件，才能完成此逐步解說：

- 支援的 Windows 版本、SharePoint 及 Visual Studio。

- Visual Studio SDK。 本逐步解說會使用 SDK 中的 **Vsix 專案** 範本來建立 vsix 封裝，以部署專案專案。 如需詳細資訊，請參閱 [Visual Studio 中的擴充 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。

  下列概念的知識很有説明，但並非必要，無法完成此逐步解說：

- 使用 SharePoint 的伺服器物件模型。 如需詳細資訊，請參閱 [使用 SharePoint Foundation Server-Side 物件模型](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14))。

- SharePoint 方案中的 Web 組件。 如需詳細資訊，請參閱 [Web 組件總覽](/previous-versions/office/ms432401(v=office.14))。

## <a name="create-the-projects"></a>建立專案
 若要完成這個逐步解說，您必須建立三個專案：

- 建立 VSIX 封裝以部署擴充功能的 VSIX 專案。

- 實擴充的類別庫專案。 這個專案必須以 .NET Framework 4.5 為目標。

- 定義自訂 SharePoint 命令的類別庫專案。 此專案必須以 the.NET Framework 3.5 為目標。

  藉由建立專案來開始逐步解說。

#### <a name="to-create-the-vsix-project"></a>建立 VSIX 專案

1. 啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2. 在功能表列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]。

3. 在 [**新增專案**] 對話方塊中，展開 [ **Visual c #** ] 或 [ **Visual Basic** 節點]，然後選擇 [擴充性 **] 節點。**

    > [!NOTE]
    > 只有當您安裝 Visual Studio SDK 時，才能使用擴充 **性節點。** 如需詳細資訊，請參閱本主題稍早的必要條件一節。

4. 在對話方塊的頂端，選擇 .NET Framework 版本清單中的 **.NET Framework 4.5** 。

5. 選擇 [ **VSIX 專案** ] 範本、將專案命名為 **WebPartNode**，然後選擇 [ **確定]** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將 **WebPartNode** 專案新增至 **方案總管**。

#### <a name="to-create-the-extension-project"></a>建立延伸模組專案

1. 在 **方案總管** 中，開啟方案節點的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增專案**]。

2. 在 [ **新增專案** ] 對話方塊中，展開 [ **Visual c #** ] 節點或 **Visual Basic** 節點，然後選擇 [ **Windows** ] 節點。

3. 在對話方塊的頂端，選擇 .NET Framework 版本清單中的 **.NET Framework 4.5** 。

4. 在專案範本清單中，選擇 [ **類別庫**]，將專案命名為 **WebPartNodeExtension**，然後選擇 [ **確定]** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將 **WebPartNodeExtension** 專案加入至方案，並開啟預設的 Class1 程式碼檔案。

5. 從專案中刪除 Class1 程式碼檔案。

#### <a name="to-create-the-sharepoint-commands-project"></a>若要建立 SharePoint 命令專案

1. 在 **方案總管** 中，開啟方案節點的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增專案**]。

2. 在 [  **新增專案** ] 對話方塊中，展開 [ **Visual c #** ] 節點或 **Visual Basic** 節點，然後選擇 [ **Windows** ] 節點。

3. 在對話方塊的頂端，選擇 .NET Framework 版本清單中的 **.NET Framework 3.5** 。

4. 在專案範本清單中，選擇 [ **類別庫**]，將專案命名為 **WebPartCommands**，然後選擇 [ **確定]** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將 **WebPartCommands** 專案加入至方案，並開啟預設的 Class1 程式碼檔案。

5. 從專案中刪除 Class1 程式碼檔案。

## <a name="configure-the-projects"></a>設定專案
 撰寫程式碼以建立擴充功能之前，您必須加入程式碼檔案和元件參考，並設定專案設定。

#### <a name="to-configure-the-webpartnodeextension-project"></a>設定 WebPartNodeExtension 專案

1. 在 WebPartNodeExtension 專案中，加入四個具有下列名稱的程式碼檔案：

    - SiteNodeExtension

    - WebPartNodeTypeProvider

    - WebPartNodeInfo

    - WebPartCommandIds

2. 開啟 **WebPartNodeExtension** 專案的快捷方式功能表，然後選擇 [ **加入參考**]。

3. 在 [ **參考管理員-WebPartNodeExtension** ] 對話方塊中，選擇 [ **Framework** ] 索引標籤，然後選取下列每個元件的核取方塊：

    - System.ComponentModel.Composition

    - System.Windows.Forms

4. 選擇 [ **擴充** 功能] 索引標籤，選取 [VisualStudio] 元件的核取方塊，然後選擇 [ **確定]** 按鈕。

5. 在 **方案總管** 中，開啟 [ **WebPartNodeExtension** ] 專案節點的快捷方式功能表，然後選擇 [ **屬性**]。

     [專案設計工具] 隨即開啟。

6. 選擇 [應用程式] 索引標籤。

7. 在 [ **預設命名空間** ] 方塊中 (c # ) 或 **根命名空間** box ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) ，請輸入 **ServerExplorer. SharePointConnections. WebPartNode**。

#### <a name="to-configure-the-webpartcommands-project"></a>設定 webpartcommands 專案

1. 在 WebPartCommands 專案中，加入名為 WebPartCommands 的程式碼檔案。

2. 在 **方案總管** 中，開啟 [ **WebPartCommands** ] 專案節點的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **現有專案**]。

3. 在 [ **加入現有專案** ] 對話方塊中，流覽至包含 WebPartNodeExtension 專案程式碼檔的資料夾，然後選擇 WebPartNodeInfo 和 WebPartCommandIds 程式碼檔。

4. 選擇 [ **加入** ] 按鈕旁的箭號，然後在出現的功能表中選擇 [ **新增為連結** ]。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將程式碼檔案加入至 WebPartCommands 專案做為連結。 因此，程式碼檔案位於 WebPartNodeExtension 專案中，但檔案中的程式碼也會在 WebPartCommands 專案中編譯。

5. 再次開啟 **WebPartCommands** 專案的快捷方式功能表，然後選擇 [ **加入參考**]。

6. 在 [ **參考管理員-WebPartCommands** ] 對話方塊中，選擇 [ **擴充** 功能] 索引標籤，選取下列每個元件的核取方塊，然後選擇 [ **確定]** 按鈕：

    - Microsoft SharePoint

    - VisualStudio 命令

7. 在 **方案總管** 中，再次開啟 **WebPartCommands** 專案的快捷方式功能表，然後選擇 [ **屬性**]。

     [專案設計工具] 隨即開啟。

8. 選擇 [應用程式] 索引標籤。

9. 在 [ **預設命名空間** ] 方塊中 (c # ) 或 **根命名空間** box ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) ，請輸入 **ServerExplorer. SharePointConnections. WebPartNode**。

## <a name="create-icons-for-the-new-nodes"></a>建立新節點的圖示
 為 **伺服器總管** 擴充功能建立兩個圖示： [新的 **網頁元件庫** ] 節點的圖示，以及 [ **Web 元件庫** ] 節點下的每個子 Web 元件節點的另一個圖示。 稍後在此逐步解說中，您將撰寫程式碼，以將這些圖示與節點產生關聯。

#### <a name="to-create-icons-for-the-nodes"></a>建立節點的圖示

1. 在 **方案總管** 中，開啟 **WebPartNodeExtension** 專案的快捷方式功能表，然後選擇 [ **屬性**]。

2. [專案設計工具] 隨即開啟。

3. 選擇 [ **資源** ] 索引標籤，然後選擇 [ **此專案不包含預設資源檔]。按一下這裡以建立一個** 連結。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 建立資源檔，並在設計工具中開啟它。

4. 在設計工具的頂端，選擇 [ **新增資源** ] 功能表命令旁邊的箭號，然後在出現的功能表中選擇 [ **加入新** 的] 圖示。

5. 在 [新增 **資源** ] 對話方塊中，將新的圖示命名為 **WebPartsNode**，然後選擇 [ **加入** ] 按鈕。

     新的圖示會在 **影像編輯器** 中開啟。

6. 編輯16x16 版本的圖示，使其具有可輕易辨識的設計。

7. 開啟32版圖示的快捷方式功能表，然後選擇 [ **刪除映射類型**]。

8. 重複步驟5到8，將第二個圖示新增至專案資源，並將此圖示命名為 **web** 專案。

9. 在 **方案總管** 的 [ **WebPartNodeExtension** ] 專案的 [**資源**] 資料夾底下，開啟 [ **WebPartsNode**] 的快捷方式功能表。

10. 在 [ **屬性** ] 視窗中，選擇 [ **建立動作**] 旁邊的箭號，然後在出現的功能表上選擇 [ **內嵌資源** ]。

11. 針對 [ **WebPart**] 重複最後兩個步驟。

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>將 Web 元件庫節點新增至伺服器總管
 建立類別，以將新的 **網頁元件庫** 節點加入至每個 SharePoint 網站節點。 若要加入新的節點，類別會實作為 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 介面。 當您想要擴充 **伺服器總管** 中現有節點的行為（例如將子節點加入至節點）時，請執行這個介面。

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>將 Web 元件庫節點新增至伺服器總管

1. 在 WebPartNodeExtension 專案中，開啟 SiteNodeExtension 程式碼檔案，然後將下列程式碼貼入其中。

    > [!NOTE]
    > 當您加入此程式碼之後，專案將會有一些編譯錯誤，但是當您在後續步驟中新增程式碼時，就會消失。

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb" id="Snippet1":::

## <a name="define-a-node-type-that-represents-a-web-part"></a>定義代表網頁元件的節點類型
 建立類別，以定義代表 Web 元件的新節點類型。 Visual Studio 使用這個新的節點類型，在 [ **網頁元件庫** ] 節點下顯示子節點。 每個子節點都代表 SharePoint 網站上的單一網頁元件。

 若要定義新的節點類型，類別會實作為 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 介面。 當您想要在 **伺服器總管** 中定義新的節點類型時，請執行這個介面。

#### <a name="to-define-the-web-part-node-type"></a>若要定義 web 元件節點類型

1. 在 WebPartNodeExtension 專案中，開啟 WebPartNodeTypeProvder 程式碼檔案，然後將下列程式碼貼入其中。

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs" id="Snippet2":::

## <a name="define-the-web-part-data-class"></a>定義 web 元件資料類別
 定義包含 SharePoint 網站上單一網頁元件相關資料的類別。 稍後在此逐步解說中，您將建立自訂 SharePoint 命令，以抓取網站上每個 Web 元件的相關資料，然後將資料指派給這個類別的實例。

#### <a name="to-define-the-web-part-data-class"></a>若要定義 web 元件資料類別

1. 在 WebPartNodeExtension 專案中，開啟 WebPartNodeInfo 程式碼檔案，然後將下列程式碼貼入其中。

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs" id="Snippet3":::

## <a name="define-the-ids-for-the-sharepoint-commands"></a>定義 SharePoint 命令的識別碼
 定義可識別自訂 SharePoint 命令的數個字串。 您稍後將在本逐步解說中執行這些命令。

#### <a name="to-define-the-command-ids"></a>定義命令識別碼

1. 在 WebPartNodeExtension 專案中，開啟 WebPartCommandIds 程式碼檔案，然後將下列程式碼貼入其中。

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs" id="Snippet4":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb" id="Snippet4":::

## <a name="create-the-custom-sharepoint-commands"></a>建立自訂 SharePoint 命令
 建立自訂命令，以呼叫 SharePoint 網站上的伺服器物件模型，以取得 sharepoint 網站上 Web 組件的相關資料。 每個命令都是已套用的方法 <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> 。

#### <a name="to-define-the-sharepoint-commands"></a>若要定義 SharePoint 命令

1. 在 WebPartCommands 專案中，開啟 WebPartCommands 程式碼檔案，然後將下列程式碼貼入其中。

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs" id="Snippet6":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb" id="Snippet6":::

## <a name="checkpoint"></a>Checkpoint
 在本逐步解說的這個階段中， **Web 元件庫** 節點和 SharePoint 命令的所有程式碼現在都位於專案中。 建立解決方案，以確定兩個專案都能編譯而不會發生錯誤。

#### <a name="to-build-the-solution"></a>若要建置方案

1. 在功能表列上，選擇 [**組建**  >  **組建方案**]。

    > [!WARNING]
    > 此時，WebPartNode 專案可能會產生組建錯誤，因為 VSIX 資訊清單檔沒有 [作者] 的值。 當您在稍後的步驟中新增值時，這個錯誤就會消失。

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>建立 VSIX 套件以部署擴充功能
 若要部署擴充功能，請在您的方案中使用 VSIX 專案來建立 VSIX 套件。 首先，藉由修改 VSIX 專案中的 extension.vsixmanifest 檔案來設定 VSIX 套件。 然後，建立解決方案來建立 VSIX 套件。

#### <a name="to-configure-the-vsix-package"></a>設定 VSIX 封裝

1. 在 **方案總管** 的 [WebPartNode] 專案底下，在資訊清單編輯器中開啟 **extension.vsixmanifest** 檔案。

     Extension.vsixmanifest 檔案是所有 VSIX 封裝所需的 extension.vsixmanifest 檔案基礎。 如需此檔案的詳細資訊，請參閱 [VSIX 延伸架構1.0 參考](/previous-versions/dd393700(v=vs.110))。

2. 在 [ **產品名稱** ] 方塊中，輸入 **伺服器總管的 [網頁元件庫] 節點**。

3. 在 [ **作者** ] 方塊中，輸入 **Contoso**。

4. 在 [ **描述** ] 方塊中，輸入 **伺服器總管中的 [SharePoint 連接] 節點加入自訂網頁元件庫節點。此延伸模組會使用自訂 SharePoint 命令來呼叫伺服器物件模型。**

5. 選擇編輯器的 [ **資產** ] 索引標籤，然後選擇 [ **新增** ] 按鈕。

     [ **加入新資產** ] 對話方塊隨即出現。

6. 在 [ **類型** ] 清單中，選擇 [ **VisualStudio. [microsoft.visualstudio.mefcomponent]**]。

    > [!NOTE]
    > 此值對應至 `MefComponent` extension.vsixmanifest 檔案中的元素。 這個元素會指定 VSIX 封裝中的擴充元件名稱。 如需詳細資訊，請參閱 [[Microsoft.visualstudio.mefcomponent] 元素 (VSX 架構) ](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))。

7. 在 [  **來源** ] 清單中，選擇 [ **目前方案中的專案**]。

8. 在 [ **專案** ] 清單中，選擇 [ **WebPartNodeExtension** ]，然後選擇 [ **確定]** 按鈕。

9. 在資訊清單編輯器中，再次選擇 [ **新增** ] 按鈕。

     [ **加入新資產** ] 對話方塊隨即出現。

10. 在 [ **類型** ] 方塊中，輸入 [ **v4**]。

    > [!NOTE]
    > 這個元素會指定您想要包含在 Visual Studio 延伸模組中的自訂擴充功能。 如需詳細資訊，請參閱 [資產元素 (VSX 架構) ](/previous-versions/dd393737(v=vs.110))。

11. 在 [ **來源** ] 清單中，選擇 [ **目前方案中的專案** ] 清單專案。

12. 在 [ **專案** ] 清單中，選擇 [ **WebPartCommands**]，然後選擇 [ **確定]** 按鈕。

13. 在功能表列上，選擇 [**組建**  >  **組建方案**]，然後確定方案會進行編譯而不會發生錯誤。

14. 請確定 WebPartNode 專案的組建輸出檔案夾現在包含 WebPartNode .vsix 檔案。

     根據預設，組建輸出檔案夾為。包含您專案檔之資料夾下的 \bin\Debug 資料夾。

## <a name="test-the-extension"></a>測試擴充功能
 您現在已準備好在 **伺服器總管** 中測試 [新的 **Web 元件庫**] 節點。 首先，開始在 Visual Studio 的實驗實例中進行擴充功能的偵錯工具。 然後，在的實驗實例中使用新的 **Web 組件** 節點 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。

#### <a name="to-start-debugging-the-extension"></a>開始進行擴充功能的調試

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]以系統管理認證重新開機，然後開啟 WebPartNode 方案。

2. 在 WebPartNodeExtension 專案中，開啟 SiteNodeExtension 程式碼檔案，然後將中斷點加入至和方法中的第一行程式碼 `NodeChildrenRequested` `CreateWebPartNodes` 。

3. 選擇 **F5** 鍵以開始進行調試。

     Visual Studio 將擴充功能安裝到伺服器 Explorer\1.0 的%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web 元件庫節點延伸，並啟動 Visual Studio 的實驗實例。 您將在 Visual Studio 的這個實例中測試專案專案。

#### <a name="to-test-the-extension"></a>測試擴充功能

1. 在的實驗實例中 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，選擇功能表列上的 [ **View**  >  **伺服器總管**]。

2. 如果您要用於測試的 SharePoint 網站未出現在 **伺服器總管** 的 [ **sharepoint 連接**] 節點底下，請執行下列步驟：

    1. 在 **伺服器總管** 中，開啟 [ **SharePoint 連接**] 的快捷方式功能表，然後選擇 [ **加入連接**]。

    2. 在 [ **加入 Sharepoint 連接** ] 對話方塊中，輸入您要連接之 SharePoint 網站的 URL，然後選擇 [ **確定]** 按鈕。

         若要在開發電腦上指定 SharePoint 網站，請輸入 **http://localhost** 。

3. 展開 [網站連線] 節點， (顯示您的網站 URL) ，然後展開 [子網站] 節點 (例如 [ **小組網站**) ]。

4. 確認另一個實例中的程式碼在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 您稍早在此方法中設定的中斷點上停止 `NodeChildrenRequested` ，然後選擇 [ **F5** ] 繼續進行專案的偵錯工具。

5. 在 Visual Studio 的實驗實例中，確認名為 **Web 元件庫** 的新節點出現在最上層網站節點下，然後展開 [ **網頁元件庫** ] 節點。

6. 確認 Visual Studio 的另一個實例中的程式碼會在您稍早在此方法中設定的中斷點上停止 `CreateWebPartNodes` ，然後選擇 **F5** 鍵繼續進行專案的偵錯工具。

7. 在 Visual Studio 的實驗實例中，確認連線網站上的所有 Web 組件都出現在 **伺服器總管** 的 [**網頁元件庫**] 節點底下。

8. 在 **伺服器總管** 中，開啟其中一個 Web 組件的快捷方式功能表，然後選擇 [ **屬性**]。

9. 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 您要進行偵錯工具的實例中，確認網頁元件的詳細資料會出現在 [ **屬性** ] 視窗中。

## <a name="uninstall-the-extension-from-visual-studio"></a>從 Visual Studio 卸載擴充功能
 完成擴充功能的測試之後，請從 Visual Studio 卸載擴充功能。

#### <a name="to-uninstall-the-extension"></a>安裝擴充功能

1. 在的實驗實例中 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，選擇功能表列上的 [**工具**  >  **擴充功能和更新**]。

     [擴充功能和更新] 對話方塊隨即開啟。

2. 在擴充功能清單中，選擇 **伺服器總管的 [Web 元件庫] 節點擴充** 功能，然後選擇 [ **卸載** ] 按鈕。

3. 在出現的對話方塊中，選擇 [是] 按鈕，確認您要卸載擴充功能，然後選擇 [**立即重新開機** **]** 按鈕以完成卸載。

4. 關閉 Visual Studio 的兩個實例 (實驗實例，以及開啟 WebPartNode 方案) 的 Visual Studio 實例。

## <a name="see-also"></a>另請參閱
- [擴充伺服器總管中的 [SharePoint 連接] 節點](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [逐步解說：在伺服器總管擴充功能中呼叫 SharePoint 用戶端物件模型](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)
- [圖示影像編輯器](/cpp/windows/image-editor-for-icons)
- [建立圖示或其他影像 &#40;圖示的影像編輯器&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)