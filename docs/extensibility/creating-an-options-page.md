---
title: "建立選項] 頁面 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[工具選項] 頁面 [Visual Studio SDK], 建立"
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
caps.latest.revision: 62
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 62
---
# 建立選項] 頁面
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本逐步解說會建立使用屬性方格中檢查和設定屬性的簡單工具\/選項頁面。  
  
 將這些屬性，以儲存備份，還原從設定檔案，請遵循下列步驟，看然後 [建立設定分類](../extensibility/creating-a-settings-category.md)。  
  
 MPF 提供兩個類別來協助您建立工具選項頁 <xref:Microsoft.VisualStudio.Shell.Package> 類別和 <xref:Microsoft.VisualStudio.Shell.DialogPage> 類別。 您建立子類別化在套件類別，這些頁面提供容器的 VSPackage。 您可以從 DialogPage 類別衍生建立每個工具選項頁面。  
  
## 必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 建立工具選項的格線頁  
 在本節中，您可以建立簡單的工具選項屬性方格。 您可以使用這個方格來顯示和變更屬性的值。  
  
#### 若要建立 VSIX 專案並加入 VSPackage  
  
1.  每個 Visual Studio 擴充功能開始 VSIX 部署專案，以將包含擴充資產。 建立 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX 專案，名為 `MyToolsOptionsExtension`。 您可以找到 VSIX 專案範本，在 **新的專案** 下的對話方塊 **Visual C\# \/ 擴充性**。  
  
2.  加入名為的 Visual Studio 套件項目範本加入 VSPackage `MyToolsOptionsPackage`。 在 **方案總管\] 中**, ，以滑鼠右鍵按一下專案節點，然後選取 **加入 \/ 新的項目**。 在 **加入新項目\] 對話方塊**, ，請移至 **Visual C\# 項目 \/ 擴充性** ，然後選取 **Visual Studio 套件**。 在 **名稱** 欄位底部的 \[\] 對話方塊中，變更的檔案名稱 `MyToolsOptionsPackage.cs`。 如需如何建立 VSPackage 的詳細資訊，請參閱 [使用 VSPackage 建立擴充功能](../extensibility/creating-an-extension-with-a-vspackage.md)。  
  
#### 若要建立工具選項屬性方格  
  
1.  程式碼編輯器中開啟 MyToolsOptionsPackage 檔案。  
  
2.  新增下列 using 陳述式。  
  
    ```c#  
    using System.ComponentModel;  
    ```  
  
3.  宣告 OptionPageGrid 類別和衍生它從 <xref:Microsoft.VisualStudio.Shell.DialogPage>。  
  
    ```c#  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  套用 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 至 VSPackage 類別，以指派給類別的選項類別目錄和 OptionPageGrid 選項頁面名稱。 結果應該如下所示︰  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5.  新增 `OptionInteger` 屬性 `OptionPageGrid` 類別。  
  
    -   套用 <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> 要指派給屬性的屬性方格的類別。  
  
    -   套用 <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> 要指派給屬性的名稱。  
  
    -   套用 <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> 要指派給屬性的描述。  
  
    ```c#  
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
    >  預設實作 <xref:Microsoft.VisualStudio.Shell.DialogPage> 支援具有適當的轉換或結構或可展開成有適當的轉換器的屬性陣列的屬性。 如需轉換的清單，請參閱 <xref:System.ComponentModel> 命名空間。  
  
6.  建置此專案並開始偵錯。  
  
