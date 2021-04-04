---
title: 逐步解說：擴充 SharePoint 專案專案類型 |Microsoft Docs
description: 在這個逐步解說中，建立 SharePoint 專案專案類型的延伸模組，例如商務資料連線 (BDC) 模型專案專案。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a91cbd863ed613804418cd5d1666412a01f8f542
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217693"
---
# <a name="walkthrough-extend-a-sharepoint-project-item-type"></a>逐步解說：擴充 SharePoint 專案專案類型
  您可以使用「 **商務資料連線模型** 」專案專案，在 SharePoint 中建立商務資料連線 (BDC) 服務的模型。 依預設，當您使用此專案專案建立模型時，模型中的資料不會顯示給使用者。 您也必須在 SharePoint 中建立外部清單，讓使用者可以查看資料。

 在這個逐步解說中，您將建立 **商務資料連線模型** 專案專案的擴充功能。 開發人員可以使用此延伸模組，在其專案中建立外部清單，以顯示 BDC 模型中的資料。 本逐步解說將示範下列工作：

- 建立可執行兩個主要工作的 Visual Studio 延伸模組：

  - 它會產生在 BDC 模型中顯示資料的外部清單。 此延伸模組會使用 SharePoint 專案系統的物件模型，產生定義清單的 *Elements.xml* 檔案。 它也會將檔案新增至專案，使其與 BDC 模型一起部署。

  - 它會在 **方案總管** 中的 **商務資料連線模型** 專案專案加入快捷方式功能表項目。 開發人員可以按一下這個功能表項目，以產生 BDC 模型的外部清單。

- 建立 Visual Studio 擴充功能 (VSIX) 套件以部署擴充元件。

- 測試擴充功能。

## <a name="prerequisites"></a>必要條件
 您需要在開發電腦上執行下列元件，才能完成此逐步解說：

- 支援的 Microsoft Windows、SharePoint 和 Visual Studio 版本。

- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。 本逐步解說會使用 SDK 中的 **Vsix 專案** 範本來建立 vsix 封裝，以部署專案專案。 如需詳細資訊，請參閱 [Visual Studio 中的擴充 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。

  下列概念的知識很有説明，但並非必要，無法完成此逐步解說：

- 中的 BDC 服務 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 。 如需詳細資訊，請參閱 [BDC 架構](/previous-versions/office/developer/sharepoint-2010/ee558876(v=office.14))。

- BDC 模型的 XML 架構。 如需詳細資訊，請參閱 [BDC 模型基礎結構](/previous-versions/office/developer/sharepoint-2010/ee556378(v=office.14))。

## <a name="create-the-projects"></a>建立專案
 若要完成這個逐步解說，您必須建立兩個專案：

- 建立 VSIX 封裝以部署專案專案擴充功能的 VSIX 專案。

- 實作為專案專案延伸的類別庫專案。

  藉由建立專案來開始逐步解說。

#### <a name="to-create-the-vsix-project"></a>建立 VSIX 專案

1. 啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2. 在功能表列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]。

3. 在 [**新增專案**] 對話方塊中，展開 [ **Visual c #** ] 或 [ **Visual Basic** 節點]，然後選擇 [擴充性 **] 節點。**

    > [!NOTE]
    > 只有當您安裝 Visual Studio SDK 時，才能使用擴充 **性節點。** 如需詳細資訊，請參閱本主題稍早的必要條件一節。

4. 在 [ **新增專案** ] 對話方塊頂端的清單中，選擇 **.NET Framework 4.5**。

     SharePoint 工具延伸模組需要此 .NET Framework 版本的功能。

5. 選擇 [ **VSIX 專案** ] 範本。

6. 在 [ **名稱** ] 方塊中，輸入 **GenerateExternalDataLists**，然後選擇 [ **確定]** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將 **GenerateExternalDataLists** 專案新增至 **方案總管**。

7. 如果 extension.vsixmanifest 檔案未自動開啟，請在 GenerateExternalDataLists 專案中開啟其快捷方式功能表，然後選擇 [**開啟**]。

8. 確認 extension.vsixmanifest 檔案具有非空白的專案 (在 [作者] 欄位中輸入 Contoso) 、儲存檔案，然後關閉它。

#### <a name="to-create-the-extension-project"></a>建立延伸模組專案

1. 在 **方案總管** 中，開啟 [ **GenerateExternalDataLists** ] 方案節點的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增專案**]。

