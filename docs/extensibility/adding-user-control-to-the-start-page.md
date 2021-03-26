---
title: 將使用者控制項加入起始頁 |Microsoft Docs
description: 瞭解如何將 Windows Presentation Foundation (WPF) 使用者控制項新增至 Visual Studio 中的起始頁。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 1e5305927ceb634c64e52bb64ce57197f1b6be4c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097600"
---
# <a name="add-user-control-to-the-start-page"></a>將使用者控制項新增至起始頁

本逐步解說將示範如何將 DLL 參考加入至自訂起始頁。 此範例會將使用者控制項加入至方案、建立使用者控制項，然後從起始頁 *.xaml* 檔案參考建立的元件。 新的索引標籤會裝載使用者控制項，作為基本的網頁瀏覽器。

您可以使用相同的程式，加入可從 *.xaml* 檔案呼叫的任何元件。

## <a name="add-a-wpf-user-control-to-the-solution"></a>將 WPF 使用者控制項新增至方案

首先，將 Windows Presentation Foundation (WPF) 使用者控制項加入起始頁方案。

1. 使用我們在 [建立自訂起始頁](../extensibility/creating-a-custom-start-page.md)中建立的起始頁。

2. 在 **方案總管** 中，以滑鼠 **按右鍵方案，按一下 [** 新增]，然後按一下 [ **新增專案**]。

3. 在 [ **新增專案** ] 對話方塊的左窗格中，展開 [ **Visual Basic** ] 或 [ **Visual c #** ] 節點，然後按一下 [ **Windows**]。 在中間窗格中，選取 [ **WPF 使用者控制項程式庫**]。

4. 為控制項命名 `WebUserControl` ，然後按一下 **[確定]**。

## <a name="implement-the-user-control"></a>執行使用者控制項

若要執行 WPF 使用者控制項，請在 XAML 中建立使用者介面 (UI) ，然後以 c # 或其他 .NET 語言撰寫程式碼後端事件。

### <a name="to-write-the-xaml-for-the-user-control"></a>撰寫使用者控制項的 XAML

1. 開啟使用者控制項的 XAML 檔案。 在 `<Grid>` 元素中，將下列資料列定義加入控制項。

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. 在主要專案中 `<Grid>` ，加入下列新專案 `<Grid>` ，其中包含用於輸入網址的文字方塊，以及用來設定新位址的按鈕。

    ```xml
    <Grid Grid.Row="0">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*" />
            <ColumnDefinition Width="Auto" />
        </Grid.ColumnDefinitions>
        <TextBox x:Name="UserSource" Grid.Column="0" />
        <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
    </Grid>
    ```

3. 將下列框架新增至最上層元素， `<Grid>` 緊接在 `<Grid>` 包含按鈕和 textbox 的元素之後。

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. 下列範例顯示使用者控制項已完成的 XAML。

    ```xml
    <UserControl x:Class="WebUserControl.UserControl1"
                 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
                 mc:Ignorable="d"
                 d:DesignHeight="300" d:DesignWidth="300">
        <Grid>
            <Grid.RowDefinitions>
                <RowDefinition Height="Auto"/>
                <RowDefinition Height="*" />
            </Grid.RowDefinitions>
            <Grid Grid.Row="0">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>
                <TextBox x:Name="UserSource" Grid.Column="0" />
                <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
            </Grid>
            <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
        </Grid>
    </UserControl>

    ```

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>撰寫使用者控制項的程式碼後端事件

1. 在 XAML 設計工具中，按兩下您加入至控制項的 [ **設定位址** ] 按鈕。

    *UserControl1* 會在程式碼編輯器中開啟。

2. 填寫 SetButton_Click 的事件處理常式，如下所示。

    ```csharp
    private void SetButton_Click(object sender, RoutedEventArgs e)
    {
        try
        {
            this.WebFrame.Source = new Uri(this.UserSource.Text, UriKind.Absolute);
        }
        catch (Exception error)
        {
            MessageBox.Show(error.Message);
        }
    }
    ```

    此程式碼會將文字方塊中輸入的網址設定為網頁瀏覽器的目標。 如果位址無效，程式碼就會擲回錯誤。

3. 您也必須處理 WebFrame_Navigated 事件：

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. 建置方案。

## <a name="add-the-user-control-to-the-start-page"></a>將使用者控制項新增至起始頁

若要使此控制項可供起始頁專案使用，請在起始頁專案檔中，加入新控制項程式庫的參考。 然後，您可以將控制項加入至起始頁 XAML 標記。

1. 在 **方案總管** 的起始頁專案中，以滑鼠右鍵按一下 [ **參考** ]，然後按一下 [ **加入參考**]。

2. 在 [ **專案** ] 索引標籤上，選取 [ **WebUserControl** ]，然後按一下 **[確定]**。

3. 在 [建置] 功能表上，按一下 [建置方案]。

    建立解決方案可將使用者控制項提供給方案中其他檔案的 IntelliSense。

    若要將控制項加入至起始頁 XAML 標記，請將命名空間參考加入至元件，然後將控制項放在頁面上。

### <a name="to-add-the-control-to-the-markup"></a>將控制項加入至標記

1. 在 **方案總管** 中，開啟 [開始] 頁面 *.xaml* 檔案。

2. 在 [ **XAML** ] 窗格中，將下列命名空間宣告加入至最上層 <xref:System.Windows.Controls.Grid> 元素。

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. 在 [ **XAML** ] 窗格中，滾動至 \<Grid> 區段。

    區段包含 <xref:System.Windows.Controls.TabControl> 元素中的元素 <xref:System.Windows.Controls.Grid> 。

4. 加入包含 \<TabControl> \<TabItem> 您的使用者控制項之參考的元素。

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    現在您可以測試控制項。

## <a name="test-a-manually-created-custom-start-page"></a>測試手動建立的自訂起始頁

1. 將您的 XAML 檔案及任何支援的文字檔或標記檔案複製到 *%USERPROFILE%\My Documents\Visual Studio 2015 \ StartPages \\* 資料夾。

2. 如果您的起始頁參考 Visual Studio 未安裝之元件中的任何控制項或類型，請複製元件，然後將它們貼到 _Visual Studio 安裝資料夾_**\Common7\IDE\PrivateAssemblies \\** 中。

3. 在 Visual Studio 的命令提示字元中，輸入 **devenv/Rootsuffix Exp** 以開啟 Visual Studio 的實驗實例。

4. 在實驗性實例中，移至 [**工具**  >  **選項**  >  **環境**  >  **啟動**] 頁面，然後從 [**自訂起始頁**] 下拉式清單中選取您的 XAML 檔案。

5. 在 [檢視]  功能表上，按一下 [起始頁] 。

    應該會顯示您的自訂起始頁。 如果您想要變更任何檔案，您必須關閉實驗性實例、進行變更、複製並貼上變更的檔案，然後重新開啟實驗實例以查看變更。

## <a name="see-also"></a>另請參閱

- [WPF 容器控制項](/previous-versions/bb675291(v=vs.110))
- [逐步解說：將自訂 XAML 新增至起始頁](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)