7.  在 Visual Studio 中，實驗性執行個體上 **工具** 功能表上，按一下 **選項**。  
  
     在左窗格中，您應該看到 **My Category**。 （選項類別目錄會列出依字母順序，它應該會出現有關中途清單向下）。 開啟 **My Category** 然後按一下 \[ **我的格線頁**。選項方格會顯示在右窗格中。 屬性類別目錄是 **My Options**, ，而屬性名稱是 **我整數選項**。 屬性描述 **我整數選項**, ，會出現在窗格的底端。 將值從 256 其初始值變更為其他項目。 按一下 \[ **確定**, ，然後再重新開啟 **我的格線頁**。 您可以看到新的值保存。  
  
     也可透過 Visual Studio 的 \[快速啟動選項頁面。 在 IDE 右上角 \[快速啟動\] 視窗中，輸入 **My Category** ，您會看到 **My Category –\> 我的格線頁** 列在下拉式清單中。  
  
## 建立自訂工具選項頁面  
 本節中，您可以建立工具選項\] 頁面使用自訂 UI。 您可以使用此頁面來顯示和變更屬性的值。  
  
1.  程式碼編輯器中開啟 MyToolsOptionsPackage 檔案。  
  
2.  新增下列 using 陳述式。  
  
    ```vb  
    using System.Windows.Forms;  
    ```  
  
3.  新增 `OptionPageCustom` 類別之前 `OptionPageGrid` 類別。 將新類別衍生自 `DialogPage`。  
  
    ```c#  
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
  
4.  將 GUID 屬性。 新增 OptionString 屬性︰  
  
    ```c#  
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
  
5.  套用第二個 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> VSPackage 類別。 選項類別目錄和選項頁面名稱，這個屬性就會指派類別。  
  
    ```c#  
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
  
6.  加入新 **使用者控制項** MyUserControl 命名專案。  
  
7.  新增 **文字方塊** 至使用者控制項的控制項。  
  
     在 **屬性** 視窗的工具列上，按一下 **事件** \] 按鈕，然後再按兩下 \[ **保留** 事件。 新的事件處理常式會出現在 MyUserControl.cs 程式碼。  
  
8.  加入公用 `OptionsPage` 欄位中， `Initialize` 方法來控制類別和更新的事件處理常式，來設定選項值的文字方塊中的內容︰  
  
    ```c#  
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
  
     `optionsPage` 欄位保存父參考 `OptionPageCustom` 執行個體。`Initialize` 方法顯示 `OptionString` 中 **文字方塊**。 事件處理常式寫入目前的值 **文字方塊** 至 `OptionString` 當專注分葉 **文字方塊**。  
  
9. 在封裝的程式碼檔案中新增的覆寫 `OptionPageCustom.Window` 至 OptionPageCustom 類別，以建立、 初始化及傳回的執行個體的屬性 `MyUserControl`。 此類別現在看起來應該像這樣︰  
  
    ```c#  
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
  
11. 在實驗執行個體中，按一下 \[ **工具 \/ 選項**。  
  
12. 尋找 **我類別** 然後 **我自訂頁面**。  
  
13. 值變更 **OptionString**。 按一下 \[ **確定**, ，然後再重新開啟 **我的自訂頁面**。 您可以看到已保存的新值。  
  
## 存取選項  
 本節中，您可以取得選項的值從 VSPackage 裝載相關聯的工具選項\] 頁面。 相同的技巧可以用來取得任何公用屬性的值。  
  
1.  在封裝的程式碼檔案中，新增名為的公用屬性 **OptionInteger** 至 **MyToolsOptionsPackage** 類別。  
  
    ```  
    public int OptionInteger  
    {  
        get  
        {  
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));  
            return page.OptionInteger;  
        }  
    }  
  
    ```  
  
     此程式碼呼叫 <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> 建立或擷取 `OptionPageGrid` 執行個體。`OptionPageGrid` 呼叫 <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> 載入它的公用屬性的選項。  
  
2.  現在加入名為的自訂命令項目範本 **MyToolsOptionsCommand** 要顯示的值。 在 **加入新項目** \] 對話方塊中，移至 **Visual C\# \/ 擴充性** ，然後選取 **自訂命令**。 在 **名稱** 視窗的底部欄位中，將命令檔名稱變更為 **MyToolsOptionsCommand.cs**。  
  
3.  在 MyToolsOptionsCommand 檔案中取代命令的主體 `ShowMessageBox` 使用下列方法︰  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  建置此專案並開始偵錯。  
  
5.  在實驗性的執行個體，在 **工具** \] 功能表上，按一下 \[ **叫用 MyToolsOptionsCommand**。  
  
     訊息方塊顯示目前的值 `OptionInteger`。  
  
## 請參閱  
 [選項和選項頁面](../extensibility/internals/options-and-options-pages.md)