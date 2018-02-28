---
title: "逐步解說： 設計 Outlook 表單區域 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: afe17d19ebe87d34ae4857b1477be6cb3e894bb7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-designing-an-outlook-form-region"></a>逐步解說：設計 Outlook 表單區域
  自訂的表單區域會擴充標準或自訂的 Microsoft Office Outlook 表單。 在此逐步解說中，您要設計自訂的表單區域，它在連絡人項目的 [偵測器] 視窗中會顯示為新頁面。 這個表單區域會將地址資訊傳送至 Windows Live 當地搜尋網站，顯示連絡人清單中每個地址的對應。 如需表單區域的資訊，請參閱[建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   建立新的 Outlook VSTO 增益集專案。  
  
-   在 VSTO 增益集專案中加入表單區域。  
  
-   設計表單區域的版面配置。  
  
-   自訂表單區域的行為。  
  
-   測試 Outlook 表單區域。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] 或 [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]。  
  
 ![影片連結](../vsto/media/playvideo.gif "影片連結")如本主題的影片版本，請參閱[影片-如何： 設計 Outlook 表單區域](http://go.microsoft.com/fwlink/?LinkID=140824)。  
  
## <a name="creating-a-new-outlook-vsto-add-in-project"></a>建立新的 Outlook VSTO 增益集專案  
 第一次建立基本的 VSTO 增益集專案。  
  
#### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>建立新的 Outlook VSTO 增益集專案  
  
1.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，建立 Outlook VSTO 增益集專案名稱**MapItAddIn**。  
  
2.  在 [新增專案]  對話方塊中，選取 [為方案建立目錄] 。  
  
3.  將專案儲存至任一目錄。  
  
     如需詳細資訊，請參閱 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
## <a name="adding-a-form-region-to-the-outlook-vsto-add-in-project"></a>在 Outlook VSTO 增益集專案中加入表單區域  
 Outlook VSTO 增益集解決方案可以包含一或多個 Outlook 表單區域項目。 專案中加入表單區域項目使用**新的 Outlook 表單區域**精靈。  
  
#### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>在 Outlook VSTO 增益集專案中加入表單區域  
  
1.  在**方案總管 中**，選取**MapItAddIn**專案。  
  
2.  在 [專案]  功能表中，按一下 [加入新項目] 。  
  
3.  在**加入新項目**對話方塊中，選取**Outlook 表單區域**，將檔案命名**為 MapIt**，然後按一下 **新增**。  
  
     **NewOutlook 表單區域**精靈 隨即啟動。  
  
4.  在**選取您要建立此表單區域的方式**頁面上，按一下**設計新表單區域**，然後按一下 **下一步**。  
  
5.  在**選取您想要建立的表單區域類型**頁面上，按一下**個別**，然後按一下 **下一步**。  
  
     A*個別*表單區域會將新頁面加入 Outlook 表單。 如需表單區域類型的詳細資訊，請參閱 [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md)。  
  
6.  在**提供描述文字和選取顯示設定**頁面上，輸入**Map It**中**名稱**方塊。  
  
     開啟連絡人項目時，這個名稱會出現在 [偵測器] 視窗的功能區上。  
  
7.  選取**處於撰寫模式**和**處於讀取模式的偵測器**，然後按一下 **下一步**。  
  
8.  上**識別將顯示此表單區域的訊息類別**頁面上，清除**郵件**，選取**連絡人**，然後按一下 **完成**.  
  
     MapIt.cs 或 MapIt.vb 檔案即會加入專案。  
  
## <a name="designing-the-layout-of-the-form-region"></a>設計表單區域的版面配置  
 使用以視覺化方式開發表單區域*表單區域設計工具*。 您可以將 Managed 控制項拖曳至表單區域設計工具介面。 使用設計工具和**屬性**視窗調整控制項的配置和外觀。  
  
#### <a name="to-design-the-layout-of-the-form-region"></a>設計表單區域的版面配置  
  
1.  在**方案總管 中**，依序展開**MapItAddIn**專案，然後再連按兩下 MapIt.cs 或 MapIt.vb 開啟表單區域設計工具。  
  
2.  設計工具中，以滑鼠右鍵按一下，然後按一下 **屬性**。  
  
3.  在**屬性**視窗中，將**大小**至**664、 469**。  
  
     這可確保表單區域大到足以顯示地圖。  
  
4.  在 [ **檢視** ] 功能表上，按一下 [ **工具箱**]。  
  
5.  從**通用控制項** 索引標籤**工具箱**，新增**WebBrowser**加入表單區域。  
  
     **WebBrowser**會顯示每個列出連絡人的地址的對應。  
  
## <a name="customizing-the-behavior-of-the-form-region"></a>自訂表單區域的行為  
 在表單區域事件處理常式中加入程式碼，以自訂表單區域在執行階段的行為方式。 程式碼會檢查此表單區域的 Outlook 項目屬性，並決定是否要顯示 Map It 表單區域。 如果它顯示表單區域，程式碼會瀏覽至 Windows Live 當地搜尋，並載入 Outlook 連絡人項目中所列的每個地址的對應。  
  
#### <a name="to-customize-the-behavior-of-the-form-region"></a>自訂表單區域的行為  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下 MapIt.cs 或 MapIt.vb，，然後按一下**檢視程式碼**。  
  
     MapIt.cs 或 MapIt.vb 會在程式碼編輯器中開啟。  
  
2.  展開**表單區域 Factory**程式碼區域。  
  
     即會公開名為 `MapItFactory` 的表單區域 Factory 類別。  
  
3.  將下列程式碼加入至 `MapItFactory_FormRegionInitializing` 事件處理常式。 當使用者開啟連絡人項目時，即會呼叫這個事件處理常式。 下列程式碼會判斷連絡人項目是否包含地址。 如果連絡人項目不包含地址，這個程式碼設定<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>屬性<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>類別**true**且不顯示表單區域。 否則，VSTO 增益集會引發 <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> 事件，並顯示表單區域。  
  
     [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
     [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
4.  將下列程式碼加入至 <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> 事件處理常式。 這個程式碼會執行下列工作：  
  
    -   串連連絡人項目中的每個地址，並建立 URL 字串。  
  
    -   呼叫 <xref:System.Windows.Forms.WebBrowser> 物件的<xref:System.Windows.Forms.WebBrowser.Navigate%2A> 方法，並將 URL 字串當成參數傳遞。  
  
     當地搜尋網站會出現在 Map It 表單區域中，並在便條簿中顯示每個地址。  
  
     [!code-csharp[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#2)]  
  
## <a name="testing-the-outlook-form-region"></a>測試 Outlook 表單區域  
 當您執行專案時，Visual Studio 會開啟 Outlook。 開啟連絡人項目，以檢視 Map It 表單區域。 在包含地址的任何連絡人項目表單中，Map It 表單區域會顯示為頁面。  
  
#### <a name="to-test-the-map-it-form-region"></a>測試 Map It 表單區域  
  
1.  按 F5 執行專案。  
  
     Outlook 即開啟。  
  
2.  在 Outlook 中，在**首頁**索引標籤上，按一下 **新項目**，然後按一下 **連絡人**。  
  
3.  在連絡人表單中，輸入**王美美**為連絡人的人員名稱，然後再指定下列三個地址。  
  
    |地址類型|地址|  
    |------------------|-------------|  
    |**商務**|**4567 Main St.北市**|  
    |**首頁**|**1234 North St.北市**|  
    |**其他**|**3456 Main St.西雅圖，華盛頓州**|  
  
4.  儲存並關閉連絡人項目。  
  
5.  重新開啟**王美美**連絡人項目。  
  
6.  在**顯示**群組中的項目功能區中，按一下  **Map It**開啟 Map It 表單區域。  
  
     Map It 表單區域即出現並顯示當地搜尋網站。 **商務**，**首頁**，和**其他**都出現在便條簿中。 在便條簿中選取想要對應的地址。  
  
## <a name="next-steps"></a>後續步驟  
 從這些主題，您可以進一步了解如何自訂 Outlook 應用程式的 UI：  
  
-   若要了解如何自訂 Outlook 項目的功能區，請參閱 [Customizing a Ribbon for Outlook](../vsto/customizing-a-ribbon-for-outlook.md)。  
  
## <a name="see-also"></a>請參閱  
 [在執行階段存取表單區域](../vsto/accessing-a-form-region-at-run-time.md)   
 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)   
 [建立 Outlook 表單區域的指導方針](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [逐步解說： 匯入在 Outlook 中設計的表單區域](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [如何： 在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [將表單區域與 Outlook 訊息類別產生關聯](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Outlook 表單區域中的自訂動作](../vsto/custom-actions-in-outlook-form-regions.md)   
 [如何：防止 Outlook 顯示表單區域](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)  
  
  