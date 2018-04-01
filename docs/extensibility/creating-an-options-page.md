---
title: 建立選項頁面 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
caps.latest.revision: 62
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d0888a584e31c26c9f64cdcff70cc2f5dc8a1453
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="creating-an-options-page"></a>建立選項頁面
這個逐步解說會建立使用屬性方格中檢查和設定屬性的簡單工具/選項頁面。  
  
 若要儲存這些屬性，並從設定檔還原，請遵循下列步驟，並接著會看到[建立設定類別](../extensibility/creating-a-settings-category.md)。  
  
 MPF 提供兩個類別，可協助您建立工具選項頁<xref:Microsoft.VisualStudio.Shell.Package>類別和<xref:Microsoft.VisualStudio.Shell.DialogPage>類別。 您建立 VSPackage 也可以提供一個容器，這些網頁的子類別化在封裝類別。 您可以衍生自 DialogPage 類別建立每個工具選項頁面。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-tools-options-grid-page"></a>建立工具選項的格線頁  
 在本節中，您可以建立一個簡單的工具選項屬性方格。 您可以使用這個方格來顯示和變更屬性的值。  
  
#### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>建立 VSIX 專案，加入 VSPackage  
  
1.  每個 Visual Studio 擴充功能開頭 VSIX 部署專案，以將包含延伸模組資產。 建立[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSIX 專案，名為`MyToolsOptionsExtension`。 您可以找到 VSIX 專案範本，在**新專案**對話方塊底下**Visual C# / 擴充性**。  
  
2.  加入名為的 Visual Studio Package 項目範本加入 VSPackage `MyToolsOptionsPackage`。 在**方案總管 中**，以滑鼠右鍵按一下專案節點，然後選取**新增 / 新項目**。 在**加入新項目對話方塊**，請移至**Visual C# 項目 / 擴充性**選取**Visual Studio Package**。 在**名稱**在對話方塊底部欄位中，將檔案名稱變更為`MyToolsOptionsPackage.cs`。 如需如何建立 VSPackage 的詳細資訊，請參閱[建立 VSPackage 擴充功能](../extensibility/creating-an-extension-with-a-vspackage.md)。  
  
#### <a name="to-create-the-tools-options-property-grid"></a>若要建立工具選項屬性方格  
  
1.  程式碼編輯器中開啟 MyToolsOptionsPackage 檔案。  
  
2.  加入下列 using 陳述式。  
  
    ```csharp  
    using System.ComponentModel;  
    ```  
  
3.  宣告 OptionPageGrid 類別和衍生從<xref:Microsoft.VisualStudio.Shell.DialogPage>。  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  套用<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>至 VSPackage 的類別，以指派給類別的選項類別目錄和 OptionPageGrid 選項頁面名稱。 結果看起來應該像這樣：  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5.  新增`OptionInteger`屬性`OptionPageGrid`類別。  
  
    -   套用<xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName>来指派給屬性的屬性方格類別目錄。  
  
    -   套用<xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName>指派給屬性名稱。  
  
    -   套用<xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName>来指派給屬性的描述。  
  
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
    >  預設實作<xref:Microsoft.VisualStudio.Shell.DialogPage>支援的屬性具有適當的轉換，或為結構或陣列可以擴充到具有適當的轉換子的屬性。 如需轉換的清單，請參閱<xref:System.ComponentModel>命名空間。  
  
6.  建置此專案並開始偵錯。  
  
7.  在 Visual Studio 的實驗執行個體上**工具**功能表上，按一下**選項**。  
  
     在左窗格中，您應該看到**我類別**。 （選項類別目錄會列出依字母順序，因此它應該會出現關於中間清單向下）。開啟**我類別**，然後按一下 **我的格線頁**。選項方格會顯示在右窗格中。 屬性類別目錄是**My Options**，而屬性名稱是**我整數選項**。 屬性描述**我整數選項**，出現在窗格的底部。 將值從 256 其初始值變更為其他項目。 按一下**確定**，然後再重新開啟**我的格線頁**。 您可以看到新的值仍然存在。  
  
     也可透過 Visual Studio 的快速啟動您的選項頁面。 在 IDE 右上角 [快速啟動] 視窗中，輸入**我類別**，您會看到**我的類別目錄]-> [我的格線頁**列在下拉式清單中。  
  
## <a name="creating-a-tools-options-custom-page"></a>建立自訂工具選項頁面  
 本節中，您可以建立工具選項頁面使用自訂的 UI。 您可以使用此頁面來顯示和變更屬性的值。  
  
1.  程式碼編輯器中開啟 MyToolsOptionsPackage 檔案。  
  
2.  加入下列 using 陳述式。  
  
    ```vb  
    using System.Windows.Forms;  
    ```  
  
3.  新增`OptionPageCustom`之前類別`OptionPageGrid`類別。 衍生新類別從`DialogPage`。  
  
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
  
4.  加入 GUID 屬性。 加入 OptionString 屬性：  
  
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
  
5.  套用第二個<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>VSPackage 類別。 選項類別目錄和選項頁面名稱，這個屬性就會指派類別。  
  
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
  
6.  加入新**使用者控制項**MyUserControl 命名專案。  
  
7.  新增**文字方塊**至使用者控制項的控制項。  
  
     在**屬性**視窗的工具列上，按一下**事件**按鈕，然後再連按兩下**保留**事件。 新的事件處理常式會出現在 MyUserControl.cs 程式碼。  
  
8.  新增公用`OptionsPage` 欄位中，`Initialize`方法的控制項類別和更新事件處理常式，來設定選項值的文字方塊中的內容：  
  
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
  
     `optionsPage`欄位保存父代參考`OptionPageCustom`執行個體。 `Initialize`方法顯示`OptionString`中**文字方塊**。 事件處理常式的目前值寫入**文字方塊中**至`OptionString`當專注分葉**文字方塊**。  
  
9. 在封裝程式碼檔中加入的覆寫`OptionPageCustom.Window`至 OptionPageCustom 類別以建立、 初始化及傳回的執行個體的屬性`MyUserControl`。 類別現在看起來應該像這樣：  
  
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
  
11. 在實驗執行個體中，按一下**工具 / 選項**。  
  
12. 尋找**我類別**然後**我自訂頁面**。  
  
13. 值變更**OptionString**。 按一下**確定**，然後再重新開啟**我的自訂頁面**。 您可以查看已保存的新值。  
  
## <a name="accessing-options"></a>存取選項  
 在本節中，您會從裝載相關聯的工具選項頁面的 VSPackage 取得選項的值。 相同的技巧可以用來取得任何公用屬性的值。  
  
1.  在封裝程式碼檔案中，加入名為的公用屬性**OptionInteger**至**MyToolsOptionsPackage**類別。  
  
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
  
     此程式碼會呼叫<xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>建立或擷取`OptionPageGrid`執行個體。 `OptionPageGrid`呼叫<xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A>載入它的選項，也就是公用屬性。  
  
2.  現在，加入名為的自訂命令項目範本**MyToolsOptionsCommand**来顯示的值。 在**加入新項目**對話方塊中，移至**Visual C# / 擴充性**選取**自訂命令**。 在**名稱**視窗的底部欄位中，將命令檔名稱變更為**MyToolsOptionsCommand.cs**。  
  
3.  在 MyToolsOptionsCommand 檔案中，將命令的主體`ShowMessageBox`以下列方法：  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  建置此專案並開始偵錯。  
  
5.  在實驗執行個體，在**工具**功能表上，按一下 **叫用 MyToolsOptionsCommand**。  
  
     訊息方塊會顯示目前的值`OptionInteger`。  
  
## <a name="see-also"></a>請參閱  
 [選項和選項頁](../extensibility/internals/options-and-options-pages.md)