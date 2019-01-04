---
title: 逐步解說：使用 c + + 建立 SDK |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2a0db4f34315f9e0eb4a5627cdc286a43a904a34
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917601"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>逐步解說：建立使用 c + + SDK
本逐步解說示範如何建立原生 c + + 數學程式庫 SDK，封裝 SDK 作為 Visual Studio 擴充功能 (VSIX)，並接著使用它來建立應用程式。 本逐步解說分為下列步驟：  
  
-   [若要建立原生和 Windows 執行階段程式庫](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [若要建立 NativeMathVSIX 擴充功能專案](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [若要建立範例應用程式使用的類別庫](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 < [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
##  <a name="createClassLibrary"></a> 若要建立原生和 Windows 執行階段程式庫  
  
1.  在功能表列上，選擇 [檔案] > [新增] > [專案]。  
  
2.  在範本清單中，依序展開**Visual c + +** > **Windows Universal**，然後選取**DLL （通用 Windows 應用程式）** 範本。 在 [**名稱**方塊中，指定`NativeMath`，然後選擇 **[確定]** ] 按鈕。  
  
3.  更新*NativeMath.h*以符合下列程式碼。  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  更新*NativeMath.cpp*以符合此程式碼：  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  在**方案總管 中**，開啟捷徑功能表**解決方案 'NativeMath'**，然後選擇**新增** > **新專案**.  
  
6.  在範本清單中，依序展開**Visual c + +**，然後選取**Windows 執行階段元件**範本。 在 [**名稱**方塊中，指定`NativeMathWRT`，然後選擇 **[確定]** ] 按鈕。  
  
7.  更新*Class1.h*以符合此程式碼：  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  更新*Class1.cpp*以符合此程式碼：  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. 在功能表列上選擇 [建置] > [建置解決方案]。  
  
##  <a name="createVSIX"></a> 若要建立 NativeMathVSIX 擴充功能專案  
  
1.  在**方案總管 中**，開啟捷徑功能表**解決方案 'NativeMath'**，然後選擇**新增** > **新專案**.  
  
2.  在範本清單中，依序展開**Visual C#** > **擴充性**，然後選取**VSIX 專案**。 在 [**名稱**方塊中，指定**NativeMathVSIX**，然後選擇 **[確定]** ] 按鈕。
  
3.  在 **方案總管 中**，開啟捷徑功能表**source.extension.vsixmanifest**，然後選擇 **檢視程式碼**。  
  
4.  使用下列 XML 取代現有的 XML。  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5.  在**方案總管**，開啟捷徑功能表**NativeMathVSIX**專案，，然後選擇**新增** > **新項目**.  
  
6.  在這份**Visual C# 項目**，展開**資料**，然後選取**XML 檔案**。 在 [**名稱**方塊中，指定`SDKManifest.xml`，然後選擇 **[確定]** ] 按鈕。  
  
7.  使用這個 XML 取代檔案的內容：  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
8. 在 **方案總管**下方**NativeMathVSIX**專案中，建立此資料夾結構：  
  
    ```xml  
    \DesignTime  
          \CommonConfiguration  
                \Neutral  
                      \Include  
          \Debug  
                \x86  
    \Redist  
          \Debug  
                \x86  
    \References  
          \CommonConfiguration  
                \Neutral  
    ```  
  
9. 中**方案總管**，開啟捷徑功能表**解決方案 'NativeMath'**，然後選擇**在檔案總管 中開啟資料夾**。  
  
10. 在 **檔案總管**，複製 *$SolutionRoot$\NativeMath\NativeMath.h*，然後在**方案總管 中**下**NativeMathVSIX**專案中，貼上 *$SolutionRoot$ \NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include\\* 資料夾。  
  
     複製 *$SolutionRoot$\Debug\NativeMath\NativeMath.lib*，然後將它貼 *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\* 資料夾。  
  
     複製 *$SolutionRoot$\Debug\NativeMath\NativeMath.dll*並貼入 *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86\\* 資料夾。  
  
     複製 *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll*並貼入 *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86*資料夾。  
     複製 *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd*並貼入 *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral*資料夾。  
  
     複製 *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri*並貼入 *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral*資料夾。  
  
11. 在  *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\* 資料夾中，建立名為文字檔案*NativeMathSDK.props*，然後將下列內容貼在其中：  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
12. 在功能表列上選擇 [**檢視** > **其他 Windows** > **屬性] 視窗**(鍵盤：選擇**F4**索引鍵)。  
  
13. 在 **方案總管**，選取**NativeMathWRT.winmd**檔案。 在**屬性**視窗中，變更**建置動作**屬性設**內容**，然後變更**Include in VSIX** 屬性**True**。  
  
     重複此程序**NativeMath.h**檔案。  
  
     重複此程序**NativeMathWRT.pri**檔案。  
  
     重複此程序**NativeMath.Lib**檔案。  
  
     重複此程序**NativeMathSDK.props**檔案。  
  
14. 在 **方案總管**，選取**NativeMath.h**檔案。 在 **屬性**視窗中，變更**Include in VSIX**屬性設 **，則為 True**。  
  
     重複此程序**NativeMath.dll**檔案。  
  
     重複此程序**NativeMathWRT.dll**檔案。  
  
     重複此程序**SDKManifest.xml**檔案。  
  
15. 在功能表列上選擇 [建置] > [建置解決方案]。  
  
16. 在 **方案總管 中**，開啟捷徑功能表**NativeMathVSIX**專案，，然後選擇**在檔案總管 中開啟資料夾**。  
  
17. 在 **檔案總管**，瀏覽至 *$SolutionRoot$ \NativeMathVSIX\bin\Debug*資料夾，然後再執行*NativeMathVSIX.vsix*開始安裝。  
  
18. 選擇**安裝**按鈕，等候安裝完成，然後再啟動 Visual Studio。  
  
##  <a name="createSample"></a> 若要建立範例應用程式使用的類別庫  
  
1. 在功能表列上，選擇 [檔案] > [新增] > [專案]。  
  
2. 在範本清單中，依序展開**Visual c + +** > **Windows Universal** ，然後選取**空白應用程式**。 在 [**名稱**方塊中，指定**NativeMathSDKSample**，然後選擇 **[確定]** ] 按鈕。  
  
3. 在 [**方案總管] 中**，開啟捷徑功能表**NativeMathSDKSample**專案，，然後選擇**新增** > **參考**.  
  
4. 中**加入參考**對話方塊中，參考類型的清單中展開**通用 Windows**，然後選取**延伸模組**。 最後，選取**原生 Math SDK**核取方塊，然後再選擇**確定** 按鈕。
  
5. 顯示 NativeMathSDKSample 專案屬性。  
  
    在中所定義的屬性*NativeMathSDK.props*加入參考時所套用。 您可以藉由檢查所套用的屬性，確認**VC + + 目錄**專案的屬性**組態屬性**。  
  
6. 在 [**方案總管] 中**，開啟**MainPage.xaml**，然後使用下列 XAML 取代其內容：  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
7. 更新*mainpage.xaml.h 中*以符合此程式碼：  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
8. 更新*MainPage.xaml.cpp*以符合此程式碼：  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
9. 選擇**F5**鍵以執行應用程式。  
  
10. 在應用程式中，輸入任何兩個數字，選取作業，然後選擇**=**  按鈕。  
  
     正確的結果會出現。  
  
    本逐步解說示範如何建立和使用擴充功能 SDK，來呼叫[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)]程式庫和非[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)]程式庫。  
  
## <a name="next-steps"></a>後續步驟  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：使用 SDK 建立C#或 Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [建立軟體開發套件](../extensibility/creating-a-software-development-kit.md)
