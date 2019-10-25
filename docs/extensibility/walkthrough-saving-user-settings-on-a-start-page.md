---
title: 逐步解說：在起始頁儲存使用者設定 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: fe3d1040089a4b78368a4da94933a4a1440afafd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647914"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>逐步解說：在起始頁儲存使用者設定

您可以保存起始頁的使用者設定。 遵循此逐步解說，您可以建立控制項，在使用者按一下按鈕時將設定儲存至登錄，然後在每次載入起始頁時，抓取該設定。 因為起始頁專案範本包含可自訂的使用者控制項，而預設起始頁 XAML 呼叫該控制項，所以您不需要修改起始頁本身。

在此逐步解說中具現化的設定存放區是 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> 介面的實例，它會在呼叫時讀取和寫入下列登錄位置：**HKCU\Software\Microsoft\VisualStudio\14.0 \\ \<CollectionName >**

當它在 Visual Studio 的實驗實例中執行時，設定會將讀取和寫入儲存至**HKCU\Software\Microsoft\VisualStudio\14.0Exp \\ \<CollectionName >。**

如需有關如何保存設定的詳細資訊，請參閱[擴充使用者設定和選項](../extensibility/extending-user-settings-and-options.md)。

## <a name="prerequisites"></a>必要條件

> [!NOTE]
> 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[VISUAL STUDIO SDK](../extensibility/visual-studio-sdk.md)。
>
> 您可以使用 [**擴充管理員**] 下載起始頁專案範本。

## <a name="set-up-the-project"></a>設定專案

1. 建立起始頁專案，如[建立自訂起始頁](creating-a-custom-start-page.md)中所述。 將專案命名為**SaveMySettings**。

2. 在**方案總管**中，將下列元件參考新增至 StartPageControl 專案：

    - EnvDTE

    - EnvDTE80

    - VisualStudio. Interop

    - VisualStudio. Shell。

3. 開啟*mycontrol.xaml*。

4. 從 [XAML] 窗格的最上層 <xref:System.Windows.Controls.UserControl> 元素定義中，在命名空間宣告之後加入下列事件宣告。

    ```xml
    Loaded="OnLoaded"
    ```

5. 在 [設計] 窗格中，按一下控制項的主要區域，然後按 [**刪除**]。

     此步驟會移除 <xref:System.Windows.Controls.Border> 元素和其中的所有專案，而且只會保留最上層 <xref:System.Windows.Controls.Grid> 元素。

6. 將 [<xref:System.Windows.Controls.StackPanel>] 控制項從 [**工具箱**] 拖曳至方格。

7. 現在將 [<xref:System.Windows.Controls.TextBlock>]、[<xref:System.Windows.Controls.TextBox>] 和 [按鈕] 拖曳至 <xref:System.Windows.Controls.StackPanel>。

8. 新增 <xref:System.Windows.Controls.TextBox> 的**x：Name**屬性和 <xref:System.Windows.Controls.Button> 的 `Click` 事件，如下列範例所示。

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>執行使用者控制項

1. 在 [XAML] 窗格中，以滑鼠右鍵按一下 <xref:System.Windows.Controls.Button> 元素的 `Click` 屬性，然後按一下 [**流覽至事件處理常式**]。

     此步驟會開啟*MyControl.xaml.cs*，並建立 `Button_Click` 事件的存根處理常式。

2. 將下列 `using` 指示詞新增至檔案頂端。

     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]

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

     這個屬性會先從使用者控制項的 <xref:System.Windows.FrameworkElement.DataContext%2A> 中取得 <xref:EnvDTE80.DTE2> 介面的參考，其中包含 Automation 物件模型，然後使用 DTE 來取得 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> 介面的實例。 然後，它會使用該實例來傳回目前的使用者設定。

4. 填寫 `Button_Click` 事件，如下所示。

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

     這會將文字方塊的內容寫入登錄中 "登入 mysettings" 集合中的 "MySetting" 欄位。 如果集合不存在，則會建立它。

5. 為使用者控制項的 `OnLoaded` 事件新增下列處理常式。

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     這段程式碼會將文字方塊的文字設定為 "MySetting" 的目前值。

6. 建立使用者控制項。

7. 在**方案總管**中，開啟*extension.vsixmanifest*。

8. 在資訊清單編輯器中，將 [**產品名稱**] 設定為 [**儲存我的設定] 起始頁**。

     這項功能會設定起始頁的名稱，因為它會出現在 [**選項**] 對話方塊的 [**自訂起始頁**] 清單中。

9. 建立*StartPage. xaml*。

## <a name="test-the-control"></a>測試控制項

1. 請按 **F5**。

     Visual Studio 的實驗實例隨即開啟。

2. 在實驗實例中，按一下 [**工具**] 功能表上的 [**選項**]。

3. 在 [**環境**] 節點中，按一下 [**啟動**]，然後在 [**自訂起始頁**] 清單中選取 **[已安裝的延伸模組] [儲存我的設定] [起始頁]** 。

     按一下 [確定]。

4. 關閉 [起始頁] （如果已開啟），然後在 [ **View** ] 功能表上，按一下 [**起始頁**]。

5. 在 [開始] 頁面上，按一下 [ **mycontrol.xaml** ] 索引標籤。

6. 在文字方塊中輸入**Cat**，然後按一下 [**儲存我的設定**]。

7. 關閉 [起始頁]，然後重新開啟它。

     [貓] 這個字應該會顯示在文字方塊中。

8. 以 "Dog" 一字取代 "Cat" 一字。 請勿按一下 [] 按鈕。

9. 關閉 [起始頁]，然後重新開啟它。

     「狗」這個字應該會顯示在文字方塊中，即使您並未儲存設定，因為 Visual Studio 會將工具視窗保留在記憶體中，即使它們已關閉，直到 Visual Studio 本身關閉為止。

10. 關閉 Visual Studio 的實驗執行個體。

11. 按**F5**重新開啟實驗實例。

12. [貓] 這個字應該會顯示在文字方塊中。

## <a name="next-steps"></a>後續步驟

您可以使用不同的事件處理常式中的不同值來取得和設定 `SettingsStore` 屬性，以修改此使用者控制項，以儲存並抓取任意數目的自訂設定。 只要您對 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A> 的每個呼叫使用不同的 `propertyName` 參數，這些值就不會覆寫登錄中的另一個。

## <a name="see-also"></a>另請參閱

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [將 Visual Studio 命令新增至起始頁](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
