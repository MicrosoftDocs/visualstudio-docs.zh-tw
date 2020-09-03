---
title: 逐步解說：使用 c + + 建立 SDK |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1312d61b2d287a5dd8cb757b73e818a9e9cb2241
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202059"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>逐步解說：使用 C++ 建立 SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說示範如何建立原生 c + + math library SDK、將 SDK 封裝為 Visual Studio 擴充 (VSIX) ，然後用它來建立應用程式。 本逐步解說分為下列幾個步驟：  
  
- [建立原生和 Windows 執行階段程式庫](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
- [若要建立 NativeMathVSIX 延伸模組專案](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
- [建立使用類別庫的範例應用程式](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Prerequisites  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 [VISUAL STUDIO SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a> 建立原生和 Windows 執行階段程式庫  
  
1. 從功能表列依序選擇 [**檔案**]、[**新增**] 及 [**專案**]。  
  
2. 在範本清單中，展開 [ **Visual C++**]、[ **windows 存放區**]，然後選取 [ **windows store 應用程式] () ** 範本的 DLL。 在 [ **名稱** ] 方塊中指定 `NativeMath` ，然後選擇 [ **確定]** 按鈕。  
  
3. 更新 NativeMath 以符合下列程式碼。  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4. 更新 NativeMath 以符合此程式碼：  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5. 在 **方案總管**中，開啟 [ **方案 ' NativeMath '**] 的快捷方式功能表，然後選擇 [ **加入**]、[ **新增專案**]。  
  
6. 在範本清單中，展開 [ **Visual C++**]，然後選取 [ **Windows 執行階段元件** ] 範本。 在 [ **名稱** ] 方塊中指定 `NativeMathWRT` ，然後選擇 [ **確定]** 按鈕。  
  
7. 更新 Class1 以符合此程式碼：  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8. 更新 Class1 以符合此程式碼：  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. 在功能表列上，選擇 [建置] ****、[建置方案] ****。  
  
## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> 若要建立 NativeMathVSIX 延伸模組專案  
  
1. 在 **方案總管**中，開啟 [ **方案 ' NativeMath '**] 的快捷方式功能表，然後選擇 [ **加入**]、[ **新增專案**]。  
  
2. 在範本清單中，展開 [ **Visual c #**]、[擴充性 **]，然後**選取 [ **VSIX 套件**]。 在 [ **名稱** ] 方塊中指定 **NativeMathVSIX**，然後選擇 [ **確定]** 按鈕。  
  
3. 當 [VSIX 資訊清單設計工具] 出現時，請將它關閉。  
  
4. 在 **方案總管**中，開啟 **extension.vsixmanifest**的快捷方式功能表，然後選擇 [ **View Code**]。  
  
5. 使用下列 XML 來取代現有的 XML。  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6. 在 **方案總管**中，開啟 **NativeMathVSIX** 專案的快捷方式功能表，然後選擇 [ **加入**]、[ **新增專案**]。  
  
7. 在 **Visual c # 專案**清單中，展開 [ **資料**]，然後選取 [ **XML**檔案]。 在 [ **名稱** ] 方塊中指定 `SDKManifest.xml` ，然後選擇 [ **確定]** 按鈕。  
  
8. 使用這個 XML 來取代檔案的內容：  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. 在 **方案總管**的 **NativeMathVSIX** 專案中，建立下列資料夾結構：  
  
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
  
10. 在 **方案總管**中，開啟 [ **方案 ' NativeMath '**] 的快捷方式功能表，然後選擇 **檔案總管中的 [開啟資料夾**]。  
  
11. 在 **檔案總管**中複製 \NativeMath\NativeMath.h，然後在 **方案總管**的 [ **NativeMathVSIX** ] 專案中，將它貼到 [\DesignTime\CommonConfiguration\Neutral\Include\] 資料夾中。  
  
     複製 \Debug\NativeMath\NativeMath.lib，然後將它貼入 \DesignTime\Debug\x86\ 資料夾。  
  
     複製 \Debug\NativeMath\NativeMath.dll 並將它貼到 \Redist\Debug\x86\ 資料夾中。  
  
     複製 DebugNativeMathWRTNativeMathWRT.dll 並將它貼到 RedistDebugx86 資料夾中。  
  
     複製 DebugNativeMathWRTNativeMathWRT，並將它貼入 ReferencesCommonConfigurationNeutral 資料夾。  
  
     複製 DebugNativeMathWRTNativeMathWRT，並將它貼入 ReferencesCommonConfigurationNeutral 資料夾。  
  
12. 在 \DesignTime\Debug\x86\ 資料夾中，建立名為 NativeMathSDK .props 的文字檔，然後在其中貼上下列內容：  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. 在功能表列上，選擇 [ **視圖**]、[ **其他視窗**]、[ **屬性視窗]** (鍵盤：選擇 F4 鍵) 。  
  
14. 在 **方案總管**中，選取 [ **NativeMathWRT** ] 檔案。 在 [ **屬性** ] 視窗中，將 [ **組建動作** ] 屬性變更為 [ **內容**]，然後將 [ **包含于 VSIX** ] 屬性變更為 [ **True**]。  
  
     針對 **SimpleMath 的 pri** 檔案重複此程式。  
  
     針對 **NativeMath .lib** 檔案重複此程式。  
  
     針對 **NativeMathSDK. .props** 檔案重複此程式。  
  
15. 在 **方案總管**中，選取 **NativeMath .h** 檔案。 在 [ **屬性** ] 視窗中，將 [ **包含于 VSIX** ] 屬性變更為 [ **True**]。  
  
     針對 **NativeMath.dll** 檔案重複此程式。  
  
     針對 **NativeMathWRT.dll** 檔案重複此程式。  
  
     針對 **SDKManifest.xml** 檔案重複此程式。  
  
16. 在功能表列上，選擇 [建置] ****、[建置方案] ****。  
  
17. 在 **方案總管**中，開啟 **NativeMathVSIX** 專案的快捷方式功能表，然後選擇 **檔案總管中的 [開啟資料夾**]。  
  
18. 在 **檔案總管**中，流覽至 \bin\Debug\ 資料夾，然後執行 NativeMathVSIX 以開始安裝。  
  
19. 選擇 [ **安裝** ] 按鈕，等候安裝完成，然後重新開機 Visual Studio。  
  
## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> 建立使用類別庫的範例應用程式  
  
1. 從功能表列依序選擇 [**檔案**]、[**新增**] 及 [**專案**]。  
  
2. 在範本清單中，展開 [ **Visual C++**]、[ **Windows 儲存區**]，然後選取 [ **空白應用程式**]。 在 [ **名稱** ] 方塊中指定 **NativeMathSDKSample**，然後選擇 [ **確定]** 按鈕。  
  
3. 在 **方案總管**中，開啟 **NativeMathSDKSample** 專案的快捷方式功能表，然後選擇 [ **加入**]、[ **參考**]。  
  
4. 在 [ **通用屬性**]、[ **架構和參考** ] 屬性頁的 [參考型別] 清單中，展開 [ **視窗**]，然後選取 [ **擴充**功能]。 在詳細資料窗格中，選取 [ **原生數學 SDK** ] 延伸模組，然後選擇 [ **加入新參考** ] 按鈕。  
  
5. 在 [ **加入參考** ] 對話方塊中，選取 [ **原生數學 SDK** ] 核取方塊，然後選擇 [ **確定]** 按鈕。  
  
6. 顯示 NativeMathSDKSample 的專案屬性。  
  
    當您加入參考時，會套用您在 NativeMathSDK. .props 中定義的屬性。 您可以檢查項目設定**屬性**的 [ **VC + + 目錄**] 屬性來確認這一點。  
  
7. 在 **方案總管**中，開啟 MainPage，然後使用下列 xaml 取代其內容：  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. 更新 Mainpage 以符合此程式碼：  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. 更新 MainPage 以符合此程式碼：  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. 選擇 F5 鍵以執行應用程式。  
  
11. 在應用程式中，輸入任何兩個數字，選取一個作業，然後選擇該 **=** 按鈕。  
  
     正確的結果隨即出現。  
  
    本逐步解說示範如何建立和使用擴充功能 SDK 來呼叫連結 [!INCLUDE[wrt](../includes/wrt-md.md)] 庫和非連結 [!INCLUDE[wrt](../includes/wrt-md.md)] 庫。  
  
## <a name="next-steps"></a>後續步驟  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：使用 c # 或 Visual Basic 建立 SDK](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [建立軟體開發套件](../extensibility/creating-a-software-development-kit.md)
