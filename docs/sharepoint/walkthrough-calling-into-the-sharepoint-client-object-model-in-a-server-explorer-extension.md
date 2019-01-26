---
title: 逐步解說：呼叫 SharePoint 用戶端物件模型，在 伺服器總管延伸模組 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b140a1dcadd86ed8d4c3634669ecf753ad84e25e
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873596"
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>逐步解說：呼叫 SharePoint 用戶端物件模型，在 伺服器總管延伸模組
  本逐步解說示範如何從的擴充功能呼叫 SharePoint 用戶端物件模型**SharePoint 連線**中的節點**伺服器總管**。 如需如何使用 SharePoint 用戶端物件模型的詳細資訊，請參閱[呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
 本逐步解說將示範下列工作：  
  
-   建立[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]可擴展**SharePoint 連線**節點**伺服器總管**如下：  
  
    -   擴充功能新增**網頁組件庫**節點中的每個 SharePoint 網站 節點底下**伺服器總管**。 這個新的節點包含代表站台上的 Web 組件庫中的每個 Web 組件的子節點。  
  
    -   延伸模組會定義新類型的節點，表示 Web 組件執行個體。 這個新的節點型別是在新的子節點的基礎**網頁組件庫**節點。 新的 Web 組件節點類型中顯示資訊**屬性**有關節點所表示之 Web 組件的視窗。  
  
-   建置 Visual Studio 擴充功能 (VSIX) 封裝來部署擴充功能。  
  
-   偵錯和測試延伸模組。  
  
> [!NOTE]  
>  您在本逐步解說中建立的延伸模組類似您在建立延伸[逐步解說：擴充伺服器總管以顯示 web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。 該逐步解說會使用 SharePoint 伺服器物件模型，但本逐步解說會使用用戶端物件模型來完成相同的工作。  
  
## <a name="prerequisites"></a>必要條件  
 您需要完成這個逐步解說在開發電腦上的下列元件：  
  
-   支援的 Windows、 SharePoint 和 Visual Studio 版本。
  
-   Visual Studio SDK 中。 本逐步解說會使用**VSIX 專案**建立 VSIX 封裝，來部署擴充功能 SDK 中的範本。 如需詳細資訊，請參閱 <<c0> [ 擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
下列概念的知識會很有幫助，但並非必要，若要完成本逐步解說：  
  
-   使用 SharePoint 用戶端物件模型。 如需詳細資訊，請參閱 <<c0> [ 受管理的用戶端物件模型](http://go.microsoft.com/fwlink/?LinkId=177797)。  
  
-   在 SharePoint 中的 web 組件。 如需詳細資訊，請參閱 < [Web 組件概觀](http://go.microsoft.com/fwlink/?LinkId=177803)。  
  
## <a name="create-the-projects"></a>建立專案
 若要完成此逐步解說中，您必須建立兩個專案：  
  
- 若要建立要部署的 VSIX 封裝 VSIX 專案**伺服器總管**延伸模組。  
  
- 實作的類別庫專案**伺服器總管**延伸模組。  
  
  開始本逐步解說建立的專案。  
  
#### <a name="to-create-the-vsix-project"></a>若要建立 VSIX 專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在功能表列上，選擇 [檔案] > [新增] > [專案]。  
  
3.  中**新的專案**對話方塊方塊中，展開**Visual C#** 或**Visual Basic**節點，然後選擇**擴充性**。  
  
    > [!NOTE]  
    >  **擴充性**節點才會提供您安裝 Visual Studio SDK。 如需詳細資訊，請參閱稍早在本主題中的必要條件 > 一節。  
  
4.  在對話方塊頂端，選擇 **.NET Framework 4.5**清單中的.NET Framework 版本。  
  
     SharePoint 工具擴充功能需要在這個版本的.NET Framework 的功能。  
  
5.  選擇**VSIX 專案**範本。  
  
6.  在 [**名稱**方塊中，輸入**WebPartNode**，然後選擇 **[確定]** ] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**WebPartNode**專案加入**方案總管 中**。  
  
#### <a name="to-create-the-extension-project"></a>若要建立擴充功能專案  
  
1.  中**方案總管**，開啟方案節點的捷徑功能表，選擇**新增**，然後選擇**新專案**。  
  
2.  在**新的專案**對話方塊方塊中，展開**Visual C#** 或**Visual Basic**節點，然後選擇**Windows**。  
  
3.  在對話方塊頂端，選擇 **.NET Framework 4.5**清單中的.NET Framework 版本。  
  
4.  在專案範本清單中，選擇**類別庫**。  
  
5.  在 [**名稱**方塊中，輸入**WebPartNodeExtension**，然後選擇 **[確定]** ] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**WebPartNodeExtension**專案加入方案，並開啟預設 Class1 的程式碼檔案。  
  
6.  從專案刪除 Class1 的程式碼檔案。  
  
## <a name="configure-the-extension-project"></a>設定擴充功能專案
 您撰寫程式碼來建立擴充功能之前，您必須新增程式碼檔案和組件參考加入至專案，也必須更新預設的命名空間。  
  
#### <a name="to-configure-the-project"></a>若要設定專案  
  
1.  在  **WebPartNodeExtension**專案中，加入名為 SiteNodeExtension 和 WebPartNodeTypeProvider 的兩個程式碼檔案。  
  
2.  開啟 WebPartNodeExtension 專案的捷徑功能表，然後選擇**加入參考**。  
  
3.  在 **參考管理員-WebPartNodeExtension**對話方塊方塊中，選擇**Framework**節點，然後針對 System.ComponentModel.Composition 和 System.Windows.Forms 的然後選取核取方塊組件。  
  
4.  選擇**延伸模組**節點，每個下列組件中，選取核取方塊，然後選擇**確定**按鈕：  
  
    -   Microsoft.SharePoint.Client  
  
    -   Microsoft.SharePoint.Client.Runtime  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  開啟捷徑功能表**WebPartNodeExtension**專案，，然後選擇**屬性**。  
  
     [專案設計工具] 隨即開啟。  
  
6.  選擇 [應用程式] 索引標籤。  
  
7.  在 [**預設命名空間**] 方塊中 (C#) 或**根命名空間**方塊 (Visual Basic) 中，輸入**ServerExplorer.SharePointConnections.WebPartNode**。  
  
## <a name="create-icons-for-the-new-nodes"></a>建立新的節點圖示
 建立兩個圖示**伺服器總管**延伸模組： 新的圖示**網頁組件庫**節點和每個子網頁組件節點下的另一個圖示**網頁組件庫**節點。 稍後在本逐步解說中，您將撰寫程式碼，將這些圖示與節點相關聯。  
  
#### <a name="to-create-icons-for-the-nodes"></a>若要建立之節點的圖示  
  
1.  在 [**專案設計工具**WebPartNodeExtension 專案中，選擇**資源**] 索引標籤。  
  
2.  選擇連結**這個專案不包含預設資源檔。若要建立一個，請按一下這裡。**  
  
     Visual Studio 建立的資源檔，並在設計工具中開啟。  
  
3.  在設計工具的頂端，選擇箭號上**加入資源** 功能表命令，然後再選擇**加入新圖示**。  
  
4.  輸入**WebPartsNode** 新增 圖示的名稱，然後再選擇**新增** 按鈕。  
  
     在中，開啟 [新增] 圖示**影像編輯器**。  
  
5.  編輯圖示的 16 x 16 個版本，使其具有可輕鬆辨識的設計。  
  
6.  開啟圖示，32 x 32 版本的捷徑功能表，然後選擇**刪除映像類型**。  
  
7.  重複步驟 3 到 7 以第二個圖示加入至專案資源，並命名此圖示**WebPart**。  
  
8.  在 [**方案總管] 中**，請在**資源**資料夾**WebPartNodeExtension**專案中，選擇*WebPartsNode.ico*。  
  
9. 在 **屬性**視窗中，開啟**建置動作**清單，，然後選擇**內嵌資源**。  
  
10. 重複最後兩個步驟*WebPart.ico*。  
  
## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>將 web 組件庫節點加入至伺服器總管
 建立的類別，會新增**網頁組件庫**SharePoint 站台的每個節點的節點。 若要新增新節點時，此類別會實作<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>介面。 實作這個介面，每當您想要擴充現有的節點中的行為**伺服器總管**，例如加入新的子節點的節點。  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>若要將 web 組件庫節點加入至伺服器總管
  
1.  貼上下列程式碼插入**SiteNodeExtension**程式碼檔案**WebPartNodeExtension**專案。  
  
    > [!NOTE]  
    >  新增下列程式碼之後，專案會有某些編譯錯誤。 當您在稍後步驟中加入程式碼時，這些錯誤就會消失運作。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="define-a-node-type-that-represents-a-web-part"></a>定義代表 web 組件的節點類型
 建立一個類別來定義新類型的節點，表示 Web 組件。 Visual Studio 會使用這個新的節點類型，以顯示子節點底下**網頁組件庫**節點。 每個這些子節點都代表單一的 Web 組件在 SharePoint 網站上。  
  
 若要定義新的節點類型，此類別會實作<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>介面。 實作這個介面，每當您想要定義新類型的節點**伺服器總管**。  
  
#### <a name="to-define-the-web-part-node-type"></a>若要定義 web 組件的節點類型
  
1.  貼上下列程式碼插入**WebPartNodeTypeProvider**程式碼檔案**WebPartNodeExtension**專案。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## <a name="checkpoint"></a>檢查點  
 逐步解說中，所有的程式碼中，此時**網頁組件庫**節點現在是在專案中。 建置**WebPartNodeExtension**專案，以確定它會編譯無誤。  
  
#### <a name="to-build-the-project"></a>建置專案  
  
1.  在 [**方案總管] 中**，開啟捷徑功能表**WebPartNodeExtension**專案，，然後選擇**建置**。  
  
## <a name="create-a-vsix-package-to-deploy-the-extension"></a>建立 VSIX 封裝，來部署擴充功能
 若要建立 VSIX 封裝部署擴充功能，請在解決方案中使用 VSIX 專案。 首先，設定 VSIX 套件藉由修改 source.extension.vsixmanifest 檔案中包含在專案中。 建立方案，然後建立 VSIX 封裝。  
  
#### <a name="to-configure-the-vsix-package"></a>若要設定 VSIX 封裝  
  
1.  在 **方案總管 中**，請在**WebPartNode**專案中，開啟**source.extension.vsixmanifest**資訊清單編輯器 中的檔案。  
  
     Source.extension.vsixmanifest 檔案中會是所有的 VSIX 套件需要 extension.vsixmanifest 檔案的基礎。 如需有關這個檔案的詳細資訊，請參閱 < [VSIX 延伸結構描述 1.0 參考](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在 **產品名稱**方塊中，輸入**的 伺服器總管 中的 Web 組件資源庫節點**。  
  
3.  在 **作者**方塊中，輸入**Contoso**。  
  
4.  在 [**描述**方塊中，輸入**將自訂的網頁組件庫節點加入至伺服器總管] 中的 SharePoint 連線節點**。  
  
5.  上**資產**索引標籤的 編輯器 中，選擇**新增** 按鈕。  
  
6.  在 **加入新資產**對話方塊中，於**型別**清單中，選擇**Microsoft.VisualStudio.MefComponent**。  
  
    > [!NOTE]  
    >  這個值會對應到`MefComponent`extension.vsixmanifest 檔案中的項目。 這個元素會指定在 VSIX 封裝中的延伸模組組件名稱。 如需詳細資訊，請參閱 < [MEFComponent 項目 （VSX 結構描述）](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))。  
  
7.  在 **來源**清單中，選擇**目前方案中的專案**。  
  
8.  在 [**專案**清單中，選擇**WebPartNodeExtension**，然後選擇 **[確定]** ] 按鈕。  
  
9. 在功能表列上選擇 **建置** > **建置方案**，然後確認方案編譯無誤。  
  
10. 請確定 WebPartNode 專案建置輸出資料夾現在包含 WebPartNode.vsix 檔案。  
  
     根據預設，會將組建輸出資料夾...在包含您的專案檔的資料夾下的 \bin\Debug 資料夾。  
  
## <a name="test-the-extension"></a>測試此擴充功能
 您現在已準備好測試的新**網頁組件庫**中的節點**伺服器總管**。 首先，開啟要偵錯擴充功能專案中的 Visual Studio 的實驗執行個體。 然後使用 新**Web 組件**Visual Studio 的實驗執行個體中的節點。  
  
#### <a name="to-start-debugging-the-extension"></a>若要開始偵錯擴充功能  
  
1.  使用系統管理認證，重新啟動 Visual Studio，然後開啟**WebPartNode**解決方案。  
  
2.  在 WebPartNodeExtension 專案中，開啟**SiteNodeExtension**程式碼檔案，然後再將中斷點新增程式碼中的前幾行`NodeChildrenRequested`和`CreateWebPartNodes`方法。  
  
3.  選擇**F5**鍵開始偵錯。  
  
     Visual Studio 會 Server Explorer\1.0 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web 組件庫節點延伸模組安裝擴充功能，並啟動 Visual Studio 的實驗執行個體。 在 Visual Studio 這個執行個體中，您將測試專案項目。  
  
#### <a name="to-test-the-extension"></a>若要測試此擴充功能  
  
1.  在實驗性 Visual Studio 執行個體，在功能表列上，選擇**檢視** > **伺服器總管**。  
  
2.  請確認您想要用於測試的 SharePoint 網站之下**SharePoint 連線**中的節點**伺服器總管**。 如果未列出，請遵循下列步驟：  
  
    1.  開啟捷徑功能表**SharePoint 連線**，然後選擇**加入連接**。  
  
    2.  在 [**加入 SharePoint 連接**對話方塊方塊中，輸入您想要連線，再選擇 SharePoint 網站的 URL**確定**] 按鈕。  
  
         若要指定 SharePoint 網站的開發電腦上，輸入**http://localhost**。  
  
3.  展開站台連線節點 （它會顯示您的網站 URL），然後再展開 子站台節點 (例如**小組網站**)。  
  
4.  確認停止您稍早在設定的中斷點上的 Visual Studio 的其他執行個體中的程式碼`NodeChildrenRequested`方法，然後選擇**F5**鍵繼續偵錯專案。  
  
5.  在 Visual Studio 的實驗性執行個體，依序展開**網頁組件庫**節點，就會出現在頂層站台 節點下。  
  
6.  確認停止您稍早在設定的中斷點上的 Visual Studio 的其他執行個體中的程式碼`CreateWebPartNodes`方法，然後選擇**F5**鍵繼續偵錯專案。  
  
7.  在 Visual Studio 的實驗性執行個體，確認 已連線的站台上的所有網頁組件都出現在**網頁組件庫**中的節點**伺服器總管**。  
  
8.  在 Web 組件中，開啟捷徑功能表，然後選擇**屬性**。  
  
9. 在 [**屬性**] 視窗中，確認詳細資料網頁組件會出現。  
  
10. 在 **伺服器總管**，針對相同的 Web 組件中，開啟捷徑功能表，然後選擇**Display Message**。  
  
     在隨即出現訊息方塊中，選擇**確定** 按鈕。  
  
## <a name="uninstall-the-extension-from-visual-studio"></a>從 Visual Studio 解除安裝擴充功能
 完成測試擴充功能之後，請從 Visual Studio 將它解除安裝。  
  
#### <a name="to-uninstall-the-extension"></a>安裝擴充功能  
  
1.  在實驗性 Visual Studio 執行個體，在功能表列上，選擇**工具** > **擴充功能和更新**。  
  
     [擴充功能和更新] 對話方塊隨即開啟。  
  
2.  在延伸模組清單中，選擇**伺服器總管 中的 Web 組件組件庫節點**，然後選擇**解除安裝** 按鈕。  
  
3.  在出現的對話方塊中，選擇**是** 按鈕。  
  
4.  選擇**立即重新啟動**按鈕以完成解除安裝。  
  
     專案項目也會解除安裝。  
  
5.  關閉 Visual Studio （實驗性執行個體和 WebPartNode 方案已開啟的 Visual Studio 執行個體） 的兩個執行個體。  
  
## <a name="see-also"></a>另請參閱
 [呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [逐步解說：擴充伺服器總管以顯示 web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [圖示影像編輯器](/cpp/windows/image-editor-for-icons)   
 [建立圖示或其他影像&#40;圖示影像編輯器&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)