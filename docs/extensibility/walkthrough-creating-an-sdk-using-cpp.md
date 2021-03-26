---
title: 逐步解說：使用 c + + 建立 SDK |Microsoft Docs
description: 瞭解如何建立原生 c + + 數學程式庫 SDK、將 SDK 封裝為 Visual Studio 擴充功能，然後使用此逐步解說來建立應用程式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5d4baeb8a93a1bb5e70f3ee6266bb1a832a2a3fe
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080407"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>逐步解說：使用 c + + 建立 SDK
本逐步解說示範如何建立原生 c + + math library SDK、將 SDK 封裝為 Visual Studio 擴充 (VSIX) ，然後用它來建立應用程式。 本逐步解說分為下列幾個步驟：

- [建立原生和 Windows 執行階段程式庫](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [若要建立 NativeMathVSIX 延伸模組專案](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [建立使用類別庫的範例應用程式](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>必要條件
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 [VISUAL STUDIO SDK](../extensibility/visual-studio-sdk.md)。

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a> 建立原生和 Windows 執行階段程式庫

1. 在功能表列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]。

2. 在範本清單中，展開 [ **Visual C++**  >  **windows 通用**]，然後選取 [ **windows 通用應用程式] ()** 範本的 DLL。 在 [ **名稱** ] 方塊中指定 `NativeMath` ，然後選擇 [ **確定]** 按鈕。

3. 更新 *NativeMath* 以符合下列程式碼。

     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]

4. 更新 *NativeMath* 以符合此程式碼：

     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]

5. 在 **方案總管** 中，開啟 [**方案 ' NativeMath '**] 的快捷方式功能表，然後選擇 [**加入**  >  **新專案**]。

6. 在範本清單中，展開 [ **Visual C++**]，然後選取 [ **Windows 執行階段元件** ] 範本。 在 [ **名稱** ] 方塊中指定 `NativeMathWRT` ，然後選擇 [ **確定]** 按鈕。

7. 更新 *Class1* 以符合此程式碼：

     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]

8. 更新 *Class1* 以符合此程式碼：

     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]

9. 在功能表列上，選擇 [**組建**  >  **組建方案**]。

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> 若要建立 NativeMathVSIX 延伸模組專案

1. 在 **方案總管** 中，開啟 [**方案 ' NativeMath '**] 的快捷方式功能表，然後選擇 [**加入**  >  **新專案**]。

2. 在範本清單中，展開 [ **Visual c #** 擴充性]  >  ****，然後選取 [ **VSIX 專案**]。 在 [ **名稱** ] 方塊中指定 **NativeMathVSIX**，然後選擇 [ **確定]** 按鈕。

3. 在 **方案總管** 中，開啟 **extension.vsixmanifest** 的快捷方式功能表，然後選擇 [ **View Code**]。

4. 使用下列 XML 來取代現有的 XML。

    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5. 在 **方案總管** 中，開啟 **NativeMathVSIX** 專案的快捷方式功能表，然後選擇 [**加入**  >  **新專案**]。

6. 在 **Visual c # 專案** 清單中，展開 [ **資料**]，然後選取 [ **XML** 檔案]。 在 [ **名稱** ] 方塊中指定 `SDKManifest.xml` ，然後選擇 [ **確定]** 按鈕。

7. 使用這個 XML 來取代檔案的內容：

     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]

8. 在 **方案總管** 的 [ **NativeMathVSIX** ] 專案底下，建立下列資料夾結構：

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

9. 在 **方案總管** 中，開啟 [ **方案 ' NativeMath '**] 的快捷方式功能表，然後選擇 **檔案總管中的 [開啟資料夾**]。

10. 在 **檔案總管** 中，複製 *$SolutionRoot $ \NativeMath\NativeMath.h*，然後在 **方案總管** 的 **NativeMathVSIX** 專案下，將它貼到 *$SolutionRoot $ \NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include \\* 資料夾。

     複製 *$SolutionRoot $ \Debug\NativeMath\NativeMath.lib*，然後將它貼到 *$SolutionRoot $ \NativeMathVSIX\DesignTime\Debug\x86 \\* 資料夾中。

     複製 *$SolutionRoot $\Debug\NativeMath\NativeMath.dll* ，並將它貼到 *$SolutionRoot $ \\ \NativeMathVSIX\Redist\Debug\x86* 資料夾中。

     複製 *$SolutionRoot $\Debug\NativeMathWRT\NativeMathWRT.dll* ，並將它貼到 *$SolutionRoot $ \NativeMathVSIX\Redist\Debug\x86* 資料夾中。
     複製 *$SolutionRoot $ \Debug\NativeMathWRT\NativeMathWRT.winmd* ，並將它貼入 *$SolutionRoot $ \NativeMathVSIX\References\CommonConfiguration\Neutral* 資料夾。

     複製 *$SolutionRoot $ \Debug\NativeMathWRT\NativeMathWRT.pri* ，並將它貼入 *$SolutionRoot $ \NativeMathVSIX\References\CommonConfiguration\Neutral* 資料夾。

