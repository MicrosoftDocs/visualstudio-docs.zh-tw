---
title: 逐步解說： 建立 SharePoint 專案延伸模組 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8d68347f2b6b9f538555e05c91b15dcb045b46d6
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295978"
---
# <a name="walkthrough-create-a-sharepoint-project-extension"></a>逐步解說： 建立 SharePoint 專案擴充功能
  此逐步解說將說明如何建立 SharePoint 專案延伸模組。 您可以使用專案擴充功能，例如加入、 刪除或重新命名專案時的專案層級事件回應。 您也可以新增自訂屬性，或當屬性值變更時回應。 不同的專案項目擴充功能，於專案延伸模組不能與特定的 SharePoint 專案類型相關聯。 當您建立的專案延伸模組時，擴充功能載入任何種類的 SharePoint 專案中開啟時[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
 在本逐步解說中，您將建立自訂的布林值屬性中建立任何 SharePoint 專案加入[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 當設定為 **，則為 True**，新的屬性加入，或將對應至您的專案的映像資源資料夾。 當設定為**False**，移除 [Images] 資料夾時，若有的話。 如需詳細資訊，請參閱 <<c0> [ 如何： 新增與移除對應的資料夾](../sharepoint/how-to-add-and-remove-mapped-folders.md)。  
  
 本逐步解說將示範下列工作：  
  
-   建立[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]會執行下列 SharePoint 專案延伸模組：  
  
    -   將 [屬性] 視窗中的自訂專案屬性。 屬性會套用至任何 SharePoint 專案。  
  
    -   若要將對應的資料夾新增至專案中使用 SharePoint 專案物件模型。  
  
    -   使用[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]automation 物件模型 (DTE) 從專案刪除對應的資料夾。  
  
-   建置[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]来部署專案屬性的延伸模組組件的擴充功能 (VSIX) 封裝。  
  
-   偵錯和測試專案屬性。  
  
## <a name="prerequisites"></a>必要條件  
 您需要完成這個逐步解說在開發電腦上的下列元件：  
  
-   支援的版本[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]、 SharePoint 和[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。 本逐步解說會使用**VSIX 專案**中的範本[!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)]建立 VSIX 封裝，來部署專案的屬性延伸模組。 如需詳細資訊，請參閱 <<c0> [ 擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="create-the-projects"></a>建立專案
 若要完成此逐步解說中，您必須建立兩個專案：  
  
- 若要建立 VSIX 封裝來部署專案擴充功能的 VSIX 專案。  
  
- 實作專案擴充功能的類別庫專案。  
  
  開始本逐步解說建立的專案。  
  
#### <a name="to-create-the-vsix-project"></a>若要建立 VSIX 專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在功能表列上，選擇 [檔案] > [新增] > [專案]。  
  
3.  中**新的專案**對話方塊方塊中，展開**Visual C#** 或**Visual Basic**節點，然後選擇**擴充性**節點。  
  
    > [!NOTE]  
    >  只有當您安裝 Visual Studio SDK 時，才使用這個節點。 如需詳細資訊，請參閱稍早在本主題中的必要條件 > 一節。  
  
4.  在對話方塊頂端，選擇 **.NET Framework 4.5**清單中的版本的.NET Framework 中，然後選擇**VSIX 專案**範本。  
  
5.  在 [**名稱**方塊中，輸入**ProjectExtensionPackage**，然後選擇 **[確定]** ] 按鈕。  
  
     **ProjectExtensionPackage**專案會顯示在**方案總管 中**。  
  
#### <a name="to-create-the-extension-project"></a>若要建立擴充功能專案  
  
1.  中**方案總管**，開啟方案節點的捷徑功能表，選擇**新增**，然後選擇**新專案**。  
  
2.  在**新的專案**對話方塊方塊中，展開**Visual C#** 或**Visual Basic**節點，然後選擇**Windows**。  
  
3.  在對話方塊頂端，選擇 **.NET Framework 4.5**版本的.NET Framework 中，清單中，然後選擇**類別庫**專案範本。  
  
4.  在 [**名稱**方塊中，輸入**ProjectExtension**，然後選擇 **[確定]** ] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**ProjectExtension**專案加入方案，並開啟預設 Class1 的程式碼檔案。  
  
5.  從專案刪除 Class1 的程式碼檔案。  
  
## <a name="configure-the-project"></a>設定專案
 您撰寫程式碼，以建立專案擴充功能之前，加入程式碼檔案和擴充功能專案的組件參考。  
  
#### <a name="to-configure-the-project"></a>若要設定專案  
  
1.  新增程式碼檔案，稱為**CustomProperty** ProjectExtension 專案。  
  
2.  開啟捷徑功能表**ProjectExtension**專案，，然後選擇**加入參考**。  
  
3.  在 **參考管理員-CustomProperty**對話方塊方塊中，選擇**Framework**節點，，然後選取 System.ComponentModel.Composition 和 System.Windows.Forms 組件旁邊的核取方塊。  
  
4.  選擇**延伸模組**節點中，選取 [Microsoft.VisualStudio.SharePoint 和 EnvDTE 組件旁邊的核取方塊，然後選擇**確定**] 按鈕。  
  
5.  在**方案總管**下方**參考**資料夾**ProjectExtension**專案中，選擇**EnvDTE**。  
  
6.  在 **屬性**視窗中，變更**內嵌 Interop 類型**屬性設**False**。  
  
## <a name="define-the-new-sharepoint-project-property"></a>定義新的 SharePoint 專案屬性
 建立一個類別來定義專案擴充功能和新的專案屬性的行為。 若要定義新的專案擴充功能，此類別會實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>介面。 每當您想要定義 SharePoint 專案擴充功能，請實作這個介面。 此外，新增<xref:System.ComponentModel.Composition.ExportAttribute>類別。 這個屬性可讓[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]來探索及載入您<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>實作。 傳遞<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>屬性的建構函式的型別。  
  
#### <a name="to-define-the-new-sharepoint-project-property"></a>若要定義新的 SharePoint 專案屬性  
  
1.  將下列程式碼貼入 CustomProperty 的程式碼檔案。  
  
     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]  
  
## <a name="build-the-solution"></a>建置方案
 接下來，建置方案，以確定它會編譯無誤。  
  
#### <a name="to-build-the-solution"></a>若要建置方案  
  
1.  在功能表列上選擇 [建置] > [建置解決方案]。  
  
## <a name="create-a-vsix-package-to-deploy-the-project-property-extension"></a>建立 VSIX 封裝，來部署專案的屬性延伸模組
 若要建立 VSIX 封裝部署專案擴充功能，請在解決方案中使用 VSIX 專案。 首先，設定 VSIX 套件藉由修改 source.extension.vsixmanifest 檔案中包含在 VSIX 專案。 建立方案，然後建立 VSIX 封裝。  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>若要設定及建立 VSIX 封裝  
  
1.  在 [**方案總管**，開啟 source.extension.vsixmanifest 檔案中，捷徑功能表，然後選擇**開啟**] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 以資訊清單設計工具中開啟檔案。 在顯示的資訊**中繼資料**索引標籤也會出現在**擴充功能和更新**。 所有的 VSIX 套件需要 extension.vsixmanifest 檔案。 如需有關這個檔案的詳細資訊，請參閱 < [VSIX 延伸結構描述 1.0 參考](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在  **Product Name**方塊中，輸入**自訂專案屬性**。  
  
3.  在 **作者**方塊中，輸入**Contoso**。  
  
4.  在 **描述**方塊中，輸入**切換至專案的映像資源資料夾的對應自訂 SharePoint 專案屬性**。  
  
5.  選擇**資產**索引標籤，然後選擇**新增** 按鈕。  
  
     **加入新資產** 對話方塊隨即出現。  
  
6.  在 **型別**清單中，選擇**Microsoft.VisualStudio.MefComponent**。  
  
    > [!NOTE]  
    >  這個值會對應到`MEFComponent`extension.vsixmanifest 檔案中的項目。 這個元素會指定在 VSIX 封裝中的延伸模組組件名稱。 如需詳細資訊，請參閱 < [MEFComponent 項目 （VSX 結構描述）](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))。  
  
7.  在 **來源**清單中，選擇**目前方案中的專案**選項按鈕。  
  
8.  在 **專案**清單中，選擇**ProjectExtension**。  
  
     這個值會識別您要建置專案中的組件的名稱。  
  
9. 選擇**確定**以關閉**加入新資產** 對話方塊。  
  
10. 在功能表列上選擇 **檔案** > **全部儲存**當您完成時，然後關閉 資訊清單設計工具。  
  
11. 在功能表列上選擇 **建置** > **建置方案**，然後確認專案編譯無誤。  
  
12. 在 **方案總管 中**，開啟捷徑功能表**ProjectExtensionPackage**專案，然後選擇**在檔案總管 中開啟資料夾** 按鈕。  
  
13. 在 **檔案總管**開啟 ProjectExtensionPackage 專案的建置輸出資料夾，然後確認該資料夾包含名為 ProjectExtensionPackage.vsix 的檔案。  
  
     根據預設，會將組建輸出資料夾...在包含您的專案檔的資料夾下的 \bin\Debug 資料夾。  
  
## <a name="test-the-project-property"></a>測試專案屬性
 您現在準備好要測試自訂專案屬性。 它是最簡單的方式偵錯和測試新的專案屬性擴充中的實驗執行個體[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 這個執行個體[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]執行 VSIX 或其他擴充性專案時建立。 專案進行偵錯之後，您可以在您的系統上安裝擴充功能，然後繼續進行偵錯和測試的一般執行個體中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>偵錯及測試 Visual Studio 的實驗執行個體中的擴充功能  
  
1.  重新啟動[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]與系統管理認證，然後開啟 ProjectExtensionPackage 解決方案。  
  
2.  藉由選擇啟動專案的偵錯組建**F5**金鑰或，功能表列選擇**偵錯** > **開始偵錯**。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom 專案 Property\1.0 來安裝擴充功能，並啟動實驗執行個體的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
3.  在實驗執行個體[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、 建立伺服器陣列方案的 SharePoint 專案和其他值，在精靈中使用的預設值。  
  
    1.  在功能表列上，選擇 [檔案] > [新增] > [專案]。  
  
    2.  在頂端**新的專案**對話方塊方塊中，選擇 **.NET Framework 3.5**清單中的.NET Framework 版本。  
  
         SharePoint 工具擴充功能所需的功能，在這個版本的[!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]。  
  
    3.  底下**範本**節點，展開**Visual C#** 或**Visual Basic**  節點，選擇**SharePoint**  節點，然後選擇  **2010年**節點。  
  
    4.  選擇**SharePoint 2010 專案**範本，然後輸入**ModuleTest**做為您的專案名稱。  
  
4.  在 **方案總管**，選擇**ModuleTest**專案節點。  
  
     新的自訂屬性**地圖影像資料夾**會出現在**屬性**視窗中的預設值**False**。  
  
5.  該屬性的值變更 **，則為 True**。  
  
     映像資源資料夾已新增至 SharePoint 專案。  
  
6.  變更該屬性的值將會回到**False**。  
  
     如果您選擇**是**按鈕**刪除映像資料夾？**  對話方塊中，資源資料夾會從 SharePoint 專案中刪除的映像。  
  
7.  關閉 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的實驗執行個體。  
  
## <a name="see-also"></a>另請參閱
 [擴充 SharePoint 專案](../sharepoint/extending-sharepoint-projects.md)   
 [如何： 將屬性加入至 SharePoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [SharePoint 專案系統類型與其他 Visual Studio 專案類型之間轉換](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [將資料儲存在 SharePoint 專案系統的擴充功能](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [將自訂的資料產生關聯的 SharePoint 工具擴充功能](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
