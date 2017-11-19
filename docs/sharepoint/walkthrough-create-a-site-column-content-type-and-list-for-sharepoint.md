---
title: "逐步解說： 建立網站資料行、 內容類型，以及 sharepoint 清單 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
ms.assetid: caebacc2-616c-4373-8e21-edc7979338e7
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d6007dee14f89f875c66009f048b47579e97028b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>逐步解說：建立 SharePoint 的網站資料行、內容類型和清單
  下列程序示範如何建立自訂 SharePoint 網站資料行，或*欄位*— 以及使用的網站資料行的內容類型。 它也會示範如何建立使用新的內容類型的清單。  
  
 本逐步解說包含下列工作：  
  
-   [建立自訂網站資料行](#BKMK_CreatingCustSiteCols)。  
  
-   [建立自訂的內容類型](#BKMK_CreateCustContType)。  
  
-   [建立清單](#BKMK_CreateList)。  
  
-   [建立清單](#BKMK_CreateList)。  
  
-   [測試應用程式](#BKMK_TestApp)。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 Windows 版本和 SharePoint。 如需詳細資訊，請參閱[開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
##  <a name="BKMK_CreatingCustSiteCols"></a>建立自訂網站資料行  
 這個範例會建立管理中醫院病患的清單。 首先，您必須建立 SharePoint 專案中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，如下所示，新增站台的資料行。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
1.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**檔案**功能表上，選擇**新增**，**專案**。  
  
2.  在**新專案**對話方塊之下**Visual C#**或**Visual Basic**，展開**SharePoint** ] 節點，然後選擇 [ **2010年**。  
  
3.  在**範本**] 窗格中，選擇**SharePoint 2010 專案**，變更的專案名稱**診所**，然後選擇 [ **[確定]**按鈕。  
  
     SharePoint 2010 專案範本是空白的專案在此範例中用來包含網站資料行和稍後加入其他專案項目。  
  
4.  在**指定偵錯的網站和安全性層級**頁面上，輸入您要加入新的自訂欄位項目，在本機 SharePoint 網站的 URL，或使用預設位置 (`http://<`*系統名稱*`>/)`.  
  
5.  在**此 SharePoint 方案的信任層級為何？**區段中，使用預設值**部署為沙箱化方案**。  
  
     如需有關沙箱化和伺服器陣列方案，請參閱[沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。  
  
6.  選擇**完成** 按鈕。 專案現在應該會列在**方案總管 中**。  
  
#### <a name="to-add-site-columns"></a>若要加入站台的資料行  
  
1.  加入新的網站資料行。 若要這樣做，請在**方案總管] 中**，開啟捷徑功能表**診所**，然後選擇 [**新增**，**新項目**。  
  
2.  在**加入新項目**對話方塊方塊中，選擇**網站資料行**，將名稱變更為**病患名稱**，然後選擇 [**新增**] 按鈕。  
  
3.  在站台資料行的 Elements.xml 檔案中，保留**類型**設定為**文字**，並變更**群組**設**診所網站資料行**。 完成時，網站資料行的 Elements.xml 檔案看起來應該像下列的範例。  
  
    ```  
    <Field  
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"  
         Name="Clinic - Patient Name"  
         DisplayName="Patient Name"  
         Type="Text"  
         Required="FALSE"  
         Group="Clinic Site Columns">  
    </Field>  
    ```  
  
4.  使用相同的程序，將兩個多站台的資料行加入至專案：**病患識別碼**(類型 = 「 整數 」) 和**醫生名稱**(類型 ="Text")。 將其群組值設定為**診所網站資料行**。  
  
##  <a name="BKMK_CreateCustContType"></a>建立自訂的內容類型  
 接下來，建立內容類型，根據連絡人內容類型 — 包含您在上一個程序中建立的網站資料行。 由現有的內容類型為基礎的內容類型，您可以節省時間，因為基底內容類型提供數個站台的資料行用於新的內容類型。  
  
#### <a name="to-create-a-custom-content-type"></a>若要建立自訂的內容類型  
  
1.  將內容類型加入專案。 若要這樣做，請在**方案總管 中**，選擇專案節點  
  
2.  在功能表列上選擇 **專案**，**加入新項目**。  
  
3.  之下**Visual C#**或**Visual Basic**，依序展開**SharePoint** ] 節點，然後選擇 [ **2010年**節點。  
  
4.  在**範本** 窗格中，選擇**內容類型**範本，將名稱變更為**病患資訊**，然後選擇 **新增** 按鈕。  
  
     **SharePoint 自訂精靈**隨即開啟。  
  
5.  在**此內容類型應該繼承的基底內容類型從**清單中，選擇**連絡人**以內容類型的基底的新的內容類型，然後選擇**完成** 按鈕。  
  
     這樣可讓您存取很有用的網站中其他資料行的連絡人內容類型，除了您在先前定義的網站資料行。  
  
6.  內容型別之後設計工具隨即出現，在**資料行**索引標籤上，新增三個站台先前定義的資料行：**病患名稱**，**病患識別碼**，和**醫生名稱**。 若要新增這些資料行，第一個清單方塊的之下的站台的資料行清單中選擇**顯示名稱**，然後選擇其中一個清單中的每個站台的資料行 一次。  
  
    > [!TIP]  
    >  若要更快速地選擇網站資料行，篩選輸入資料行名稱的前幾個字母的清單。  
  
7.  除了三個自訂網站資料行中，新增**註解**從站台的資料行清單的網站資料行。  
  
8.  選取**必要**核取方塊**病患名稱**和**病患識別碼**網站資料行，使其必要的欄位。  
  
9. 上**內容型別**索引標籤上，確定內容類型名稱是**病患資訊**，然後變更要描述**病患資訊卡**。  
  
10. 變更**群組名稱**至**診所內容類型**，和其他設定保留其預設值。  
  
11. 在功能表列上選擇 **檔案**，**全部儲存**，然後關閉 內容類型設計工具。  
  
##  <a name="BKMK_CreateList"></a>建立清單  
 現在，建立使用新內容型別和站台的資料行的清單。  
  
#### <a name="to-create-a-list"></a>若要建立清單  
  
1.  將清單加入專案。 若要這樣做，請在**方案總管 中**，選擇專案節點。  
  
2.  在功能表列上選擇 **專案**，**加入新項目**。  
  
3.  之下**Visual C#**或**Visual Basic**，依序展開**SharePoint** ] 節點，然後選擇 [ **2010年**節點。  
  
4.  在**範本** 窗格中，選擇**清單**範本，將名稱變更為**病患**，然後選擇 **新增** 按鈕。  
  
5.  保留**自訂清單根據**設定為**預設 （空白）**，然後選擇 [**完成**] 按鈕。  
  
6.  在清單設計工具中，選擇 **內容類型** 按鈕以顯示**內容類型設定** 對話方塊。  
  
7.  選擇新的資料列，請選擇**病患資訊**內容類型清單中的內容類型，然後選擇 [**確定**] 按鈕。  
  
     如此一來加入所有站台的資料行從**病患資訊**內容的清單中的類型。  
  
8.  刪除所有網站中的資料行的清單，但下列除外：  
  
    -   病患識別碼  
  
    -   病患的名稱  
  
    -   住家電話  
  
    -   電子郵件  
  
    -   醫生名稱  
  
    -   註解  
  
9. 在下**資料行的顯示名稱**、 選擇 空白的資料列中，加入自訂清單資料行，並將它命名**醫院**。 將保留做為其資料型別**單一文字行**。  
  
     自訂清單資料行只適用於這份清單。 當您新增自訂清單資料行清單時，新清單的內容類型，包括所有資料行加入至清單中，建立並設定為預設的清單。  
  
    > [!TIP]  
    >  如果您的網站資料行清單中選擇資料行，則會使用現有的網站資料行。 不過，如果您輸入的資料行名稱的值而不在清單中選擇的任何資料行時，自訂清單建立資料行是，即使在清單中已經有相同名稱的資料行。  
  
     （選擇性） 而不是設定之自訂清單資料行的資料型別**單一文字行**您改為可以查閱，設定此資料行的資料類型，會從資料表或另一個清單中擷取其值。 查閱資料行的相關資訊，請參閱[清單關聯性，在 SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=224994)和[查閱和清單關聯性](http://go.microsoft.com/fwlink/?LinkID=224995)。  
  
10. 旁邊**病患識別碼**和**病患名稱**方塊中，選取**需要**核取方塊。  
  
11. 在**檢視**索引標籤上，選擇 空白資料列來建立檢視。 輸入**病患詳細資料**。  
  
     在**檢視**索引標籤上，您可以指定您想要顯示 SharePoint 清單中的資料行。  
  
12. 選擇新**病患詳細資料**資料列，然後再選擇**設為預設值** 按鈕。  
  
     新檢視現在是清單的預設檢視。  
  
13. 將下列資料行加入**選取的資料行**清單順序如下：  
  
    -   病患識別碼  
  
    -   病患的名稱  
  
    -   住家電話  
  
    -   電子郵件  
  
    -   醫生名稱  
  
    -   醫院  
  
    -   註解  
  
14. 在**屬性**清單中，選擇**排序和分組**屬性，然後選擇省略符號按鈕![省略符號圖示](../sharepoint/media/ellipsisicon.gif "省略符號圖示")顯示**排序和分組** 對話方塊。  
  
15. 在**資料行名稱**清單中，選擇**病患名稱**，請確定**排序**資料行設為**遞增**，然後選擇 [ **確定**] 按鈕。  
  
##  <a name="BKMK_TestApp"></a>測試應用程式  
 既然自訂網站資料行、 內容類型和清單準備好時，將其部署至 SharePoint，並執行應用程式進行測試。  
  
#### <a name="to-test-the-application"></a>若要測試應用程式  
  
1.  在功能表列上，依序選擇 [檔案] 和 [全部儲存]。  
  
2.  選擇 F5 鍵以執行應用程式。  
  
     編譯應用程式，，然後其功能是部署至 SharePoint，並啟動。  
  
3.  在 快速巡覽列上選擇 **病患**連結可以顯示**病患**清單。  
  
     在清單中的資料行名稱應符合您在上輸入**檢視**索引標籤中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
4.  選擇**加入新項目**連結，以建立病患資訊卡。  
  
5.  在欄位中輸入資訊，然後選擇**儲存** 按鈕。  
  
     新的記錄會出現在清單中。  
  
## <a name="see-also"></a>另請參閱  
 [建立 SharePoint 的網站資料行、 內容類型和清單](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)   
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)   
 [如何： 建立自訂欄位類型](http://go.microsoft.com/fwlink/?LinkId=192079)   
 [內容類型](http://go.microsoft.com/fwlink/?LinkId=192080)   
 [資料行](http://go.microsoft.com/fwlink/?LinkId=192081)  
  
  