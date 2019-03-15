---
title: 逐步解說：建立網站資料行、 內容類型，以及適用於 SharePoint 清單 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 244841b5b9416709eda0913d53535d29c83df647
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57870395"
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>逐步解說：建立 SharePoint 網站資料行、 內容類型和清單
  下列程序示範如何建立自訂的 SharePoint 網站資料行，或*欄位*— 以及使用的網站資料行的內容類型。 它也會示範如何建立會使用新的內容類型的清單。

 本逐步解說包含下列工作：

- [建立自訂網站欄](#create-custom-site-columns)。

- [建立自訂的內容類型](#create-a-custom-content-type)。

- [建立清單](#create-a-list)。

- [測試應用程式](#test-the-application)。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

-   支援的 Windows 和 SharePoint 版本。

-   Visual Studio。

## <a name="create-custom-site-columns"></a>建立自訂網站欄
 這個範例會建立管理病患在醫院中的清單。 首先，您必須建立 SharePoint 專案中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]和網站資料行加入它，如下所示。

#### <a name="to-create-the-project"></a>若要建立專案

1.  在  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**檔案**功能表上，選擇**新增** > **專案**。

2.  中**新的專案**對話方塊中，在**Visual C#** 或**Visual Basic**，展開**SharePoint** ] 節點，然後選擇 [ **2010年**。

3.  中**範本** 窗格中，選擇**SharePoint 2010 專案**，變更至專案的名稱**Clinic**，然後選擇**確定**按鈕。

     SharePoint 2010 專案範本是空的專案在此範例中用來包含網站欄和稍後加入其他專案項目。

4.  在 **指定偵錯的網站和安全性層級**頁面上，輸入您要加入新的自訂欄位項目，本機 SharePoint 網站的 URL，或使用預設位置 (`http://<`*SystemName*`>/)`.

5.  在 **此 SharePoint 方案的信任層級為何？** 區段中，使用預設值**部署為沙箱化方案**。

     如需有關沙箱和伺服器陣列方案，請參閱[沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。

6.  選擇**完成** 按鈕。 專案現在應該會列在**方案總管 中**。

#### <a name="to-add-site-columns"></a>若要加入站台的資料行

1.  加入新的網站資料行。 若要這樣做，請在**方案總管 中**，開啟捷徑功能表**實務課程**，然後選擇**新增** > **新項目**。

2.  中**加入新項目**對話方塊方塊中，選擇**網站資料行**，將名稱變更為**病患名稱**，然後選擇**新增** 按鈕。

3.  在網站資料行的*Elements.xml*檔案中，保留**型別**設為**文字**，並將變更**群組**設為  **實習課程中的網站欄**。 完成時，網站資料行的*Elements.xml*檔案應該看起來如下列範例所示。

    ```xml
    <Field
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"
         Name="Clinic - Patient Name"
         DisplayName="Patient Name"
         Type="Text"
         Required="FALSE"
         Group="Clinic Site Columns">
    </Field>
    ```

4.  使用相同的程序，會將兩個站台的資料行加入至專案：**病患識別碼**(類型 ="Integer") 和**醫生名稱**(類型 ="Text")。 將其群組的值設定為**實習課程中的網站欄**。

## <a name="create-a-custom-content-type"></a>建立自訂的內容類型
 接下來，建立內容類型，根據連絡人內容類型，其中包含您在上一個程序中建立的網站資料行。 藉由現有的內容類型為基礎的內容類型，您可以節省時間，因為基底內容類型提供數個站台的資料行，以用於新的內容類型。

#### <a name="to-create-a-custom-content-type"></a>若要建立自訂的內容類型

1.  您可以將內容類型加入專案。 若要這樣做，請在**方案總管 中**，選擇專案節點

2.  在功能表列中，選擇 [專案] > [加入新項目]。

3.  之下**Visual C#** 或**Visual Basic**，展開**SharePoint**  節點，然後選擇**2010年**節點。

4.  中**範本**窗格中，選擇**內容類型**範本，將名稱變更為**病患資訊**，然後選擇**新增** 按鈕。

     **SharePoint 自訂精靈**隨即開啟。

5.  在**這個內容類型應該繼承的基底內容類型從**清單中，選擇**連絡人**上要當成新的內容類型，然後選擇 [內容類型為**完成**] 按鈕。

     執行此動作可讓您存取連絡人內容類型，除了您在先前定義的網站資料行中的其他有用的網站資料行。

6.  內容類型設計工具出現之後，在**資料行**索引標籤上，新增三個站台先前定義的資料行：**病患名稱**，**病患識別碼**，以及**醫生名稱**。 若要新增這些資料行，第一個清單方塊的清單中選擇站台資料行底下**顯示名稱**，然後選擇其中一個清單中的每個站台的資料行 一次。

    > [!TIP]
    >  若要更快速地選擇網站資料行，請輸入的資料行名稱的前幾個字母來篩選清單。

7.  除了三個自訂網站欄中，新增**註解**從網站資料行清單的網站資料行。

8.  選取 **必要**核取方塊**病患名稱**並**病患識別碼**網站資料行，使其必要的欄位。

9. 上**內容型別**索引標籤上，請確定內容類型名稱**病患資訊**，然後將變更的描述**病患資訊卡**。

10. 變更**群組名稱**要**實務課程內容類型**，和其他設定保留其預設值。

11. 在功能表列上選擇 **檔案** > **全部儲存**，然後關閉 內容類型設計工具。

## <a name="create-a-list"></a>建立清單
 現在，建立會使用新內容類型和站台的資料行的清單。

#### <a name="to-create-a-list"></a>若要建立清單

1.  將清單加入專案。 若要這樣做，請在**方案總管 中**，選擇專案節點。

2.  在功能表列中，選擇 [專案] > [加入新項目]。

3.  之下**Visual C#** 或**Visual Basic**，展開**SharePoint**  節點，然後選擇**2010年**節點。

4.  中**範本**窗格中，選擇**清單**範本，將名稱變更為**病患**，然後選擇**新增** 按鈕。

5.  離開**自訂清單為基礎**設為**預設 （空白）**，然後選擇**完成** 按鈕。

6.  在清單設計工具中，選擇**內容類型** 按鈕以顯示**內容類型設定** 對話方塊。

7.  選擇新的資料列，然後選擇**病患資訊**內容清單中的內容類型的類型，然後選擇**確定** 按鈕。

     這麼做會新增所有站台的資料行從**病患資訊**內容至清單的類型。

8.  刪除所有網站中的資料行的清單，但下列除外：

    -   病患識別碼

    -   病患的名稱

    -   住家電話

    -   電子郵件

    -   醫生名稱

    -   註解

9. 底下**資料行的顯示名稱**，選擇 空白的資料列、 加入自訂清單資料行，並將它命名**醫院**。 保留為其資料型別**單一文字行**。

     自訂清單資料行僅適用於這份清單。 當您將自訂的清單資料行加入清單時，新清單的內容類型，包括所有資料行加入至清單中，建立並設定為預設的清單。

    > [!TIP]
    >  如果您從站台的資料行清單中選擇資料行，則會使用現有的網站資料行。 不過，如果您輸入的資料行名稱的值而不在清單中選擇任何資料行時，自訂清單建立資料行是，即使在清單中已經有相同名稱的資料行。

     （選擇性） 而不是設定的自訂清單資料行的資料類型**單一文字行**、 您改為可以設定此資料行的資料類型為查閱，以及從資料表或另一個清單，會擷取其值。 查閱資料行的相關資訊，請參閱[SharePoint 2010 中的清單關聯性](http://go.microsoft.com/fwlink/?LinkId=224994)並[查閱和清單的關聯性](http://go.microsoft.com/fwlink/?LinkID=224995)。

10. 旁**病患識別碼**並**病患名稱**方塊中，選取**需要**核取方塊。

11. 在 **檢視**索引標籤上，選擇 空白的資料列來建立檢視。 請輸入**病患詳細資料**。

     在 **檢視**索引標籤上，您可以指定您想要出現在 SharePoint 清單中的資料行。

12. 選擇新**病患詳細資料**資料列，然後選擇**設為預設值** 按鈕。

     新檢視現在是清單的預設檢視。

13. 將下列資料行加入**選取的資料行**依下列順序的清單：

    -   病患識別碼

    -   病患的名稱

    -   住家電話

    -   電子郵件

    -   醫生名稱

    -   醫院

    -   註解

14. 在**屬性**清單中，選擇**排序及分組**屬性，然後選擇省略符號按鈕![省略符號圖示](../sharepoint/media/ellipsisicon.gif "省略符號圖示")以顯示**排序及分組** 對話方塊。

15. 在**資料行名稱**清單中，選擇**病患名稱**，請確定**排序**資料行會設定為**遞增**，然後選擇 [ **確定**] 按鈕。

## <a name="test-the-application"></a>測試應用程式
 既然自訂站台的資料行、 內容類型和清單準備好時，將其部署至 SharePoint，並執行應用程式以進行測試。

#### <a name="to-test-the-application"></a>若要測試應用程式

1.  在功能表列上，依序選擇 [檔案] > [全部儲存]。

2.  選擇**F5**鍵以執行應用程式。

     已編譯應用程式，且其功能會部署到 SharePoint，然後啟動。

3.  快速瀏覽列上，選擇**病患**連結，以顯示**病患**清單。

     在清單中的資料行名稱應該符合您在上輸入**檢視**索引標籤中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

4.  選擇**加入新項目**建立病患資訊卡的連結。

5.  在欄位中輸入資訊，然後選擇**儲存** 按鈕。

     新的記錄會出現在清單中。

## <a name="see-also"></a>另請參閱
- [建立 SharePoint 網站資料行、 內容類型和清單](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
- [如何：建立自訂欄位類型](http://go.microsoft.com/fwlink/?LinkId=192079)
- [內容類型](http://go.microsoft.com/fwlink/?LinkId=192080)
- [資料行](http://go.microsoft.com/fwlink/?LinkId=192081)
