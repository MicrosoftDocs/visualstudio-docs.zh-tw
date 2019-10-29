---
title: 建立 SharePoint 的網站資料行、內容類型和清單
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
ms.openlocfilehash: e78594a98066dec6cedff6da6f3f1de823bec796
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985009"
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>逐步解說：建立 SharePoint 的網站資料行、內容類型和清單
  下列程式示範如何建立自訂 SharePoint 網站資料行（或*欄位*），以及使用網站資料行的內容類型。 它也會顯示如何建立使用新內容類型的清單。

 本逐步解說包含下列工作：

- [建立自訂網站資料行](#create-custom-site-columns)。

- [建立自訂內容類型](#create-a-custom-content-type)。

- [建立清單](#create-a-list)。

- [測試應用程式](#test-the-application)。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisites
 您需要下列元件才能完成此逐步解說：

- 支援的 Windows 和 SharePoint 版本。

- [!INCLUDE[vsprvs-current](../sharepoint/includes/vsprvs-current-md.md)]

## <a name="create-custom-site-columns"></a>建立自訂網站資料行
 這個範例會建立一個清單，用於管理醫院中的病人。 首先，您必須在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中建立 SharePoint 專案，並在其中新增網站欄，如下所示。

#### <a name="to-create-the-project"></a>建立專案

1. 在 **[[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 檔案**] 功能表上，選擇 [**新增** > **專案**]。

2. 在 [**新增專案**] 對話方塊的 [**視覺效果C#**  ] 或 [ **Visual Basic**] 底下，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010**]。

3. 在 [**範本**] 窗格中，選擇 [ **SharePoint 2010 專案**]，將專案名稱**變更為 [** 實務]，然後選擇 [**確定]** 按鈕。

     SharePoint 2010 專案範本是一個空的專案，在此範例中會用來包含稍後新增的網站資料行和其他專案專案。

4. 在 [**指定網站和安全性層級進行偵錯工具**] 頁面上，輸入您要加入新的自訂欄位專案之本機 SharePoint 網站的 URL，或使用預設位置（`http://<`*SystemName*`>/)`。

5. 在 [**此 SharePoint 方案的信任層級為何？** ] 區段中，使用預設值 [**部署為沙箱化方案**]。

     如需沙箱和伺服器陣列方案的詳細資訊，請參閱[沙箱化方案考慮](../sharepoint/sandboxed-solution-considerations.md)。

6. 選擇 [**完成]** 按鈕。 專案現在會列在**方案總管**中。

#### <a name="to-add-site-columns"></a>若要新增網站資料行

1. 加入新的網站資料行。 若要這麼做，請在**方案總管** **中，開啟**[實務] 的快捷方式功能表，然後選擇 [**加入** > **新專案**]。

2. 在 [**加入新專案**] 對話方塊中，選擇 [**網站資料行**]，將名稱變更為 [**患者名稱**]，然後選擇 [**新增**] 按鈕。

3. 在 [網站] 資料行的 [ *Elements* ] 檔案中，將 [**類型**] 設定保留為 [**文字**]，然後將 [**群組**] 設定變更為 [實務**網站欄**]。 完成時，網站資料行的*Elements .xml*檔案看起來應該類似下列範例。

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

4. 使用相同的程式，將兩個以上的網站資料行新增至專案： [**患者 ID** ] （類型 = "Integer"）和**醫生名稱**（類型 = "Text"）。 將其 [群組] 值設定為 [實習**網站] 欄**。

## <a name="create-a-custom-content-type"></a>建立自訂內容類型
 接下來，根據 [連絡人] 內容類型建立內容類型，其中包含您在上一個程式中建立的網站資料行。 藉由在現有內容類型上建立內容類型的基礎，您可以節省時間，因為基底內容類型會提供數個網站欄供新的內容類型使用。

#### <a name="to-create-a-custom-content-type"></a>若要建立自訂內容類型

1. 將內容類型新增至專案。 若要這麼做，請在**方案總管**中，選擇 [專案] 節點

2. 在功能表列中，選擇 [專案] > [加入新項目]。

3. 在 [**視覺C#效果**] 或 [ **Visual Basic**] 底下，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

4. 在 [**範本**] 窗格中，選擇 [**內容類型**] 範本，將名稱變更為 [**患者資訊**]，然後選擇 [**新增**] 按鈕。

     **SharePoint 自訂嚮導**隨即開啟。

5. 在 [**此內容類型的繼承來源**] 清單中，選擇 [**連絡人**] 做為新內容類型的基底內容類型，然後選擇 [**完成]** 按鈕。

     這麼做可讓您存取連絡人內容類型中其他可能有用的網站資料行，以及您先前定義的網站資料行。

6. 內容類型設計工具出現之後，請在 [資料**行**] 索引標籤中，新增您先前定義的三個網站資料行： [**患者名稱**]、[**患者識別碼**] 和 [**醫生名稱**]。 若要新增這些資料行，請在 [**顯示名稱**] 底下的 [網站資料行] 清單中選擇第一個清單方塊，然後在清單中一次選擇一個 [網站] 資料行。

    > [!TIP]
    > 若要更快速地選擇網站資料行，請輸入資料行名稱的前幾個字母，以篩選清單。

7. 除了三個自訂網站資料行之外，也請從 [網站資料行] 清單中加入 [**批註**網站] 資料行。

8. 選取 [**患者名稱**] 和 [**患者 ID**網站] 欄的 [**必要**] 核取方塊，使其成為必要欄位。

9. 在 [**內容類型**] 索引標籤上，確認 [內容類型名稱] 為 [**患者資訊**]，然後將 [描述] 變更為 [**患者資訊卡片**]。

10. 將 [**組名**] 變更為 [實習**內容類型**]，並將其他設定保留為預設值。

11. 在功能表列上 **，選擇 [** 檔案] > [**全部儲存**]，然後關閉 [內容類型設計工具]。

## <a name="create-a-list"></a>建立清單
 現在，請建立使用新內容類型和網站資料行的清單。

#### <a name="to-create-a-list"></a>建立清單

1. 將清單加入至專案。 若要這麼做，請在**方案總管**中，選擇專案節點。

2. 在功能表列中，選擇 [專案] > [加入新項目]。

3. 在 [**視覺C#效果**] 或 [ **Visual Basic**] 底下，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

4. 在 [**範本**] 窗格中，選擇 [**清單**] 範本，將名稱變更為 [**病人**]，然後選擇 [**新增**] 按鈕。

5. 保留 [**根據預設值自訂清單** **（空白）** ]，然後選擇 [**完成]** 按鈕。

6. 在 [清單設計工具] 中，選擇 [**內容類型**] 按鈕以顯示 [**內容類型設定**] 對話方塊。

7. 選擇新的資料列，選擇內容類型清單中的 [**患者資訊**] 內容類型，然後選擇 [**確定]** 按鈕。

     這麼做會將 [**患者資訊**] 內容類型中的所有網站資料行新增至清單中。

8. 刪除清單中的所有網站資料行，但不包括下列各項：

    - 患者識別碼

    - 患者名稱

    - 家用電話

    - 位址

    - 醫生姓名

    - 註解

9. 在 [資料行**顯示名稱**] 下，選擇空白資料列、加入自訂清單欄，並將其命名為「**醫院**」。 將其資料類型保留為 [**單行文字**]。

     自訂清單資料行僅適用于這份清單。 當您將自訂清單資料行新增至清單時，會建立新的清單內容類型（包括新增至清單中的所有資料行），並將其設定為預設清單。

    > [!TIP]
    > 如果您從網站資料行清單中選擇資料行，則會使用現有的網站資料行。 不過，如果您輸入資料行名稱值，但未挑選清單中的任何資料行，則會建立自訂清單資料行，即使清單中已經有相同名稱的資料行也一樣。

     您可以選擇性地將 [自訂清單] 資料行的資料類型設定為 [**單行文字**]，而不是將資料類型設為 [查閱]，而它的值會從資料表或其他清單中抓取。 如需查閱資料行的詳細資訊，請參閱[在 SharePoint 2010 中列出關聯](/previous-versions/msp-n-p/ff798514(v=pandp.10))性和查閱[和列出關聯](/previous-versions/office/developer/sharepoint-2010/ff623048(v=office.14))性。

10. 在 [**患者識別碼**] 和 [**患者名稱**] 方塊旁，選取 [**必要**] 核取方塊。

11. 在 [ **Views** ] 索引標籤上，選擇空白資料列以建立視圖。 輸入**患者詳細資料**。

     在 [ **Views** ] 索引標籤上，您可以指定要顯示在 SharePoint 清單中的資料行。

12. 選擇 [新的**患者詳細資料**] 列，然後選擇 [**設為預設值**] 按鈕。

     新的視圖現在是清單的預設視圖。

13. 依照下列順序，將下列資料行新增至 [選取的資料**行**] 清單：

    - 患者識別碼

    - 患者名稱

    - 家用電話

    - 位址

    - 醫生姓名

    - 醫院

    - 註解

14. 在 [**屬性**] 清單中，選擇 [**排序和群組**] 屬性，然後選擇省略號按鈕![省略號圖示](../sharepoint/media/ellipsisicon.gif "省略符號圖示")，以顯示 [**排序與群組**] 對話方塊。

15. 在 [資料**行名稱**] 清單中，選擇 [**患者名稱**]，確定 [**排序**] 資料行設定為 [**遞增**]，然後選擇 [**確定]** 按鈕。

## <a name="test-the-application"></a>測試應用程式
 現在，自訂網站資料行、內容類型和清單已就緒，請將其部署至 SharePoint，然後執行應用程式來進行測試。

#### <a name="to-test-the-application"></a>若要測試應用程式

1. 在功能表列上，依序選擇 [檔案] > [全部儲存]。

2. 選擇**F5**鍵以執行應用程式。

     應用程式會經過編譯，然後它的功能會部署到 SharePoint 並加以啟用。

3. 在快速導覽列上，選擇 [**病人**] 連結以顯示 [**病人**] 清單。

     清單中的資料行名稱應符合您在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]的 [ **Views** ] 索引標籤中輸入的名稱。

4. 選擇 [**加入新專案**] 連結以建立患者資訊卡。

5. 在欄位中輸入資訊，然後選擇 [**儲存**] 按鈕。

     新的記錄會出現在清單中。

## <a name="see-also"></a>請參閱
- [建立 SharePoint 的網站資料行、內容類型和清單](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
- [如何：建立自訂欄位類型](/previous-versions/office/developer/sharepoint-2010/bb862248(v=office.14))
- [內容類型](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14))
- [資料行](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))
