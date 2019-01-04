---
title: 逐步解說：在 [開始] 頁面上儲存使用者設定 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 563c9206e72788cc26eccdfab7d0e0993d14d1a8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53948767"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>逐步解說：起始頁上儲存使用者設定
您可以保存您的起始頁的使用者設定。 依照本逐步解說中，您可以建立將設定儲存至登錄中，當使用者按一下按鈕，並接著會擷取該設定，每次載入起始頁的控制項。 由於起始頁專案範本包含可自訂的使用者控制項，而且預設啟動頁面 XAML 呼叫該控制項，您不需要修改 [啟動] 頁面本身。  
  
 在此逐步解說中具現化的設定存放區是的執行個體<xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore>介面，它會讀取並寫入下列登錄位置，當呼叫它：**HKCU\Software\Microsoft\VisualStudio\14.0\\\<集合名稱 >**  
  
 當執行它時，Visual Studio 的實驗執行個體中時，設定存放區讀取並寫入**HKCU\Software\Microsoft\VisualStudio\14.0Exp\\\<集合名稱 >。**  
  
 如需如何保存設定的詳細資訊，請參閱[Extending User Settings and 選項](../extensibility/extending-user-settings-and-options.md)。  
  
## <a name="prerequisites"></a>必要條件  
  
> [!NOTE]
>  若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 < [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
>   
>  您可以使用，以下載起始頁專案範本**延伸模組管理員**。  
  
## <a name="setting-up-the-project"></a>設定專案  
  
### <a name="to-configure-the-project-for-this-walkthrough"></a>若要設定專案以進行本逐步解說  
  
1.  建立起始頁專案中所述[建立自訂起始頁](creating-a-custom-start-page.md)。 將專案命名為**SaveMySettings**。  
  
2.  在 [**方案總管] 中**，加入下列組件參考加入 StartPageControl 專案：  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
3.  開啟*MyControl.xaml*。  
  
4.  從 [XAML] 窗格中，在最上層<xref:System.Windows.Controls.UserControl>項目定義中，加入下列事件宣告的命名空間宣告之後。  
  
    ```xml 
    Loaded="OnLoaded"  
    ```  
  
5.  在 [設計] 窗格中，按一下主要區域的控制項，然後按**刪除**。  
  
     這個步驟會移除<xref:System.Windows.Controls.Border>項目，並在其中的所有項目，並將只傳回前保留在層級<xref:System.Windows.Controls.Grid>項目。  
  
6.  從**工具箱**，拖曳<xref:System.Windows.Controls.StackPanel>方格控制項。  
  
7.  現在將拖曳<xref:System.Windows.Controls.TextBlock>，則<xref:System.Windows.Controls.TextBox>，和一個按鈕<xref:System.Windows.Controls.StackPanel>。  
  
8.  新增**X:name**屬性<xref:System.Windows.Controls.TextBox>，以及`Click`事件<xref:System.Windows.Controls.Button>，如下列範例所示。  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implement-the-user-control"></a>實作使用者控制項  
  
### <a name="to-implement-the-user-control"></a>若要實作使用者控制項  
  
1.  在 [XAML] 窗格中，以滑鼠右鍵按一下`Click`的屬性<xref:System.Windows.Controls.Button>項目，然後再按一下**巡覽至事件處理常式**。  
  
     此步驟會開啟*MyControl.xaml.cs*，並建立虛設常式的處理常式`Button_Click`事件。  
  
2.  新增下列`using`至檔案頂端的陳述式。  
  
     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]  
  
