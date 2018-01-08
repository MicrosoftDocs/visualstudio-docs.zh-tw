---
title: "逐步解說： 在 [開始] 頁面上儲存使用者設定 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 16de0e205d71e2a71b14f523dedbb45354157355
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-saving-user-settings-on-a-start-page"></a>逐步解說： 在 [開始] 頁面上儲存使用者設定
您可以保存使用者設定起始頁。 依循這個逐步解說，您可以建立將設定儲存至登錄中，當使用者按一下按鈕時，並接著會擷取該設定，每次在開始頁面載入的控制項。 由於起始頁專案範本包含可自訂的使用者控制項，而且預設起始頁 XAML 會呼叫該控制項，您不必修改本身的起始頁。  
  
 具現化這個逐步解說中設定存放區是的執行個體<xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore>介面，來讀取和寫入下列登錄位置呼叫時： HKCU\Software\Microsoft\VisualStudio\14.0\\ *CollectionName*  
  
 當執行它時，Visual Studio 的實驗執行個體中時，設定存放區來讀取和寫入 HKCU\Software\Microsoft\VisualStudio\14.0Exp\\*CollectionName。*  
  
 如需如何保存設定的詳細資訊，請參閱[擴充使用者設定和選項](../extensibility/extending-user-settings-and-options.md)。  
  
## <a name="prerequisites"></a>必要條件  
  
> [!NOTE]
>  若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
>   
>  您可以使用，下載起始頁專案範本**擴充管理員**。  
  
## <a name="setting-up-the-project"></a>設定專案  
  
#### <a name="to-configure-the-project-for-this-walkthrough"></a>若要設定此逐步解說專案  
  
1.  建立起始頁專案中所述[建立自訂起始頁](creating-a-custom-start-page.md)。 將專案命名**SaveMySettings**。  
  
2.  在**方案總管 中**，加入下列組件參考加入 StartPageControl 專案：  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
3.  開啟 MyControl.xaml。  
  
4.  從 [XAML] 窗格，在最上層<xref:System.Windows.Controls.UserControl>元素定義，加入下列事件宣告的命名空間宣告之後。  
  
    ```  
    Loaded="OnLoaded"  
    ```  
  
5.  在 設計 窗格中，按一下 控制項的主要區域，然後按 DELETE 鍵。  
  
     這會移除<xref:System.Windows.Controls.Border>項目及所有內容中，且只有最上層的分葉<xref:System.Windows.Controls.Grid>項目。  
  
6.  從**工具箱**，拖曳<xref:System.Windows.Controls.StackPanel>控制項至格線。  
  
7.  現在將<xref:System.Windows.Controls.TextBlock>、 <xref:System.Windows.Controls.TextBox>，並按鈕<xref:System.Windows.Controls.StackPanel>。  
  
8.  新增**X:name**屬性<xref:System.Windows.Controls.TextBox>，和`Click`事件<xref:System.Windows.Controls.Button>，如下列範例所示。  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implementing-the-user-control"></a>實作使用者控制項  
  
#### <a name="to-implement-the-user-control"></a>若要實作使用者控制項  
  
1.  在 [XAML] 窗格中，以滑鼠右鍵按一下`Click`屬性<xref:System.Windows.Controls.Button>項目，然後再按一下**巡覽至事件處理常式**。  
  
     這會開啟 MyControl.xaml.cs，並建立虛設常式的處理常式`Button_Click`事件。  
  
2.  加入下列`using`檔案最上方的陳述式。  
  
     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]  
  
3.  加入私用`SettingsStore`屬性，如下列範例所示。  
  
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
  
     這個屬性會先取得參考<xref:EnvDTE80.DTE2>介面，其中包含從 Automation 物件模型，<xref:System.Windows.FrameworkElement.DataContext%2A>的使用者控制項，然後再使用來取得執行個體的 DTE<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>介面。 然後它會使用該執行個體傳回目前的使用者設定。  
  
4.  填寫`Button_Click`事件，如下所示。  
  
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
  
     這會將文字方塊的內容寫入"MySetting 」 中的欄位"MySettings 」 集合在登錄中。 如果集合不存在，則會建立它。  
  
5.  加入下列處理常式`OnLoaded`使用者控制項的事件。  
  
    ```csharp  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     這會將文字方塊的文字"MySetting 」 的目前值。  
  
6.  建置使用者控制項。  
  
7.  在**方案總管 中**，開啟 source.extension.vsixmanifest。  
  
8.  在資訊清單編輯器中，設定**產品名稱**至**儲存我的設定起始頁**。  
  
     這會設定起始頁的名稱，所以才會出現在**自訂起始頁**清單中**選項** 對話方塊。  
  
9. 建置 StartPage.xaml。  
  
## <a name="testing-the-control"></a>測試控制項  
  
#### <a name="to-test-the-user-control"></a>若要測試的使用者控制項  
  
1.  按 F5。  
  
     Visual Studio 的實驗執行個體隨即開啟。  
  
2.  在實驗執行個體，在**工具**功能表上，按一下 **選項**。  
  
3.  在**環境**] 節點，按一下 [**啟動**，然後在**自訂起始頁**清單中，選取**[安裝擴充功能] 儲存我的設定啟動頁面**.  
  
     按一下 [確定 **Deploying Office Solutions**]。  
  
4.  如果它已開啟，然後在關閉起始頁**檢視**功能表上，按一下 **起始頁**。  
  
5.  在 [開始] 頁面中，按一下 [ **MyControl** ] 索引標籤。  
  
6.  在文字方塊中，輸入**Cat**，然後按一下 **儲存我的設定**。  
  
7.  關閉 [開始] 頁面，然後再次開啟。  
  
     在文字方塊中，應該會顯示"Cat"這個字。  
  
8.  "Cat"這個字取代成"Dog"這個字。 請勿按下按鈕。  
  
9. 關閉 [開始] 頁面，然後再次開啟。  
  
     Word"dog 四"應該顯示在文字方塊中，即使未儲存的設定。 這是因為 Visual Studio 會將工具視窗保留在記憶體中，即使它們已關閉，直到關閉 Visual Studio 本身。  
  
10. 關閉 Visual Studio 的實驗執行個體。  
  
11. 按 F5 以重新開啟實驗執行個體。  
  
12. 在文字方塊中，應該會顯示"Cat"這個字。  
  
## <a name="next-steps"></a>後續步驟  
 您可以修改這個使用者控制項，以儲存並擷取任何數目的自訂設定來取得及設定使用不同的值，從不同的事件處理常式`SettingsStore`屬性。 只要您使用不同`propertyName`參數，每次呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>，值不會覆寫彼此的登錄中。  
  
## <a name="see-also"></a>請參閱  
 <xref:EnvDTE80.DTE2?displayProperty=fullName>     
 [將 Visual Studio 命令加入至起始頁](../extensibility/adding-visual-studio-commands-to-a-start-page.md)