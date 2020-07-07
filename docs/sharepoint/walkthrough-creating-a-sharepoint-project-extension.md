---
title: 逐步解說：建立 SharePoint 專案延伸模組 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5df10e2da9e6b4c31894dce0669e9aa0e580b92f
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015078"
---
# <a name="walkthrough-create-a-sharepoint-project-extension"></a>逐步解說：建立 SharePoint 專案延伸模組
  本逐步解說將說明如何建立 SharePoint 專案的擴充功能。 您可以使用專案延伸來回應專案層級的事件，例如新增、刪除或重新命名專案。 當屬性值變更時，您也可以新增自訂屬性或回應。 不同于專案專案延伸模組，專案延伸模組無法與特定的 SharePoint 專案類型相關聯。 當您建立專案延伸模組時，在中開啟任何類型的 SharePoint 專案時，會載入擴充功能 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。

 在此逐步解說中，您將建立自訂的布林值屬性，這個屬性會加入至中建立的任何 SharePoint 專案 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 當設定為**True**時，新的屬性會將 Images 資源資料夾加入或對應至您的專案。 當設定為**False**時，會移除 Images 資料夾（如果有的話）。 如需詳細資訊，請參閱[如何：新增和移除對應的資料夾](../sharepoint/how-to-add-and-remove-mapped-folders.md)。

 本逐步解說將示範下列工作：

- 建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 專案的擴充功能，以執行下列動作：

  - 將自訂專案屬性加入至屬性視窗。 屬性會套用至任何 SharePoint 專案。

  - 使用 SharePoint 專案物件模型，將對應的資料夾加入至專案。

  - 使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] automation 物件模型（DTE）從專案中刪除對應的資料夾。

- 建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能（VSIX）封裝以部署專案屬性的延伸模組元件。

- 調試和測試專案屬性。

## <a name="prerequisites"></a>必要條件
 您需要在開發電腦上有下列元件，才能完成此逐步解說：

- 支援的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 、SharePoint 和版本 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。

