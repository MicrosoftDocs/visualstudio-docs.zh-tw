---
title: 建立設定類別 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f4b2fa9d82181d0eb899bf9680e8a9debd6c50b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739603"
---
# <a name="create-a-settings-category"></a>建立設定類別

在本演練中,您將創建 Visual Studio 設置類別,並用它來將值保存到設定檔中並將值還原。 設置類別是顯示為「自定義設置點」的相關屬性的一組;即,作為 **「導入和匯出設置」** 嚮導中的複選框。 (您可以在 **"工具"** 選單中找到它。設置將作為類別保存或還原,並且單個設置不會顯示在嚮導中。 如需詳細資訊，請參閱[環境設定](../ide/environment-settings.md)。

通過從類派生設置類別來<xref:Microsoft.VisualStudio.Shell.DialogPage>創建設置類別。

要開始本演練,必須首先完成[「創建選項」頁的第一](../extensibility/creating-an-options-page.md)部分。 產生的 Options 屬性網格允許您檢查和更改類別中的屬性。 在設定檔中保存屬性類別後,將檢查該檔以查看屬性值的存儲方式。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-settings-category"></a>建立設定類別
 在本節中,您可以使用自定義設置點來保存和恢復設置類別的值。

### <a name="to-create-a-settings-category"></a>建立設定類別

1. 完成['建立選項" 頁](../extensibility/creating-an-options-page.md)。

2. 開啟*VSPackage.resx*檔案並新增以下三個字串資源:

    |名稱|值|
    |----------|-----------|
    |106|我的類別|
    |107|我的設定|
    |108|選項整數和期權浮動|

     這將創建名稱為"我的類別"類別、物件"我的設置"和類別描述"Optioninger 和 OptionFloat"的資源。

    > [!NOTE]
    > 在這三個中,只有類別名稱不會出現在 **「匯入和匯出設定」精靈中**。

3. 在*MyToolsOptionsPackage.cs*MyToolsOptionsPackage.cs`float`中`OptionFloat``OptionPageGrid`,向 類添加名為的屬性,如以下示例所示。

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;
        private float optionFloat = 3.14F;

        [Category("My Options")]
        [DisplayName("My Integer option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
        [Category("My Options")]
        [DisplayName("My Float option")]
        [Description("My float option")]
        public float OptionFloat
        {
            get { return optionFloat; }
            set { optionFloat = value; }
        }
    }
    ```

    > [!NOTE]
    > 名為`OptionPageGrid`「我的類別」 的類別現在由兩`OptionInteger`個`OptionFloat`屬性與 。

4. 加入`MyToolsOptionsPackage`類別<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>的類別名稱,將可命名為「我的設定」,並將「ToolsOptionPage」設定為 true。 將類別 ResourceID、物件名稱資源 ID 和描述資源 ID 設定為前面創建的相應字串資源 ID。

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. 建置此專案並開始偵錯。 在實驗實例中,您應該看到 **「我的網格頁**」現在同時具有整數和浮點值。

## <a name="examine-the-settings-file"></a>檢查設定檔
 在本節中,您將屬性類別值匯出到設置檔。 檢查文件,然後將值導入屬性類別。

1. 通過按**F5**在調試模式下啟動專案。 這將啟動實驗實例。

2. 開啟 **「工具** > **」選項「** 對話框」。

3. 在左邊窗格中的樹視圖中,展開 **「我的類別」,** 然後單擊「**我的網格頁**」。

4. 將**OptionFloat**的值更改為 3.1416,將**選項 Integer**更改為 12。 按一下 [確定]  。

5. 按一下 [工具]**** 功能表上的 [匯入和匯出設定]****。

     將顯示「**導入和匯出設定」** 精靈。

6. 確保選擇了 **「匯出選定的環境設置**」,然後單擊「**下一步**」。

     將顯示 **「選擇要匯出的設定**」頁。

7. 按下 **「我的設置**」。。

     **描述**變更為**選項Integer和 OptionFloat**。

8. 請確保 **「我的設置」** 是唯一被選中的類別,然後單擊「**下一步**」。

     將顯示設定**檔名稱「** 頁」。

9. 命名新設定檔*MySettings.vs 設置*並將其保存在相應的目錄中。 按一下 [完成]  。

     匯**出完整「** 頁報告您的設定已成功匯出」。

10. 在 [檔案]**** 功能表上，指向 [開啟舊檔]****，再按一下 [檔案]****。 找到 *"我的設置"* 然後打開它。

     您可以在檔案的以下部分找到匯出的屬性類別(您的 GUID 會有所不同)。

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

     請注意,整個類別名稱是通過向類別名稱添加下劃線後跟物件名稱來形成。 選項 Float 和 OptionInteger 及其匯出的值將顯示在類別中。

11. 關閉設定檔而不更改它。

12. 在 **「工具」** 選單上,**按下「選項**」展開**我的類別**,按下 **「我的網格頁面**」,然後將**OptionFloat**的值更改為 1.0,將**OptionInteger**更改為 1。 按一下 [確定]  。

13. 在 **「工具」** 選單上,按下「**導入與匯出設定**」,選擇 **「導入選定的環境設定**」,然後按**下「 下一步**」 。

     將顯示「**保存當前設定」** 頁。

14. 選擇 **"否",只需導入新設置**,然後單擊"**下一步**"。

     將顯示 **「選擇要導入的設置集合**」。

15. 在樹檢視的「**我的設定」** 節點中選擇 *「MySettings.vs 設定」* 檔。 如果檔未顯示在樹視圖中,請按下「**瀏覽」 並**查找它。 按 [下一步]  。

     將顯示 **「選擇」以導入對話**框。

16. 確保選擇了 **「我的設置」** 然後按下「**完成**」。 當「**導入完成」** 頁出現時,按一下「**關閉**」。

17. 在 **「工具」** 選單上,**按下「選項**」展開**我的類別**」,按下 **「我的網格頁面」** 並驗證屬性類別值是否已還原。
