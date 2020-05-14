---
title: 建立選項頁面 |微軟文件
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1607af2a6f68bd5593f9a185188b25b364926fe4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739524"
---
# <a name="create-an-options-page"></a>建立選項頁

本演練創建一個簡單的工具/選項頁,該頁使用屬性網格來檢查和設置屬性。

 要將這些屬性儲存到設定檔中並從中還原它們,請按照以下步驟操作,然後請參閱[建立設定類別](../extensibility/creating-a-settings-category.md)。

 MPF 提供兩個類,以説明您創建工具選項頁<xref:Microsoft.VisualStudio.Shell.Package>、<xref:Microsoft.VisualStudio.Shell.DialogPage>類和 類。 透過對類別,`Package`建立 VSPackage 為這些頁面提供容器。 通過派生`DialogPage`類創建每個工具選項頁。

## <a name="prerequisites"></a>Prerequisites

 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-tools-options-grid-page"></a>建立工具選項格格頁

 在本節中,您將創建一個簡單的工具選項屬性網格。 使用此網格可以顯示和更改屬性的值。

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>建立 VSIX 專案並加入 VS 套件

1. 每個 Visual Studio 擴展都從 VSIX 部署專案開始,該專案將包含擴展資產。 建立[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]名為的`MyToolsOptionsExtension`VSIX 專案。 您可以通過搜尋"vsix"在 **"新項目**"對話框中找到 VSIX 專案範本。

2. 通過添加名為`MyToolsOptionsPackage`的可視化工作室包專案範本來添加 VS 包。 在**解決方案資源管理器**中,右鍵單擊專案節點並選擇「**添加新** > **項**」。 在 **'新增新項目'對話框**中,轉到**視覺化 C# 專案** > **延伸性**並選擇**視覺化工作室套件**。 在對話框底部的 **「 名稱」** 欄位中,將檔案`MyToolsOptionsPackage.cs`名稱變更為 。 有關如何建立 VSPackage 的詳細資訊,請參閱[使用 VSPackage 建立延伸](../extensibility/creating-an-extension-with-a-vspackage.md)。

### <a name="to-create-the-tools-options-property-grid"></a>建立「工具選項」屬性格線

1. 在程式碼編輯器中開啟*MyToolsOptions 套件*檔案。

2. 使用 語句添加以下內容。

   ```csharp
   using System.ComponentModel;
   ```

3. 宣告類別`OptionPageGrid`並從 派<xref:Microsoft.VisualStudio.Shell.DialogPage>生它 。

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. 將<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>應用`VSPackage`到 類以為選項頁網格向類分配選項類別和選項頁名稱。 結果應如下所示:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. 向`OptionPageGrid`類`OptionInteger`添加屬性。

    - 應用<xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName>以將 屬性網格類別分配給屬性。

    - 應用<xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName>以向屬性分配名稱。

    - 應用<xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName>以將說明分配給屬性。

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
    > 預設實現<xref:Microsoft.VisualStudio.Shell.DialogPage>支援 具有適當轉換器或結構或陣列的屬性,這些屬性可以擴展到具有適當轉換器的屬性。 有關轉換器清單,請參閱<xref:System.ComponentModel>命名空間。

6. 建置此專案並開始偵錯。

7. 在 Visual Studio 的實驗實例中,在 **「工具」** 選單上單擊 **「選項**」。

     在左側窗格中,應看到 **"我的類別**"。 (選項類別按字母順序列出,因此應顯示清單的中途。開啟**我的類別**,然後按下**我的格格頁面**。 選項格格顯示在右側窗格中。 屬性類別是 **「我的選項**」,屬性名稱為 **「我的整數選項**」。 屬性描述「**我的整數」 選項**會顯示在窗格的底部。 將值從初始值 256 更改為其他值。 按下 **「確定**」,然後重新打開 **「我的網格頁面**」。 您可以看到新值仍然存在。

     您的選項頁面也可通過 Visual Studio 的搜索框獲得。 在 IDE 頂部附近的搜尋框中,鍵入 **「我的類別」,** 您將看到結果中列出的 **「我的類別 ->我的网格页面」。**

## <a name="create-a-tools-options-custom-page"></a>建立工具選項自訂頁面

 在本節中,您將創建一個包含自定義 UI 的工具選項頁面。 使用此頁面顯示和更改屬性的值。

1. 在程式碼編輯器中開啟*MyToolsOptions 套件*檔案。

2. 使用 語句添加以下內容。

    ```csharp
    using System.Windows.Forms;
    ```

3. 在`OptionPageGrid`類`OptionPageCustom`之前添加一個類。 派生新類別。`DialogPage`

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

4. 添加 GUID 屬性。 新增 OptionString 屬性:

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

5. 將第二<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>個應用到 VSPackage 類。 此屬性為類分配一個選項類別和選項頁名稱。

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

6. 向專案添加新**的使用者控制項**,稱為 MyUserControl。

7. 將**TextBox**控制件加入使用者控制元件。

     在工具列上的「**屬性」** 視窗中,按下「**事件」** 按鈕,然後按兩下 **「離開**」事件。 新的事件處理程式將顯示在*MyUserControl.cs*代碼中。

8. 將公共`OptionsPage`欄位(`Initialize`方法 )新增到控制項類別,並更新事件處理程式以將選項值設定為文字框的內容:

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

     該`optionsPage`欄位包含對`OptionPageCustom`父 實例的引用。 該方法`Initialize`顯示`OptionString`在**TextBox**中。 當焦點離開**TextBox**`OptionString`時, 事件處理程式將**TextBox**的目前值寫入 。

9. 在包代碼檔中,向`OptionPageCustom.Window``OptionPageCustom`類添加屬性的重寫以創建、初始化和返回`MyUserControl`的實例。 類現在應如下所示:

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

11. 在實驗實例中,按下 **「工具** > **選項**」 。。

12. 找到**我的類別**,然後**我的自訂頁面**。

13. 更改**OptionString**的值。 按下 **「確定**」,然後重新打開 **「我的自訂頁面**」。 您可以看到新值已保留。

## <a name="access-options"></a>存取選項

 在本節中,從承載關聯的工具選項頁的 VSPackage 中獲取選項的值。 相同的技術可用於獲取任何公共屬性的值。

1. 在包代碼檔中,向**MyToolsOptions包**類添加名為**OptionInteger**的公共屬性。

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

     此代碼調用<xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>以創建或檢`OptionPageGrid`索 實例。 `OptionPageGrid`調用<xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A>以載入其選項,即公共屬性。

2. 現在添加名為**MyToolsOptions 命令**的自訂命令項範本以顯示該值。 在「**新增新項目」** 對話框中,轉到**可視化 C#** > **擴充性**並選擇 **「自訂命令**」。 在視窗底部的 **「 名稱」** 欄位中,將指令檔名變更為*MyToolsOptionsCommand.cs*。

3. 在*MyToolsOptionsCommand*檔中,`ShowMessageBox`將命令方法的正文取代為以下內容:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. 建置此專案並開始偵錯。

5. 在實驗實例中,在 **「工具」** 選單上,按下 **「調用我的工具選項命令**」。。

     消息框顯示`OptionInteger`的 當前值。

## <a name="see-also"></a>另請參閱

- [選項與選項頁](../extensibility/internals/options-and-options-pages.md)