- [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。 本逐步解說會使用中的**Vsix 專案**範本 [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] 來建立 vsix 封裝，以部署專案屬性延伸模組。 如需詳細資訊，請參閱[Visual Studio 中的擴充 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。

## <a name="create-the-projects"></a>建立專案
 若要完成此逐步解說，您必須建立兩個專案：

- 建立 VSIX 封裝以部署專案延伸的 VSIX 專案。

- 實作為專案延伸的類別庫專案。

  藉由建立專案來啟動逐步解說。

#### <a name="to-create-the-vsix-project"></a>建立 VSIX 專案

1. 啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2. 在功能表列上 **，選擇 [** 檔案] [新增] [  >  **New**  >  **專案**]。

3. 在 [**新增專案**] 對話方塊中，展開 [ **Visual c #** ] 或 [ **Visual Basic** ] 節點，然後選擇 [擴充性 **] 節點。**

    > [!NOTE]
    > 只有當您安裝 Visual Studio SDK 時，才可以使用此節點。 如需詳細資訊，請參閱本主題稍早的必要條件一節。

4. 在對話方塊的頂端，選擇 .NET Framework 版本清單中的 [ **.NET Framework 4.5** ]，然後選擇 [ **VSIX 專案**] 範本。

5. 在 [**名稱**] 方塊中，輸入**ProjectExtensionPackage**，然後選擇 [**確定]** 按鈕。

     **ProjectExtensionPackage**專案會顯示在**方案總管**中。

#### <a name="to-create-the-extension-project"></a>若要建立擴充功能專案

1. 在**方案總管**中，開啟 [方案] 節點的快捷方式功能表，選擇 [**加入**]，然後選擇 [**新增專案**]。

2. 在 [**新增專案**] 對話方塊中，展開 [ **Visual c #** ] 或 [ **Visual Basic** ] 節點，然後選擇 [ **Windows**]。

3. 在對話方塊的頂端，選擇 .NET Framework 版本清單中的 [ **.NET Framework 4.5** ]，然後選擇 [**類別庫**] 專案範本。

4. 在 [**名稱**] 方塊中，輸入**ProjectExtension**，然後選擇 [**確定]** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]將**ProjectExtension**專案新增至方案，並開啟預設的 Class1 程式碼檔案。

5. 從專案中刪除 Class1 程式碼檔案。

## <a name="configure-the-project"></a>設定專案
 在您撰寫程式碼來建立專案延伸模組之前，請先將程式碼檔案和元件參考加入擴充功能專案中。

#### <a name="to-configure-the-project"></a>若要設定專案

1. 將名為**CustomProperty**的程式碼檔案加入至 ProjectExtension 專案。

2. 開啟**ProjectExtension**專案的快捷方式功能表，然後選擇 [**加入參考**]。

3. 在 [**參考管理員-CustomProperty** ] 對話方塊中，選擇 [ **Framework** ] 節點，然後選取 [System.workflow.componentmodel.activity] 和 [system.web] 元件旁的核取方塊。

4. 選擇 [**擴充**功能] 節點，選取 [VisualStudio] 和 [EnvDTE] 元件旁的核取方塊，然後選擇 [**確定]** 按鈕。

5. 在**方案總管**中，在**ProjectExtension**專案的 [**參考**] 資料夾底下，選擇 [ **EnvDTE**]。

6. 在 [**屬性**] 視窗中，將 [**內嵌 Interop 類型**] 屬性變更為 [ **False**]。

## <a name="define-the-new-sharepoint-project-property"></a>定義新的 SharePoint 專案屬性
 建立類別，以定義專案延伸和新專案屬性的行為。 為了定義新的專案延伸模組，類別會實作為 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 介面。 當您想要定義 SharePoint 專案的擴充功能時，請執行此介面。 此外，將新增 <xref:System.ComponentModel.Composition.ExportAttribute> 至類別。 這個屬性可讓 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 探索和載入您的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 執行。 將 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 類型傳遞給屬性的函式。

#### <a name="to-define-the-new-sharepoint-project-property"></a>若要定義新的 SharePoint 專案屬性

1. 將下列程式碼貼到 CustomProperty 程式碼檔案中。

     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]

## <a name="build-the-solution"></a>建立解決方案
 接下來，建立解決方案，以確保它會編譯而不會發生錯誤。

#### <a name="to-build-the-solution"></a>若要建置方案

1. 在功能表列上，選擇 [**組建**] [組建  >  **方案**]。

## <a name="create-a-vsix-package-to-deploy-the-project-property-extension"></a>建立 VSIX 封裝以部署專案屬性延伸模組
 若要部署專案延伸模組，請使用方案中的 VSIX 專案來建立 VSIX 封裝。 首先，藉由修改包含在 VSIX 專案中的 extension.vsixmanifest 檔案來設定 VSIX 封裝。 然後，藉由建立方案來建立 VSIX 封裝。

#### <a name="to-configure-and-create-the-vsix-package"></a>設定和建立 VSIX 封裝

1. 在**方案總管**中，開啟 extension.vsixmanifest 檔案的快捷方式功能表，然後選擇 [**開啟**] 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]在資訊清單設計工具中開啟檔案。 出現在 [**中繼資料**] 索引標籤中的資訊也會出現在 [**延伸模組和更新**] 中。 所有 VSIX 封裝都需要 extension.vsixmanifest 檔案。 如需這個檔案的詳細資訊，請參閱[VSIX 延伸模組架構1.0 參考](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。

2. 在 [**產品名稱**] 方塊中，輸入**自訂專案屬性**。

3. 在 [**作者**] 方塊中，輸入**Contoso**。

4. 在 [**描述**] 方塊中，輸入**自訂 SharePoint 專案屬性，以切換影像資源資料夾與專案的對應**。

5. 選擇 [**資產**] 索引標籤，然後選擇 [**新增**] 按鈕。

     [**加入新資產**] 對話方塊隨即出現。

6. 在 [**類型**] 清單中，選擇 [ **VisualStudio [microsoft.visualstudio.mefcomponent]**]。

    > [!NOTE]
    > 這個值會對應至 `MEFComponent` extension.vsixmanifest 檔案中的元素。 這個元素會指定 VSIX 封裝中的擴充元件名稱。 如需詳細資訊，請參閱[[Microsoft.visualstudio.mefcomponent] 元素（VSX 架構）](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))。

7. 在 [**來源**] 清單中，選擇 [**目前方案中的專案**] 選項按鈕。

8. 在 [**專案**] 清單中，選擇 [ **ProjectExtension**]。

     這個值會識別您在專案中建立之元件的名稱。

9. 選擇 [**確定]** 以關閉 [**加入新資產**] 對話方塊。

10. 在功能表列上 **，選擇**  >  [檔案] [**全部儲存**]，然後關閉 [資訊清單設計工具]。

11. 在功能表列上，選擇 [**組建**] [組建] [  >  **方案**]，然後確認專案編譯無誤。

12. 在**方案總管**中，開啟**ProjectExtensionPackage**專案的快捷方式功能表，然後選擇 [**在檔案瀏覽器中開啟資料夾**] 按鈕。

13. 在 [檔案**管理器**] 中，開啟 ProjectExtensionPackage 專案的 [組建輸出] 資料夾，然後確認該資料夾包含名為 ProjectExtensionPackage 的檔案。

     根據預設，組建輸出檔案夾為.。包含您專案檔之資料夾下的 \bin\Debug 資料夾。

## <a name="test-the-project-property"></a>測試專案屬性
 您現在已經準備好測試自訂專案屬性。 最簡單的方法是在的實驗實例中，對新的專案屬性延伸進行偵錯工具和測試 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]當您執行 VSIX 或其他擴充性專案時，會建立這個實例。 在您進行專案的調試之後，您可以在系統上安裝擴充功能，然後繼續在的一般實例中進行偵錯工具和測試 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。

