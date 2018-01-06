---
title: "逐步解說： 擴充伺服器總管 以顯示 Web 組件 |Microsoft 文件"
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
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
ms.assetid: 5b1f104a-0eaf-4929-9f1f-d7afcfc8b707
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8fea089340c0d51fb5b88bf20d5521defc5dcc71
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-extending-server-explorer-to-display-web-parts"></a>逐步解說：擴充伺服器總管以顯示 Web 組件
  在 Visual Studio 中，您可以使用**SharePoint 連接**節點**伺服器總管**檢視 SharePoint 網站上的元件。 不過，**伺服器總管**預設不會顯示某些元件。 在本逐步解說中，您將會延長**伺服器總管**，使其顯示 Web 組件庫上每個連線的 SharePoint 網站。  
  
 本逐步解說將示範下列工作：  
  
-   建立 Visual Studio 擴充功能擴充**伺服器總管**如下：  
  
    -   擴充功能加入**網頁組件庫**節點中的每個 SharePoint 網站 節點下**伺服器總管**。 此一新節點會包含代表站台上的 Web 組件庫中的每個 Web 組件的子節點。  
  
    -   延伸模組會定義新類型的節點，表示 Web 組件執行個體。 這個新的節點型別是在新的子節點的基礎**網頁組件庫**節點。 新的 Web 組件節點類型會顯示在資訊**屬性**它代表 Web 組件相關的視窗。 節點型別也包含您可以使用做為起點來執行其他與 Web 組件相關聯的工作的自訂快顯功能表項目。  
  
