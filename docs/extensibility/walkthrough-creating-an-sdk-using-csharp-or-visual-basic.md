---
title: '逐步解說：使用 c # 或 Visual Basic 建立 SDK |Microsoft Docs'
description: '瞭解如何使用 Visual c # 建立簡單的數學程式庫 SDK，然後使用本逐步解說將 SDK 封裝為 Visual Studio 延伸模組。'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 5b44566e4a8df323af6132128a8881b54c6f493f
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217290"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>逐步解說：使用 c # 或 Visual Basic 建立 SDK
在本逐步解說中，您將瞭解如何使用 Visual c # 建立簡單的數學程式庫 SDK，然後將 SDK 封裝為 (VSIX) 的 Visual Studio 延伸模組。 您將完成下列程式：

- [若要建立 SimpleMath Windows 執行階段元件](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [若要建立 SimpleMathVSIX 延伸模組專案](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [建立使用類別庫的範例應用程式](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>必要條件
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 [VISUAL STUDIO SDK](../extensibility/visual-studio-sdk.md)。

## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a> 若要建立 SimpleMath Windows 執行階段元件

1. 在功能表列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]。

2. 在範本清單中，展開 [ **Visual c #** ] 或 [ **Visual Basic**，選擇 [ **Windows Store** ] 節點，然後選擇 [ **Windows 執行階段元件** ] 範本。

3. 在 [ **名稱** ] 方塊中指定 **SimpleMath**，然後選擇 [ **確定]** 按鈕。

4. 在 **方案總管** 中，開啟 [ **SimpleMath** ] 專案節點的快捷方式功能表，然後選擇 [ **屬性**]。

5. 將 **Class1** 重新命名為 .cs **，並加以** 更新，以符合下列程式碼：

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs" id="Snippet3":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb" id="Snippet3":::

6. 在 **方案總管** 中，開啟 [ **方案 ' SimpleMath '** ] 節點的快捷方式功能表，然後選擇 [ **設定管理員**]。

    [ **設定管理員** ] 對話方塊隨即開啟。

7. 在 [使用中的 **方案** 設定] 清單中，選擇 [ **發行**]。

8. **在 [設定**] 欄中，確認 [ **SimpleMath** ] 資料列已設定為 [**發行**]，然後選擇 [**關閉**] 按鈕以接受變更。

   > [!IMPORTANT]
   > SimpleMath 元件的 SDK 只包含一項設定。 此設定必須是發行組建，或使用該元件的應用程式不會傳遞的認證 [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] 。

9. 在 **方案總管** 中，開啟 [ **SimpleMath** ] 專案節點的快捷方式功能表，然後選擇 [ **組建**]。

## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a> 若要建立 SimpleMathVSIX 延伸模組專案

1. 在 [**方案 ' SimpleMath '** ] 節點的快捷方式功能表上，選擇 [**加入**  >  **新專案**]。

2. 在範本清單中，展開 [ **Visual c #** ] 或 [ **Visual Basic**，選擇 [擴充性 **] 節點，** 然後選擇 [ **VSIX 專案** ] 範本。

3. 在 [ **名稱** ] 方塊中指定 **SimpleMathVSIX**，然後選擇 [ **確定]** 按鈕。

4. 在 **方案總管** 中，選擇 **extension.vsixmanifest** 專案。

5. 在功能表列上，選擇 [**視圖** 程式  >  **代碼**]。

6. 以下列 XML 取代現有的 XML：

   ```xml
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Metadata>
       <Identity Id="SimpleMath" Version="1.0" Language="en-US" Publisher="[YourName]" />
       <DisplayName>SimpleMath Library</DisplayName>
       <Description xml:space="preserve">Basic arithmetic operations in a WinRT-compatible library. Implemented in C#.</Description>
     </Metadata>
     <Installation Scope="Global" AllUsers="true">
       <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />
     </Installation>
     <Prerequisites>
       <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[14.0,16.0]" />
     </Prerequisites>
     <Dependencies>
       <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />
     </Dependencies>
     <Assets>
       <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
     </Assets>
   </PackageManifest>
   ```

7. 在 **方案總管** 中，選擇 [ **SimpleMathVSIX** ] 專案。

8. 在功能表列上，選擇 [ **Project**  >  **加入新專案**]。

9. 在 **一般專案** 清單中，展開 [ **資料**]，然後選擇 [ **XML** 檔案]。

10. 在 [ **名稱** ] 方塊中指定 `SDKManifest.xml` ，然後選擇 [ **加入** ] 按鈕。

11. 在 **方案總管** 中，開啟的快捷方式功能表 `SDKManifest.xml` ，選擇 [ **屬性**]，然後將 [ **Include in VSIX** ] 屬性的值變更為 **True**。

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

13. 在 **方案總管** 中，開啟 **SimpleMathVSIX** 專案的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增資料夾**]。

14. 將資料夾重新命名為 `references` 。

15. 開啟 [ **參考** ] 資料夾的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **新增資料夾**]。

16. 將子資料夾重新命名為 `commonconfiguration` ，在其中建立子資料夾，然後為子資料夾命名 `neutral` 。

17. 重複上述四個步驟，這次將第一個資料夾重新命名為 `redist` 。

     專案現在包含下列資料夾結構：

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. 在 **方案總管** 中，開啟 **SimpleMath** 專案的快捷方式功能表，然後選擇 **檔案總管中的 [開啟資料夾**]。

19. 在 **檔案總管** 中，流覽至 [ *bin\Release* ] 資料夾，開啟 **SimpleMath** 的快捷方式功能表，然後選擇 [ **複製**]。

20. 在 **方案總管** 中，將檔案貼入 **SimpleMathVSIX** 專案的 *references\commonconfiguration\neutral* 資料夾中。

21. 重複上述步驟，將 **SimpleMath pri** 檔案貼入 **SimpleMathVSIX** 專案的 *redist\commonconfiguration\neutral* 資料夾中。

22. 在 **方案總管** 中，選擇 [ **SimpleMath**]。

23. 在功能表列上，選擇 [**視圖**  >  **屬性**] (鍵盤：選擇 **F4** 鍵) 。

24. 在 [ **屬性** ] 視窗中，將 [ **組建動作** ] 屬性變更為 [ **內容**]，然後將 [ **包含于 VSIX** ] 屬性變更為 [ **True**]。

25. 在 **方案總管** 中，針對 **SimpleMath** 重複此程式。

26. 在 **方案總管** 中，選擇 [ **SimpleMathVSIX** ] 專案。

27. 在功能表列上，選擇 [**組建**  >  **組建 SimpleMathVSIX**]。

28. 在 **方案總管** 中，開啟 **SimpleMathVSIX** 專案的快捷方式功能表，然後選擇 **檔案總管中的 [開啟資料夾**]。

29. 在 **檔案總管** 中，流覽至 *\bin\Release* 資料夾，然後執行 *SimpleMathVSIX* 來安裝它。

30. 選擇 [ **安裝** ] 按鈕，等候安裝完成，然後重新開機 Visual Studio。

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> 建立使用類別庫的範例應用程式

1. 在功能表列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]。

2. 在範本清單中，展開 [ **Visual c #** ] 或 [ **Visual Basic**]，然後選擇 [ **Windows 存放區** ] 節點。

3. 選擇 [ **空白應用程式** ] 範本，將專案命名為 **ArithmeticUI**，然後選擇 [ **確定]** 按鈕。

4. 在 **方案總管** 中，開啟 **ArithmeticUI** 專案的快捷方式功能表，然後選擇 [**加入**  >  **參考**]。

5. 在 [參考型別] 清單中，展開 [ **視窗**]，然後選擇 [ **擴充** 功能]。

6. 在詳細資料窗格中，選擇 [ **WinRT 數學程式庫** ] 延伸模組。

    SDK 的其他相關資訊隨即出現。 您可以選擇要開啟的 [ **更多資訊** ] 連結 https://msdn.microsoft.com/ ，如同您稍早在本逐步解說的 SDKManifest.xml 檔案中所指定。

7. 在 [ **參考管理員** ] 對話方塊中，選取 [ **WinRT 數學程式庫** ] 核取方塊，然後選擇 [ **確定]** 按鈕。

8. 在功能表列上，選擇 [**視圖**  >  **物件瀏覽器**]。

9. 在 [ **流覽]** 清單中，選擇 [ **簡單數學**]。

     您現在可以探索 SDK 的內容。

10. 在 **方案總管** 中，開啟 **MainPage**，並將其內容取代為下列 xaml：

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

11. 更新 **MainPage** 以符合下列程式碼：

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Windows.Foundation;
using Windows.Foundation.Collections;
using Windows.UI.Xaml;
using Windows.UI.Xaml.Controls;
using Windows.UI.Xaml.Controls.Primitives;
using Windows.UI.Xaml.Data;
using Windows.UI.Xaml.Input;
using Windows.UI.Xaml.Media;
using Windows.UI.Xaml.Navigation;

// The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238

namespace ArithmeticUI
{
    /// <summary>
    /// An empty page that can be used on its own or navigated to within a Frame.
    /// </summary>
    public sealed partial class MainPage : Page
    {
        public static string operation = null;

        public MainPage()
        {
            this.InitializeComponent();
        }

        /// <summary>
        /// Invoked when this page is about to be displayed in a Frame.
        /// </summary>
        /// <param name="e">Event data that describes how this page was reached.  The Parameter
        /// property is typically used to configure the page.</param>
        protected override void OnNavigatedTo(NavigationEventArgs e)
        {
        }

        /// <summary>
        /// Sets the operator chosen by the user
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void OnOperatorClick(object sender, RoutedEventArgs e)
        {
            operation = (sender as Button).Content.ToString();
        }

        /// <summary>
        /// Calls the SimpleMath SDK to do simple arithmetic
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void OnResultsClick(object sender, RoutedEventArgs e)
        {
            try
            {
                float firstNumber = float.Parse(this._firstNumber.Text);
                float secondNumber = float.Parse(this._secondNumber.Text);

                SimpleMath.Arithmetic math = new SimpleMath.Arithmetic();

                switch (operation)
                {
                    case "+":
                        this._result.Text = (math.add(firstNumber, secondNumber)).ToString();
                        break;
                    case "-":
                        this._result.Text = (math.subtract(firstNumber, secondNumber)).ToString();
                        break;
                    case "*":
                        this._result.Text = (math.multiply(firstNumber, secondNumber)).ToString();
                        break;
                    case "/":
                        this._result.Text = (math.divide(firstNumber, secondNumber)).ToString();
                        break;
                    default:
                        this._result.Text = "Choose operator";
                        break;
                }
            }
            catch
            {
                this._result.Text = "Enter valid #";
            }
        }
    }
}
```

```vb
' The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238

''' <summary>
''' An empty page that can be used on its own or navigated to within a Frame.
''' </summary>
Public NotInheritable Class MainPage
    Inherits Page

    ''' <summary>
    ''' Invoked when this page is about to be displayed in a Frame.
    ''' </summary>
    ''' <param name="e">Event data that describes how this page was reached.  The Parameter
    ''' property is typically used to configure the page.</param>
    Protected Overrides Sub OnNavigatedTo(e As Navigation.NavigationEventArgs)
    
    End Sub

    Public Shared operation As String = Nothing

    ''' <summary>
    ''' Sets the operator chosen by the user
    ''' </summary>
    ''' <param name="sender"></param>
    ''' <param name="e"></param>
    Private Sub OnOperatorClick(ByVal sender As Object, ByVal e As RoutedEventArgs)
        operation = If(TypeOf sender Is Button, CType(sender, Button), Nothing).Content.ToString()
    End Sub


    ''' <summary>
    ''' Calls the SimpleMath SDK to do simple arithmetic
    ''' </summary>
    ''' <param name="sender"></param>
    ''' <param name="e"></param>
    Private Sub OnResultsClick(ByVal sender As Object, ByVal e As RoutedEventArgs)

        Try

            Dim firstNumber As Single = Single.Parse(Me._firstNumber.Text)
            Dim secondNumber As Single = Single.Parse(Me._secondNumber.Text)

            Dim math As New SimpleMath.Arithmetic()

            Select Case (operation)

                Case "+"
                    Me._result.Text = (math.Add(firstNumber, secondNumber)).ToString()

                Case "-"
                    Me._result.Text = (math.Subtract(firstNumber, secondNumber)).ToString()
                Case "*"
                    Me._result.Text = (math.Multiply(firstNumber, secondNumber)).ToString()
                Case "/"
                    Me._result.Text = (math.Divide(firstNumber, secondNumber)).ToString()
                Case Else
                    Me._result.Text = "Choose operator"

            End Select

        Catch
            Me._result.Text = "Enter valid #"
        End Try
    End Sub
End Class
```

12. 選擇 **F5** 鍵以執行應用程式。

13. 在應用程式中，輸入任何兩個數字，選擇作業，然後選擇 **=** 按鈕。

     正確的結果隨即出現。

    您已成功建立並使用延伸模組 SDK。

## <a name="see-also"></a>另請參閱
- [逐步解說：使用 c + + 建立 SDK](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [逐步解說：使用 JavaScript 建立 SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [建立軟體開發套件](../extensibility/creating-a-software-development-kit.md)