3.  新增私用`SettingsStore`屬性，如下列範例所示。  
  
    ```csharp  
    private IVsWritableSettingsStore _settingsStore = null;  
    private IVsWritableSettingsStore SettingsStore  
    {  
        get  
        {  
            if (_settingsStore == null)  
            {  
                // Get a reference to the DTE from the DataContext.   
                var typeDescriptor = DataContext as ICustomTypeDescriptor;  
                var propertyCollection = typeDescriptor.GetProperties();  
                var dte = propertyCollection.Find("DTE", false).GetValue(  
                    DataContext) as DTE2;  
  
                // Get the settings manager from the DTE.   
                var serviceProvider = new ServiceProvider(  
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
                var settingsManager = serviceProvider.GetService(  
                    typeof(SVsSettingsManager)) as IVsSettingsManager;  
  
                // Write the user settings to _settingsStore.  
                settingsManager.GetWritableSettingsStore(  
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,  
                    out _settingsStore);  
            }  
            return _settingsStore;  
        }  
    }  
    ```  
  
     這個屬性會先取得的參考<xref:EnvDTE80.DTE2>介面，其中包含自動化物件模型中，從<xref:System.Windows.FrameworkElement.DataContext%2A>的使用者控制項，然後再使用來取得執行個體的 DTE<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>介面。 然後它會使用該執行個體傳回目前的使用者設定。  
  
4.  填寫`Button_Click`，如下所示的事件。  
  
    ```csharp  
    private void Button_Click(object sender, RoutedEventArgs e)  
    {  
        int exists = 0;  
        SettingsStore.CollectionExists("MySettings", out exists);  
        if (exists != 1)  
        {  
            SettingsStore.CreateCollection("MySettings");  
        }  
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);  
    }  
    ```  
  
     這會將文字方塊的內容寫入登錄中的"MySettings 」 集合中的"MySetting 」 欄位。 如果集合不存在，它會建立它。  
  
5.  新增下列處理常式`OnLoaded`使用者控制項的事件。  
  
    ```csharp  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     此程式碼會設定文字方塊的文字，"MySetting 」 的目前值。  
  
6.  建置使用者控制項。  
  
7.  在 **方案總管**，開啟*source.extension.vsixmanifest*。  
  
8.  在資訊清單編輯器中，設定**Product Name**要**儲存我的設定起始頁**。  
  
     這項功能設定的 入門 頁面的名稱，才會出現在所顯示的原狀**自訂起始頁**列入**選項** 對話方塊。  
  
9. 建置*StartPage.xaml*。  
  
## <a name="test-the-control"></a>測試控制項  
  
### <a name="to-test-the-user-control"></a>若要測試的使用者控制項  
  
1.  請按 **F5**。  
  
     Visual Studio 的實驗執行個體隨即開啟。  
  
2.  在實驗執行個體，在**工具**功能表上，按一下**選項**。  
  
3.  在**環境**節點中，按一下**啟動**，然後在**自訂起始頁**清單中，選取 **[安裝延伸模組] 儲存我的設定開始頁面**.  
  
     按一下 [確定 **Deploying Office Solutions**]。  
  
4.  如果已開啟，然後在關閉 [入門] 頁面**檢視**功能表上，按一下**起始頁**。  
  
5.  在 [啟動] 頁面中，按一下 [ **MyControl** ] 索引標籤。  
  
6.  在 [文字] 方塊中，鍵入**Cat**，然後按一下**儲存我的設定**。  
  
7.  關閉 [入門] 頁面，然後再重新開啟它。  
  
     "Cat"這個字應該會顯示在文字方塊中。  
  
8.  文字"Cat"取代成"Dog"這個字。 請勿按的按鈕。  
  
9. 關閉 [入門] 頁面，然後再重新開啟它。  
  
     即使您沒有儲存設定因為 Visual Studio 會將工具視窗保留在記憶體中，即使它們已關閉，直到關閉 Visual Studio 本身時，"Dog"這個字應該會顯示在文字方塊中。  
  
10. 關閉 Visual Studio 的實驗執行個體。  
  
11. 按下**F5**重新開啟實驗的執行個體。  
  
12. "Cat"這個字應該會顯示在文字方塊中。  
  
## <a name="next-steps"></a>後續步驟  
 您可以修改這個使用者控制項，來儲存和擷取任意數目的自訂設定來取得及設定使用不同的值，從不同的事件處理常式`SettingsStore`屬性。 只要您使用不同`propertyName`每次呼叫的參數<xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>，值不會覆寫另一個登錄中。  
  
## <a name="see-also"></a>另請參閱  
 <xref:EnvDTE80.DTE2?displayProperty=fullName>     
 [將 Visual Studio 命令加入至起始頁](../extensibility/adding-visual-studio-commands-to-a-start-page.md)