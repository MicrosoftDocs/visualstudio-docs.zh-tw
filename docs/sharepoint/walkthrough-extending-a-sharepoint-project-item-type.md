---
title: 逐步解說： 擴充 SharePoint 專案項目類型 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ed2c425af4127af443254bfdc269d58c653bb3c9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-extending-a-sharepoint-project-item-type"></a>逐步解說：擴充 SharePoint 專案項目類型
  您可以使用**商務資料連接模型**專案項目在 SharePoint 中建立商務資料連線 (BDC) 服務的型號。 根據預設，當您建立模型時使用此專案項目中，模型中的資料不是顯示給使用者。 您也必須建立一個外部清單，在 SharePoint 中，讓使用者可以檢視資料。  
  
 在本逐步解說，您將建立的副檔名**商務資料連接模型**專案項目。 開發人員可以使用延伸模組的 BDC 模型中的資料顯示其專案中建立外部清單。 本逐步解說將示範下列工作：  
  
-   建立 Visual Studio 擴充功能會執行兩個主要工作：  
  
    -   它會產生一個外部清單，BDC 模型中顯示的資料。 延伸模組會使用 SharePoint 專案系統的物件模型來產生定義清單的 Elements.xml 檔案。 它也將檔案加入專案，以便為 BDC 模型一起部署。  
  
    -   它會加入快顯功能表項目**商務資料連接模型**專案中的項目**方案總管 中**。 開發人員可以按一下這個功能表項目，來產生 BDC 模型的外部清單。  
  
-   建立 Visual Studio 擴充功能 (VSIX) 封裝部署延伸模組組件。  
  
-   測試擴充功能。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說在開發電腦上：  
  