-   建立兩個自訂 SharePoint 命令的延伸模組組件呼叫。 SharePoint 命令是使用伺服器物件模型中的應用程式開發介面 for SharePoint 的延伸模組組件可以呼叫的方法。 在本逐步解說中，您可以建立從開發電腦上之本機 SharePoint 網站擷取 Web 組件資訊的命令。 如需詳細資訊，請參閱[呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
-   建置 Visual Studio 擴充功能 (VSIX) 封裝，部署延伸模組。  
  
-   偵錯和測試擴充功能。  
  
> [!NOTE]  
>  For SharePoint 會使用用戶端物件模型，而不是其伺服器物件模型本逐步解說的替代版本，請參閱[逐步解說： 呼叫 SharePoint 用戶端物件模型，在伺服器總管擴充功能](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說在開發電腦上：  
  
-   支援的 Windows、 SharePoint 和 Visual Studio 版本。 如需詳細資訊，請參閱[開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio SDK。 本逐步解說使用**VSIX 專案**SDK，以建立 VSIX 封裝，來部署專案項目中的範本。 如需詳細資訊，請參閱[擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 了解下列概念是有幫助，但並非必要，完成此逐步解說：  
  
-   使用 for SharePoint 的伺服器物件模型。 如需詳細資訊，請參閱[使用 SharePoint Foundation 伺服器端物件模型](http://go.microsoft.com/fwlink/?LinkId=177796)。  
  
-   SharePoint 方案中的 web 組件。 如需詳細資訊，請參閱[Web 組件概觀](http://go.microsoft.com/fwlink/?LinkId=177803)。  
  
## <a name="creating-the-projects"></a>建立專案  
 若要完成此逐步解說，您必須建立三個專案：  
  
-   若要建立 VSIX 封裝，來部署擴充功能 VSIX 專案。  
  
-   類別庫專案，可實作延伸。 此專案必須以.NET Framework 4.5 為目標。  
  
-   類別庫專案來定義自訂 SharePoint 命令。 此專案必須以.net Framework 3.5 為目標。  
  
 開始本逐步解說建立的專案。  
  
#### <a name="to-create-the-vsix-project"></a>若要建立 VSIX 專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。  
  
3.  在**新專案**對話方塊方塊中，展開  **Visual C#**或**Visual Basic**節點，然後選擇 **擴充性**節點。  
  
    > [!NOTE]  
    >  **擴充性**節點才會提供您安裝 Visual Studio SDK。 如需詳細資訊，請參閱稍早在本主題中的必要條件 > 一節。  
  
4.  在對話方塊頂端，選擇  **.NET Framework 4.5**清單中的.NET Framework 版本。  
  
5.  選擇**VSIX 專案**範本，將專案**WebPartNode**，然後選擇 [**確定**] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]新增**WebPartNode**專案加入**方案總管 中**。  
  
#### <a name="to-create-the-extension-project"></a>若要建立擴充功能專案  
  
1.  在**方案總管] 中**，開啟 [解決方案] 節點的捷徑功能表，選擇**新增**，然後選擇 [**新專案**。  
  
2.  在**新專案**對話方塊方塊中，展開 [ **Visual C#**節點或**Visual Basic** ] 節點，然後再選擇**Windows**節點。  
  
3.  在對話方塊頂端，選擇  **.NET Framework 4.5**清單中的.NET Framework 版本。  
  
4.  在專案範本清單中選擇**類別庫**，將專案命名**WebPartNodeExtension**，然後選擇 [ **[確定]** ] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]新增**WebPartNodeExtension**專案加入方案，並開啟預設 Class1 的程式碼檔。  
  
5.  從專案刪除 Class1 的程式碼檔案。  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>若要建立 SharePoint 命令專案  
  
1.  在**方案總管] 中**，開啟 [解決方案] 節點的捷徑功能表，選擇**新增**，然後選擇 [**新專案**。  
  
2.  在**新專案**對話方塊方塊中，展開  **Visual C#**節點或**Visual Basic**  節點，然後選擇  **Windows**節點。  
  
3.  在對話方塊頂端，選擇  **.NET Framework 3.5**清單中的.NET Framework 版本。  
  
4.  
  
5.  在專案範本清單中選擇**類別庫**，將專案命名**WebPartCommands**，然後選擇 [ **[確定]** ] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]新增**WebPartCommands**專案加入方案，並開啟預設 Class1 的程式碼檔。  
  
6.  從專案刪除 Class1 的程式碼檔案。  
  
## <a name="configuring-the-projects"></a>設定專案  
 您撰寫程式碼來建立擴充功能之前，您必須新增程式碼檔案和組件參考，並設定專案設定。  
  
#### <a name="to-configure-the-webpartnodeextension-project"></a>若要設定 WebPartNodeExtension 專案  
  
1.  在 WebPartNodeExtension 專案中，加入四個具有下列名稱的程式碼檔案：  
  
    -   SiteNodeExtension  
  
    -   WebPartNodeTypeProvider  
  
    -   WebPartNodeInfo  
  
    -   WebPartCommandIds  
  
2.  開啟快顯功能表**WebPartNodeExtension**專案，然後再選擇**加入參考**。  
  
3.  在**參考管理員-WebPartNodeExtension**對話方塊方塊中，選擇**Framework**索引標籤，然後選取下列組件的每個核取方塊：  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
4.  選擇**延伸**索引標籤上，對於 Microsoft.VisualStudio.SharePoint 組件中，選取核取方塊，然後選擇**確定** 按鈕。  
  
5.  在**方案總管 中**，開啟捷徑功能表**WebPartNodeExtension**專案節點，然後選擇**屬性**。  
  
     [專案設計工具] 隨即開啟。  
  
6.  選擇 [應用程式] 索引標籤。  
  
7.  在**預設命名空間**方塊 (C#) 或**根命名空間**方塊 ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)])，輸入**ServerExplorer.SharePointConnections.WebPartNode**。  
  
#### <a name="to-configure-the-webpartcommands-project"></a>若要設定 WebPartCommands 專案  
  
1.  在 WebPartCommands 專案中，加入名為 WebPartCommands 的程式碼檔案。  
  
2.  在**方案總管] 中**，開啟捷徑功能表**WebPartCommands**專案節點時，選擇**新增**，然後選擇 [**現有項目**.  
  
3.  在**加入現有項目**對話方塊中，瀏覽至包含 WebPartNodeExtension 專案的程式碼檔案的資料夾，然後選擇 WebPartNodeInfo 和 WebPartCommandIds 的程式碼檔案。  
  
4.  選擇箭號旁**新增**按鈕，然後再選擇**加入做為連結**中出現的功能表。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]將程式碼檔案加入至 WebPartCommands 專案中，做為連結。 如此一來，在程式碼檔案位於 WebPartNodeExtension 專案，但檔案中的程式碼也會編譯 WebPartCommands 專案中。  
  
5.  開啟快顯功能表**WebPartCommands**同樣地，專案，選擇**加入參考**。  
  
6.  在**參考管理員-WebPartCommands**對話方塊方塊中，選擇**延伸**索引標籤上的下列組件中，每個選取核取方塊，然後選擇 **確定**按鈕：  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
7.  在**方案總管 中**，開啟捷徑功能表**WebPartCommands**同樣地，專案，然後選擇**屬性**。  
  
     [專案設計工具] 隨即開啟。  
  
8.  選擇 [應用程式] 索引標籤。  
  
9. 在**預設命名空間**方塊 (C#) 或**根命名空間**方塊 ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)])，輸入**ServerExplorer.SharePointConnections.WebPartNode**。  
  
## <a name="creating-icons-for-the-new-nodes"></a>建立新的節點圖示  
 建立兩個圖示的**伺服器總管**延伸模組： 新的圖示**網頁組件庫**節點，然後在每一個子系 Web 組件節點的另一個圖示**網頁組件庫**節點。 稍後在本逐步解說，您將撰寫將這些圖示與節點相關聯的程式碼。  
  
#### <a name="to-create-icons-for-the-nodes"></a>若要建立節點圖示  
  
1.  在**方案總管 中**，開啟捷徑功能表**WebPartNodeExtension**專案，然後再選擇**屬性**。  
  
2.  [專案設計工具] 隨即開啟。  
  
3.  選擇**資源**索引標籤，然後選擇 **這個專案未包含預設的資源檔。按一下這裡可建立一個**連結。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]建立資源檔，並在設計工具中開啟。  
  
4.  在設計工具的頂端，選擇箭號旁**加入資源**功能表命令，然後再選擇**加入新圖示**中出現的功能表。  
  
5.  在**加入新的資源**對話方塊中，名稱為 [新增] 圖示**WebPartsNode**，然後選擇 [**新增**] 按鈕。  
  
     在中，開啟 [新增] 圖示**影像編輯器**。  
  
6.  編輯 16 x 16 版本的圖示，使其具有容易辨識的設計。  
  
7.  開啟 32 x 32 版本圖示的捷徑功能表，然後選擇**刪除映像類型**。  
  
8.  重複步驟 5 至 8，將第二個圖示新增至專案資源，並命名此圖示**WebPart**。  
  
9. 在**方案總管 中**下**資源**資料夾**WebPartNodeExtension**專案中，開啟捷徑功能表**WebPartsNode.ico**.  
  
10. 在**屬性**視窗中，選擇箭號旁**建置動作**，然後選擇 **內嵌資源**上出現的功能表。  
  
11. 重複最後兩個步驟**WebPart.ico**。  
  
## <a name="adding-the-web-part-gallery-node-to-server-explorer"></a>將網頁組件庫節點新增至伺服器總管  
 建立類別，會新增**網頁組件庫**SharePoint 站台的每個節點的節點。 若要加入新的節點，該類別會實作<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>介面。 實作這個介面，每當您想要擴充現有的節點中的行為**伺服器總管**，例如新增節點的子節點。  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>若要將網頁組件庫節點新增至伺服器總管  
  
1.  在 WebPartNodeExtension 專案中，開啟 SiteNodeExtension 程式碼檔案，並接著將下列程式碼貼入其中。  
  
    > [!NOTE]  
    >  加入下列程式碼，專案就會發生編譯錯誤，但它們會消失之後當您加入程式碼在稍後步驟中。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="defining-a-node-type-that-represents-a-web-part"></a>定義代表 Web 組件的節點類型  
 建立一個類別來定義新類型的節點，表示 Web 組件。 Visual Studio 會使用這個新的節點類型來顯示下的子節點**網頁組件庫**節點。 每個子節點都代表單一的 Web 組件在 SharePoint 網站上。  
  
 若要定義新的節點類型，該類別會實作<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>介面。 實作這個介面，每當您想要定義新類型的節點中**伺服器總管**。  
  
#### <a name="to-define-the-web-part-node-type"></a>若要定義 Web 組件的節點型別  
  
1.  在 WebPartNodeExtension 專案中，開啟 WebPartNodeTypeProvder 程式碼檔案，並接著將下列程式碼貼入其中。  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]  
  
## <a name="defining-the-web-part-data-class"></a>定義在 Web 組件的資料類別  
 定義包含在 SharePoint 網站上的單一 Web 組件的相關資料的類別。 稍後在本逐步解說，您將建立自訂 SharePoint 命令會擷取站台上每個 Web 組件相關的資料，然後將資料指派給此類別的執行個體。  
  
#### <a name="to-define-the-web-part-data-class"></a>若要定義 Web 組件的資料類別  
  
1.  在 WebPartNodeExtension 專案中，開啟 WebPartNodeInfo 程式碼檔案，並接著將下列程式碼貼入其中。  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]  
  
## <a name="defining-the-ids-for-the-sharepoint-command"></a>SharePoint 命令定義 Id  
 定義數個識別自訂 SharePoint 命令的字串。 您將在本逐步解說稍後實作這些命令。  
  
#### <a name="to-define-the-command-ids"></a>若要定義的命令 Id  
  
1.  在 WebPartNodeExtension 專案中，開啟 WebPartCommandIds 程式碼檔案，並接著將下列程式碼貼入其中。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]  
  
## <a name="creating-the-custom-sharepoint-commands"></a>建立自訂 SharePoint 命令  
 建立自訂的命令，呼叫以擷取 SharePoint 網站上的 Web 組件的相關資料的 sharepoint 伺服器物件模型。 每個命令是一種方法具有<xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute>套用到它。  
  
#### <a name="to-define-the-sharepoint-commands"></a>若要定義 SharePoint 命令  
  
1.  在 WebPartCommands 專案中，開啟 WebPartCommands 程式碼檔案，並接著將下列程式碼貼入其中。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]  
  
