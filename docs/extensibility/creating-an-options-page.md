---
title: 建立選項頁 |Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b0b8108470d5f9f14c76e422591a536648b5485e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350981"
---
# <a name="create-an-options-page"></a>建立選項頁面

本逐步解說會建立簡單的工具/選項頁面用以檢查和設定屬性的屬性方格。

 若要這些屬性，以從儲存和還原它們的設定檔，請執行下列步驟，然後看到[建立設定類別](../extensibility/creating-a-settings-category.md)。

 MPF 會提供可協助您建立工具選項 頁面中，兩個類別<xref:Microsoft.VisualStudio.Shell.Package>類別和<xref:Microsoft.VisualStudio.Shell.DialogPage>類別。 您建立 VSPackage 來提供這些頁面中的容器，子類別化`Package`類別。 您建立每個工具選項 頁面，藉由衍生自`DialogPage`類別。

## <a name="prerequisites"></a>必要條件

 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-tools-options-grid-page"></a>建立工具選項的格線頁

 在本節中，您會建立一個簡單的工具選項屬性方格。 您可以使用這個方格來顯示和變更屬性的值。

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>建立 VSIX 專案，並加入 VSPackage

1. 每個 Visual Studio 擴充功能會開始使用 VSIX 部署專案，其中將包含的延伸模組資產。 建立[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSIX 專案，名為`MyToolsOptionsExtension`。 您可以找到在 VSIX 專案範本**新的專案**藉由搜尋 「 vsix 」 的對話方塊。

2. 藉由新增名為 Visual Studio 封裝項目範本加入 VSPackage `MyToolsOptionsPackage`。 在 **方案總管**，以滑鼠右鍵按一下專案節點，然後選取**新增** > **新項目**。 在 [**加入新項目] 對話方塊**，請移至**Visual C# 項目** > **擴充性**，然後選取**Visual Studio Package**。 在 **名稱**底部的對話方塊欄位中，將檔案名稱變更為`MyToolsOptionsPackage.cs`。 如需如何建立 VSPackage 的詳細資訊，請參閱[建立 VSPackage 擴充功能](../extensibility/creating-an-extension-with-a-vspackage.md)。

### <a name="to-create-the-tools-options-property-grid"></a>若要建立工具選項屬性方格

1. 開啟*MyToolsOptionsPackage*程式碼編輯器中的檔案。

2. 新增下列 using 陳述式。

   ```csharp
   using System.ComponentModel;
   ```

3. 宣告`OptionPageGrid`類別，並將它從衍生出來<xref:Microsoft.VisualStudio.Shell.DialogPage>。

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. 適用於<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>至`VSPackage`選項類別目錄和 OptionPageGrid 選項頁面名稱指派給類別的類別。 結果應該如下所示：

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. 新增`OptionInteger`屬性設`OptionPageGrid`類別。

    - 套用<xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName>来指派給屬性的屬性方格類別目錄。

    - 套用<xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName>来指派給屬性的名稱。

    - 套用<xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName>来指派給屬性的描述。

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
    > 預設實作<xref:Microsoft.VisualStudio.Shell.DialogPage>支援的屬性具有適當的轉換或結構或可擴充至具有適當的轉換子的屬性的陣列。 如需轉換器的清單，請參閱<xref:System.ComponentModel>命名空間。

6. 建置此專案並開始偵錯。

7. 在 Visual Studio 中，實驗執行個體上**工具**功能表上，按一下**選項**。

     在左窗格中，您應該會看到**My Category**。 （選項會列出分類依字母順序，因此它應該會出現有關中途往下到清單。）開啟**My Category** ，然後按一下**我的格線頁**。 選項方格會出現在右窗格中。 屬性類別目錄會**My Options**，而屬性名稱為**My 整數選項**。 屬性描述**我整數選項**，出現在窗格的底部。 將值從 256 其初始值變更為其他項目。 按一下  **確定**，然後再重新開啟**我的格線頁**。 您可以看到新的值仍然存在。

     也可透過 Visual Studio 的 [搜尋] 方塊選項頁面。 在 IDE 頂端附近的 [搜尋] 方塊中，輸入**My Category** ，您會看到**My Category]-> [我的格線頁**結果清單中。

## <a name="create-a-tools-options-custom-page"></a>建立自訂工具選項 頁面

 在本節中中,，您可以建立工具選項頁面使用自訂的 UI。 您可以使用此頁面以顯示變更的屬性值。

1. 開啟*MyToolsOptionsPackage*程式碼編輯器中的檔案。

2. 新增下列 using 陳述式。

    ```csharp
    using System.Windows.Forms;
    ```

3. 新增`OptionPageCustom`類別，之前`OptionPageGrid`類別。 新類別衍生自`DialogPage`。

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

4. 將 GUID 屬性。 加入 OptionString 屬性：

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

5. 適用於第二個<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>VSPackage 的類別。 分類選項和選項頁面名稱，這個屬性就會指派類別。

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

6. 加入新**使用者控制項**MyUserControl 命名專案。

7. 新增**TextBox**至使用者控制項的控制項。

     在 **屬性**視窗的工具列上，按一下**事件**按鈕，然後再連按兩下**保留**事件。 新的事件處理常式會出現在*MyUserControl.cs*程式碼。

8. 新增公用`OptionsPage`欄位中，`Initialize`至控制項類別，並更新為事件處理常式，來設定選項值的文字方塊內容的方法：

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

     `optionsPage`欄位保留父代參考`OptionPageCustom`執行個體。 `Initialize`方法會顯示`OptionString`中**TextBox**。 事件處理常式寫入目前的值**TextBox**要`OptionString`當專注分葉**文字方塊**。

9. 在封裝的程式碼檔案中新增的覆寫`OptionPageCustom.Window`屬性，以`OptionPageCustom`類別來建立、 初始化及傳回的執行個體`MyUserControl`。 類別現在看起來應該像這樣：

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

11. 在實驗執行個體中，按一下**工具** > **選項**。

12. 尋找**My Category** ，然後**我的自訂頁面**。

13. 值變更**OptionString**。 按一下  **確定**，然後再重新開啟**我的自訂頁面**。 您可以看到已保存的新值。

## <a name="access-options"></a>存取選項

 在本節中，您會從裝載相關聯的 [工具選項] 頁面的 VSPackage 取得選項的值。 相同的技巧可用來取得任何公用屬性的值。

1. 在封裝的程式碼檔案中，新增名為的公用屬性**OptionInteger**要**MyToolsOptionsPackage**類別。

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

     此程式碼會呼叫<xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>建立或擷取`OptionPageGrid`執行個體。 `OptionPageGrid` 呼叫<xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A>載入它的選項，也就是公用屬性。

2. 現在將新增名為的自訂命令項目範本**MyToolsOptionsCommand**来顯示的值。 在 **加入新項目**對話方塊中，移至**Visual C#**  > **擴充性**，然後選取**自訂命令**。 在 **名稱**視窗的底部欄位中，將命令的檔案名稱變更為*MyToolsOptionsCommand.cs*。

3. 在  *MyToolsOptionsCommand*檔案中，將命令的主體`ShowMessageBox`以下列方法：

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. 建置此專案並開始偵錯。

5. 在實驗執行個體，在**工具**功能表上，按一下**叫用 MyToolsOptionsCommand**。

     訊息方塊會顯示目前的值`OptionInteger`。

## <a name="see-also"></a>另請參閱

- [選項和選項頁](../extensibility/internals/options-and-options-pages.md)
