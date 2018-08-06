---
title: 逐步解說： 建立使用 C# 或 Visual Basic SDK |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 397147bdc5c6ae11c06bfaa47667ad24aa53e2dc
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497871"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>逐步解說： 建立使用 C# 或 Visual Basic SDK
在本逐步解說中，您將了解如何使用 Visual C# 來建立簡單的數學程式庫 SDK，然後再封裝 SDK 作為 Visual Studio 擴充功能 (VSIX)。 您會完成下列程序：  
  
-   [若要建立 SimpleMath Windows 執行階段元件](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
-   [若要建立 SimpleMathVSIX 擴充功能專案](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
-   [若要建立範例應用程式使用的類別庫](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 < [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
##  <a name="createClassLibrary"></a> 若要建立 SimpleMath Windows 執行階段元件  
  
1.  在功能表列上選擇 **檔案** > **新增** > **新專案**。  
  
2.  在範本清單中，依序展開**Visual C#** 或**Visual Basic**，選擇  **Windows 市集** 節點，然後選擇  **Windows 執行階段元件**範本。  
  
3.  在 [**名稱**方塊中，指定**SimpleMath**，然後選擇 **[確定]** ] 按鈕。  
  
4.  在 **方案總管**，開啟捷徑功能表**SimpleMath**專案節點，然後選擇**屬性**。  
  
5.  重新命名**Class1.cs**要**Arithmetic.cs**並更新它以符合下列程式碼：  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]  
  
6.  在**方案總管 中**，開啟捷徑功能表**解決方案 'SimpleMath'** 節點，然後選擇**Configuration Manager**。  
  
     **Configuration Manager**對話方塊隨即開啟。  
  
7.  在 **現用方案組態**清單中，選擇**發行**。  
  
8.  中**組態** 欄中，確認**SimpleMath**資料列設定為**版本**，然後選擇**關閉**按鈕以接受變更。  
  
    > [!IMPORTANT]
    >  SimpleMath 元件 SDK 包含只有一個組態。 此設定必須是發行組建，或使用元件的應用程式，將不會傳遞認證[!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]。  
  
9. 在 **方案總管**，開啟捷徑功能表**SimpleMath**專案節點，然後選擇**建置**。  
  
##  <a name="createVSIX"></a> 若要建立 SimpleMathVSIX 擴充功能專案  
  
1.  上的捷徑功能表**解決方案 'SimpleMath'** 節點，選擇**新增** > **新專案**。  
  
2.  在範本清單中，依序展開**Visual C#** 或**Visual Basic**，選擇 [**擴充性**] 節點，然後選擇**VSIX 專案**範本。  
  
3.  在 [**名稱**方塊中，指定**SimpleMathVSIX**，然後選擇 **[確定]** ] 按鈕。  
  
4.  在 **方案總管**，選擇**source.extension.vsixmanifest**項目。  
  
5.  在功能表列上依序選擇 [檢視] > [程式碼]。  
  
6.  以下列 XML 取代現有的 XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7.  在 **方案總管**，選擇**SimpleMathVSIX**專案。  
  
8.  在功能表列中，選擇 [專案] > [加入新項目]。  
  
9. 在這份**常見的項目**，展開**資料**，，然後選擇  **XML 檔案**。  
  
10. 在 [**名稱**方塊中，指定`SDKManifest.xml`，然後選擇**新增**] 按鈕。  
  
11. 在**方案總管**，開啟捷徑功能表`SDKManifest.xml`，選擇**屬性**，然後再將值變更**Include in VSIX** 屬性 **，則為 true**。  
  
12. 以下列 XML 取代檔案的內容：  

    **C#**
    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="http://www.msdn.microsoft.com/">
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
      MoreInfo="http://www.msdn.microsoft.com/">
    </FileList>
    ```  
  
13. 中**方案總管 中**，開啟捷徑功能表**SimpleMathVSIX**專案，選擇**新增**，然後選擇**新資料夾**。  
  
14. 若要將資料夾重新命名`references`。  
  
15. 開啟捷徑功能表**參考**資料夾中，選擇**新增**，然後選擇**新資料夾**。  
  
16. 重新命名的子資料夾`commonconfiguration`，建立子資料夾，並將命名的子資料夾`neutral`。  
  
17. 重複先前的四個步驟中，重新命名的第一個資料夾，以這次`redist`。  
  
     專案現在會包含下列資料夾結構：  
  
    ```xml
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. 在 **方案總管 中**，開啟捷徑功能表**SimpleMath**專案，，然後選擇**在檔案總管 中開啟資料夾**。  
  
19. 在 **檔案總管**，瀏覽至*bin\Release*資料夾中，開啟捷徑功能表**SimpleMath.winmd**檔案，然後再選擇 **複製**.  
  
20. 在 [**方案總管] 中**，貼上檔案*references\commonconfiguration\neutral*資料夾中的**SimpleMathVSIX**專案。  
  
21. 重複上一個步驟中，貼上**SimpleMath.pri**檔案載入*redist\commonconfiguration\neutral*中的資料夾**SimpleMathVSIX**專案。  
  
22. 在 **方案總管**，選擇**SimpleMath.winmd**。  
  
23. 在功能表列上選擇 **檢視** > **屬性**(鍵盤： 選擇**F4**索引鍵)。  
  
24. 在**屬性**視窗中，變更**建置動作**屬性設**內容**，然後變更**Include in VSIX** 屬性**True**。  
  
25. 在 **方案總管**，重複此程序**SimpleMath.pri**。  
  
26. 在 **方案總管**，選擇**SimpleMathVSIX**專案。  
  
27. 在功能表列上選擇 **建置** > **建置 SimpleMathVSIX**。  
  
28. 在 **方案總管 中**，開啟捷徑功能表**SimpleMathVSIX**專案，，然後選擇**在檔案總管 中開啟資料夾**。  
  
29. 在 **檔案總管**，瀏覽至*\bin\Release*資料夾，然後再執行*SimpleMathVSIX.vsix*進行安裝。  
  
30. 選擇**安裝**按鈕，等候安裝完成，然後再重新啟動 Visual Studio。  
  
##  <a name="createSample"></a> 若要建立範例應用程式使用的類別庫  
  
1.  在功能表列上選擇 **檔案** > **新增** > **新專案**。  
  
2.  在範本清單中，依序展開**Visual C#** 或是**Visual Basic**，然後選擇  **Windows 市集**節點。  
  
3.  選擇**空白應用程式**範本，將專案命名為**ArithmeticUI**，然後選擇**確定** 按鈕。  
  
4.  在 [**方案總管] 中**，開啟捷徑功能表**ArithmeticUI**專案，，然後選擇**新增** > **參考**.  
  
5.  在參考類型的清單中，依序展開**Windows**，然後選擇**延伸模組**。  
  
6.  在 [詳細資料] 窗格中，選擇**簡單的數學 SDK**延伸模組。  
  
     您的 SDK 的其他資訊會出現。 您可以選擇**更多資訊**連結，以開啟http://www.msdn.microsoft.com，如您在稍早在本逐步解說在 SDKManifest.xml 檔案中指定。  
  
7.  在 **參考管理員**對話方塊中，選取**簡單數學 SDK**核取方塊，，然後選擇  **確定**  按鈕。  
  
8.  在功能表列上選擇 **檢視** > **物件瀏覽器**。  
  
9. 在 **瀏覽**清單中，選擇**簡單數學**。  
  
     您現在可以探索 SDK 的功能。  
  
10. 在 **方案總管**，開啟**MainPage.xaml**，並以下列 XAML 取代其內容：  

    **C#**
    ```xml
    <Page
        x:Class="WinRTMathTestCS.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTestCS"
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
        x:Class="WinRTMathTest.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTest"
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
  
11. 更新**MainPage.xaml.cs**以符合下列程式碼：  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]  
  
12. 選擇**F5**鍵以執行應用程式。  
  
13. 在應用程式中，輸入任何兩個數字，選擇一項運算，然後選擇**=**  按鈕。  
  
     正確的結果會出現。  
  
 您已成功建立和使用擴充功能 SDK。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說： 建立使用 c + + SDK](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [逐步解說： 建立使用 JavaScript SDK](http://msdn.microsoft.com/en-us/6195ff56-4a27-45fc-bd29-4b0451225f4b)   
 [建立軟體開發套件](../extensibility/creating-a-software-development-kit.md)