## <a name="checkpoint"></a>檢查點  
 逐步解說中，所有的程式碼中，此時**網頁組件庫**節點和 SharePoint 命令是現在專案中。 建置方案，以確定這兩個專案編譯無誤。  
  
#### <a name="to-build-the-solution"></a>若要建置方案  
  
1.  在功能表列上，選擇 [建置] 、[建置方案] 。  
  
    > [!WARNING]  
    >  此時，WebPartNode 專案可能有建置錯誤，因為 VSIX 資訊清單檔案不會有的作者的值。 當您將在稍後步驟中的值，這個錯誤就會消失運作。  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>建立 VSIX 封裝，來部署擴充功能  
 若要部署擴充功能，方案中使用 VSIX 專案建立 VSIX 封裝。 首先，設定 VSIX 封裝，藉由修改 source.extension.vsixmanifest 檔案中的，在 VSIX 專案。 建立方案，然後建立 VSIX 封裝。  
  
#### <a name="to-configure-the-vsix-package"></a>若要設定 VSIX 套件  
  
1.  在**方案總管 中**，WebPartNode 專案底下開啟**source.extension.vsixmanifest**資訊清單編輯器中的檔案。  
  
     Source.extension.vsixmanifest 檔案是所有的 VSIX 套件需要 extension.vsixmanifest 檔案的基礎。 如需有關這個檔案的詳細資訊，請參閱[VSIX 擴充功能結構描述 1.0 參考](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在**產品名稱**方塊中，輸入**伺服器總管 的 Web 組件庫節點**。  
  
3.  在**作者**方塊中，輸入**Contoso**。  
  
4.  在**描述**方塊中，輸入**將自訂的 Web 組件庫節點加入至伺服器總管中的 SharePoint 連線節點。此延伸模組會使用自訂 SharePoint 命令呼叫的伺服器物件模型。**  
  
5.  選擇**資產** 索引標籤的編輯器，然後選擇 **新增** 按鈕。  
  
     **加入新資產** 對話方塊隨即出現。  
  
6.  在**類型**清單中，選擇**Microsoft.VisualStudio.MefComponent**。  
  
    > [!NOTE]  
    >  這個值會對應到`MefComponent`extension.vsixmanifest 檔案中的項目。 這個項目 VSIX 封裝中指定延伸模組組件的名稱。 如需詳細資訊，請參閱[MEFComponent 元素 （VSX 結構描述）](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
7.  在**來源**清單中，選擇**目前方案中的專案**。  
  
8.  在**專案**清單中，選擇**WebPartNodeExtension** ，然後選擇 [**確定**] 按鈕。  
  
9. 在資訊清單編輯器中，選擇 **新增**按鈕一次。  
  
     **加入新資產** 對話方塊隨即出現。  
  
10. 在**類型**方塊中，輸入**SharePoint.Commands.v4**。  
  
    > [!NOTE]  
    >  這個項目會指定您想要包含在 Visual Studio 擴充功能的自訂延伸模組。 如需詳細資訊，請參閱[資產項目 （VSX 結構描述）](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737)。  
  
11. 在**來源**清單中，選擇**目前方案中的專案**清單項目。  
  
12. 在**專案**清單中，選擇**WebPartCommands**，然後選擇 [**確定**] 按鈕。  
  
13. 在功能表列上選擇 **建置**，**建置方案**，然後確認方案編譯無誤。  
  
14. 請確定 WebPartNode 專案建置輸出資料夾現在包含 WebPartNode.vsix 檔案。  
  
     根據預設，會將組建輸出資料夾...包含專案檔的資料夾下的 \bin\Debug 資料夾。  
  
## <a name="testing-the-extension"></a>測試擴充功能  
 您現在可以測試新**網頁組件庫**節點**伺服器總管**。 首先，開始偵錯 Visual studio 的實驗執行個體中的擴充功能。 然後，使用 新**Web 組件**實驗執行個體中的節點[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
#### <a name="to-start-debugging-the-extension"></a>若要啟動偵錯擴充功能  
  
1.  重新啟動[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]與系統管理認證，然後再開啟 WebPartNode 方案。  
  
2.  在 WebPartNodeExtension 專案中，開啟 SiteNodeExtension 程式碼檔案，並再將中斷點加入至程式碼中的第一行`NodeChildrenRequested`和`CreateWebPartNodes`方法。  
  
3.  選擇 F5 鍵開始偵錯。  
  
     Visual Studio 會伺服器 Explorer\1.0 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web 組件庫節點的擴充功能安裝擴充功能，並啟動 Visual studio 的實驗執行個體。 您將這個執行個體的 Visual Studio 中測試的專案項目。  
  
#### <a name="to-test-the-extension"></a>若要測試擴充功能  
  
1.  在實驗執行個體[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，在功能表列上選擇 **檢視**，**伺服器總管**。  
  
2.  執行下列步驟，如果您想要用於測試的 SharePoint 網站不會出現在**SharePoint 連接**節點**伺服器總管**:  
  
    1.  在**伺服器總管**，開啟捷徑功能表**SharePoint 連接**，然後選擇 **加入連接**。  
  
    2.  在**加入 SharePoint 連接**對話方塊方塊中，輸入您想要連接，再選擇 SharePoint 網站的 URL**確定** 按鈕。  
  
         若要在開發電腦上指定的 SharePoint 網站，請輸入**http://localhost**。  
  
3.  展開站台連線節點 （它會顯示您的網站的 URL），然後再展開子站台節點 (例如，**小組網站**)。  
  
4.  確認其他執行個體中的程式碼[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]您稍早在設定的中斷點上停止`NodeChildrenRequested`方法，然後選擇 f5 鍵繼續偵錯專案。  
  
5.  在 Visual Studio 的實驗執行個體，請確認新節點名為**網頁組件庫**的頂層站台節點下，會出現，然後展開 **網頁組件庫**節點。  
  
6.  確認 Visual Studio 的其他執行個體中的程式碼是您稍早在設定的中斷點上停止`CreateWebPartNodes`方法，然後選擇 F5 鍵以繼續進行偵錯專案。  
  
7.  在 Visual Studio 的實驗執行個體，確認 已連線的站台上的所有網頁組件都出現在**網頁組件庫**節點**伺服器總管**。  
  
8.  在**伺服器總管**，其中一個 Web 組件中，開啟捷徑功能表，然後選擇**屬性**。  
  
9. 執行個體中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]您要偵錯，請確認網頁組件的詳細資料，會出現在**屬性**視窗。  
  
## <a name="uninstalling-the-extension-from-visual-studio"></a>從 Visual Studio 解除安裝擴充功能  
 在您完成測試擴充功能之後，解除安裝擴充功能，從 Visual Studio。  
  
#### <a name="to-uninstall-the-extension"></a>安裝擴充功能  
  
1.  在實驗執行個體[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，在功能表列上選擇 **工具**，**擴充功能和更新**。  
  
     [擴充功能和更新] 對話方塊隨即開啟。  
  
2.  在擴充功能清單中，選擇  **Web 組件 Gallery 節點擴充伺服器總管**，然後選擇 **解除安裝** 按鈕。  
  
3.  在出現的對話方塊中，選擇 **是**按鈕，以確認您要解除安裝擴充功能，然後選擇 **立即重新啟動**按鈕，以完成解除安裝。  
  
4.  關閉 Visual Studio （實驗性執行個體和 WebPartNode 方案已開啟的 Visual Studio 執行個體） 的兩個執行個體。  
  
## <a name="see-also"></a>請參閱  
 [擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [逐步解說： 呼叫 SharePoint 用戶端物件模型，在伺服器總管擴充功能](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)   
 [圖示影像編輯器](/cpp/windows/image-editor-for-icons)   
 [建立圖示或其他影像 &#40; 影像編輯器的圖示 &#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  