---
title: "逐步解說： 從現有的 SharePoint 網站匯入的項目 |Microsoft 文件"
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
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b9d1bcc72bd22e7c528b2a3d8752d15b7005fea5
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>逐步解說：從現有的 SharePoint 網站匯入項目
  本逐步解說示範如何從現有的 SharePoint 網站將匯入的項目[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 專案。  
  
 本逐步解說將示範下列工作：  
  
-   透過加入自訂的網站資料行來自訂 SharePoint 網站 (也稱為*欄位*。  
  
-   匯出至.wsp 檔案的 SharePoint 網站。  
  
-   匯入.wsp 檔案貼入[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 使用.wsp 匯入專案。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的版本[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]和 SharePoint。 如需詳細資訊，請參閱[開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
## <a name="customizing-a-sharepoint-site"></a>自訂 SharePoint 網站  
 例如，您會建立和自訂 SharePoint 子網站，藉由加入新的網站資料行並建立另一個子網站，供後續使用。 稍後，您將匯出到.wsp 檔案的第一個子網站，然後使用匯入自訂的網站資料行至第二個子網站.wsp 匯入專案。  
  
#### <a name="to-create-and-customize-a-sharepoint-site"></a>建立和自訂 SharePoint 網站  
  
1.  開啟 SharePoint 網站使用網頁瀏覽器，例如 http://*系統名稱*/SitePages/Home.aspx。  
  
2.  建立子網站，從主要的 SharePoint 網站開啟**網站動作**功能表，然後選擇**新站台**。  
  
3.  在網站的**建立**對話方塊方塊中，選擇**空白網站**型別。  
  
4.  在**標題**方塊中，輸入**網站資料行測試 1**; 在**URL 名稱**方塊中，輸入**columntest1**; 其他設定保留其預設值值，然後選擇 [**建立**] 按鈕。  
  
5.  在建立網站之後，瀏覽至主要站台，在瀏覽器中 http://*系統名稱*/SitePages/Home.aspx。  
  
6.  同樣地，建立空白的子網站，從主要的 SharePoint 網站開啟**網站動作**功能表上，選擇**新站台**，然後選擇 **空白網站**型別。  
  
7.  在**標題**方塊中，輸入**網站資料行測試 2**; 在**URL 名稱**方塊中，輸入**columntest2**; 其他設定保留其預設值值，然後選擇 [**建立**] 按鈕。  
  
8.  瀏覽回到第一個子網站，http://*系統名稱*/columntest1/default.aspx。  
  
9. 在**網站動作**功能表上，選擇**站台設定**顯示站台設定 頁面。  
  
10. 在**圖庫**區段中，選擇**站台的資料行**連結。  
  
11. 在頂端**庫網站資料行**頁面上，選擇**建立** 按鈕。  
  
12. 在**資料行名稱**方塊中，輸入**測試資料行**，保留其他預設值，然後選擇**確定** 按鈕。  
  
13. **測試資料行**資料行會出現在自訂的資料行標題在站台的資料行組件庫。  
  
## <a name="exporting-the-sharepoint-site"></a>匯出 SharePoint 網站  
 接下來，取得 SharePoint 安裝程式 (.wsp) 檔案，其中包含的 SharePoint 項目和您想要匯入的項目您[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 專案。 如果您還沒有.wsp 檔案，然後您必須建立一個從現有的 SharePoint 網站。 針對此範例中，您會將預設的 SharePoint 網站匯出.wsp 檔案。  
  
> [!IMPORTANT]  
>  如果您收到執行階段錯誤，執行下列程序，您必須有權存取 SharePoint 網站的系統上執行程序。  
  
#### <a name="to-export-an-existing-sharepoint-site"></a>若要匯出的現有 SharePoint 網站  
  
1.  在 SharePoint 網站中，選擇 **站台設定**上**網站動作**索引標籤以顯示 站台設定 頁面。  
  
2.  在**網站動作**> 一節的站台設定] 頁面上，選擇 [**另存為範本的站台**連結。  
  
3.  在**檔案名稱**方塊中，輸入**ExampleSite**，然後在**範本名稱**方塊中，輸入**範例站台**。  
  
4.  此範例中，將保留**內容包含**清除核取方塊。  
  
     如果您選取此方塊，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]所有清單和文件庫和其內容，將.wsp 檔案。 雖然這在某些情況下非常有用，但是它不需要此範例中。  
  
5.  作業成功完成時，選擇 **解決方案資源庫**連結，即可檢視.wsp 檔案。  
  
     若要檢視更新版本中開啟方案庫頁面**網站動作**功能表上，選擇**站台設定**，選擇**移至頂層站台設定**中連結**網站集合管理**區段，然後再選擇**解決方案**中連結**圖庫**> 一節。  
  
6.  在解決方案資源庫中，選擇  **ExampleSite**連結。  
  
7.  在**檔案下載**對話方塊方塊中，選擇**儲存**按鈕以儲存您的本機系統上的檔案依預設，在下載資料夾。  
  
## <a name="importing-the-wsp-file"></a>匯入.wsp 檔案  
 現在您有包含您想要重複使用 （自訂的網站資料行測試資料行） 的項目.wsp 檔案，匯入.wsp 檔案存取權。  
  
#### <a name="to-import-a-wsp-file"></a>若要匯入.wsp 檔案  
  
1.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，在功能表列上選擇 [**檔案**，**新增**，**專案**顯示**新專案**] 對話方塊。 如果您的 IDE 設定為使用 Visual Basic 開發設定，在功能表列上，選擇**檔案**，**新專案**。  
  
2.  展開**SharePoint**節點之下**Visual C#**或**Visual Basic**，然後選擇  **2010年**節點。  
  
3.  選擇**匯入 SharePoint 2010 方案套件**中的範本**範本**] 窗格中，保留與 WspImportProject1，專案名稱，然後選擇 [**確定**按鈕。  
  
     **SharePoint 自訂精靈**隨即出現。  
  
4.  在**指定偵錯的網站和安全性層級**頁面上，輸入[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]您稍早建立的第二個 SharePoint 子網站。 您將加入新的自訂項目、 欄位 http://*系統名稱*/columntest2，該子網站。  
  
5.  在**此 SharePoint 方案的信任層級為何？**區段中，選擇**部署為沙箱化方案**。  
  
6.  在**指定新專案來源**頁面上，瀏覽至系統上儲存.wsp 檔案先前的位置，然後選擇**下一步** 按鈕。  
  
    > [!NOTE]  
    >  如果您選擇**完成**將匯入在這個頁面上，將.wsp 檔案中所有可用的項目 按鈕。  
  
7.  在**選取要匯入項目**方塊中，清除所有核取方塊，在清單中，除了**測試資料行**，然後選擇 **完成**按鈕。  
  
     清單包含許多項目，因為您可以選擇 Ctrl + A 鍵來選擇所有的項目在清單中，選擇空格鍵以清除所有核取方塊，然後核取方塊旁的 **測試資料行**項目。  
  
     匯入作業完成時，新的專案，名為之後**WspImportProject1**建立，其中包含名為的資料夾**欄位**。 這個資料夾就是自訂的網站資料行**測試資料行**及其 Elements.xml 的定義檔。  
  
## <a name="deploying-the-project"></a>部署專案  
 最後，部署**WspImportProject1**至第二個 SharePoint 子網站，您先前建立檢視的自訂網站資料行。  
  
#### <a name="to-deploy-the-project"></a>部署專案  
  
1.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，選擇 F5 鍵來部署和執行.wsp 匯入專案。  
  
2.  在 SharePoint 網站上開啟**網站動作**功能表，然後選擇 [**站台設定**顯示站台設定] 頁面。  
  
3.  在**圖庫**區段中，選擇**站台的資料行**連結。  
  
4.  向下捲動至**自訂資料行**> 一節。  
  
     請注意您從第一個 SharePoint 網站匯入的自訂網站資料行出現在清單中。  
  
## <a name="see-also"></a>請參閱  
 [從現有的 SharePoint 網站匯入的項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)   
 [為 Web 組件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  