---
title: 建立選項頁 |Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be826b73e28a73216ea88ceba8e23eb1e9ea457b
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903816"
---
# <a name="create-an-options-page"></a>建立選項頁面

此逐步解說會建立一個簡單的 [工具]/[選項] 頁面，使用屬性方格來檢查和設定屬性。

 若要將這些屬性儲存至，並從配置檔案還原它們，請遵循下列步驟，然後參閱 [[建立設定] 類別](../extensibility/creating-a-settings-category.md)。

 MPF 提供兩個類別，可協助您建立 [工具選項] 頁面、 <xref:Microsoft.VisualStudio.Shell.Package> 類別和 <xref:Microsoft.VisualStudio.Shell.DialogPage> 類別。 您可以建立 VSPackage，藉由子類別化類別來提供這些頁面的容器 `Package` 。 藉由衍生自類別，您可以建立每個 [工具選項] 頁面 `DialogPage` 。

## <a name="prerequisites"></a>必要條件

 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選擇性功能。 您稍後也可以安裝 VS SDK。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-tools-options-grid-page"></a>建立工具選項格線頁

 在本節中，您會建立簡單的 [工具選項] 屬性方格。 您可以使用此方格來顯示及變更屬性的值。

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>建立 VSIX 專案並加入 VSPackage

1. 每個 Visual Studio 延伸模組都是以 VSIX 部署專案為開頭，其中會包含擴充功能資產。 建立 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 名為的 VSIX 專案 `MyToolsOptionsExtension` 。 藉由搜尋「vsix」，您可以在 [**新增專案**] 對話方塊中尋找 VSIX 專案範本。

