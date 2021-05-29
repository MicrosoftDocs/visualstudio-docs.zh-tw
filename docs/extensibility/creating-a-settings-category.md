---
title: 建立設定分類 |Microsoft Docs
description: 瞭解如何建立 Visual Studio 設定類別，並使用它來儲存和還原設定檔案中的值。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fe46ea835a119978fd3decd26949db3d59944e5e
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687618"
---
# <a name="create-a-settings-category"></a>建立設定分類

在這個逐步解說中，您會建立 Visual Studio 設定類別，並使用它來儲存值，並從配置檔案還原值。 設定類別是一組顯示為「自訂設定點」的相關屬性;也就是 [匯 **入和匯出設定** ] wizard 中的核取方塊。  (可以在 [ **工具** ] 功能表上找到。 ) 設定會儲存或還原為類別，而個別設定不會顯示在嚮導中。 如需詳細資訊，請參閱[環境設定](../ide/environment-settings.md)。

您可以從類別衍生設定類別來建立 <xref:Microsoft.VisualStudio.Shell.DialogPage> 。

若要開始這個逐步解說，您必須先完成 [ [建立選項] 頁面](../extensibility/creating-an-options-page.md)的第一個區段。 [產生的選項] 屬性方格可讓您檢查及變更類別目錄中的屬性。 在設定檔案中儲存屬性類別目錄之後，您會檢查檔案以查看屬性值的儲存方式。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-settings-category"></a>建立設定分類
 在本節中，您會使用自訂設定點來儲存和還原 [設定] 類別的值。

### <a name="to-create-a-settings-category"></a>建立設定分類

1. 完成 [ [建立選項] 頁面](../extensibility/creating-an-options-page.md)。

2. 開啟 *VSPackage .resx* 檔案，並新增下列三個字串資源：

    |Name|值|
    |----------|-----------|
    |106|我的類別|
    |107|我的設定|
    |108|OptionInteger 和 OptionFloat|

     這會建立名為「我的類別」、「我的設定」物件和「OptionInteger 和 OptionFloat」類別目錄描述的資源。

    > [!NOTE]
    > 在這三個中，只有類別目錄名稱不會出現在 [匯 **入和匯出設定** ] wizard 中。

3. 在 *MyToolsOptionsPackage* 中，將名為 `float` 的屬性加入 `OptionFloat` 至 `OptionPageGrid` 類別，如下列範例所示。

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;
        private float optionFloat = 3.14F;

        [Category("My Options")]
        [DisplayName("My Integer option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
        [Category("My Options")]
        [DisplayName("My Float option")]
        [Description("My float option")]
        public float OptionFloat
        {
            get { return optionFloat; }
            set { optionFloat = value; }
        }
    }
    ```

    > [!NOTE]
    > `OptionPageGrid`名稱為 "My category" 的類別現在包含兩個屬性： `OptionInteger` 和 `OptionFloat` 。

4. 將加入 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 至 `MyToolsOptionsPackage` 類別，並將其命名為「我的分類」，為它指定「我的設定」，並將 isToolsOptionPage 設定為 true。 將 categoryResourceID、objectNameResourceID 和 DescriptionResourceID 設定為稍早建立的對應字串資源識別碼。

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. 建置此專案並開始偵錯。 在實驗性實例中，您應該會看到 **我的格線頁** 現在同時具有整數和浮點值。

## <a name="examine-the-settings-file"></a>檢查設定檔案
 在本節中，您會將屬性類別目錄值匯出至設定檔。 您會檢查檔案，然後將值匯入回屬性類別目錄。

1. 按下 **F5**，在 [偵錯工具] 模式中啟動專案。 這會啟動實驗實例。

2. 開啟 [**工具**  >  **選項**] 對話方塊。

3. 在左窗格的樹狀檢視中，展開 [ **我的類別** ]，然後按一下 [ **我的格線頁**]。

4. 將 **OptionFloat** 的值變更為3.1416，並將 **OptionInteger** 變更為12。 按一下 [確定]。

5. 按一下 [工具] 功能表上的 [匯入和匯出設定]。

     隨即出現 [匯 **入和匯出設定** ]。

6. 確認已選取 [ **匯出選取的環境設定** ]，然後按 **[下一步]**。

     [ **選擇要匯出的設定** ] 頁面隨即出現。

7. 按一下 [ **我的設定**]。

     **描述** 會變更為 **OptionInteger 和 OptionFloat**。

8. 確認 [ **我的設定** ] 是唯一選取的類別，然後按 **[下一步]**。

     [ **命名您的設定檔** ] 頁面隨即出現。

9. 將新的設定檔命名為 *MySettings .vssettings* ，並將它儲存在適當的目錄中。 按一下 [完成] 。

   檔案 `.vssettings` 是 Visual Studio 設定檔案。 檔案的架構已開啟。 最常見的情況是，架構會遵循 XML 結構，其中每個類別都是標記，它本身就包含子類別標記。 這些子類別標記可以包含屬性值標記。 雖然大部分的封裝都使用通用結構，但是 Visual Studio 中的任何封裝都可以使用它所選擇的架構，對檔案提供任意的 XML。

   **匯出完成** 頁面會報告您的設定已成功匯出。

10. 在 [檔案] 功能表上，指向 [開啟舊檔]，再按一下 [檔案]。 找出並開啟 *MySettings .vssettings* 。

     您可以在檔案的下列區段中找到您匯出的屬性類別 (您的 Guid 會) 不同。

    ```
    <Category name="My Category_My Settings"
          Category="{4802bc3e-3d9d-4591-8201-23d1a05216a6}"
          Package="{6bb6942e-014c-489e-a612-a935680f703d}"
          RegisteredName="My Category_My Settings">
          PackageName="MyToolsOptionsPackage">
       <PropertyValue name="OptionFloat">3.1416</PropertyValue>
       <PropertyValue name="OptionInteger">12</PropertyValue>
    </Category>
    ```

     請注意，完整的類別目錄名稱是藉由在類別目錄名稱後面加上物件名稱的底線來形成。 OptionFloat 和 OptionInteger 會顯示在類別中，連同其匯出的值。

11. 關閉設定檔，而不加以變更。

12. 在 [ **工具** ] 功能表上，依序按一下 [ **選項**]、[ **我的類別**]、[ **格線頁** ]，然後將 **OptionFloat** 的值變更為1.0，並將 **OptionInteger** 變更為1。 按一下 [確定]。

13. 按一下 [**工具**] 功能表上的 [匯 **入和匯出設定**]，選取 [匯 **入選取的環境設定**]，然後按 **[下一步]**

     [ **儲存目前的設定** ] 頁面隨即出現。

14. 選取 [ **否]，只匯入新的設定** ，然後按 **[下一步]**。

     [ **選擇要匯入的設定集合** ] 頁面隨即出現。

15. 在樹狀檢視的 [**我的設定**] 節點中，選取 [ *MySettings] .vssettings* 檔案。 如果檔案未出現在樹狀檢視中，請按一下 **[流覽]** 並尋找它。 按一下 [下一步] 。

     [ **選擇要匯入的設定** ] 對話方塊隨即出現。

16. 確認已選取 [ **我的設定** ]，然後按一下 **[完成]**。 當 [匯 **入完成** ] 頁面出現時，按一下 [ **關閉**]。

17. 在 [ **工具** ] 功能表上，依序按一下 [ **選項**]、[ **我的類別**]、[ **我的格線頁** ]，然後確認屬性類別目錄值已還原。
