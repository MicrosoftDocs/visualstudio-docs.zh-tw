---
title: 逐步解說：設計 Outlook 表單區域
description: 瞭解如何在連絡人項目的 [偵測器] 視窗中，設計會顯示為新頁面的自訂 Microsoft Outlook 表單區域。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 80c574799029f3fe8c4769d852886a625ffd93aa
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824274"
---
# <a name="walkthrough-design-an-outlook-form-region"></a>逐步解說：設計 Outlook 表單區域
  自訂的表單區域會擴充標準或自訂的 Microsoft Office Outlook 表單。 在此逐步解說中，您要設計自訂的表單區域，它在連絡人項目的 [偵測器] 視窗中會顯示為新頁面。 這個表單區域會將地址資訊傳送至 Windows Live 當地搜尋網站，顯示連絡人清單中每個地址的對應。 如需表單區域的詳細資訊，請參閱 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 本逐步解說將說明下列工作：

- 建立新的 Outlook VSTO 增益集專案。

- 在 VSTO 增益集專案中加入表單區域。

- 設計表單區域的版面配置。

- 自訂表單區域的行為。

- 測試 Outlook 表單區域。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)] 或更新版本。

  ![影片連結](../vsto/media/playvideo.gif "視訊的連結") 如需本主題的影片版本，請參閱 [影片 how to：設計 Outlook 表單區域](/previous-versions/visualstudio/visual-studio-2008/cc837160(v=vs.90))。

## <a name="create-a-new-outlook-vsto-add-in-project"></a>建立新的 Outlook VSTO 增益集專案
 第一次建立基本的 VSTO 增益集專案。

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>建立新的 Outlook VSTO 增益集專案

1. 在中 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，建立名稱為 **MapItAddIn** 的 Outlook VSTO 增益集專案。

2. 在 [新增專案]  對話方塊中，選取 [為方案建立目錄] 。

3. 將專案儲存至任一目錄。

     如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

## <a name="add-a-form-region-to-the-outlook-vsto-add-in-project"></a>將表單區域加入至 Outlook VSTO 增益集專案
 Outlook VSTO 增益集解決方案可以包含一或多個 Outlook 表單區域項目。 使用 [ **新的 Outlook 表單區域** ] 嚮導，將表單區域專案加入至您的專案。

### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>在 Outlook VSTO 增益集專案中加入表單區域

1. 在 **方案總管** 中，選取 **MapItAddIn** 專案。

2. 在 [專案] 功能表上，按一下 [加入新項目]。

3. 在 [ **加入新專案** ] 對話方塊中，選取 [ **Outlook 表單區域**]，將檔案命名為 **Mapit.vb**，然後按一下 [ **新增**]。

     [ **NewOutlook] 表單區域** wizard 隨即啟動。

4. 在 [ **選取您要如何建立表單區域** ] 頁面上，按一下 [ **設計新的表單區域**]，然後按 **[下一步]**。

5. 在 [ **選取您要建立的表單區欄位型別** ] 頁面上，按一下 [ **獨立**]，然後按 **[下一步]**。

     *不同* 的表單區域會將新頁面新增至 Outlook 表單。 如需表單區欄位型別的詳細資訊，請參閱 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)。

6. 在 [**提供描述文字] 並選取 [顯示喜好** 設定] 頁面上，在 [**名稱**] 方塊中輸入 **Map** 。

     開啟連絡人項目時，這個名稱會出現在 [偵測器] 視窗的功能區上。

7. 選取處於 **撰寫模式** 的偵測器以及處於 **讀取模式** 的偵測器，然後按 **[下一步]**。

8. 在 [ **識別將顯示此表單區域的訊息類別** ] 頁面上，清除 [ **郵件訊息**]，選取 [ **連絡人**]，然後按一下 **[完成]**。

     系統會將 *mapit.vb .cs* 或 *mapit.vb .vb* 檔案新增至您的專案。

## <a name="design-the-layout-of-the-form-region"></a>設計表單區域的版面配置
 使用 [ *表單區域設計* 工具] 以視覺化方式開發表單區域。 您可以將 Managed 控制項拖曳至表單區域設計工具介面。 使用設計工具和 [ **屬性** ] 視窗來調整控制項版面配置和外觀。

### <a name="to-design-the-layout-of-the-form-region"></a>設計表單區域的版面配置

1. 在 **方案總管** 中，展開 [ **MapItAddIn** ] 專案，然後按兩下 [ *mapit.vb* ] 或 [ *Mapit.vb* ] 以開啟 [表單區域設計工具]。

2. 以滑鼠右鍵按一下設計工具，然後按一下 [ **屬性**]。

3. 在 [ **屬性** ] 視窗中，將 [ **大小** ] 設定為 **664、469**。

     這可確保表單區域大到足以顯示地圖。