2. 新增名為的 Visual Studio 封裝專案範本來新增 VSPackage `MyToolsOptionsPackage` 。 在 [**方案總管**中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]。 在 [**加入新專案] 對話方塊**中，移至 [ **Visual c # 專案**擴充性]  >  **Extensibility** ，然後選取 [ **Visual Studio 封裝**]。 在對話方塊底部的 [**名稱**] 欄位中，將檔案名變更為 `MyToolsOptionsPackage.cs` 。 如需如何建立 VSPackage 的詳細資訊，請參閱[使用 VSPackage 建立擴充](../extensibility/creating-an-extension-with-a-vspackage.md)功能。

### <a name="to-create-the-tools-options-property-grid"></a>若要建立工具選項屬性方格

1. 在程式碼編輯器中開啟*MyToolsOptionsPackage*檔案。

2. 新增下列 using 語句。

   ```csharp
   using System.ComponentModel;
   ```

3. 宣告 `OptionPageGrid` 類別，並從將其衍生 <xref:Microsoft.VisualStudio.Shell.DialogPage> 。

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. 將套用 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 至 `VSPackage` 類別，以將 OptionPageGrid 的 [選項] 分類和 [選項] 頁面名稱指派給類別。 結果看起來應該像這樣：

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. 將 `OptionInteger` 屬性加入至 `OptionPageGrid` 類別。

    - 套用 <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> ，將屬性方格分類指派給屬性。

    - 套用 <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> 來指派名稱給屬性。

    - 套用 <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> 以將描述指派給屬性。

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;

        [Category("My Category")]
        [DisplayName("My Integer Option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
    }
    ```

    > [!NOTE]
    > 的預設執行 <xref:Microsoft.VisualStudio.Shell.DialogPage> 支援具有適當轉換器的屬性，或是可以展開為具有適當轉換器之屬性的結構或陣列。 如需轉換器的清單，請參閱 <xref:System.ComponentModel> 命名空間。

6. 建置此專案並開始偵錯。

7. 在 Visual Studio 的實驗實例中，按一下 [**工具**] 功能表上的 [**選項**]。

     在左窗格中，您應該會看到**我的類別目錄**。 （選項分類會以字母順序列出，因此應該會出現在清單的正下方）。開啟 [**我的類別**]，然後按一下 [我的**格線頁**]。 [選項] 方格會出現在右窗格中。 屬性類別目錄是**My Options**，而屬性名稱是**我的 Integer 選項**。 [屬性描述]、[**我的整數] 選項**會出現在窗格的底部。 將該值從256的初始值變更為其他值。 按一下 **[確定]**，然後重新開啟**我的格線頁**。 您可以看到新的值持續存在。

     您也可以透過 Visual Studio 的搜尋方塊來取得 [選項] 頁面。 在 IDE 頂端附近的 [搜尋] 方塊中，輸入**我**的類別，您會看到**我的類別目錄-> 我的格線頁**列在結果中。

## <a name="create-a-tools-options-custom-page"></a>建立工具選項自訂頁面

 在本節中，您會建立具有自訂 UI 的 [工具選項] 頁面。 您可以使用此頁面來顯示和變更屬性的值。

1. 在程式碼編輯器中開啟*MyToolsOptionsPackage*檔案。

2. 新增下列 using 語句。

    ```csharp
    using System.Windows.Forms;
    ```

3. 新增 `OptionPageCustom` 類別，剛好在類別之前 `OptionPageGrid` 。 從衍生新的類別 `DialogPage` 。

    ```csharp
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

4. 新增 GUID 屬性。 新增 OptionString 屬性：

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

5. 將第二個套用 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 至 VSPackage 類別。 這個屬性會指派 [選項] 分類和 [選項] 頁面名稱給類別。

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    [ProvideOptionPage(typeof(OptionPageCustom),
        "My Category", "My Custom Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

6. 將名為 MyUserControl 的新**使用者控制項**加入至專案。

7. 將**TextBox**控制項加入至使用者控制項。

     在 [**屬性**] 視窗的工具列上，按一下 [**事件**] 按鈕，然後按兩下 [**離開**] 事件。 新的事件處理常式會出現在*MyUserControl.cs*程式碼中。

8. 將公用 `OptionsPage` 欄位、方法新增 `Initialize` 至控制項類別，並更新事件處理常式，以將選項值設定為文字方塊的內容：

    ```csharp
    public partial class MyUserControl : UserControl
    {
        public MyUserControl()
        {
            InitializeComponent();
        }

        internal OptionPageCustom optionsPage;

        public void Initialize()
        {
            textBox1.Text = optionsPage.OptionString;
        }

        private void textBox1_Leave(object sender, EventArgs e)
        {
            optionsPage.OptionString = textBox1.Text;
        }
    }
    ```

     `optionsPage`欄位會保存父實例的參考 `OptionPageCustom` 。 `Initialize`方法會顯示 `OptionString` 在**文字方塊**中。 **TextBox** `OptionString` 當焦點離開**文字方塊**時，事件處理常式會將文字方塊的目前值寫入。

9. 在封裝程式碼檔案中，將屬性的覆寫加入至 `OptionPageCustom.Window` `OptionPageCustom` 類別，以建立、初始化和傳回的實例 `MyUserControl` 。 類別現在看起來應該像這樣：

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }

        protected override IWin32Window Window
        {
            get
            {
                MyUserControl page = new MyUserControl();
                page.optionsPage = this;
                page.Initialize();
                return page;
            }
        }
    }
    ```

10. 建置並執行專案。

11. 在實驗實例中，按一下 [**工具**] [  >  **選項**]。

12. 尋找**我的類別**，然後按**我的自訂頁面**。

13. 變更**OptionString**的值。 按一下 **[確定]**，然後重新開啟**我的自訂頁面**。 您可以看到新的值已保存。

## <a name="access-options"></a>存取選項

 在本節中，您會從裝載 [關聯的工具選項] 頁面的 VSPackage 取得選項的值。 相同的技巧可以用來取得任何公用屬性的值。

1. 在封裝程式碼檔案中，將名為**OptionInteger**的公用屬性新增至**MyToolsOptionsPackage**類別。

    ```csharp
    public int OptionInteger
    {
        get
        {
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));
            return page.OptionInteger;
        }
    }

    ```

     這段程式碼會呼叫 <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> 來建立或抓取 `OptionPageGrid` 實例。 `OptionPageGrid`呼叫 <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> 以載入其選項，也就是公用屬性。

2. 現在新增名為**MyToolsOptionsCommand**的自訂命令專案範本，以顯示值。 在 [**新增專案**] 對話方塊中，移至 [ **Visual c #** 擴充性]，  >  **Extensibility**然後選取 [**自訂命令**]。 在視窗底部的 [**名稱**] 欄位中，將命令檔名稱變更為*MyToolsOptionsCommand.cs*。

3. 在*MyToolsOptionsCommand*檔案中，將命令的方法的主體取代為 `ShowMessageBox` 下列內容：

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. 建置此專案並開始偵錯。

5. 在實驗實例中，按一下 [**工具**] 功能表上的 [叫用**MyToolsOptionsCommand**]。

     訊息方塊會顯示目前的值 `OptionInteger` 。

## <a name="see-also"></a>另請參閱

- [選項和選項頁面](../extensibility/internals/options-and-options-pages.md)
