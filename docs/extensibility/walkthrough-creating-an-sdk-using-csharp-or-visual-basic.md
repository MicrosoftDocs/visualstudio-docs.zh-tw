---
title: "逐步解說： 建立使用 C# 或 Visual Basic SDK |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: d40de5bedbb0e77aee2a0dbed34f8dc22d3835c9
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>逐步解說： 建立使用 C# 或 Visual Basic 的 SDK
在本逐步解說，您將學習如何使用 Visual C# 來建立簡單的數學程式庫 SDK，然後再封裝 SDK 為 Visual Studio 擴充功能 (VSIX)。 您將完成下列程序：  
  
-   [若要建立 SimpleMath Windows 執行階段元件](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
-   [若要建立 SimpleMathVSIX 擴充功能專案](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
-   [若要建立範例應用程式使用的類別庫](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
##  <a name="createClassLibrary"></a>若要建立 SimpleMath Windows 執行階段元件  
  
1.  在功能表列上選擇 **檔案**，**新增**，**新專案**。  
  
2.  在範本清單中，展開  **Visual C#**或**Visual Basic**，選擇**Windows 市集** 節點，然後選擇  **的Windows執行階段元件**範本。  
  
3.  在**名稱**方塊中，指定**SimpleMath**，然後選擇 [**確定**] 按鈕。  
  
4.  在**方案總管 中**，開啟捷徑功能表**SimpleMath**專案節點，然後選擇**屬性**。  
  
5.  重新命名**Class1.cs**至**Arithmetic.cs**並更新其符合下列程式碼：  
  
     [!code-csharp[CreatingAnSDKUsingWinRT #3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)][!code-vb[CreatingAnSDKUsingWinRT #3  ](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]  
  
6.  在**方案總管 中**，開啟捷徑功能表**方案 'SimpleMath'**  節點，然後選擇  **Configuration Manager**。  
  
     **Configuration Manager**對話方塊隨即開啟。  
  
7.  在**現用方案組態**清單中，選擇**發行**。  
  
8.  中**組態**資料行中，確認**SimpleMath**資料列設為**發行**，然後選擇 [**關閉**] 按鈕，接受變更。  
  
    > [!IMPORTANT]
    >  SDK SimpleMath 元件包含只能在一個設定。 此設定必須是 「 版本 」 組建，或使用元件的應用程式將不會通過憑證[!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]。  
  
9. 在**方案總管 中**，開啟捷徑功能表**SimpleMath**專案節點，然後選擇**建置**。  
  
##  <a name="createVSIX"></a>若要建立 SimpleMathVSIX 擴充功能專案  
  
1.  在捷徑功能表上**方案 'SimpleMath'**  節點，選擇**新增**，**新專案**。  
  
2.  在範本清單中，展開  **Visual C#**或**Visual Basic**，選擇**擴充性** 節點，然後選擇  **VSIX 專案**範本。  
  
3.  在**名稱**方塊中，指定**SimpleMathVSIX**，然後選擇 [**確定**] 按鈕。  
  
4.  在**方案總管 中**，選擇**source.extension.vsixmanifest**項目。  
  
5.  在功能表列上選擇 [檢視] 、[程式碼] 。  
  
6.  以下列 XML 取代現有的 XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT # 1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7.  在**方案總管 中**，選擇**SimpleMathVSIX**專案。  
  
8.  在功能表列上選擇 **專案**，**加入新項目**。  
  
9. 在清單中**一般項目**，依序展開**資料**，然後選擇  **XML 檔案**。  
  
10. 在**名稱**方塊中，指定`SDKManifest.xml`，然後選擇 [**新增**] 按鈕。  
  
11. 在**方案總管 中**，開啟捷徑功能表`SDKManifest.xml`，選擇**屬性**，然後再將值變更**包含在 VSIX 中的**屬性**True**。  
  
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
  
13. 在**方案總管] 中**，開啟捷徑功能表**SimpleMathVSIX**專案，選擇**新增**，然後選擇 [**新資料夾**。  
  
14. 若要將資料夾重新命名`references`。  
  
15. 開啟快顯功能表**參考**資料夾中，選擇**新增**，然後選擇 **新資料夾**。  
  
16. 重新命名的子資料夾`commonconfiguration`、 建立的子資料夾中，並將命名子資料夾`neutral`。  
  
17. 重複上述四個步驟，重新命名的第一個資料夾目前`redist`。  
  
     專案現在會包含下列資料夾結構：  
  
    ```
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. 在**方案總管 中**，開啟捷徑功能表**SimpleMath**專案，然後再選擇**在檔案總管 中開啟資料夾**。  
  
19. 在**檔案總管**、 瀏覽至 bin\Release 資料夾、 開啟 SimpleMath.winmd 檔案的捷徑功能表，然後選擇**複製**。  
  
20. 在**方案總管 中**，將檔案貼到 references\commonconfiguration\neutral 資料夾**SimpleMathVSIX**專案。  
  
21. 重複上述步驟，將 SimpleMath.pri 檔案貼到 [redist\commonconfiguration\neutral] 資料夾中**SimpleMathVSIX**專案。  
  
22. 在**方案總管 中**，選擇**SimpleMath.winmd**。  
  
23. 在功能表列上選擇 **檢視**，**屬性**(鍵盤： 選擇 F4 鍵)。  
  
24. 在**屬性**視窗中，變更**建置動作**屬性**內容**，然後變更**包含在 VSIX 中的**屬性**True**。  
  
25. 在**方案總管 中**，重複這個程序所**SimpleMath.pri**。  
  
26. 在**方案總管 中**，選擇**SimpleMathVSIX**專案。  
  
27. 在功能表列上選擇 **建置**，**建置 SimpleMathVSIX**。  
  
28. 在**方案總管 中**，開啟捷徑功能表**SimpleMathVSIX**專案，然後再選擇**在檔案總管 中開啟資料夾**。  
  
29. 在**檔案總管**，巡覽至 \bin\Release 資料夾，然後再執行 SimpleMathVSIX.vsix 來安裝它。  
  
30. 選擇**安裝**按鈕，等候安裝完成，然後再重新啟動 Visual Studio。  
  
##  <a name="createSample"></a>若要建立範例應用程式使用的類別庫  
  
1.  在功能表列上選擇 **檔案**，**新增**，**新專案**。  
  
2.  在範本清單中，展開  **Visual C#**或**Visual Basic**，然後選擇  **Windows 市集**節點。  
  
3.  選擇**空白應用程式**範本，將專案**ArithmeticUI**，然後選擇 [**確定**] 按鈕。  
  
4.  在**方案總管 中**，開啟捷徑功能表**ArithmeticUI**專案，然後再選擇**新增**，**參考**。  
  
5.  在參考類型的清單中，展開  **Windows**，然後選擇 **延伸**。  
  
6.  在 詳細資料 窗格中，選擇 **簡單數學 SDK**延伸模組。  
  
     您的 SDK 的其他資訊隨即顯示。 您可以選擇**更多資訊**開啟 http://www.msdn.microsoft.com，為您稍早在本逐步解說 SDKManifest.xml 檔案中所指定的連結。  
  
7.  在**參考管理員**對話方塊中，選取**簡單數學 SDK**核取方塊，，然後選擇 [**確定**] 按鈕。  
  
8.  在功能表列上選擇 **檢視**，**物件瀏覽器**。  
  
9. 在**瀏覽**清單中，選擇**簡單數學**。  
  
     您現在可以瀏覽功能的 SDK。  
  
10. 在**方案總管 中**、 開啟 MainPage.xaml，並以下列 XAML 取代其內容：  

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
  
11. 將 MainPage.xaml.cs 更新以符合下列程式碼：  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp #2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)][!code-vb[CreatingAnSDKUsingWinRTDemoApp #2  ](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]  
  
12. 選擇 F5 鍵執行應用程式。  
  
13. 在應用程式中輸入任何兩個數字，選擇一項運算，然後選擇 **=**   按鈕。  
  
     正確的結果會出現。  
  
 您已成功建立和使用擴充功能 SDK。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說： 建立使用 c + + SDK](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [逐步解說： 建立使用 JavaScript SDK](http://msdn.microsoft.com/en-us/6195ff56-4a27-45fc-bd29-4b0451225f4b)   
 [建立軟體開發套件](../extensibility/creating-a-software-development-kit.md)