2. 在 [ **加入新專案** ] 對話方塊中，展開 [ **Visual c #** ] 或 [ **Visual Basic** 節點]，然後選擇 [ **Windows** ] 節點。

3. 在對話方塊頂端的清單中，選擇 **.NET Framework 4.5**。

4. 在專案範本清單中，選擇 [ **類別庫**]。

5. 在 [ **名稱** ] 方塊中，輸入 **BdcProjectItemExtension**，然後選擇 [ **確定]** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將 **BdcProjectItemExtension** 專案加入至方案，並開啟預設的 Class1 程式碼檔案。

6. 從專案中刪除 Class1 程式碼檔案。

## <a name="configure-the-extension-project"></a>設定擴充功能專案
 撰寫程式碼以建立專案專案擴充功能之前，請先將程式碼檔和元件參考加入至擴充功能專案。

#### <a name="to-configure-the-project"></a>若要設定專案

1. 在 BdcProjectItemExtension 專案中，新增兩個具有下列名稱的程式碼檔案：

    - ProjectItemExtension

    - GenerateExternalDataLists

2. 選擇 [BdcProjectItemExtension] 專案，然後在功能表列上選擇 [**專案**  >  **加入參考**]。

3. 在 [ **元件** ] 節點下，選擇 [ **架構** ] 節點，然後選取下列每個元件的核取方塊：

    - System.ComponentModel.Composition

    - WindowsBase

4. 在 [ **元件** ] 節點下，選擇 [ **擴充** 功能] 節點，然後選取下列元件的核取方塊：

    - VisualStudio SharePoint

5. 選擇 [確定]  按鈕。

## <a name="define-the-project-item-extension"></a>定義專案專案延伸模組
 建立類別，以定義 **商務資料連線模型** 專案專案的延伸。 為了定義擴充功能，類別會實作為 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 介面。 當您想要擴充現有的專案專案類型時，請執行這個介面。

#### <a name="to-define-the-project-item-extension"></a>若要定義專案專案延伸模組

1. 將下列程式碼貼入 ProjectItemExtension 程式碼檔案中。

    > [!NOTE]
    > 加入此程式碼之後，專案會有一些編譯錯誤。 當您在後續步驟中新增程式碼時，這些錯誤就會消失。

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb" id="Snippet1":::

## <a name="create-the-external-data-lists"></a>建立外部資料欄表
 加入類別的部分定義，此定義 `GenerateExternalDataListsExtension` 會為 BDC 模型中的每個實體建立外部資料欄表。 若要建立外部資料清單，此程式碼會先剖析 BDC 模型檔案中的 XML 資料，以讀取 BDC 模型中的實體資料。 然後，它會根據 BDC 模型建立一個清單實例，並將此清單實例加入至專案。

#### <a name="to-create-the-external-data-lists"></a>若要建立外部資料清單

1. 將下列程式碼貼入 GenerateExternalDataLists 程式碼檔案中。

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs" id="Snippet2":::

## <a name="checkpoint"></a>Checkpoint
 在本逐步解說的這個階段中，專案專案延伸模組的所有程式碼現在都在專案中。 建立方案，以確保專案編譯而不會發生錯誤。

#### <a name="to-build-the-solution"></a>若要建置方案

1. 在功能表列上，選擇 [**組建**  >  **組建方案**]。

## <a name="create-a-vsix-package-to-deploy-the-project-item-extension"></a>建立 VSIX 套件以部署專案專案延伸模組
 若要部署擴充功能，請在您的方案中使用 VSIX 專案來建立 VSIX 套件。 首先，藉由修改 VSIX 專案中包含的 extension.vsixmanifest 檔案來設定 VSIX 套件。 然後，建立解決方案來建立 VSIX 套件。

#### <a name="to-configure-and-create-the-vsix-package"></a>設定和建立 VSIX 封裝

1. 在 **方案總管** 中，開啟 GenerateExternalDataLists 專案中 extension.vsixmanifest 檔案的快捷方式功能表，然後選擇 [ **開啟**]。

     Visual Studio 在資訊清單編輯器中開啟檔案。 Extension.vsixmanifest 檔案是 extension.vsixmanifest 檔案的基礎，所有 VSIX 封裝都需要此檔案。 如需此檔案的詳細資訊，請參閱 [VSIX 延伸架構1.0 參考](/previous-versions/dd393700(v=vs.110))。

2. 在 [ **產品名稱** ] 方塊中，輸入 **外部資料清單** 產生器。

3. 在 [ **作者** ] 方塊中，輸入 **Contoso**。

4. 在 [ **描述** ] 方塊中，輸入 **可用來產生外部資料清單之商務資料連線模型專案專案的延伸模組**。

5. 在編輯器的 [ **資產** ] 索引標籤上，選擇 [ **新增** ] 按鈕。

     [ **加入新資產** ] 對話方塊隨即出現。

6. 在 [ **類型** ] 清單中，選擇 [ **VisualStudio. [microsoft.visualstudio.mefcomponent]**]。

    > [!NOTE]
    > 此值對應至 `MefComponent` extension.vsixmanifest 檔案中的元素。 這個元素會指定 VSIX 封裝中的擴充元件名稱。 如需詳細資訊，請參閱 [[Microsoft.visualstudio.mefcomponent] 元素 (VSX 架構) ](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))。

