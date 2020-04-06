---
title: 演練:使用 C# 或可視化基本 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16eb20452601a65c498ff112ea996f2d93559940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697548"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>演練:使用 C# 或視覺化基本功能建立 SDK
在本演練中,您將學習如何使用 Visual C++ 創建簡單的數學庫 SDK,然後將 SDK 打包為可視化工作室擴展 (VSIX)。 您將完成以下過程:

- [建立簡單數學視窗執行時元件](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [建立 SimpleMathVSIX 擴充專案](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [建立使用類別庫的範例應用程式](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Prerequisites
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 有關詳細資訊,請參閱[可視化工作室 SDK](../extensibility/visual-studio-sdk.md)。

## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a>建立簡單數學視窗執行時元件

1. 在選單列上,選擇 **「檔** > **新專案** > **」。。**

2. 在範本清單中,展開 Visual **C++** 或**可視化基本**,選擇**Windows 應用商店**節點,然後選擇 Windows**運行時元件**樣本。

3. 在 **「名稱」** 框中,指定 **「簡單數學**」,然後選擇 **「確定**」按鈕。

4. 在**解決方案資源管理員**中,開啟**SimpleMath**專案節點的快捷方式選單,然後選擇**屬性**。

5. 重新命名**Class1.cs****以Arithmetic.cs**並更新它以符合以下代碼:

    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]

6. 在**解決方案資源管理員中**,開啟**解決方案「簡單數學」** 節點的快捷選單,然後選擇**設定管理員**。

    將開啟 **「設定管理員**」 對話框。

7. 在 **「活動解決方案配置**」清單中,選擇 **「釋放**」。。

8. 在 **「設定」** 列中,驗證**SimpleMath**行是否設定為**釋放**,然後選擇 **「關閉**」按鈕以接受更改。

   > [!IMPORTANT]
   > SimpleMath 元件的 SDK 僅包含一個配置。 此配置必須是發佈版本,或者使用元件的應用不會通過的[!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]認證。

9. 在**解決方案資源管理器**中,打開**SimpleMath**專案節點的快捷方式功能表,然後選擇 **「生成**」。

## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a>建立 SimpleMathVSIX 擴充專案

1. 在**解決方案「簡單數學」** 節點的快捷選單上,選擇 **「** > **添加新專案**」。

2. 在樣本清單中,展開**視覺化 C#** 或**可視化基本**,選擇 **「可擴充性」** 節點,然後選擇**VSIX 專案**樣本。

3. 在 **「名稱」** 框中,指定**SimpleMathVSIX**,然後選擇 **「確定**」按鈕。

4. 在**解決方案資源管理器**中,選擇**源.擴展.vsixmanifest**項。

5. 在功能表列上,選擇 **「查看** > **程式碼**」 。。

6. 將現有 XML 取代為以下 XML:

     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]

7. 在**解決方案資源管理器中**,選擇**簡單數學VSIX**專案。

8. 在功能表列上,選擇 **「專案** > **添加新專案**」。。

9. 在 **「常見項目**」 清單中,展開**資料**,然後選擇**XML 檔**。

10. 在 **「名稱」** 框`SDKManifest.xml`中, 指定 ,然後選擇「**新增**」 按鈕。

11. 在**解決方案資源管理員**中`SDKManifest.xml`, 開啟的捷徑選單,**選擇**屬性,然後將**VSIX 屬性中的「包括」** 的值改變為**True**。

12. 以下列 XML 取代檔案的內容：

    **C#**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

13. 在**解決方案資源管理器**中,打開**SimpleMathVSIX**專案的快捷選單,選擇 **「添加**」,然後選擇 **「新建資料夾**」。

14. 將資料夾重新命名為`references`。

15. 開啟 **「引用」** 資料夾的快捷選單,選擇 **"添加**」,然後選擇 **'新增資料夾**"。

16. 將子資料夾重新命名為`commonconfiguration`,在內建立子資料夾,並命名子`neutral`資料夾 。

17. 重複前面的四個步驟,這次將第一個資料夾重新命名為`redist`。

     該專案目前包含以下資料夾結構:

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. 在**解決方案資源管理器**中,打開**SimpleMath**專案的快捷方式功能表,然後在**檔案資源管理器中選擇「打開資料夾**」 。

19. 在**檔案資源管理器**中,導航到*bin_釋放*資料夾,打開**SimpleMath.winmd**檔的快捷功能表,然後選擇 **「複製**」。

20. 在**解決方案資源管理員**中,將檔粘貼到**簡單MathVSIX**專案中的*引用_公共配置\中性*資料夾中。

21. 重複上一步,將**SimpleMath.pri**檔貼貼到**SimpleMathVSIX**專案中的*redist_common 配置_中性*資料夾中。

22. 在**解決方案資源管理器中**,選擇 **「簡單數學.winmd」。。**

23. 在選單列上,選擇 **「查看** > **屬性**」(鍵盤:選擇**F4**鍵)。

24. 在 **「屬性」** 視窗中,將**產生操作**屬性變更為**內容**,然後將**VSIX 中的「包括」** 屬性改變為**True**。

25. 在**解決方案資源管理員中**,對**SimpleMath.pri**重複此過程。

26. 在**解決方案資源管理器中**,選擇**簡單數學VSIX**專案。

27. 在功能表欄上,選擇 **「構建** > **簡單數學」。。**

28. 在**解決方案資源管理員**中,打開**SimpleMathVSIX**專案的快捷方式功能表,然後在**檔案資源管理器中選擇「打開資料夾**」。

29. 在**檔案資源管理器中**,導航到*\bin_釋放*資料夾,然後運行*SimpleMathVSIX.vsix*來安裝它。

30. 選擇 **「安裝**」按鈕,等待安裝完成,然後重新啟動 Visual Studio。

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>建立使用類別庫的範例應用程式

1. 在選單列上,選擇 **「檔** > **新專案** > **」。。**

2. 在範本清單中,展開**視覺化 C#** 或**可視化基本**,然後選擇**Windows 應用商店**節點。

3. 選擇**空白應用**樣本,命名項目**算術UI,** 然後選擇 **「確定**」 按鈕。

4. 在**解決方案資源管理器**中,打開**算術UI**專案的快捷功能表,然後選擇 **「添加** > **參考**」。。

5. 在參考類型清單中,展開**Windows,** 然後選擇**延伸**。

6. 在詳細資訊窗格中,選擇**WinRT 數學庫**擴展名。

    將顯示有關 SDK 的其他資訊。 在本演練前面,您可以選擇「**詳細資訊**」https://msdn.microsoft.com/連結 以打開,如在本演練前面的 SDKManifest.xml 檔中指定的。

7. 在 **「參考管理器**」對話框中,選擇**WinRT 數學庫**複選框,然後選擇「**確定**」按鈕。

8. 在功能表列上,選擇 **「查看** > **物件瀏覽器**」 。。

9. 在 **「瀏覽」** 清單中,選擇 **「簡單數學**」。。

     現在,您可以流覽 SDK 中的內容。

10. 在**解決方案資源管理員中**,開啟**MainPage.xaml**,並將其內容取代為以下 XAML:

    **C#**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

    **Visual Basic**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

11. 更新**MainPage.xaml.cs**以符合以下代碼:

     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]

12. 選擇**F5**鍵來運行應用。

13. 在應用中,輸入任意兩個數字,選擇操作,然後選擇**=** 按鈕。

     將顯示正確的結果。

    您已成功建立和使用擴展 SDK。

## <a name="see-also"></a>另請參閱
- [演練:使用C++創建 SDK](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [演練:使用 JavaScript 建立 SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [建立軟體開發套件](../extensibility/creating-a-software-development-kit.md)
