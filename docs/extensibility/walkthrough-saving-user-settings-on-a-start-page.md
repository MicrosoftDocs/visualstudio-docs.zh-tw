---
title: 演練:在「開始」頁上保存用戶設置 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 8c791bb33d6c6a3952c14d5073857b0c3131cecf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697083"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>演練:在「開始」頁上保存用戶設置

您可以保留「開始頁面」的用戶設置。 通過本演練,您可以創建一個控件,在使用者按下按鈕時將設置保存到註冊表中,然後在每次載入「開始頁」時檢索該設置。 由於「開始頁」專案範本包含可自定義的使用者控制件,以及預設的「開始頁 XAML」調用該控制項,因此您不必修改「起始頁」 本身。

本演練中實例化的設置儲存是<xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore>介面的實例,該介面在調用時讀取並寫入以下註冊表位置 **:HKCU_Software_Microsoft_VisualStudio_14.0\\\<集合名稱>**

當它在 Visual Studio 的實驗實例中運行時,設置存儲讀取並寫入**HKCU_軟體_Microsoft_VisualStudio_14.0Exp\\\<集合名稱>。**

關於如何保留設定的詳細資訊,請參考[擴充裝置設定與選項](../extensibility/extending-user-settings-and-options.md)。

## <a name="prerequisites"></a>Prerequisites

> [!NOTE]
> 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 有關詳細資訊,請參閱[可視化工作室 SDK](../extensibility/visual-studio-sdk.md)。
>
> 您可以使用**延伸管理器**下載「開始頁」專案範本。

## <a name="set-up-the-project"></a>設定專案

1. 創建「[創建自訂起始頁」](creating-a-custom-start-page.md)中所述的「開始頁」 專案。 命名專案 **「保存我的設定」。。**

2. 在**解決方案資源管理員中**,向 StartPageControl 專案新增以下程式集參考:

    - EnvDTE

    - EnvDTE80

    - 微軟.VisualStudio.OLE.Interop

    - 微軟.VisualStudio.shell.Interop.11.0

3. 開啟*MyControl.xaml*。

4. 在頂級<xref:System.Windows.Controls.UserControl>元素定義中,在 XAML 窗格中,在命名空間聲明之後添加以下事件聲明。

    ```xml
    Loaded="OnLoaded"
    ```

5. 在設計窗格中,按下控制項的主要區域,然後按 **「刪除**」。

     此步驟將刪除<xref:System.Windows.Controls.Border>元素及其中的所有內容,並僅保留<xref:System.Windows.Controls.Grid>頂級 元素。

6. 從**工具箱**中<xref:System.Windows.Controls.StackPanel>,將控件拖動到網格。

7. 現在將<xref:System.Windows.Controls.TextBlock><xref:System.Windows.Controls.TextBox>. 與 按鈕<xref:System.Windows.Controls.StackPanel>拖曳到 。

8. 為添加的<xref:System.Windows.Controls.TextBox> **x:name**屬性`Click`<xref:System.Windows.Controls.Button>,並為 添加事件,如以下範例所示。

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>實現使用者控制

1. 在 XAML 窗格中,`Click`右鍵 按一<xref:System.Windows.Controls.Button>下元素的屬性,然後單擊 **「導航到事件處理程式**」 。。

     此步驟*將MyControl.xaml.cs*打開,`Button_Click`並為 事件創建一個存根處理程式。

2. 將以下`using`指令添加到文件頂部。

     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]

3. 添加私有`SettingsStore`屬性,如以下示例所示。

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

     此屬性首先從使用者控制項獲取對包含<xref:EnvDTE80.DTE2>自動化物件模型<xref:System.Windows.FrameworkElement.DataContext%2A>的介面的引用,然後使用 DTE 獲取<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>介面的實例。 然後,它使用該實例返回當前用戶設置。

4. 請填寫如下`Button_Click`事件。

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

     這將文本框的內容寫入註冊表中的"MySettings"集合中的"MySettings"欄位。 如果集合不存在,則創建該集合。

5. 為使用者控制項`OnLoaded`的事件添加以下處理程式。

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     此代碼將文字框的文本設置為"MySet"的當前值。

6. 生成使用者控制件。

7. 在**解決方案資源管理員**中,*開源. 延伸. vsixmanifest*。

8. 在清單編輯器中,將**產品名稱**設置為 **「保存我的設置開始頁**」。

     此功能設定「開始頁」的名稱,因為它將顯示在 **「選項**」對話框中的 **「自訂起始頁**」清單中。

9. 產生*StartPage.xaml*。

## <a name="test-the-control"></a>測試控制項

1. 按 **F5**。

     視覺工作室的實驗實例打開。

2. 在實驗實例中,在 **「工具」** 選單上,按下 **「選項**」。

3. 在 **"環境'** 節點中,按下 **"啟動**",然後在 **"自訂開始頁"** 清單中選擇 **[已安裝擴展] 保存我的設置"開始頁**"。

     按一下 [確定]  。

4. 如果"開始頁"打開,請關閉它,然後在 **"查看"** 功能表上按一下 **「開始頁**」。。

5. 在"開始"頁上,按兩下 **"我的控制"** 選項卡。

6. 在文字框中,鍵入 **「Cat」,** 然後按下 **「 保存我的設定**」 。

7. 關閉"開始頁",然後再次打開它。

     文字框中應顯示"Cat"一詞。

8. 將「貓」一詞替換為「狗」 一詞。 不要按下這個按鈕。

9. 關閉"開始頁",然後再次打開它。

     "Dog"一詞應顯示在文字框中,即使您沒有保存設置,因為 Visual Studio 會將工具視窗保留在記憶體中,即使它們已關閉,直到 Visual Studio 本身關閉。

10. 關閉 Visual Studio 的實驗執行個體。

11. 按**F5**重新打開實驗實例。

12. 文字框中應顯示"Cat"一詞。

## <a name="next-steps"></a>後續步驟

您可以使用不同事件處理程式的不同值來獲取和設置`SettingsStore`屬性,從而修改此使用者控制項以保存和檢索任意數量的自定義設置。 只要對 的每次調`propertyName`<xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>用 使用不同的參數,這些值就不會在註冊表中相互覆蓋。

## <a name="see-also"></a>另請參閱

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [將視覺化工作室指令加入到「開始」頁](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