#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>若要在的實驗實例中，將擴充功能進行 debug 和 test Visual Studio

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]以系統管理認證重新開機，然後開啟 ProjectExtensionPackage 解決方案。

2. 選擇**F5**鍵，或在功能表列上選擇 [ **debug**] [  >  **開始調試**程式]，以啟動專案的 debug 組建。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]將擴充功能安裝至%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom 專案 Property\1.0，並啟動的實驗實例 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。

3. 在的實驗實例中 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，建立伺服器陣列方案的 SharePoint 專案，並在嚮導中使用其他值的預設值。

    1. 在功能表列上 **，選擇 [** 檔案] [新增] [  >  **New**  >  **專案**]。

    2. 在 [**新增專案**] 對話方塊的頂端，選擇 .NET Framework 版本清單中的 [ **.NET Framework 3.5** ]。

         SharePoint 工具延伸模組需要此版本的功能 [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] 。

    3. 在 [**範本**] 節點底下，展開 [ **Visual c #** ] 或 [ **Visual Basic** ] 節點，選擇 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

    4. 選擇 [ **SharePoint 2010] 專案**範本，然後輸入**ModuleTest**做為專案的名稱。

4. 在**方案總管**中，選擇 [ **ModuleTest** ] 專案節點。

     新的自訂屬性**對應影像資料夾**會出現在 [**屬性**] 視窗中，預設值為 [ **False**]。

5. 將該屬性的值變更為**True**。

     [影像] 資源資料夾會加入至 SharePoint 專案。

6. 將該屬性的值變更回**False**。

     如果您選擇 [**刪除影像資料夾嗎？** ] 對話方塊中的 [**是**] 按鈕，就會從 SharePoint 專案中刪除 images 資源資料夾。

7. 關閉 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的實驗執行個體。

## <a name="see-also"></a>另請參閱
- [擴充 SharePoint 專案](../sharepoint/extending-sharepoint-projects.md)
- [如何：將屬性加入至 SharePoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [SharePoint 專案系統類型與其他 Visual Studio 專案類型之間的轉換](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [儲存 SharePoint 專案系統延伸模組中的資料](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [將自訂資料與 SharePoint 工具擴充功能產生關聯](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