-   支援的 Microsoft Windows、 SharePoint 和 Visual Studio 版本。 如需詳細資訊，請參閱[開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。 本逐步解說使用**VSIX 專案**SDK，以建立 VSIX 封裝，來部署專案項目中的範本。 如需詳細資訊，請參閱[擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 了解下列概念是有幫助，但並非必要，完成此逐步解說：  
  
-   中的 BDC 服務[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]。 如需詳細資訊，請參閱[BDC 架構](http://go.microsoft.com/fwlink/?LinkId=177798)。  
  
-   BDC 模型的 XML 結構描述。 如需詳細資訊，請參閱[BDC 模型基礎結構](http://go.microsoft.com/fwlink/?LinkId=177799)。  
  
## <a name="creating-the-projects"></a>建立專案  
 若要完成此逐步解說，您必須建立兩個專案：  
  
-   若要建立 VSIX 封裝來部署專案項目擴充功能 VSIX 專案。  
  
-   實作專案項目擴充功能的類別庫專案。  
  
 開始本逐步解說建立的專案。  
  
#### <a name="to-create-the-vsix-project"></a>若要建立 VSIX 專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。  
  
3.  在**新專案**對話方塊方塊中，展開  **Visual C#**或**Visual Basic**節點，然後選擇 **擴充性**節點。  
  
    > [!NOTE]  
    >  **擴充性**節點才會提供您安裝 Visual Studio SDK。 如需詳細資訊，請參閱稍早在本主題中的必要條件 > 一節。  
  
4.  在清單頂端的**新專案**對話方塊方塊中，選擇**.NET Framework 4.5**。  
  
     SharePoint 工具擴充功能需要這個版本的.NET Framework 中的功能。  
  
5.  選擇**VSIX 專案**範本。  
  
6.  在**名稱**方塊中，輸入**GenerateExternalDataLists**，然後選擇 [**確定**] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**GenerateExternalDataLists**專案加入**方案總管 中**。  
  
7.  如果未自動開啟 source.extension.vsixmanifest 檔案中，在 GenerateExternalDataLists 專案中，開啟其捷徑功能表，然後選擇**開啟**  
  
8.  確認 source.extension.vsixmanifest 檔案中有非空白的項目 （輸入 Contoso） 的 [作者] 欄位中，儲存檔案，並關閉。  
  
#### <a name="to-create-the-extension-project"></a>若要建立擴充功能專案  
  
1.  在**方案總管] 中**，開啟捷徑功能表**GenerateExternalDataLists**方案節點，選擇**新增**，然後選擇 [ **新的專案**.  
  
2.  在**加入新的專案**對話方塊方塊中，展開  **Visual C#**或**Visual Basic**節點，然後選擇  **Windows**節點。  
  
3.  在清單頂端的對話方塊中，選擇  **.NET Framework 4.5**。  
  
4.  在專案範本清單中選擇**類別庫**。  
  
5.  在**名稱**方塊中，輸入**BdcProjectItemExtension**，然後選擇 [**確定**] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**BdcProjectItemExtension**專案加入方案，並開啟預設 Class1 的程式碼檔。  
  
6.  從專案刪除 Class1 的程式碼檔案。  
  
## <a name="configuring-the-extension-project"></a>設定擴充功能專案  
 您撰寫程式碼以建立專案項目擴充功能之前，加入程式碼檔案和擴充功能專案中的組件參考。  
  
#### <a name="to-configure-the-project"></a>若要設定專案  
  
1.  在 BdcProjectItemExtension 專案中，加入兩個具有下列名稱的程式碼檔案：  
  
    -   ProjectItemExtension  
  
    -   GenerateExternalDataLists  
  
2.  選擇 BdcProjectItemExtension 專案，然後在功能表列上選擇 **專案**，**加入參考**。  
  
3.  在下**組件** 節點，選擇**Framework**節點，然後選取核取方塊為每個下列組件：  
  
    -   System.ComponentModel.Composition  
  
    -   WindowsBase  
  
4.  在下**組件** 節點，選擇**延伸**節點，然後再選取核取方塊，為下列組件：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  選擇 [確定]  按鈕。  
  
## <a name="defining-the-project-item-extension"></a>定義專案項目擴充功能  
 建立一個類別來定義的擴充功能**商務資料連接模型**專案項目。 若要定義的延伸模組，該類別會實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>介面。 每當您想要擴充現有類型的專案項目，請實作這個介面。  
  
#### <a name="to-define-the-project-item-extension"></a>若要定義專案項目擴充功能  
  
1.  貼上下列程式碼 ProjectItemExtension 程式碼檔案。  
  
    > [!NOTE]  
    >  加入下列程式碼之後，專案將會有一些編譯錯誤。 當您在稍後步驟中加入程式碼，這些錯誤就會消失運作。  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb#1)]  
  
## <a name="creating-the-external-data-lists"></a>建立外部資料清單  
 新增的部分定義`GenerateExternalDataListsExtension`BDC 模型中建立外部資料清單的每個實體的類別。 若要建立外部資料 清單中，此程式碼會先讀取 BDC 模型中的實體資料藉由剖析 BDC 模型檔案中的 XML 資料。 然後，它會建立 BDC 模型為基礎，並將此清單執行個體加入至專案的清單執行個體。  
  
#### <a name="to-create-the-external-data-lists"></a>若要建立外部資料清單  
  
1.  將下列程式碼貼到 GenerateExternalDataLists 程式碼檔案。  
  
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs#2)]  
  
## <a name="checkpoint"></a>檢查點  
 此時在逐步解說中，所有的程式碼專案項目擴充功能現在是在專案中。 建置方案，以確定專案編譯無誤。  
  
#### <a name="to-build-the-solution"></a>若要建置方案  
  
1.  在功能表列上，選擇 [建置] 、[建置方案] 。  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-item-extension"></a>建立 VSIX 封裝，來部署專案項目擴充功能  
 若要部署擴充功能，方案中使用 VSIX 專案建立 VSIX 封裝。 首先，設定 VSIX 封裝，藉由修改 source.extension.vsixmanifest 檔案中包含在 VSIX 專案。 建立方案，然後建立 VSIX 封裝。  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>若要設定，並建立 VSIX 封裝  
  
1.  在**方案總管] 中**GenerateExternalDataLists 專案中，開啟 source.extension.vsixmanifest 檔案中的捷徑功能表，然後選擇 [**開啟**。  
  
     Visual Studio 會在資訊清單編輯器中開啟檔案。 Source.extension.vsixmanifest 檔案是所有的 VSIX 套件所需的基礎 extension.vsixmanifest 檔案。 如需有關這個檔案的詳細資訊，請參閱[VSIX 擴充功能結構描述 1.0 參考](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在**產品名稱**方塊中，輸入**外部的資料清單產生器**。  
  
3.  在**作者**方塊中，輸入**Contoso**。  
  
4.  在**描述**方塊中，輸入**商務資料連接模型專案項目可以用來產生外部資料清單的擴充功能**。  
  
5.  上**資產** 索引標籤的 編輯器 中，選擇 **新增** 按鈕。  
  
     **加入新資產** 對話方塊隨即出現。  
  
6.  在**類型**清單中，選擇**Microsoft.VisualStudio.MefComponent**。  
  
    > [!NOTE]  
    >  這個值會對應到`MefComponent`extension.vsixmanifest 檔案中的項目。 這個項目 VSIX 封裝中指定延伸模組組件的名稱。 如需詳細資訊，請參閱[MEFComponent 元素 （VSX 結構描述）](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
7.  在**來源**清單中，選擇**目前方案中的專案**。  
  
8.  在**專案**清單中，選擇**BdcProjectItemExtension**，然後選擇 [**確定**] 按鈕。  
  
9. 在功能表列上，選擇 [建置] 、[建置方案] 。  
  
10. 請確定專案會編譯和建置無誤。  
  
11. 請確定 GenerateExternalDataLists 專案建置輸出資料夾現在包含 GenerateExternalDataLists.vsix 檔案。  
  
     根據預設，會將組建輸出資料夾...包含專案檔的資料夾下的 \bin\Debug 資料夾。  
  
## <a name="testing-the-project-item-extension"></a>測試專案項目擴充功能  
 現在您已經準備好進行測試的專案項目擴充功能。 首先，開始偵錯擴充功能專案中的 Visual Studio 實驗執行個體中。 然後，使用 Visual Studio 的實驗執行個體中的延伸模組來產生外部 BDC 模型的清單。 最後，開啟外部清單以確認它如預期般運作的 SharePoint 網站上。  
  
#### <a name="to-start-debugging-the-extension"></a>若要啟動偵錯擴充功能  
  
1.  如有必要，系統管理認證，以重新啟動 Visual Studio，然後開啟 GenerateExternalDataLists 方案。  
  
2.  在 BdcProjectItemExtension 專案中，開啟 ProjectItemExtension 程式碼檔案，然後加入中斷點的程式碼行中`Initialize`方法。  
  
3.  開啟 GenerateExternalDataLists 程式碼檔案，然後再將中斷點加入至程式碼中的第一行`GenerateExternalDataLists_Execute`方法。  
  
4.  開始偵錯方法選擇 F5 鍵，或是在功能表列上，選擇**偵錯**，**開始偵錯**。  
  
     Visual Studio %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External 資料清單 Generator\1.0 來安裝擴充功能，並啟動 Visual studio 的實驗執行個體。 您將這個執行個體的 Visual Studio 中測試的專案項目。  
  
#### <a name="to-test-the-extension"></a>若要測試擴充功能  
  
1.  在功能表列上的 Visual Studio 實驗執行個體選擇**檔案**，**新增**，**專案**。  
  
2.  中**新專案**對話方塊方塊中，展開 **範本** 節點，展開**Visual C#**  節點，展開**SharePoint**  節點，然後選擇**2010年**。  
  
3.  在清單頂端的對話方塊中，請確定**.NET Framework 3.5**已選取。 專案[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]需要這個版本的.NET Framework。  
  
4.  在專案範本清單中選擇**SharePoint 2010 專案**。  
  
5.  在**名稱**方塊中，輸入**SharePointProjectTestBDC**，然後選擇 [**確定**] 按鈕。  
  
6.  在 SharePoint 自訂精靈中，輸入您想要用於偵錯，請選擇網站的 URL**部署為伺服陣列方案**，然後選擇 **完成** 按鈕。  
  
7.  開啟 SharePointProjectTestBDC 專案的捷徑功能表，選擇 **新增**，然後選擇 **新項目**。  
  
8.  在**新增 NewItem-SharePointProjectTestBDC**對話方塊方塊中，展開安裝的語言節點，展開  **SharePoint**節點。  
  
9. 選擇**2010年**] 節點，然後選擇 [**商務資料連接模型 （僅限陣列方案）**範本。  
  
10. 在**名稱**方塊中，輸入**TestBDCModel**，然後選擇 [**新增**] 按鈕。  
  
11. 確認 Visual Studio 的其他執行個體中的程式碼停止於您在中設定中斷點`Initialize`ProjectItemExtension 程式碼檔案的方法。  
  
12. 在 Visual Studio 已停止執行個體，選擇**F5**金鑰，或在功能表列上選擇 **偵錯**，**繼續**繼續進行偵錯專案。  
  
13. 在 Visual Studio 的實驗執行個體，選擇  **F5**金鑰，或在功能表列上選擇 **偵錯**，**開始偵錯**建置、 部署和執行**TestBDCModel**專案。  
  
     網頁瀏覽器會開啟至指定的偵錯的 SharePoint 網站的預設頁面。  
  
14. 確認**列出**快速啟動 區域中的區段不尚未包含在專案中預設 BDC 模型為基礎的清單。 您必須先建立外部資料 清單中，使用 SharePoint 使用者介面，或使用專案項目擴充功能。  
  
15. 關閉網頁瀏覽器。  
  
16. 中已 TestBDCModel 專案開啟的 Visual Studio 執行個體，開啟捷徑功能表**TestBDCModel**中的節點**方案總管] 中**，然後選擇 [**產生外部資料清單**。  
  
17. 確認 Visual Studio 的其他執行個體中的程式碼停止於您在中設定中斷點`GenerateExternalDataLists_Execute`方法。 選擇**F5**金鑰，或在功能表列上選擇 **偵錯**，**繼續**繼續進行偵錯專案。  
  
18. Visual Studio 的實驗執行個體加入名為的清單執行個體**Entity1DataList** TestBDCModel 至專案，以及執行個體也會產生名為功能**Feature2**清單執行個體。  
  
19. 選擇**F5**金鑰，或在功能表列上選擇 **偵錯**，**開始偵錯**建置、 部署和執行 TestBDCModel 專案。  
  
     網頁瀏覽器會開啟用來偵錯的 SharePoint 網站的預設頁面。  
  
20. 在**列出**區段的 快速啟動 區域中，選擇  **Entity1DataList**清單。  
  
21. 請確認此清單包含名為 Identifier1 和訊息時，除了 Identifier1 值為 0 的 Hello World 訊息值的一個項目之外的資料行。  
  
     **商務資料連接模型**專案範本會產生預設 BDC 模型，提供所有資料。  
  
22. 關閉網頁瀏覽器。  
  
## <a name="cleaning-up-the-development-computer"></a>清除開發電腦  
 完成測試的專案項目擴充功能之後，從 SharePoint 網站移除外部清單和 BDC 模型，並移除 Visual Studio 中的專案項目擴充功能。  
  
#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>若要從 SharePoint 網站移除外部資料清單  
  
1.  在 SharePoint 網站 快速啟動 區域中，選擇  **Entity1DataList**清單。  
  
2.  在功能區中的 SharePoint 網站上，選擇 [**清單**] 索引標籤。  
  
3.  在**清單**索引標籤的**設定**群組中，選擇**清單設定**。  
  
4.  下**權限與管理**，選擇**刪除這份清單**，然後選擇 **確定**以確認您想要將清單傳送至資源回收筒。  
  
5.  關閉網頁瀏覽器。  
  
#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>若要從 SharePoint 網站移除 BDC 模型  
  
1.  在功能表列上的 Visual Studio 實驗執行個體選擇**建置**， **Retract**。  
  
     Visual Studio 會從 SharePoint 網站移除 BDC 模型。  
  
#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>若要從 Visual Studio 中移除專案項目擴充功能  
  
1.  在功能表列上的 Visual Studio 實驗執行個體選擇**工具**，**擴充功能和更新**。  
  
     [擴充功能和更新] 對話方塊隨即開啟。  
  
2.  在 擴充功能的清單中，選擇 **外部的資料清單產生器**，然後選擇 **解除安裝** 按鈕。  
  
3.  在出現的對話方塊中，選擇 **是**以確認您想要解除安裝擴充功能。  
  
4.  選擇**立即重新啟動**完成解除安裝。  
  
5.  關閉 Visual Studio （實驗性執行個體和 GenerateExternalDataLists 方案已開啟的執行個體） 的兩個執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)   
 [建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  