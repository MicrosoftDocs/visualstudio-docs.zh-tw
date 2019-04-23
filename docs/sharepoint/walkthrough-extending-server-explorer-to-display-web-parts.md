---
title: 逐步解說：擴充伺服器總管以顯示 Web 組件 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 29fcd40a2fc64a12ed7b29845b0a9f0ea3db5589
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040568"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>逐步解說：擴充伺服器總管以顯示 web 組件
  在 Visual Studio 中，您可以使用**SharePoint 連線**節點**伺服器總管**檢視 SharePoint 網站上的元件。 不過，**伺服器總管**預設不會顯示某些元件。 在本逐步解說中，您將會延長**伺服器總管**，以顯示 Web 組件庫上每個連線的 SharePoint 網站。

 本逐步解說將示範下列工作：

- 正在建立 Visual Studio 延伸模組，擴充**伺服器總管**如下：

    - 擴充功能新增**網頁組件庫**節點中的每個 SharePoint 網站 節點底下**伺服器總管**。 這個新的節點包含代表站台上的 Web 組件庫中的每個 Web 組件的子節點。

    - 延伸模組會定義新類型的節點，表示 Web 組件執行個體。 這個新的節點型別是在新的子節點的基礎**網頁組件庫**節點。 新的 Web 組件節點類型中顯示資訊**屬性**有關它所代表之 Web 組件的視窗。 節點型別也包含自訂快顯功能表項目，您可以使用做為起點，來執行其他 Web 組件與相關的工作。

