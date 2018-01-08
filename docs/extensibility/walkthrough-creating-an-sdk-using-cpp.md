---
title: "逐步解說： 建立使用 c + + SDK |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: "32"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 065d5b16e99ce7c1356f710ab2a6cc42bbd6cde4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>逐步解說： 建立使用 c + + SDK
本逐步解說示範如何建立原生 c + + 數學程式庫 SDK，封裝 SDK 為 Visual Studio 擴充功能 (VSIX)，並再用它來建立應用程式。 本逐步解說分成下列步驟：  
  
-   [若要建立原生和 Windows 執行階段程式庫](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [若要建立 NativeMathVSIX 擴充功能專案](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [若要建立範例應用程式使用的類別庫](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
##  <a name="createClassLibrary"></a>若要建立原生和 Windows 執行階段程式庫  
  
1.  在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。  
  
2.  在範本清單中，展開  **Visual c + +**， **Windows 市集**，然後選取**DLL （Windows 市集應用程式）**範本。 在**名稱**方塊中，指定`NativeMath`，然後選擇 [**確定**] 按鈕。  
  
3.  更新 NativeMath.h 以符合下列程式碼。  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  更新 NativeMath.cpp 以符合這個程式碼：  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  在**方案總管] 中**，開啟捷徑功能表**方案 'NativeMath'**，然後選擇 [**新增**，**新專案**。  
  
6.  在範本清單中，展開  **Visual c + +**，然後選取**Windows 執行階段元件**範本。 在**名稱**方塊中，指定`NativeMathWRT`，然後選擇 [**確定**] 按鈕。  
  
7.  更新以符合這個程式碼 Class1.h:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  更新 Class1.cpp 以符合這個程式碼：  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. 在功能表列上，選擇 [建置] 、[建置方案] 。  
  
##  <a name="createVSIX"></a>若要建立 NativeMathVSIX 擴充功能專案  
  
1.  在**方案總管] 中**，開啟捷徑功能表**方案 'NativeMath'**，然後選擇 [**新增**，**新專案**。  
  
2.  在範本清單中，展開  **Visual C#**，**擴充性**，然後選取**VSIX 封裝**。 在**名稱**方塊中，指定**NativeMathVSIX**，然後選擇 [**確定**] 按鈕。  
  
3.  VSIX 資訊清單設計工具出現時，請將它關閉。  
  
4.  在**方案總管] 中**，開啟捷徑功能表**source.extension.vsixmanifest**，然後選擇 [**檢視程式碼**。  
  
5.  使用下列 XML 取代現有的 XML。  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

6.  在**方案總管 中**，開啟捷徑功能表**NativeMathVSIX**專案，然後再選擇**新增**，**新項目**。  
  
7.  在清單中**Visual C# 項目**，依序展開**資料**，然後選取**XML 檔案**。 在**名稱**方塊中，指定`SDKManifest.xml`，然後選擇 [**確定**] 按鈕。  
  
8.  使用此 XML 取代檔案的內容：  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
9. 在**方案總管 中**，請在**NativeMathVSIX**專案中，建立此資料夾結構：  
  
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
  
10. 在**方案總管 中**，開啟捷徑功能表**方案 'NativeMath'**，然後選擇 **在檔案總管 中開啟資料夾**。  
  
11. 在**檔案總管**，複製 \NativeMath\NativeMath.h，然後在**方案總管 中**，請在**NativeMathVSIX**專案中，將它貼入 \DesignTime\ 中CommonConfiguration\Neutral\Include\ 資料夾。  
  
     複製 \Debug\NativeMath\NativeMath.lib，，然後再將它貼入 \DesignTime\Debug\x86\ 資料夾中。  
  
     複製 \Debug\NativeMath\NativeMath.dll，並將它貼入 \Redist\Debug\x86\ 資料夾中。  
  
     複製 DebugNativeMathWRTNativeMathWRT.dll，並將它貼入 RedistDebugx86 資料夾中。  
  
     複製 DebugNativeMathWRTNativeMathWRT.winmd，並將它貼入 ReferencesCommonConfigurationNeutral 資料夾中。  
  
     複製 DebugNativeMathWRTNativeMathWRT.pri，並將它貼入 ReferencesCommonConfigurationNeutral 資料夾中。  
  
12. 在 \DesignTime\Debug\x86\ 資料夾，建立名為 NativeMathSDK.props 的文字檔，然後將下列內容貼在它：  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. 在功能表列上選擇 [**檢視**，**其他視窗**，**屬性] 視窗**(鍵盤： 選擇 F4 鍵)。  
  
14. 在**方案總管 中**，選取**NativeMathWRT.winmd**檔案。 在**屬性**視窗中，變更**建置動作**屬性**內容**，然後變更**包含在 VSIX 中的**屬性**True**。  
  
     重複這個程序所**SimpleMath.pri**檔案。  
  
     重複這個程序所**NativeMath.Lib**檔案。  
  
     重複這個程序所**NativeMathSDK.props**檔案。  
  
15. 在**方案總管 中**，選取**NativeMath.h**檔案。 在**屬性**視窗中，變更**包含在 VSIX 中的**屬性**True**。  
  
     重複這個程序所**NativeMath.dll**檔案。  
  
     重複這個程序所**NativeMathWRT.dll**檔案。  
  
     重複這個程序所**SDKManifest.xml**檔案。  
  
16. 在功能表列上，選擇 [建置] 、[建置方案] 。  
  
17. 在**方案總管 中**，開啟捷徑功能表**NativeMathVSIX**專案，然後再選擇**在檔案總管 中開啟資料夾**。  
  
18. 在**檔案總管**，瀏覽至 \bin\Debug\ 資料夾，然後再執行 NativeMathVSIX.vsix 開始安裝。  
  
19. 選擇**安裝**按鈕，等候安裝完成，然後再重新啟動 Visual Studio。  
  
##  <a name="createSample"></a>若要建立範例應用程式使用的類別庫  
  
1.  在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。  
  
2.  在範本清單中，展開  **Visual c + +**， **Windows 市集**，然後選取**空白應用程式**。 在**名稱**方塊中，指定**NativeMathSDKSample**，然後選擇 [**確定**] 按鈕。  
  
3.  在**方案總管 中**，開啟捷徑功能表**NativeMathSDKSample**專案，然後再選擇**新增**，**參考**。  
  
4.  在**通用屬性**，**架構和參考**參考類型的清單中的屬性頁上，依序展開**Windows**，然後選取**擴充功能**. 在 [詳細資料] 窗格中，選取**原生數學 SDK**延伸模組，然後選擇 [**加入新參考**] 按鈕。  
  
5.  在**加入參考**對話方塊中，選取**原生數學 SDK**核取方塊，，然後選擇 [**確定**] 按鈕。  
  
6.  顯示 NativeMathSDKSample 專案屬性。  
  
     加入參考時，已套用在 NativeMathSDK.props 中所定義的屬性。 您可以藉由檢查確認這**VC + + 目錄**專案屬性**組態屬性**。  
  
7.  在**方案總管 中**，開啟 MainPage.xaml，然後使用下列 XAML 取代其內容：  
  
     [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
8.  更新 mainpage.xaml.h 中，以符合這個程式碼：  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
9. 更新 MainPage.xaml.cpp 以符合這個程式碼：  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
10. 選擇 F5 鍵執行應用程式。  
  
11. 應用程式中輸入任何兩個數字選取作業，然後選擇 [  **=**  ] 按鈕。  
  
     正確的結果會出現。  
  
 本逐步解說說明如何建立和使用擴充功能 SDK 來呼叫[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)]程式庫和非[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)]程式庫。  
  
## <a name="next-steps"></a>後續步驟  
  
## <a name="see-also"></a>請參閱  
 [逐步解說： 建立使用 C# 或 Visual Basic 的 SDK](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [建立軟體開發套件](../extensibility/creating-a-software-development-kit.md)