7. 在 [ **來源** ] 清單中，選擇 [ **目前方案中的專案**]。

8. 在 [ **專案** ] 清單中，選擇 [ **BdcProjectItemExtension**]，然後選擇 [ **確定]** 按鈕。

9. 在功能表列上，選擇 [**組建**  >  **組建方案**]。

10. 確定專案會編譯並建立，而不會發生錯誤。

11. 請確定 GenerateExternalDataLists 專案的組建輸出檔案夾現在包含 GenerateExternalDataLists .vsix 檔案。

     根據預設，組建輸出檔案夾為。包含您專案檔之資料夾下的 \bin\Debug 資料夾。

## <a name="test-the-project-item-extension"></a>測試專案專案延伸模組
 您現在已準備好測試專案專案延伸模組。 首先，在 Visual Studio 的實驗實例中啟動偵錯工具擴充功能專案。 然後，在 Visual Studio 的實驗實例中使用延伸模組，以產生 BDC 模型的外部清單。 最後，開啟 SharePoint 網站上的外部清單，確認它如預期般運作。

#### <a name="to-start-debugging-the-extension"></a>開始進行擴充功能的調試

1. 如有必要，請使用系統管理認證重新開機 Visual Studio，然後開啟 GenerateExternalDataLists 方案。

2. 在 BdcProjectItemExtension 專案中，開啟 ProjectItemExtension 程式碼檔案，然後將中斷點加入至方法中的程式程式碼 `Initialize` 。

3. 開啟 GenerateExternalDataLists 程式碼檔案，然後將中斷點新增至方法中的第一行程式碼 `GenerateExternalDataLists_Execute` 。

4. 選擇 **F5** 鍵，或是在功能表列上選擇 [ **Debug**  >  **開始調試** 程式]，以開始進行偵錯工具。

     Visual Studio 將擴充功能安裝至%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External 資料清單 Generator\1.0，並啟動 Visual Studio 的實驗實例。 您將在 Visual Studio 的這個實例中測試專案專案。

#### <a name="to-test-the-extension"></a>測試擴充功能

1. 在 Visual Studio 的實驗實例中 **，選擇功能表** 欄上的 [檔案  >  **新增**  >  **專案**]。

2. 在 [ **新增專案** ] 對話方塊中，展開 [ **範本** ] 節點，展開 [ **Visual c #** ] 節點，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010**]。

3. 在對話方塊頂端的清單中，確認已選取 **.NET Framework 3.5** 。 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]需要此 .NET Framework 版本的專案。

4. 在專案範本清單中，選擇 [ **SharePoint 2010 專案**]。

5. 在 [ **名稱** ] 方塊中，輸入 **SharePointProjectTestBDC**，然後選擇 [ **確定]** 按鈕。

6. 在 [SharePoint 自訂嚮導] 中，輸入您要用於偵錯工具的網站 URL，選擇 [ **部署為伺服器陣列方案**]，然後選擇 [ **完成]** 按鈕。

7. 開啟 SharePointProjectTestBDC 專案的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增專案**]。

8. 在 [ **加入 NewItem-SharePointProjectTestBDC** ] 對話方塊中，依序展開 [已安裝的語言] 節點和 [ **SharePoint** ] 節點。

9. 選擇 [ **2010** ] 節點，然後選擇 [ **商務資料連線模型 (伺服器陣列方案])** 範本。

10. 在 [ **名稱** ] 方塊中，輸入 **TestBDCModel**，然後選擇 [ **加入** ] 按鈕。

