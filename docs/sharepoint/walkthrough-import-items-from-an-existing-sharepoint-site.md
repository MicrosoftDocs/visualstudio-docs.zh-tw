---
title: 逐步解說：從現有的 SharePoint 網站匯入專案 |Microsoft Docs
titleSuffix: ''
description: 在這個逐步解說中，將專案從現有的 SharePoint 網站匯入 Visual Studio 的 SharePoint 專案。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 861b6ff20f9ceb73c279e54fa89ee513389b6b91
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900956"
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>逐步解說：從現有的 SharePoint 網站匯入專案
  本逐步解說示範如何將專案從現有的 SharePoint 網站匯入至 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 專案。

 本逐步解說將示範下列工作：

- 藉由新增自訂網站欄 (也稱為 *欄位* 來自訂 SharePoint 網站。

- 將 SharePoint 網站匯出至 .wsp 檔。

- 使用 .wsp 匯入專案將 .wsp 檔案匯入到 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- 支援的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 和 SharePoint 版本。

- Visual Studio。

## <a name="customize-a-sharepoint-site"></a>自訂 SharePoint 網站
 在此範例中，您將建立和自訂 SharePoint 子網站，方法是在其中加入新的網站資料行，並建立另一個子網站以供稍後使用。 稍後，您會將第一個子網站匯出至 .wsp 檔案，然後使用 .wsp 匯入專案將自訂網站資料行匯入至第二個子網站。

### <a name="to-create-and-customize-a-sharepoint-site"></a>若要建立和自訂 SharePoint 網站

1. 使用網頁瀏覽器開啟 SharePoint 網站，例如 HTTP://<em>系統名稱</em>/SitePages/Home.aspx。

2. 開啟 [ **網站動作** ] 功能表，然後選擇 [ **新增網站**]，以從主要 SharePoint 網站建立子網站。

3. 在網站的 [ **建立** ] 對話方塊中，選擇 **空白的網站** 類型。

4. 在 [ **標題** ] 方塊中，輸入 **Site Column Test 1**;在 [ **URL 名稱** ] 方塊中，輸入 **columntest1**;將其他設定保留為預設值;然後選擇 [ **建立** ] 按鈕。

5. 建立網站之後，在瀏覽器中流覽回到主要網站 HTTP://<em>系統名稱</em>/SitePages/Home.aspx。

6. 同樣地，開啟 [ **網站動作** ] 功能表，選擇 [ **新網站**]，然後選擇 **空白的網站** 類型，以從主要 SharePoint 網站建立空白的子網站。

7. 在 [ **標題** ] 方塊中，輸入 **Site Column Test 2**;在 [ **URL 名稱** ] 方塊中，輸入 **columntest2**;將其他設定保留為預設值;然後選擇 [ **建立** ] 按鈕。

8. 流覽回到第一個子網站： HTTP://<em>SystemName</em>/columntest1/default.aspx。

9. 在 [ **網站動作** ] 功能表上，選擇 [ **網站設定** ] 以顯示 [網站設定] 頁面。

10. 在 [資源 **庫** ] 區段中，選擇 [ **網站資料行** ] 連結。

11. 在 [ **網站資料行資源庫** ] 頁面的頂端，選擇 [ **建立** ] 按鈕。

12. 在 [資料 **行名稱** ] 方塊中，輸入 [ **測試資料行**]，保留其他預設值，然後選擇 [ **確定]** 按鈕。

13. [ **測試資料行** ] 資料行會出現在 [網站] 資料行圖庫的 [自訂資料行] 標題下。

## <a name="exporting-the-sharepoint-site"></a>匯出 SharePoint 網站
 接下來，取得 SharePoint 安裝程式 ( .wsp) 檔案，其中包含您想要匯入至 sharepoint 專案的 SharePoint 專案和元素 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 如果您還沒有 .wsp 檔，則必須從現有的 SharePoint 網站建立一個檔案。 在此範例中，您會將預設的 SharePoint 網站匯出至 .wsp 檔。

> [!IMPORTANT]
> 如果您在執行下列程式時收到執行階段錯誤，則必須在具有 SharePoint 網站存取權的系統上執行該程式。

### <a name="to-export-an-existing-sharepoint-site"></a>若要匯出現有的 SharePoint 網站

1. 在 SharePoint 網站中，選擇 [**網站動作**] 索引標籤上的 [**網站設定**]，以顯示 [網站設定] 頁面。

2. 在 [網站設定] 頁面的 [ **網站動作** ] 區段中，選擇 [ **另存網站為範本** ] 連結。

3. 在 [ **檔案名** ] 方塊中，輸入 **ExampleSite**，然後在 [ **範本名稱** ] 方塊中輸入 **範例網站**。

4. 在此範例中，請將 [ **包含內容** ] 核取方塊保留為清除。

     如果您選取此方塊，則會 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將所有清單和文件庫及其內容儲存至 .wsp 檔案。 雖然這在某些情況下很有用，但此範例並不需要這麼做。

5. 當作業成功完成時，請選擇 [ **方案庫** ] 連結來查看 .wsp 檔案。

     若要在稍後查看 [方案庫] 頁面，請開啟 [**網站動作**] 功能表，選擇 [**網站設定**]，選擇 [**網站集合管理**] 區段中的 [**移至最上層網站設定**] 連結，然後選擇 [資源 **庫**] 區段中的 [**方案**] 連結。

6. 在 [方案庫] 中，選擇 [ **ExampleSite** ] 連結。

7. 在 [檔案 **下載** ] 對話方塊中，選擇 [ **儲存** ] 按鈕，依預設，將檔案儲存在本機系統上的 [下載] 資料夾中。

## <a name="import-the-wsp-file"></a>匯入 .wsp 檔案
 現在您有一個 *.wsp* 檔案，其中包含您想要重複使用的專案 (自訂網站資料行測試資料行) ，請匯入 *.wsp* 檔案加以存取。

### <a name="to-import-a-wsp-file"></a>匯入 .wsp 檔案

1. 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的功能表列上，選擇 [**檔案**  >  **新增**  >  **專案**]，以顯示 [**新增專案**] 對話方塊。 如果您的 IDE 設定為使用 Visual Basic 開發設定，請在功能表列 **上選擇 [** 檔案  >  **新增專案**]。

2. 展開 [ **Visual c #** ] 或 [ **Visual Basic**] 底下的 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

3. 選擇 [**範本**] 窗格中的 [匯 **入 SharePoint 2010 方案套件**] 範本，將專案的名稱保留為 WspImportProject1，然後選擇 [**確定]** 按鈕。

    [ **SharePoint 自訂] Wizard** 隨即出現。

4. 在 [ **指定偵錯工具的網站和安全性層級** ] 頁面上，輸入 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 您稍早建立的第二個 SharePoint 子網站的。 您會將新的自訂欄位專案 HTTP://<em>系統名稱</em>/columntest2 新增至該子網站。

5. 在 [ **此 SharePoint 方案的信任層級為何？** ] 區段中，將選取專案保留為 [ **部署為沙箱化方案**]。

6. 在 [ **指定新的專案來源** ] 頁面中，流覽至系統上先前儲存 *.wsp* 檔案的位置，然後選擇 [ **下一步]** 按鈕。

   > [!NOTE]
   > 如果您選擇這個頁面上的 [ **完成]** 按鈕，就會匯入 *.wsp* 檔案中的所有可用專案。

7. 在 [ **選取要匯入的專案** ] 方塊中，清除 [ **測試資料行**] 以外的清單中的所有核取方塊，然後選擇 [ **完成]** 按鈕。

    因為此清單包含許多專案，所以您可以選擇 **Ctrl** + 鍵來挑選清單中的所有專案，選擇空格鍵以清除所有核取方塊，然後只選取 [測試] 資料 **行** 專案旁的核取方塊。

    匯入作業完成後，會建立名為 **WspImportProject1** 的新專案，其中包含名為 [ **欄位**] 的資料夾。 在此資料夾中，[自訂網站資料行] **測試資料行** 及其定義檔 *Elements.xml*。

## <a name="deploy-the-project"></a>部署專案
 最後，將 **WspImportProject1** 部署到您稍早建立的第二個 SharePoint 子網站，以查看自訂網站資料行。

### <a name="to-deploy-the-project"></a>若要部署此專案

1. 在中 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，選擇 **F5** 鍵來部署和執行 *.wsp* 匯入專案。

2. 在 SharePoint 網站上，開啟 [ **網站動作** ] 功能表，然後選擇 [ **網站設定** ] 以顯示 [網站設定] 頁面。

3. 在 [資源 **庫** ] 區段中，選擇 [ **網站資料行** ] 連結。

4. 向下滾動至 [ **自訂資料行** ] 區段。

     請注意，您從第一個 SharePoint 網站匯入的自訂網站欄會出現在清單中。

## <a name="see-also"></a>另請參閱
- [從現有的 SharePoint 網站匯入專案](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
- [為 web 元件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
