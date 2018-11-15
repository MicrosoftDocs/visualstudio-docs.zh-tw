---
title: 逐步解說： 從現有的 SharePoint 網站匯入項目 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 86256cdecd878c78c34d7128a05eb7b795067701
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909753"
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>逐步解說： 從現有的 SharePoint 網站匯入項目
  本逐步解說示範如何從現有的 SharePoint 網站將匯入項目[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 專案。  
  
 本逐步解說將示範下列工作：  
  
- 透過加入自訂的網站資料行來自訂 SharePoint 網站 (也稱為*欄位*。  
  
- 匯出至.wsp 檔案的 SharePoint 網站。  
  
- 匯入.wsp 檔案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 使用.wsp 匯入專案。  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的版本[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]和 SharePoint。  
  
-   Visual Studio。  
  
## <a name="customize-a-sharepoint-site"></a>自訂 SharePoint 網站
 此範例中，您會建立並自訂 SharePoint 子網站，藉由將新的網站欄和建立另一個子網站，供後續使用。 更新版本中，您將匯出到.wsp 檔案的第一個子網站，並接著使用匯入自訂的網站資料行至第二個的子網站.wsp 匯入專案。  
  
#### <a name="to-create-and-customize-a-sharepoint-site"></a>若要建立和自訂 SharePoint 網站  
  
1. 開啟 SharePoint 網站使用網頁瀏覽器，例如 http://<em>系統名稱</em>/SitePages/Home.aspx。  
  
2. 建立從主要的 SharePoint 網站的子網站，開啟**站台動作**功能表，然後選擇**新的站台**。  
  
3. 在站台中**建立**對話方塊方塊中，選擇**空白網站**型別。  
  
4. 在 [**標題**方塊中，輸入**站台資料行測試 1**; 在**URL 名稱**方塊中，輸入**columntest1**; 其他設定保留其預設值值，然後選擇**建立**] 按鈕。  
  
5. 在建立網站之後，瀏覽回到主要網站中，瀏覽器中 http://<em>系統名稱</em>/SitePages/Home.aspx。  
  
6. 同樣地，建立空白的子網站，從主要的 SharePoint 網站開啟**網站動作**功能表上，選擇**新的站台**，然後選擇**空白網站**型別。  
  
7. 在 [**標題**方塊中，輸入**站台資料行測試 2**; 在**URL 名稱**方塊中，輸入**columntest2**; 其他設定保留其預設值值，然後選擇**建立**] 按鈕。  
  
8. 瀏覽回到第一個子網站， http://<em>SystemName</em>/columntest1/default.aspx 。  
  
9. 上**站台動作**功能表上，選擇**站台設定**以顯示 [站台設定] 頁面。  
  
10. 在 **資源庫**區段中，選擇**站台的資料行**連結。  
  
11. 在頂端**藝廊網站資料行**頁面上，選擇**建立** 按鈕。  
  
12. 在 **資料行名稱**方塊中，輸入**測試資料行**，保留其他預設值，然後選擇**確定**按鈕。  
  
13. **測試資料行**資料行會出現在自訂資料行標題在站台的資料行組件庫。  
  
## <a name="exporting-the-sharepoint-site"></a>匯出 SharePoint 網站
 接下來，取得 SharePoint 安裝程式 (.wsp) 檔案，其中包含的 SharePoint 項目和您想要匯入的項目您[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 專案。 如果您還沒有的.wsp 檔，然後您必須建立一個從現有的 SharePoint 網站。 針對此範例中，您會將預設的 SharePoint 網站匯出到.wsp 檔案。  
  
> [!IMPORTANT]  
>  如果您收到執行階段錯誤，執行下列程序，您必須對 SharePoint 網站存取的系統上執行程序。  
  
#### <a name="to-export-an-existing-sharepoint-site"></a>將現有的 SharePoint 網站  
  
1.  在 SharePoint 網站中，選擇**站台設定**上**站台動作**索引標籤，顯示 [站台設定] 頁面。  
  
2.  中**站台動作**區段的 [站台設定] 頁面中，選擇**另存為範本的站台**連結。  
  
3.  在 **檔案名稱**方塊中，輸入**ExampleSite**，然後在**範本名稱**方塊中，輸入**範例網站**。  
  
4.  此範例中，保持**內容包括**清除核取方塊。  
  
     如果您選取此方塊中，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]所有清單和文件庫和其內容，將.wsp 檔案。 雖然這樣非常有用，在某些情況下，它不需要這個範例。  
  
5.  當作業成功完成時，選擇**解決方案資源庫**連結來檢視.wsp 檔案。  
  
     若要檢視更新版本中，開啟解決方案資源庫頁面**網站動作**功能表上，選擇**站台設定**，選擇**移至頂層站台設定**連結**網站集合管理**區段，然後再選擇**解決方案**連結**組件庫**一節。  
  
6.  在 解決方案資源庫中，選擇**ExampleSite**連結。  
  
7.  在 **檔案下載**對話方塊方塊中，選擇**儲存**按鈕以儲存您的本機系統上的檔案依預設，在 下載 資料夾。  
  
## <a name="import-the-wsp-file"></a>匯入.wsp 檔案
 您現在已 *.wsp*檔案，其中包含您想要重複使用 （自訂的網站資料行測試資料行），匯入的項目 *.wsp*檔案來存取它。  
  
#### <a name="to-import-a-wsp-file"></a>若要匯入.wsp 檔案  
  
1. 在  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，在功能表列上選擇 **檔案** > **新增** > **專案**顯示**新專案** 對話方塊。 如果您的 IDE 設定為使用 Visual Basic 開發設定，在功能表列上，選擇**檔案** > **新專案**。  
  
2. 依序展開**SharePoint**節點之下**Visual C#** 或**Visual Basic**，然後選擇**2010年**節點。  
  
3. 選擇**匯入 SharePoint 2010 方案套件**中的範本**範本**窗格中，保留 WspImportProject1，作為專案名稱，然後選擇**確定**按鈕。  
  
    **SharePoint 自訂精靈**隨即出現。  
  
4. 在 **指定偵錯的網站和安全性層級**頁面上，輸入[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]您稍早建立的第二個 SharePoint 子網站。 您將會加入新的自訂項目時，欄位 http://<em>系統名稱</em>/columntest2，該子網站。  
  
5. 在 **此 SharePoint 方案的信任層級為何？** 區段中，保留選取項目為**部署為沙箱化方案**。  
  
6. 在 [**指定新專案來源**頁面上，瀏覽至您儲存在系統上位置 *.wsp*先前檔案，然後選擇 [**下一步]** ] 按鈕。  
  
   > [!NOTE]  
   >  如果您選擇**完成**按鈕，在此頁面上，在所有可用的項目 *.wsp*將匯入檔案。  
  
7. 在**選取要匯入項目**方塊中，清除所有核取方塊，在清單中，除了**測試資料行**，然後選擇**完成** 按鈕。  
  
    清單包含許多項目，因為您可以選擇**Ctrl**+**A**金鑰選擇的所有項目在清單中，選擇空格鍵以清除所有核取方塊，然後選取 只檢查中的 下一步**測試資料行**項目。  
  
    匯入作業完成時，新的專案，名為之後**WspImportProject1**建立，其中包含名為的資料夾**欄位**。 在此資料夾是自訂的網站資料行**測試資料行**及其定義檔*Elements.xml*。  
  
## <a name="deploy-the-project"></a>部署專案
 最後，部署**WspImportProject1**到第二個 SharePoint 子網站，您稍早建立若要檢視自訂的網站資料行。  
  
#### <a name="to-deploy-the-project"></a>若要將專案部署  
  
1.  在  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，選擇**F5**來部署和執行的索引鍵 *.wsp*匯入專案。  
  
2.  在 SharePoint 網站上開啟**網站動作**功能表上，然後選擇**站台設定**以顯示 [站台設定] 頁面。  
  
3.  在 **資源庫**區段中，選擇**站台的資料行**連結。  
  
4.  向下捲動至**自訂資料行**一節。  
  
     請注意您從第一個 SharePoint 網站匯入自訂的網站資料行出現在清單中。  
  
## <a name="see-also"></a>另請參閱
 [從現有的 SharePoint 網站匯入項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)   
 [建立可重複使用的控制項，為 web 組件或應用程式頁面](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
