---
title: 將使用者控制項新增到「開始」頁 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: b426cfbbfca2e301797644a1fc73f188054d0cfa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740123"
---
# <a name="add-user-control-to-the-start-page"></a>將使用者控制件添加到"開始頁面"

本演練演示如何向自定義起始頁添加 DLL 引用。 該示例將使用者控制件添加到解決方案,生成使用者控制項,然後從「起始頁 *.xaml*檔」引用生成的程式集。 新選項卡承載使用者控件,該控件充當基本 Web 瀏覽器。

可以使用同一進程添加可以從 *.xaml*檔調用的任何程式集。

## <a name="add-a-wpf-user-control-to-the-solution"></a>向解決方案新增 WPF 使用者控制項

首先,將 Windows 演示文稿基礎 (WPF) 使用者控制件添加到「開始頁」解決方案。

1. 使用我們在[創建自定義起始頁](../extensibility/creating-a-custom-start-page.md)中創建的創建起始頁。

2. 在 **「解決方案資源管理器」** 中,右鍵單擊解決方案,按下「**添加**」,然後按下 **「新專案**」。

3. 在 **「新項目**」 對話框的左邊窗格中,展開 **「視覺基本」** 或 **「視覺 C#」** 節點,然後按**下 Windows**。 在中間窗格中,選擇**WPF 使用者控制庫**。

4. 命名控制項`WebUserControl`,然後按下 **「確定**」。

## <a name="implement-the-user-control"></a>實現使用者控制

要實現 WPF 使用者控制件,請在 XAML 中建構使用者介面 (UI),然後用 C# 或其他 .NET 語言編寫代碼背後的事件。

### <a name="to-write-the-xaml-for-the-user-control"></a>為使用者控制程式編寫 XAML

1. 打開用於使用者控制的 XAML 檔。 在`<Grid>`元素中,向控件添加以下行定義。

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. 在主`<Grid>`元素中,添加以下`<Grid>`新 元素,其中包含用於鍵入 Web 位址的文本框和用於設置新位址的按鈕。

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

3. 將以下框架添加到包含按鈕和文字框`<Grid>``<Grid>`的元素之後的頂層元素。

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. 下面的範例顯示了使用者控制項的已完成的 XAML。

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

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>為使用者控制程式編寫程式碼背後的事件

1. 在 XAML 設計器中,按兩下添加到控制項的 **「設定位址」** 按鈕。

    *UserControl1.cs*檔將在代碼編輯器中打開。

2. 填寫SetButton_Click事件處理程式,如下所示。

    ```csharp
    private void SetButton_Click(object sender, RoutedEventArgs e)
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

    此代碼將文字框中鍵入的 Web 位址集為 Web 瀏覽器的目標。 如果位址無效,代碼將引發錯誤。

3. 您必須處理WebFrame_Navigated事件:

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. 建置方案。

## <a name="add-the-user-control-to-the-start-page"></a>將使用者控制件添加到"開始頁面"

要使此控制件可用於「開始頁」專案,在「開始頁」專案檔中,添加對新控制項庫的引用。 然後,您可以將控制項添加到起始頁 XAML 標籤。

1. 在 **「解決方案資源管理員**」中,在「開始頁」專案中,右鍵單擊 **「引用**」,然後單擊「**添加參考**」 。

2. 在「**項目」** 選項卡上,選擇**WebUser 控制**,然後單擊「**確定**」。

3. 在 [建置]**** 功能表上，按一下 [建置方案]****。

    構建解決方案使 IntelliSense 可用於解決方案中的其他檔案的使用者控制。

    要將控制項添加到「開始頁 XAML 標記」,向程式集添加命名空間引用,然後將該控制件放在頁面上。

### <a name="to-add-the-control-to-the-markup"></a>將控制項加入標記

1. 在**解決方案資源管理員中**,打開起始頁 *.xaml*檔案。

2. 在**XAML**窗格中,將以下命名空間聲明添加<xref:System.Windows.Controls.Grid>到頂級 元素。

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. 在**XAML**窗格中,\<滾動 到網格>部分。

    該節包含<xref:System.Windows.Controls.Grid>元素<xref:System.Windows.Controls.TabControl>中的元素。

4. 添加\<TabControl\<>元素, 其中包含包含對使用者控制件的引用的 TabItem>。

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    現在,您可以測試該控制項。

## <a name="test-a-manually-created-custom-start-page"></a>測試手動建立的自訂開始頁

1. 將 XAML 檔以及任何支援的文字檔或標記檔案複製到 *%USERPROFILE%*我的文件_Visual Studio 2015_StartPages\\*資料夾。

2. 如果起始頁引用 Visual Studio 未安裝的程式集中的任何控制項或類型,請複製程式集,然後將它們貼上_Visual Studio 安裝資料夾_**[公共7_IDE\\私有程式集**中。

3. 在 Visual Studio 命令提示符中,鍵入**devenv /rootsuffix Exp**以打開 Visual Studio 的實驗實例。

4. 在實驗實例中,轉到 **「工具** > **選項** > **環境** > **啟動」** 頁,然後從 **「自訂起始頁」** 下拉清單中選擇 XAML 檔。

5. 在 [檢視] **** 功能表上，按一下 [起始頁] ****。

    應顯示自定義起始頁。 如果要更改任何檔,則必須關閉實驗實例、進行更改、複製和粘貼已更改的檔,然後重新打開實驗實例以查看更改。

## <a name="see-also"></a>另請參閱

- [WPF 容器控制項](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
- [演練:將自訂 XAML 新增到起始頁](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
