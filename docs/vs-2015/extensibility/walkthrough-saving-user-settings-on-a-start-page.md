---
title: 逐步解說：在起始頁儲存使用者設定 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8976d329f6303d60cc00609bc9ed9471456c1b63
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2020
ms.locfileid: "91391706"
---
# <a name="walkthrough-saving-user-settings-on-a-start-page"></a>逐步解說︰將使用者設定儲存於起始頁
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以保存起始頁的使用者設定。 依照本逐步解說的指示，您可以建立一個控制項，在使用者按一下按鈕時將設定儲存至登錄，然後在每次載入起始頁時抓取該設定。 由於起始頁專案範本包含可自訂的使用者控制項，而預設起始頁 XAML 會呼叫該控制項，因此您不需要修改起始頁本身。  
  
 在此逐步解說中具現化的設定存放區是介面的實例，其會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> 在呼叫時讀取和寫入至下列登錄位置： HKCU\Software\Microsoft\VisualStudio\14.0 \\ *CollectionName*  
  
 當它在 Visual Studio 的實驗實例中執行時，這些設定會將讀取和寫入儲存至 HKCU\Software\Microsoft\VisualStudio\14.0Exp \\ *CollectionName。*  
  
 如需有關如何保存設定的詳細資訊，請參閱 [擴充使用者設定和選項](../extensibility/extending-user-settings-and-options.md)。  
  
## <a name="prerequisites"></a>必要條件  
  
> [!NOTE]
> 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 [VISUAL STUDIO SDK](../extensibility/visual-studio-sdk.md)。  
>   
> 您可以使用 [ **擴充管理員**] 下載起始頁專案範本。  
  
## <a name="setting-up-the-project"></a>設定專案  
  
#### <a name="to-configure-the-project-for-this-walkthrough"></a>若要設定此逐步解說的專案  
  
1. 使用起始頁專案範本建立起始頁專案，如 [建立您自己的起始頁](../misc/creating-your-own-start-page.md)所述。 將專案命名為 **SaveMySettings**。  
  
2. 在 **方案總管**中，將下列元件參考新增至 StartPageControl 專案：  
  
    - EnvDTE  
  
    - EnvDTE80  
  
    - VisualStudio： Interop  
  
    - VisualStudio <. a. 11。0  
  
3. 開啟 MyControl.xaml。  
  
4. 從 [XAML] 窗格的最上層專案 <xref:System.Windows.Controls.UserControl> 定義中，將下列事件宣告加入命名空間宣告之後。  
  
    ```  
    Loaded="OnLoaded"  
    ```  
  
5. 在 [設計] 窗格中，按一下控制項的主要區域，然後按 [刪除]。  
  
     這會移除 <xref:System.Windows.Controls.Border> 專案和其中的所有專案，而只保留最上層 <xref:System.Windows.Controls.Grid> 元素。  
  
6. 從 [ **工具箱**] 將 <xref:System.Windows.Controls.StackPanel> 控制項拖曳至方格。  
  
7. 現在將 <xref:System.Windows.Controls.TextBlock> 、 <xref:System.Windows.Controls.TextBox> 和按鈕拖曳至 <xref:System.Windows.Controls.StackPanel> 。  
  
8. 加入的 **x：Name** 屬性 <xref:System.Windows.Controls.TextBox> ，以及的事件， `Click` <xref:System.Windows.Controls.Button> 如下列範例所示。  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implementing-the-user-control"></a>執行使用者控制項  
  
#### <a name="to-implement-the-user-control"></a>若要執行使用者控制項  
  
1. 在 [XAML] 窗格中，以滑鼠右鍵按一下專案的 `Click` 屬性 <xref:System.Windows.Controls.Button> ，然後按一下 [ **流覽至事件處理常式**]。  
  
     這會開啟 MyControl.xaml.cs，並建立事件的存根處理常式 `Button_Click` 。  
  
