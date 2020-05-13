---
title: 演練:使用C++創建 SDK |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65643e65490eacb79eea4d76aa49ff10d6cccf66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697637"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>演練:使用C++創建 SDK
本演練演示如何創建本機C++數學庫 SDK,將 SDK 打包為可視化工作室擴展 (VSIX),然後使用它創建應用。 演練分為以下步驟:

- [建立本機與 Windows 執行時庫](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [建立本機MathVSIX延伸專案](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [建立使用類別庫的範例應用程式](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Prerequisites
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 有關詳細資訊,請參閱[可視化工作室 SDK](../extensibility/visual-studio-sdk.md)。

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>建立本機與 Windows 執行時庫

1. 在選單列上,選擇 **「檔** > **新專案** > **」。。**

2. 在範本清單中,展開**VisualC++** > **Windows 通用**,然後選擇**DLL(Windows 通用應用)** 範本。 在 **「名稱」** 框`NativeMath`中, 指定 ,然後選擇 **「確定**」 按鈕。

3. 更新*本機 Math.h*以匹配以下代碼。

     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]

4. 更新*本機 Math.cpp*以符合此代碼:

     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]

5. 在**解決方案資源管理器中**,打開**解決方案「本機數學」** 的快捷選單,然後選擇「**添加新** > **專案**」。

6. 在範本清單中,展開**視覺化C++,** 然後選擇**Windows執行時元件**範本。 在 **「名稱」** 框`NativeMathWRT`中, 指定 ,然後選擇 **「確定**」 按鈕。

7. 更新*Class1.h*以符合此代碼:

     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]

8. 更新*Class1.cpp*以符合此代碼:

     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]

9. 在功能表欄上,選擇 **「生成** > **解決方案**」。

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a>建立本機MathVSIX延伸專案

1. 在**解決方案資源管理器中**,打開**解決方案「本機數學」** 的快捷選單,然後選擇「**添加新** > **專案**」。

2. 在樣本清單中,展開**視覺化 C#** > **可擴充性**,然後選擇**VSIX 專案**。 在 **「名稱」** 框中,指定**本機 MathVSIX,** 然後選擇 **「確定**」 按鈕。

3. 在**解決方案資源管理器中**,打開**source.擴展.vsixmanifest 的**快捷選單,然後選擇 **「查看代碼**」 。。

4. 使用以下 XML 替換現有 XML。

    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5. 在**解決方案資源管理器**中,打開**NativeMathVSIX**專案的快捷選單,**Add** > 然後選擇「**添加新項**」。

6. 在**視覺化 C# 項目**清單中,展開**資料**,然後選擇**XML 檔**。 在 **「名稱」** 框`SDKManifest.xml`中, 指定 ,然後選擇 **「確定**」 按鈕。

7. 使用此 XML 取代檔案的內容:

     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]

8. 在**解決方案資源管理員**中,在**本機MathVSIX**專案下,建立此資料夾結構:

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

9. 在**解決方案資源管理員**中,打開**解決方案「本機 Math」** 的快捷方式選單,然後在**檔案資源管理器中選擇「打開資料夾**」 。

10. 在**檔案資源管理器**中,複製 *$SolutionRoot$$_NativeMath_NativeMath.h,* 然後在**解決方案資源管理器**中,在**本機MathVSIX**專案下,將其粘貼到 *$SolutionRoot$$_NativeMathVSIX_設計\\時間\通用配置\中性\ 包括*資料夾中。

     複製 *$SolutionRoot$$_調試\本機Math_NativeMath.lib*,然後將其粘貼到 *$SolutionRoot$_NativeMathVSIX_設計時間\調試\\\x86*資料夾中。

     複製 *$SolutionRoot$_Debug_NativeMath_NativeMath.dll*並將其貼上*到\\$SolutionRoot$_NativeMathVSIX_Redist_Debug_x86*資料夾中。

     複製 *$SolutionRoot$$_調試\本機 MathWRT_NativeMathWRT.dll 並將其*粘貼到 *$SolutionRoot$_NativeMathVSIX_Redist_Debug_x86*資料夾中。
     複製 *$SolutionRoot$$_調試\本機 MathWRT_NativeMathWRT.winmd,* 並將其粘貼到 *$SolutionRoot$_NativeMathVSIX_引用\通用配置\中性*資料夾中。

     複製 *$SolutionRoot$_Debug_NativeMathWRT_NativeMathWRT.pri*並將其粘貼到 *$SolutionRoot$_NativeMathVSIX_引用\通用配置\中性*資料夾中。