4. 在 [檢視] 功能表上，按一下 [工具箱]。

5. 從 [**工具箱**] 的 [**通用控制項**] 索引標籤中，將 **WebBrowser** 新增至表單區域。

     **WebBrowser** 會顯示為連絡人列出的每個位址的對應。

## <a name="customize-the-behavior-of-the-form-region"></a>自訂表單區域的行為
 在表單區域事件處理常式中加入程式碼，以自訂表單區域在執行階段的行為方式。 程式碼會檢查此表單區域的 Outlook 項目屬性，並決定是否要顯示 Map It 表單區域。 如果它顯示表單區域，程式碼會瀏覽至 Windows Live 當地搜尋，並載入 Outlook 連絡人項目中所列的每個地址的對應。

### <a name="to-customize-the-behavior-of-the-form-region"></a>自訂表單區域的行為

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ *mapit.vb* ] 或 [ *mapit.vb*]，然後按一下 [ **視圖程式碼**]。

    *Mapit.vb .cs* 或 *mapit.vb* 會在程式碼編輯器中開啟。

2. 展開 **表單區域 Factory** 程式碼區域。

    即會公開名為 `MapItFactory` 的表單區域 Factory 類別。

3. 將下列程式碼加入至 `MapItFactory_FormRegionInitializing` 事件處理常式。 當使用者開啟連絡人項目時，即會呼叫這個事件處理常式。 下列程式碼會判斷連絡人項目是否包含地址。 如果連絡人項目不包含位址，這個程式碼就會將 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 類別的屬性設定 <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> 為 **true** ，而且不會顯示表單區域。 否則，VSTO 增益集會引發 <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> 事件，並顯示表單區域。

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet1":::

4. 將下列程式碼加入至 <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> 事件處理常式。 此程式碼會執行下列工作：

   - 串連連絡人項目中的每個地址，並建立 URL 字串。

   - 呼叫 <xref:System.Windows.Forms.WebBrowser> 物件的<xref:System.Windows.Forms.WebBrowser.Navigate%2A> 方法，並將 URL 字串當成參數傳遞。

     當地搜尋網站會出現在 Map It 表單區域中，並在便條簿中顯示每個地址。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet2":::

## <a name="test-the-outlook-form-region"></a>測試 Outlook 表單區域
 當您執行專案時，Visual Studio 會開啟 Outlook。 開啟連絡人項目，以檢視 Map It 表單區域。 在包含地址的任何連絡人項目表單中，Map It 表單區域會顯示為頁面。

### <a name="to-test-the-map-it-form-region"></a>測試 Map It 表單區域

1. 按 **F5** 執行專案。

     Outlook 即開啟。

2. 在 Outlook 的 [ **首頁** ] 索引標籤上，按一下 [ **新增專案**]，然後按一下 [ **連絡人**]。

3. 在 [連絡人] 表單中，輸入 [ **王王美美** ] 做為連絡人名稱，然後指定下列三個位址。

    |地址類型|位址|
    |------------------|-------------|
    |**商務**|**4567 Main 聖. Buffalo，紐約州**|
    |**首頁**|**1234北方聖. Buffalo，紐約州**|
    |**其他**|**3456主要聖西雅圖，WA**|

4. 儲存並關閉連絡人項目。

5. 重新開啟 [ **王王美美** contact] 專案。

    在 Outlook 中，可以在 [ **尋找** ] 群組中開啟連絡人的通訊錄，或將 [王王美美] 輸入 **搜尋人員** 來完成這項操作。

6. 在專案功能區的 [ **顯示** ] 群組中，按一下 [ **對應** ] 以開啟地圖 it 表單區域。

     Map It 表單區域即出現並顯示當地搜尋網站。 [ **商務**]、[ **首頁**] 和 [ **其他** 位址] 會出現在 [臨時板] 中。 在便條簿中選取想要對應的地址。

## <a name="next-steps"></a>下一步
 從這些主題，您可以進一步了解如何自訂 Outlook 應用程式的 UI：

- 若要瞭解如何自訂 Outlook 專案的功能區，請參閱 [自訂 outlook 功能區](../vsto/customizing-a-ribbon-for-outlook.md)。

## <a name="see-also"></a>另請參閱
- [在執行時間存取表單區域](../vsto/accessing-a-form-region-at-run-time.md)
- [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)
- [建立 Outlook 表單區域的指導方針](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [逐步解說：匯入在 Outlook 中設計的表單區域](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [如何：在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [將表單區域與 Outlook 訊息類別產生關聯](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Outlook 表單區域中的自訂動作](../vsto/custom-actions-in-outlook-form-regions.md)
- [如何：防止 Outlook 顯示表單區域](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
