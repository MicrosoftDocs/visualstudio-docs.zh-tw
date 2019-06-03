---
title: 逐步解說：使用 SDK 建立C++|Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1312d61b2d287a5dd8cb757b73e818a9e9cb2241
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110033"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>逐步解說：使用 C++ 建立 SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說示範如何建立原生C++數學程式庫 SDK，封裝 SDK 作為 Visual Studio 擴充功能 (VSIX)，並接著使用它來建立應用程式。 本逐步解說分為下列步驟：  
  
- [若要建立原生和 Windows 執行階段程式庫](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
- [若要建立 NativeMathVSIX 擴充功能專案](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
- [若要建立範例應用程式使用的類別庫](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 < [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="createClassLibrary"></a> 若要建立原生和 Windows 執行階段程式庫  
  
1. 在功能表列上，選擇 [檔案]  、[新增]  、[專案]  。  
  
2. 在範本清單中，依序展開**Visual C++** ， **Windows Store**，然後選取**DLL （Windows 市集應用程式）** 範本。 在 [**名稱**方塊中，指定`NativeMath`，然後選擇 **[確定]** ] 按鈕。  
  
3. 更新 NativeMath.h 以符合下列程式碼。  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4. 更新 NativeMath.cpp 以符合此程式碼：  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5. 在**方案總管 中**，開啟捷徑功能表**解決方案 'NativeMath'** ，然後選擇**新增**，**新專案**。  
  
6. 在範本清單中，依序展開**Visual C++** ，然後選取**Windows 執行階段元件**範本。 在 [**名稱**方塊中，指定`NativeMathWRT`，然後選擇 **[確定]** ] 按鈕。  
  
7. 更新以符合此程式碼的 Class1.h:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8. 更新 Class1.cpp 以符合此程式碼：  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. 在功能表列上，選擇 [建置]  、[建置方案]  。  
  
## <a name="createVSIX"></a> 若要建立 NativeMathVSIX 擴充功能專案  
  
1. 在**方案總管 中**，開啟捷徑功能表**解決方案 'NativeMath'** ，然後選擇**新增**，**新專案**。  
  
2. 在範本清單中，依序展開**Visual C#** ，**擴充性**，然後選取**VSIX 封裝**。 在 [**名稱**方塊中，指定**NativeMathVSIX**，然後選擇 **[確定]** ] 按鈕。  
  
3. VSIX 資訊清單設計工具出現時，請將它關閉。  
  
4. 在 **方案總管 中**，開啟捷徑功能表**source.extension.vsixmanifest**，然後選擇 **檢視程式碼**。  
  
5. 使用下列 XML 取代現有的 XML。  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6. 在 [**方案總管] 中**，開啟捷徑功能表**NativeMathVSIX**專案，，然後選擇**新增**，**新項目**。  
  
7. 在這份**Visual C# 項目**，展開**資料**，然後選取**XML 檔案**。 在 [**名稱**方塊中，指定`SDKManifest.xml`，然後選擇 **[確定]** ] 按鈕。  
  
8. 使用這個 XML 取代檔案的內容：  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. 在 **方案總管**，請在**NativeMathVSIX**專案中，建立此資料夾結構：  
  
    ```  
  
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
  
10. 中**方案總管**，開啟捷徑功能表**解決方案 'NativeMath'** ，然後選擇**在檔案總管 中開啟資料夾**。  
  
11. 中**檔案總管**，複製 \NativeMath\NativeMath.h，然後在**方案總管**，請在**NativeMathVSIX**專案中，將它貼在 \DesignTime\CommonConfiguration\Neutral\Include\ 資料夾中。  
  
     複製 \Debug\NativeMath\NativeMath.lib，，然後將它貼在 \DesignTime\Debug\x86\ 資料夾中。  
  
     複製 \Debug\NativeMath\NativeMath.dll，並將它貼入 \Redist\Debug\x86\ 資料夾中。  
  
     複製 DebugNativeMathWRTNativeMathWRT.dll，並將它貼入 RedistDebugx86 資料夾中。  
  
     複製 DebugNativeMathWRTNativeMathWRT.winmd，並將它貼入 ReferencesCommonConfigurationNeutral 資料夾中。  
  
     複製 DebugNativeMathWRTNativeMathWRT.pri，並將它貼入 ReferencesCommonConfigurationNeutral 資料夾中。  
  
12. 在 \DesignTime\Debug\x86\ 資料夾，建立名為 NativeMathSDK.props，文字檔案，然後將下列內容貼在它：  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. 在功能表列上選擇 [**檢視**，**其他 Windows**，**屬性] 視窗**(鍵盤：選擇 F4 鍵）。  
  
14. 在 **方案總管**，選取**NativeMathWRT.winmd**檔案。 在**屬性**視窗中，變更**建置動作**屬性設**內容**，然後變更**Include in VSIX** 屬性**True**。  
  
     重複此程序**SimpleMath.pri**檔案。  
  
     重複此程序**NativeMath.Lib**檔案。  
  
     重複此程序**NativeMathSDK.props**檔案。  
  
15. 在 **方案總管**，選取**NativeMath.h**檔案。 在 **屬性**視窗中，變更**Include in VSIX**屬性設 **，則為 True**。  
  
     重複此程序**NativeMath.dll**檔案。  
  
     重複此程序**NativeMathWRT.dll**檔案。  
  
     重複此程序**SDKManifest.xml**檔案。  
  
16. 在功能表列上，選擇 [建置]  、[建置方案]  。  
  
17. 在 **方案總管 中**，開啟捷徑功能表**NativeMathVSIX**專案，，然後選擇**在檔案總管 中開啟資料夾**。  
  
18. 在 **檔案總管**，巡覽至的 \bin\Debug\ 資料夾，然後再執行 NativeMathVSIX.vsix 開始安裝。  
  
19. 選擇**安裝**按鈕，等候安裝完成，然後再重新啟動 Visual Studio。  
  
## <a name="createSample"></a> 若要建立範例應用程式使用的類別庫  
  
1. 在功能表列上，選擇 [檔案]  、[新增]  、[專案]  。  
  
2. 在範本清單中，依序展開**Visual C++** ， **Windows Store**，然後選取**空白應用程式**。 在 [**名稱**方塊中，指定**NativeMathSDKSample**，然後選擇 **[確定]** ] 按鈕。  
  
3. 在 [**方案總管] 中**，開啟捷徑功能表**NativeMathSDKSample**專案，，然後選擇**新增**，**參考**。  
  
4. 上**通用屬性**，**架構和參考**參考類型的清單中的屬性頁面上，展開**Windows**，然後選取 **延伸模組**. 在詳細資料 窗格中，選取**原生 Math SDK**延伸模組，然後選擇**加入新參考** 按鈕。  
  
5. 在 **加入參考**對話方塊中，選取**原生 Math SDK**核取方塊，，然後選擇  **確定**  按鈕。  
  
6. 顯示 NativeMathSDKSample 專案屬性。  
  
    新增參考時，已套用在 NativeMathSDK.props 中所定義的屬性。 您可以檢查來確認這**VC + + 目錄**專案的屬性**組態屬性**。  
  
7. 在 [**方案總管] 中**，開啟 MainPage.xaml，然後使用下列 XAML 取代其內容：  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. 更新 mainpage.xaml.h 中，以符合此程式碼：  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. 更新 MainPage.xaml.cpp 以符合此程式碼：  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. 選擇 F5 鍵執行應用程式。  
  
11. 在應用程式中，輸入任何兩個數字，選取作業，然後選擇 **=**  按鈕。  
  
     正確的結果會出現。  
  
    本逐步解說示範如何建立和使用擴充功能 SDK，來呼叫[!INCLUDE[wrt](../includes/wrt-md.md)]程式庫和非[!INCLUDE[wrt](../includes/wrt-md.md)]程式庫。  
  
## <a name="next-steps"></a>後續步驟  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：使用 SDK 建立C#或 Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [建立軟體開發套件](../extensibility/creating-a-software-development-kit.md)