11. 在 *$SolutionRoot$$_NativeMathVSIX_DesignTime_Debug_x86\\*資料夾中,建立名為*NativeMathSDK.props*的文字檔,然後粘貼以下內容:

    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]

12. 在選單列上,選擇 **「查看** > **其他 Windows** > **屬性」視窗**(鍵盤:選擇**F4**鍵)。

13. 在**解決方案資源管理器**中,選擇**本機MathWRT.winmd**檔。 在 **「屬性」** 視窗中,將**產生操作**屬性變更為**內容**,然後將**VSIX 中的「包括」** 屬性改變為**True**。

     對**本機 Math.h**檔重複此過程。

     對**本機 MathWRT.pri**檔重複此過程。

     對**本機 Math.Lib**檔重複此過程。

     對**本機 MathSDK.props**檔重複此過程。

14. 在**解決方案資源管理員中**,選擇**本機Math.h**檔案。 在 **「屬性」** 視窗中,將**VSIX 中的「包括」** 屬性改變為**True**。

     對**本機 Math.dll**檔重複此過程。

     對**本機 MathWRT.dll**檔重複此過程。

     對**SDKManifest.xml**檔重複此過程。

15. 在功能表欄上,選擇 **「生成** > **解決方案**」。

16. 在**解決方案資源管理員**中,打開**本機MathVSIX**專案的快捷功能表,然後在**檔案資源管理器中選擇"打開資料夾**"。

17. 在**檔案資源管理器中**,導航到 *$SolutionRoot$$_NativeMathVSIX_bin_除錯*資料夾,然後執行*本機 MathVSIX.vsix*開始安裝。

18. 選擇 **「安裝**」按鈕,等待安裝完成,然後打開 Visual Studio。

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>建立使用類別庫的範例應用程式

1. 在選單列上,選擇 **「檔** > **新專案** > **」。。**

2. 在樣本清單中,展開 **「視窗C++** > **Windows 通用**,然後選擇**空白應用**。 在 **「名稱」** 框中,指定**本機 MathSDKSample,** 然後選擇 **「確定**」按鈕。

3. 在**解決方案資源管理器**中,打開**NativeMathSDKSample**專案的快捷選單,然後選擇 **「添加** > **參考**」。

4. 在「**添加引用」** 對話方塊中,在引用類型清單中,展開**通用 Windows,** 然後選擇 **「擴展**」。。 最後,選擇**本機數學 SDK**複選框,然後選擇 **「確定**」按鈕。

5. 顯示本機 MathSDK 採樣的項目屬性。

    添加引用時,應用了在*NativeMathSDK.props*中定義的屬性。 您可以通過檢查項目的**配置屬性**的**VC# 目錄**屬性來驗證已應用的屬性。

6. 在**解決方案資源管理員中**,開啟**MainPage.xaml**,然後使用以下 XAML 取代其內容:

    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]

7. 更新*主頁.xaml.h*以符合此代碼:

    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]

8. 更新*MainPage.xaml.cpp*以符合此代碼:

     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]

9. 選擇**F5**鍵來運行應用。

10. 在應用中,輸入任意兩個數字,選擇一個操作,然後選擇該**=** 按鈕。

     將顯示正確的結果。

    本演練展示如何建立和使用擴展 SDK[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)]呼叫到庫[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)]和非庫中。

## <a name="next-steps"></a>後續步驟

## <a name="see-also"></a>另請參閱
- [演練:使用 C# 或視覺化基本功能建立 SDK](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [建立軟體開發工具組](../extensibility/creating-a-software-development-kit.md)