- 建立兩個延伸模組組件呼叫的自訂 SharePoint 命令。 SharePoint 命令是使用伺服器物件模型中的 Api，適用於 SharePoint 的延伸模組組件可以呼叫的方法。 在本逐步解說中，您可以建立從開發電腦上的本機 SharePoint 網站擷取 Web 組件資訊的命令。 如需詳細資訊，請參閱 <<c0> [ 呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。

- 建置 Visual Studio 擴充功能 (VSIX) 封裝來部署擴充功能。

- 偵錯和測試延伸模組。

> [!NOTE]
>  使用適用於 SharePoint 的用戶端物件模型，而其伺服器物件模型不是本逐步解說的替代版本，請參閱[逐步解說：呼叫 SharePoint 用戶端物件模型，在 伺服器總管延伸模組](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)。

## <a name="prerequisites"></a>必要條件
 您需要完成這個逐步解說在開發電腦上的下列元件：

- 支援的 Windows、 SharePoint 和 Visual Studio 版本。

- Visual Studio SDK 中。 本逐步解說會使用**VSIX 專案**SDK 來建立 VSIX 封裝，來部署專案項目中的範本。 如需詳細資訊，請參閱 <<c0> [ 擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。

  下列概念的知識會很有幫助，但並非必要，若要完成本逐步解說：

- 使用適用於 SharePoint 的伺服器物件模型。 如需詳細資訊，請參閱 <<c0> [ 使用 SharePoint Foundation 伺服器端物件模型](http://go.microsoft.com/fwlink/?LinkId=177796)。

- SharePoint 方案中的 web 組件。 如需詳細資訊，請參閱 < [Web 組件概觀](http://go.microsoft.com/fwlink/?LinkId=177803)。

## <a name="create-the-projects"></a>建立專案
 若要完成此逐步解說中，您必須建立三個專案：

- 若要建立 VSIX 封裝，來部署擴充功能的 VSIX 專案。

- 實作延伸的類別庫專案。 此專案必須以.NET Framework 4.5 為目標。

- 定義自訂的 SharePoint 命令的類別庫專案。 此專案必須以.net Framework 3.5 為目標。

  開始本逐步解說建立的專案。

#### <a name="to-create-the-vsix-project"></a>若要建立 VSIX 專案

1. 啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2. 在功能表列上，選擇 [檔案] > [新增] > [專案]。

3. 中**新的專案**對話方塊方塊中，展開**Visual C#** 或**Visual Basic**節點，然後選擇**擴充性**節點。

    > [!NOTE]
    >  **擴充性**節點才會提供您安裝 Visual Studio SDK。 如需詳細資訊，請參閱稍早在本主題中的必要條件 > 一節。

4. 在對話方塊頂端，選擇 **.NET Framework 4.5**清單中的.NET Framework 版本。

5. 選擇**VSIX 專案**範本，將專案命名為**WebPartNode**，然後選擇**確定** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**WebPartNode**專案加入**方案總管 中**。

#### <a name="to-create-the-extension-project"></a>若要建立擴充功能專案

1. 中**方案總管**，開啟方案節點的捷徑功能表，選擇**新增**，然後選擇**新專案**。

2. 在**新的專案**對話方塊方塊中，展開**Visual C#** 節點或**Visual Basic**節點，然後選擇**Windows**節點。

3. 在對話方塊頂端，選擇 **.NET Framework 4.5**清單中的.NET Framework 版本。

4. 在專案範本清單中，選擇**類別庫**，將專案命名為**WebPartNodeExtension**，然後選擇**確定**  按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**WebPartNodeExtension**專案加入方案，並開啟預設 Class1 的程式碼檔案。

5. 從專案刪除 Class1 的程式碼檔案。

#### <a name="to-create-the-sharepoint-commands-project"></a>若要建立 SharePoint 命令專案

1. 中**方案總管**，開啟方案節點的捷徑功能表，選擇**新增**，然後選擇**新專案**。

2. 中**新的專案**對話方塊方塊中，展開**Visual C#** 節點或**Visual Basic**  節點，然後選擇**Windows**節點。

3. 在對話方塊頂端，選擇 **.NET Framework 3.5**清單中的.NET Framework 版本。

4. 在專案範本清單中，選擇**類別庫**，將專案命名為**WebPartCommands**，然後選擇**確定**  按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**WebPartCommands**專案加入方案，並開啟預設 Class1 的程式碼檔案。

5. 從專案刪除 Class1 的程式碼檔案。

## <a name="configure-the-projects"></a>將專案設定
 您撰寫程式碼來建立擴充功能之前，您必須新增程式碼檔案和組件參考，並設定專案設定。

#### <a name="to-configure-the-webpartnodeextension-project"></a>若要設定 WebPartNodeExtension 專案

1. 在 WebPartNodeExtension 專案中加入四個具有下列名稱的程式碼檔案：

    - SiteNodeExtension

    - WebPartNodeTypeProvider

    - WebPartNodeInfo

    - WebPartCommandIds

2. 開啟捷徑功能表**WebPartNodeExtension**專案，，然後選擇**加入參考**。

3. 在 **參考管理員-WebPartNodeExtension**對話方塊方塊中，選擇**Framework**索引標籤，然後再選取下列組件的每個的 核取方塊：

    - System.ComponentModel.Composition

    - System.Windows.Forms

4. 選擇**延伸模組**索引標籤上的 Microsoft.VisualStudio.SharePoint 組件中，選取核取方塊，然後選擇**確定** 按鈕。

5. 在 **方案總管**，開啟捷徑功能表**WebPartNodeExtension**專案節點，然後選擇**屬性**。

     [專案設計工具] 隨即開啟。

6. 選擇 [應用程式] 索引標籤。

7. 在 [**預設命名空間**] 方塊中 (C#) 或**根命名空間**方塊 ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)])，輸入**ServerExplorer.SharePointConnections.WebPartNode**。

#### <a name="to-configure-the-webpartcommands-project"></a>若要設定 webpartcommands 專案

1. 在 WebPartCommands 專案中，加入名為 WebPartCommands 的程式碼檔案。

2. 在**方案總管 中**，開啟捷徑功能表**WebPartCommands**專案節點，選擇 **新增**，然後選擇 **現有項目**.

3. 在 **加入現有項目** 對話方塊中，瀏覽至包含 WebPartNodeExtension 專案中，程式碼檔案的資料夾，然後選擇 WebPartNodeInfo 和 WebPartCommandIds 的程式碼檔案。

4. 選擇箭號旁**新增**按鈕，然後再選擇**加入做為連結**中出現的功能表。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將程式碼檔案加入至 WebPartCommands 專案中，做為連結。 如此一來，程式碼檔案位於 WebPartNodeExtension 專案，但檔案中的程式碼也會經過編譯 WebPartCommands 專案中。

5. 開啟捷徑功能表**WebPartCommands**同樣地，專案，然後選擇**加入參考**。

6. 在 **參考管理員-WebPartCommands**對話方塊方塊中，選擇**擴充功能**索引標籤上，針對每個下列組件中，選取核取方塊，然後選擇**確定**按鈕：

    - Microsoft.SharePoint

    - Microsoft.VisualStudio.SharePoint.Commands

7. 在 **方案總管**，開啟捷徑功能表**WebPartCommands**同樣地，專案，然後選擇**屬性**。

     [專案設計工具] 隨即開啟。

8. 選擇 [應用程式] 索引標籤。

9. 在 [**預設命名空間**] 方塊中 (C#) 或**根命名空間**方塊 ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)])，輸入**ServerExplorer.SharePointConnections.WebPartNode**。

## <a name="create-icons-for-the-new-nodes"></a>建立新的節點圖示
 建立兩個圖示**伺服器總管**延伸模組： 新的圖示**網頁組件庫**節點，然後在每一個子網頁組件節點的另一個圖示**網頁組件庫**節點。 稍後在本逐步解說中，您將撰寫程式碼，將這些圖示與節點相關聯。

#### <a name="to-create-icons-for-the-nodes"></a>若要建立之節點的圖示

1. 在 [**方案總管] 中**，開啟捷徑功能表**WebPartNodeExtension**專案，，然後選擇**屬性**。

2. [專案設計工具] 隨即開啟。

3. 選擇**資源**索引標籤，然後選擇 **這個專案不包含預設資源檔。按一下這裡可建立一個**連結。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 建立資源檔，並在設計工具中開啟。

4. 在設計工具的頂端，選擇箭號旁**加入資源** 功能表命令，然後再選擇**加入新圖示**中出現的功能表。

5. 在**加入新的資源** 對話方塊中，名稱為 新增 圖示**WebPartsNode**，然後選擇**新增** 按鈕。

     在中，開啟 [新增] 圖示**影像編輯器**。

6. 編輯圖示的 16 x 16 個版本，使其具有可輕鬆辨識的設計。

7. 開啟圖示，32 x 32 版本的捷徑功能表，然後選擇**刪除映像類型**。

8. 重複步驟 5 至 8，將第二個圖示新增至專案資源，並命名此圖示**WebPart**。

9. 在 [**方案總管] 中**下方**資源**資料夾**WebPartNodeExtension**專案中，開啟捷徑功能表**WebPartsNode.ico**.

10. 在**屬性** 視窗中，選擇箭號旁**建置動作**，然後選擇**內嵌資源**上出現的功能表。

11. 重複最後兩個步驟**WebPart.ico**。

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>將網頁組件庫節點新增至伺服器總管
 建立的類別，會新增**網頁組件庫**SharePoint 站台的每個節點的節點。 若要新增新節點時，此類別會實作<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>介面。 實作這個介面，每當您想要擴充現有的節點中的行為**伺服器總管**，例如新增至節點的子節點。

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>若要將網頁組件庫節點新增至伺服器總管

1. 在 WebPartNodeExtension 專案中，開啟 SiteNodeExtension 程式碼檔案，並接著將下列程式碼貼到它。

    > [!NOTE]
    >  新增下列程式碼，專案會有某些編譯錯誤，但它們就會消失之後當您加入程式碼在稍後的步驟。

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>定義代表 web 組件的節點類型
 建立一個類別來定義新類型的節點，表示 Web 組件。 Visual Studio 會使用這個新的節點類型，以顯示子節點底下**網頁組件庫**節點。 每個子節點代表 SharePoint 網站上的單一 Web 組件。

 若要定義新的節點類型，此類別會實作<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>介面。 實作這個介面，每當您想要定義新類型的節點**伺服器總管**。

#### <a name="to-define-the-web-part-node-type"></a>若要定義 web 組件的節點類型

1. 在 WebPartNodeExtension 專案中，開啟 WebPartNodeTypeProvder 程式碼檔案，並接著將下列程式碼貼到它。

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]

## <a name="define-the-web-part-data-class"></a>定義 web 組件的資料類別
 定義包含單一的 Web 組件在 SharePoint 網站上的相關資料的類別。 稍後在本逐步解說中，您將建立自訂的 SharePoint 命令會擷取每個站台上的 Web 組件相關的資料，然後將資料指派給此類別的執行個體。

#### <a name="to-define-the-web-part-data-class"></a>若要定義 web 組件的資料類別

1. 在 WebPartNodeExtension 專案中，開啟 WebPartNodeInfo 程式碼檔案，並接著將下列程式碼貼到它。

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]

## <a name="define-the-ids-for-the-sharepoint-commands"></a>定義之 SharePoint 命令的識別碼
 定義識別自訂的 SharePoint 命令的數個字串。 您將在此逐步解說稍後實作這些命令。

#### <a name="to-define-the-command-ids"></a>若要定義命令識別碼

1. 在 WebPartNodeExtension 專案中，開啟 WebPartCommandIds 程式碼檔案，並接著將下列程式碼貼到它。

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]

## <a name="create-the-custom-sharepoint-commands"></a>建立自訂的 SharePoint 命令
 建立自訂的命令，來擷取 SharePoint 網站上的 Web 組件的相關資料的 SharePoint 伺服器物件模型呼叫。 每個命令是一種方法具有<xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute>套用到它。

#### <a name="to-define-the-sharepoint-commands"></a>若要定義的 SharePoint 命令

1. 在 WebPartCommands 專案中，開啟 WebPartCommands 程式碼檔案，並接著將下列程式碼貼到它。

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]

## <a name="checkpoint"></a>檢查點
 逐步解說中，所有的程式碼中，此時**網頁組件庫**節點和 SharePoint 命令已在專案中。 建置方案，以確定這兩個專案編譯無誤。

#### <a name="to-build-the-solution"></a>若要建置方案

1. 在功能表列上選擇 [建置] > [建置解決方案]。

    > [!WARNING]
    >  到目前為止，WebPartNode 專案可能有建置錯誤，因為在 VSIX 資訊清單檔案不具有任何值給作者。 當您將在稍後步驟中的值，這個錯誤就會消失運作。

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>建立 VSIX 封裝，來部署擴充功能
 若要建立 VSIX 封裝部署擴充功能，請在解決方案中使用 VSIX 專案。 首先，設定 VSIX 套件藉由修改 source.extension.vsixmanifest 檔案中的，在 VSIX 專案。 建立方案，然後建立 VSIX 封裝。

#### <a name="to-configure-the-vsix-package"></a>若要設定 VSIX 封裝

1. 在**方案總管**，，WebPartNode 專案之下，開啟**source.extension.vsixmanifest**資訊清單編輯器 中的檔案。

     Source.extension.vsixmanifest 檔案中會是所有的 VSIX 套件需要 extension.vsixmanifest 檔案的基礎。 如需有關這個檔案的詳細資訊，請參閱 < [VSIX 延伸結構描述 1.0 參考](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。

2. 在 **產品名稱**方塊中，輸入**的 伺服器總管 中的 Web 組件資源庫節點**。

3. 在 **作者**方塊中，輸入**Contoso**。

4. 在 [**描述**方塊中，輸入**將自訂的網頁組件庫節點加入至伺服器總管] 中的 SharePoint 連線節點。此延伸模組會呼叫伺服器物件模型中使用自訂的 SharePoint 命令。**

5. 選擇**資產**索引標籤，然後選擇**新增** 按鈕。

     **加入新資產** 對話方塊隨即出現。

6. 在 **型別**清單中，選擇**Microsoft.VisualStudio.MefComponent**。

    > [!NOTE]
    >  這個值會對應到`MefComponent`extension.vsixmanifest 檔案中的項目。 這個元素會指定在 VSIX 封裝中的延伸模組組件名稱。 如需詳細資訊，請參閱 < [MEFComponent 項目 （VSX 結構描述）](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))。

7. 在 **來源**清單中，選擇**目前方案中的專案**。

8. 在 **專案**清單中，選擇**WebPartNodeExtension** ，然後選擇 **確定** 按鈕。

9. 在資訊清單編輯器中，選擇**新增**按鈕一次。

     **加入新資產** 對話方塊隨即出現。

10. 在 **型別**方塊中，輸入**SharePoint.Commands.v4**。

    > [!NOTE]
    >  這個元素會指定您想要包含在 Visual Studio 擴充功能的自訂延伸模組。 如需詳細資訊，請參閱 <<c0> [ 資產項目 （VSX 結構描述）](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737)。

11. 在 **來源**清單中，選擇**目前方案中的專案**清單項目。

12. 在 [**專案**清單中，選擇**WebPartCommands**，然後選擇 **[確定]** ] 按鈕。

13. 在功能表列上選擇 **建置** > **建置方案**，然後確認方案編譯無誤。

14. 請確定 WebPartNode 專案建置輸出資料夾現在包含 WebPartNode.vsix 檔案。

     根據預設，會將組建輸出資料夾...在包含您的專案檔的資料夾下的 \bin\Debug 資料夾。

## <a name="test-the-extension"></a>測試此擴充功能
 您現在準備好進行測試的新**網頁組件庫**中的節點**伺服器總管**。 首先，啟動偵錯 Visual Studio 的實驗執行個體中的擴充功能。 然後，使用 新**Web 組件**實驗性執行個體中的節點[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

#### <a name="to-start-debugging-the-extension"></a>若要開始偵錯擴充功能

1. 重新啟動[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]與系統管理認證，然後開啟 WebPartNode 解決方案。

2. 在 WebPartNodeExtension 專案中，開啟 SiteNodeExtension 程式碼檔案，然後加入中斷點至第一行中的程式碼`NodeChildrenRequested`和`CreateWebPartNodes`方法。

3. 選擇**F5**鍵開始偵錯。

     Visual Studio 會 Server Explorer\1.0 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web 組件庫節點延伸模組安裝擴充功能，並啟動 Visual Studio 的實驗執行個體。 在 Visual Studio 這個執行個體中，您將測試專案項目。

#### <a name="to-test-the-extension"></a>若要測試此擴充功能

1. 在實驗執行個體[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，在功能表列上選擇**檢視** > **伺服器總管**。

2. 如果您想要用於測試的 SharePoint 網站不會出現在執行下列步驟**SharePoint 連線**中的節點**伺服器總管**:

    1. 在**伺服器總管**，開啟捷徑功能表**SharePoint 連線**，然後選擇**加入連接**。

    2. 在 [**加入 SharePoint 連接**對話方塊方塊中，輸入您想要連線，再選擇 SharePoint 網站的 URL**確定**] 按鈕。

         若要指定 SharePoint 網站的開發電腦上，輸入**http://localhost**。

3. 展開站台連線節點 （它會顯示您的網站 URL），然後再展開 子站台節點 (例如**小組網站**)。

4. 確認的其他執行個體中的程式碼[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]您稍早在設定的中斷點上停止`NodeChildrenRequested`方法，然後選擇**F5**繼續進行偵錯專案。

5. 在 Visual Studio 的實驗性執行個體，請確認新節點名為**網頁組件庫**下方的頂層站台 節點中，將會出現，然後展開**網頁組件庫**節點。

6. 確認停止您稍早在設定的中斷點上的 Visual Studio 的其他執行個體中的程式碼`CreateWebPartNodes`方法，然後選擇**F5**鍵繼續偵錯專案。

7. 在 Visual Studio 的實驗性執行個體，確認 連線的站台上的所有網頁組件都出現在**網頁組件庫**中的節點**伺服器總管**。

8. 在 **伺服器總管**，其中一個 Web 組件中，開啟捷徑功能表，然後選擇**屬性**。

9. 執行個體中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]您要偵錯，請確認 網頁組件的詳細資料，會出現在**屬性**視窗。

## <a name="uninstall-the-extension-from-visual-studio"></a>從 Visual Studio 解除安裝擴充功能
 完成測試擴充功能之後，解除安裝延伸模組，從 Visual Studio。

#### <a name="to-uninstall-the-extension"></a>安裝擴充功能

1. 在實驗執行個體[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，在功能表列上選擇**工具** > **擴充功能和更新**。

     [擴充功能和更新] 對話方塊隨即開啟。

2. 在延伸模組清單中，選擇**Web 組件庫的 伺服器總管 中的節點擴充**，然後選擇**解除安裝** 按鈕。

3. 在出現的對話方塊中，選擇 **[是]** 按鈕，以確認您要解除安裝延伸模組，然後選擇**立即重新啟動**按鈕以完成解除安裝。

4. 關閉 Visual Studio （實驗性執行個體和 WebPartNode 方案已開啟的 Visual Studio 執行個體） 的兩個執行個體。

## <a name="see-also"></a>另請參閱
- [擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [逐步解說：呼叫 SharePoint 用戶端物件模型，在 伺服器總管延伸模組](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)
- [圖示影像編輯器](/cpp/windows/image-editor-for-icons)
- [建立圖示或其他影像&#40;圖示影像編輯器&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)
