---
title: 建立 SharePoint 的網站資料行、內容類型和清單
titleSuffix: ''
description: 在這個逐步解說中，建立自訂網站資料行 (欄位) 、使用 [網站] 欄的自訂內容類型，以及在 SharePoint 中使用內容類型的清單。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d205203797d8bd50c7b3132df86fbff9dbad1771
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937689"
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>逐步解說：建立 SharePoint 的網站資料行、內容類型和清單
  下列程式示範如何建立自訂 SharePoint 網站資料行（或 *欄位*），以及使用網站資料行的內容類型。 它也會顯示如何建立使用新內容類型的清單。

 本逐步解說包含下列工作：

- [建立自訂網站資料行](#create-custom-site-columns)。

- [建立自訂內容類型](#create-a-custom-content-type)。

- [建立清單](#create-a-list)。

- [測試應用程式](#test-the-application)。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- 支援的 Windows 和 SharePoint 版本。

- [!INCLUDE[vsprvs-current](../sharepoint/includes/vsprvs-current-md.md)]

## <a name="create-custom-site-columns"></a>建立自訂網站資料行
 這個範例會建立一份清單來管理醫院中的患者。 首先，您必須在中建立 SharePoint 專案， [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 然後在其中新增網站資料行，如下所示。

#### <a name="to-create-the-project"></a>若要建立專案

1. 在 [檔案] [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 功能表上，選擇 [**新增**  >  **專案**]。
::: moniker range="=vs-2017"
2. 在 [ **新增專案** ] 對話方塊的 [ **Visual c #** ] 或 [ **Visual Basic**] 底下，展開 [ **Office/SharePoint** ] 節點，然後選取 [ **SharePoint 方案**]。

3. 在 [ **範本** ] 窗格中，針對您已安裝的特定 sharepoint 版本，選擇 **sharepoint 空白專案** 。 例如，如果您有 SharePoint 2016 安裝，請選取 **sharepoint 2016-空白專案** 範本。  

4. 將專案的名稱 **變更為 [** 實務]，然後選擇 [ **確定]** 按鈕。

5. 在 [**指定偵錯工具的網站和安全性層級**] 對話方塊中，輸入您要加入新自訂欄位專案之本機 SharePoint 網站的 URL，或使用預設位置 (SystemName] `http://<`  `>/)` 。

6. 在 [ **此 SharePoint 方案的信任層級為何？** ] 區段中，使用預設值 [ **部署為沙箱化方案**]。

     如需有關沙箱和伺服器陣列方案的詳細資訊，請參閱 [沙箱化方案考慮](../sharepoint/sandboxed-solution-considerations.md)。

7. 選擇 [完成] 按鈕。 專案現在會列在 **方案總管** 中。
::: moniker-end
::: moniker range=">=vs-2019"
2.  在 [ **建立新專案** ] 對話方塊中，針對您已安裝的特定 sharepoint 版本，選取 **sharepoint 空白專案** 。 例如，如果您有 SharePoint 2016 安裝，請選取 **sharepoint 2016-空白專案** 範本。
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. 將專案的名稱 **變更為 [** 實務]，然後選擇 [ **建立** ] 按鈕。

4. 在 [**指定偵錯工具的網站和安全性層級**] 對話方塊中，輸入您要加入新自訂欄位專案之本機 SharePoint 網站的 URL，或使用預設位置 (SystemName] `http://<`  `>/)` 。

5. 在 [ **此 SharePoint 方案的信任層級為何？** ] 區段中，使用預設值 [ **部署為沙箱化方案**]。

     如需有關沙箱和伺服器陣列方案的詳細資訊，請參閱 [沙箱化方案考慮](../sharepoint/sandboxed-solution-considerations.md)。

6. 選擇 [完成] 按鈕。 專案現在會列在 **方案總管** 中。
::: moniker-end

#### <a name="to-add-site-columns"></a>新增網站資料行

1. 加入新的網站資料行。 若要這樣做，請在 **方案總管** 中，以滑鼠右鍵按一下 [實務 **] 專案，然後選擇 [** **加入**  >  **新專案**]。

2. 在 [ **加入新專案** ] 對話方塊中，選擇 [ **網站資料行**]，將名稱變更為 **PatientName**，然後選擇 [ **加入** ] 按鈕。

3. 在 [網站] 資料行的 *Elements.xml* 檔案中，將 [ **類型** ] 設定保留為 [ **文字**]，將 **群組** 設定變更為 [實習 **網站資料行**]。 完成時，網站欄的 *Elements.xml* 檔案看起來應該如下列範例所示。

    ```xml
    <Field
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"
         Name="PatientName"
         DisplayName="Patient Name"
         Type="Text"
         Required="FALSE"
         Group="Clinic Site Columns">
    </Field>
    ```

    > [!TIP]
    > 如果您在網站資料行的名稱中使用 camel 大小寫，Visual Studio 將會自動為您新增 DisplayName 中的空格。
    > 建議不要在網站資料行名稱中使用空格，因為當您嘗試將方案部署到 SharePoint 時，可能會造成問題。

4. 使用相同的程式，在專案中加入兩個以上的網站資料行： **>patientid** (Type = "Integer" ) and **DoctorName** (type = "Text" ) 。 將其群組值設定為 [實習網站] 資料 **行**。

## <a name="create-a-custom-content-type"></a>建立自訂內容類型
 接下來，根據 [連絡人] 內容類型建立內容類型，其中包含您在上一個程式中建立的網站資料行。 藉由在現有的內容類型上建立內容類型，您就可以節省時間，因為基底內容類型提供數個網站資料行以用於新的內容類型。

#### <a name="to-create-a-custom-content-type"></a>若要建立自訂內容類型

1. 將內容類型加入至專案。 若要這樣做，請在 **方案總管** 中，選擇專案節點

2. 在功能表列上，選擇 [ **Project**  >  **加入新專案**]。

3. 在 [ **Visual c #** ] 或 [ **Visual Basic**] 下，展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

4. 在 [ **範本** ] 窗格中，選擇 [ **內容類型** ] 範本，將名稱變更為 [ **患者資訊**]，然後選擇 [ **新增** ] 按鈕。

     [ **SharePoint 自訂嚮導]** 隨即開啟。

5. 在 [ **此內容類型應該繼承自清單的基底內容** 類型] 中，選擇 [ **連絡人** ] 作為新內容類型的基礎內容類型，然後選擇 [ **完成]** 按鈕。

     這樣做可讓您在 [連絡人] 內容類型中，除了您先前定義的網站資料行之外，還能存取其他可能有用的網站資料行。

6. 在內容類型設計工具出現之後，在 [資料 **行** ] 索引標籤中，新增您先前定義的三個網站資料行： **患者名稱**、 **患者識別碼** 和 **醫生名稱**。 若要加入這些資料行，請在 [ **顯示名稱**] 底下，選擇 [網站資料行] 清單中的第一個清單方塊，然後一次選擇一個清單中的每個網站資料行。

    > [!TIP]
    > 若要更快速地選擇網站資料行，請輸入資料行名稱的前幾個字母來篩選清單。

7. 除了三個自訂網站資料行之外，請從 [網站資料行] 清單中加入 [ **批註** 網站] 資料行。

8. 針對 [**患者名稱**] 和 [**患者識別碼** 網站] 欄選取 [**必要**] 核取方塊，以使其成為必要欄位。

9. 在 [ **內容類型** ] 索引標籤上，確定內容類型名稱是 [ **患者資訊**]，然後將描述變更為 **患者資訊卡片**。

10. 將 [ **組名** ] 變更為 [課程 **內容類型**]，並將其他設定保留為預設值。

11. 在功能表列上 **，選擇 [**  >  **全部儲存**]，然後關閉 [內容類型設計工具]。

## <a name="create-a-list"></a>建立清單
 現在，建立使用新的內容類型和網站資料行的清單。

#### <a name="to-create-a-list"></a>建立清單

1. 將清單新增至專案。 若要這樣做，請在 **方案總管** 中，選擇專案節點。

2. 在功能表列上，選擇 [ **Project**  >  **加入新專案**]。

3. 在 [ **Visual c #** ] 或 [ **Visual Basic**] 下，展開 [ **SharePoint** ] 節點。

4. 在 [ **範本** ] 窗格中，選擇 **清單** 範本，將名稱變更為 **患者**，然後選擇 [ **新增** ] 按鈕。

5. 根據 [**預設 (自訂清單**]，保留 [**依據設定自訂清單**]) ，然後選擇 [**完成]** 按鈕。

6. 在 [清單設計工具] 中，選擇 [ **內容類型** ] 按鈕以顯示 [ **內容類型設定** ] 對話方塊。

7. 選擇新的資料列，在 [內容類型] 清單中選擇 [ **患者資訊** ] 內容類型，然後選擇 [ **確定]** 按鈕。

     這樣做會將 **患者資訊** 內容類型中的所有網站資料行新增至清單中。

8. 刪除清單中的所有網站資料行，但下列除外：

    - 患者識別碼

    - 患者名稱

    - 住家電話

    - 電子郵件

    - 醫生名稱

    - 註解

9. 在 [資料行 **顯示名稱**] 底下，選擇空白資料列、加入自訂清單資料行，然後將它命名為 **醫院**。 將其資料類型保留為 **單行文字**。

     自訂清單資料行僅適用于這份清單。 當您將自訂清單資料行新增至清單時，會建立新的清單內容類型，包括加入清單中的所有資料行，並設定為預設清單。

    > [!TIP]
    > 如果您從網站資料行清單中選擇資料行，則會使用現有的網站資料行。 但是，如果您輸入資料行名稱值，但未挑選清單中的任何資料行，則會建立自訂清單資料行，即使清單中已經有相同名稱的資料行也是如此。

     您可以選擇性地將此資料行的資料類型設定為 [查閱]，而不是將自訂清單資料 **行** 的資料類型設定為 [查閱]，而是從資料表或其他清單抓取其值。 如需查閱資料行的詳細資訊，請參閱 [SharePoint 2010 中的清單關聯](/previous-versions/msp-n-p/ff798514(v=pandp.10)) 性和查閱 [和清單關聯](/previous-versions/office/developer/sharepoint-2010/ff623048(v=office.14))性。

10. 在 [ **患者識別碼** 和 **患者名稱** ] 方塊旁，選取 [ **必要** ] 核取方塊。

11. 在 [ **流覽** ] 索引標籤上，選擇空白資料列來建立視圖。 在 [ **View Name** ] 資料行底下的空白資料列中輸入 **患者詳細資料**。

     在 [ **流覽** ] 索引標籤上，您可以指定要在 SharePoint 清單中顯示的資料行。

12. 選擇 [新的 **患者詳細資料] 資料** 列，然後選擇 [ **設為預設值** ] 按鈕。

     新的 view 現在是清單的預設視圖。

13. 依下列順序將下列資料行新增至 [選取的資料 **行** ] 清單：

    - 患者識別碼

    - 患者名稱

    - 住家電話

    - 電子郵件

    - 醫生名稱

    - 醫院

    - 註解

14. 在 [ **屬性** ] 清單中，選擇 [ **排序與群組** ] 屬性，然後選擇省略號按鈕 ![省略號圖示](../sharepoint/media/ellipsisicon.gif "省略符號圖示") ，即可顯示 [ **排序與群組** ] 對話方塊。

15. 在 [資料 **行名稱** ] 清單中，選擇 [ **患者名稱**]，確認 [ **排序** ] 資料行設定為 [ **遞增**]，然後選擇 [ **確定]** 按鈕。

## <a name="test-the-application"></a>測試應用程式
 既然自訂網站資料行、內容類型和清單都已就緒，請將其部署至 SharePoint，然後執行應用程式來進行測試。

#### <a name="to-test-the-application"></a>若要測試應用程式

1. 在功能表列上 **，選擇 [**  >  **全部儲存**]。

2. 選擇 **F5** 鍵以執行應用程式。

     應用程式會進行編譯，然後將其功能部署到 SharePoint 並啟用。

3. 在快速流覽列上，選擇 [ **患者** ] 連結，以顯示 [ **患者** ] 清單。

     清單中的資料行名稱應符合您在的 [ **視圖** ] 索引標籤中輸入的名稱 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。

4. 選擇 [ **加入新專案** ] 連結，以建立患者資訊卡片。

5. 在欄位中輸入資訊，然後選擇 [ **儲存** ] 按鈕。

     新的記錄會出現在清單中。

## <a name="see-also"></a>另請參閱
- [建立 SharePoint 的網站資料行、內容類型和清單](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
- [如何：建立自訂欄位類型](/previous-versions/office/developer/sharepoint-2010/bb862248(v=office.14))
- [內容類型](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14))
- [資料行](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))