11. 確認 Visual Studio 的另一個實例中的程式碼會在您于 ProjectItemExtension 程式碼檔案的方法中設定的中斷點上停止 `Initialize` 。

12. 在 [已停止的 Visual Studio 實例] 中，選擇 **F5** 鍵，或是在功能表列上選擇 [ **Debug**  >  **continue** ]，繼續進行專案的偵錯工具。

13. 在 Visual Studio 的實驗實例中，選擇 **F5** 鍵，或是在功能表列上，選擇 [ **Debug**  >  **開始調試** 程式] 來建立、部署和執行 **TestBDCModel** 專案。

     Web 瀏覽器會開啟至 SharePoint 網站的預設頁面，該頁面是針對進行偵錯工具所指定。

14. 確認快速啟動區域中的 [ **清單** ] 區段尚未包含以專案中預設 BDC 模型為基礎的清單。 您必須先使用 SharePoint 使用者介面或專案專案延伸來建立外部資料欄表。

15. 關閉網頁瀏覽器。

16. 在開啟 TestBDCModel 專案的 Visual Studio 實例中，開啟 [ **TestBDCModel** ] **方案總管** 節點的快捷方式功能表，然後選擇 [ **產生外部資料清單**]。

17. 確認 Visual Studio 的另一個實例中的程式碼會在您于方法中設定的中斷點上停止 `GenerateExternalDataLists_Execute` 。 選擇 **F5** 鍵，或是在功能表列上選擇 [ **Debug**  >  **continue** ]，繼續進行專案的調試。

18. Visual Studio 的實驗實例會將名為 **Entity1DataList** 的清單實例加入至 TestBDCModel 專案，而且此實例也會針對清單實例產生名為 **Feature2** 的功能。

19. 選擇 **F5** 鍵，或是在功能表列上，選擇 [ **Debug**  >  **開始** 錯] 來建立、部署和執行 TestBDCModel 專案。

     Web 瀏覽器會開啟至 SharePoint 網站的預設頁面，以用於進行調試。

20. 在 [快速啟動] 區域的 [ **清單** ] 區段中，選擇 [ **Entity1DataList** ] 清單。

21. 確認清單中包含名為 Identifier1 和 Message 的資料行，以及 Identifier1 值為0且訊息值為 Hello World 的一個專案。

     **商務資料連線模型** 專案範本會產生提供所有資料的預設 BDC 模型。

22. 關閉網頁瀏覽器。

## <a name="clean-up-the-development-computer"></a>清除開發電腦
 在您完成專案專案延伸模組的測試之後，請從 SharePoint 網站移除外部清單和 BDC 模型，然後從 Visual Studio 移除專案專案延伸。

#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>從 SharePoint 網站移除外部資料清單

1. 在 SharePoint 網站的 [快速啟動] 區域中，選擇 [ **Entity1DataList** ] 清單。

2. 在 SharePoint 網站上的功能區中，選擇 [ **清單** ] 索引標籤。

3. 在 [ **清單** ] 索引標籤的 [ **設定** ] 群組中，選擇 [ **清單設定**]。

4. 在 [ **許可權與管理**] 之下，選擇 [ **刪除此清單**]，然後選擇 **[確定]** 以確認您要將清單傳送至資源回收筒。

5. 關閉網頁瀏覽器。

#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>從 SharePoint 網站移除 BDC 模型

1. 在 Visual Studio 的實驗實例中，選擇功能表列上的 [**組建** 撤銷]  >  ****。

     Visual Studio 從 SharePoint 網站移除 BDC 模型。

#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>若要從 Visual Studio 移除專案專案延伸

1. 在 Visual Studio 的實驗實例中，選擇功能表列上的 [**工具**  >  **擴充功能和更新**]。

     [擴充功能和更新] 對話方塊隨即開啟。

2. 在擴充功能清單中，選擇 [ **外部資料清單** 產生器]，然後選擇 [ **卸載** ] 按鈕。

3. 在出現的對話方塊中，選擇 [ **是** ] 以確認您要卸載延伸模組。

4. 選擇 [ **立即重新開機** ] 以完成卸載。

5. 關閉 Visual Studio 的兩個實例 (實驗實例，以及開啟 GenerateExternalDataLists 方案) 的實例。

## <a name="see-also"></a>另請參閱
- [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)
- [建立商務資料連線模型](../sharepoint/creating-a-business-data-connectivity-model.md)
- [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)