11. 在 *$SolutionRoot $ \NativeMathVSIX\DesignTime\Debug\x86 \\* 資料夾中，建立名為 *NativeMathSDK .props* 的文字檔，然後在其中貼上下列內容：

    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]

12. 在功能表列上，選擇 [ **View**  >  **Other Windows**  >  **Properties Window]** (鍵盤：選擇 **F4** 鍵) 。

13. 在 **方案總管** 中，選取 [ **NativeMathWRT** ] 檔案。 在 [ **屬性** ] 視窗中，將 [ **組建動作** ] 屬性變更為 [ **內容**]，然後將 [ **包含于 VSIX** ] 屬性變更為 [ **True**]。

     針對 **NativeMath .h** 檔案重複此程式。

     針對 **NativeMathWRT 的 pri** 檔案重複此程式。

     針對 **NativeMath .lib** 檔案重複此程式。

     針對 **NativeMathSDK. .props** 檔案重複此程式。

14. 在 **方案總管** 中，選取 **NativeMath .h** 檔案。 在 [ **屬性** ] 視窗中，將 [ **包含于 VSIX** ] 屬性變更為 [ **True**]。

     針對 **NativeMath.dll** 檔案重複此程式。

     針對 **NativeMathWRT.dll** 檔案重複此程式。

     針對 **SDKManifest.xml** 檔案重複此程式。

15. 在功能表列上，選擇 [**組建**  >  **組建方案**]。

16. 在 **方案總管** 中，開啟 **NativeMathVSIX** 專案的快捷方式功能表，然後選擇 **檔案總管中的 [開啟資料夾**]。

17. 在 **檔案總管** 中，流覽至 *$SolutionRoot $ \NativeMathVSIX\bin\Debug* 資料夾，然後執行 *NativeMathVSIX* 以開始安裝。

18. 選擇 [ **安裝** ] 按鈕，等候安裝完成，然後開啟 Visual Studio。

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> 建立使用類別庫的範例應用程式

1. 在功能表列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]。

2. 在範本清單中，展開 [ **Visual C++**  >  **Windows 通用**]，然後選取 [**空白應用程式**]。 在 [ **名稱** ] 方塊中指定 **NativeMathSDKSample**，然後選擇 [ **確定]** 按鈕。

3. 在 **方案總管** 中，開啟 **NativeMathSDKSample** 專案的快捷方式功能表，然後選擇 [**加入**  >  **參考**]。

4. 在 [ **加入參考** ] 對話方塊的 [參考型別] 清單中，展開 [ **通用視窗**]，然後選取 [ **擴充** 功能]。 最後，選取 [ **原生數學 SDK** ] 核取方塊，然後選擇 [ **確定]** 按鈕。

5. 顯示 NativeMathSDKSample 的專案屬性。

    當您加入參考時，會套用您在 *NativeMathSDK. .props* 中定義的屬性。 您可以檢查項目設定 **屬性** 的 [ **VC + + 目錄**] 屬性，以確認是否已套用這些屬性。

6. 在 **方案總管** 中，開啟 **MainPage**，然後使用下列 xaml 取代其內容：

    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]

7. 更新 *Mainpage* 以符合此程式碼：

    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]

8. 更新 *MainPage* 以符合此程式碼：

     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]

9. 選擇 **F5** 鍵以執行應用程式。

10. 在應用程式中，輸入任何兩個數字，選取一個作業，然後選擇該 **=** 按鈕。

     正確的結果隨即出現。

    本逐步解說示範如何建立和使用擴充功能 SDK 來呼叫連結 [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] 庫和非連結 [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] 庫。

## <a name="next-steps"></a>後續步驟

## <a name="see-also"></a>另請參閱
- [逐步解說：使用 c # 或 Visual Basic 建立 SDK](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [建立軟體發展工具組](../extensibility/creating-a-software-development-kit.md)