2. 在檔案頂端新增下列 `using` 陳述式。  
  
     [!code-csharp[StartPageDTE#11](../snippets/csharp/VS_Snippets_VSSDK/startpagedte/cs/startpagecontrol/mycontrol.xaml.cs#11)]  
  
3. 新增私用 `SettingsStore` 屬性，如下列範例所示。  
  
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
  
     這個屬性會先 <xref:EnvDTE80.DTE2> 從使用者控制項的取得介面的參考，其中包含 Automation 物件模型， <xref:System.Windows.FrameworkElement.DataContext%2A> 然後使用 DTE 取得介面的實例 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> 。 然後，它會使用該實例來傳回目前的使用者設定。  
  
4. 填寫事件，如下所示 `Button_Click` 。  
  
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
  
     這會將文字方塊的內容寫入登錄中 "MySettings" 集合內的 "出名為 mysetting" 欄位。 如果集合不存在，就會建立此集合。  
  
5. 為使用者控制項的事件新增下列處理常式 `OnLoaded` 。  
  
    ```csharp  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     這會將文字方塊的文字設定為目前的 "出名為 mysetting" 值。  
  
6. 建立使用者控制項。  
  
7. 在 **方案總管**中，開啟 extension.vsixmanifest。  
  
8. 在資訊清單編輯器中，設定 **產品名稱** 以 **儲存我的設定開始頁面**。  
  
     這會設定開始頁面的名稱，就像在 [**選項**] 對話方塊的 [**自訂起始頁**] 清單中所顯示的一樣。  
  
9. 建立 StartPage. xaml。  
  
## <a name="testing-the-control"></a>測試控制項  
  
#### <a name="to-test-the-user-control"></a>測試使用者控制項  
  
1. 按下 F5。  
  
     Visual Studio 的實驗實例隨即開啟。  
  
2. 在實驗性實例中，按一下 [ **工具** ] 功能表上的 [ **選項**]。  
  
3. 在 [ **環境** ] 節點中，按一下 [ **啟動**]，然後在 [ **自訂起始頁** ] 清單中，選取 **[已安裝的延伸模組] 儲存我的設定開始頁面**。  
  
     按一下 [確定]。  
  
4. 如果開啟，請關閉起始頁，然後在 [ **視圖** ] 功能表上，按一下 [ **起始頁**]。  
  
5. 在 [開始] 頁面上，按一下 [ **mycontrol.xaml** ] 索引標籤。  
  
6. 在文字方塊中，輸入 **貓**，然後按一下 [ **儲存我的設定**]。  
  
7. 關閉 [開始] 頁面，然後重新開啟它。  
  
     文字方塊中應該會顯示 "貓" 這個字。  
  
8. 以 "Dog" 這個字取代 "貓" 這個字。 請勿按一下按鈕。  
  
9. 關閉 [開始] 頁面，然後重新開啟它。  
  
     即使未儲存設定，也應該在文字方塊中顯示 "Dog" 這個字。 發生這種情況是因為 Visual Studio 會將工具視窗保持在記憶體中，即使已關閉，直到 Visual Studio 本身關閉為止。  
  
10. 關閉 Visual Studio 的實驗執行個體。  
  
11. 按下 F5 以重新開啟實驗實例。  
  
12. 文字方塊中應該會顯示 "貓" 這個字。  
  
## <a name="next-steps"></a>後續步驟  
 您可以使用不同的事件處理常式來取得和設定屬性，以修改此使用者控制項，以儲存並取出任意數目的自訂設定 `SettingsStore` 。 只要您 `propertyName` 針對的每個呼叫使用不同的參數 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A> ，這些值就不會在登錄中互相覆寫。  
  
## <a name="see-also"></a>另請參閱  
 <xref:EnvDTE80.DTE2?displayProperty=fullName>   
 [建立您自己的起始頁](../misc/creating-your-own-start-page.md)   
 [將 Visual Studio 命令加入至起始頁](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
