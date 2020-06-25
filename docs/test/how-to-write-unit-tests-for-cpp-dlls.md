---
title: 撰寫 C++ DLL 的單元測試
ms.date: 05/01/2019
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 3bfbe5fd0147a04d6fc6142fd1d722f8f2304586
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287034"
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>在 Visual Studio 中撰寫 C++ DLL 的單元測試

有幾種方式可以測試 DLL 程式碼，這取決於它是否匯出您要測試的函式。 請選擇下列其中一種方式：

**單元測試只會呼叫從 DLL 匯出的函式：** 新增個別的測試專案，如[撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp.md)中所述。 在測試專案中，加入 DLL 專案的參考。

移至[從 DLL 專案參考匯出的函式](#projectRef)程序。

**DLL 建置為 .exe 檔：** 新增個別的測試專案。 將它連結至輸出目的檔。

移至[將測試連結至物件或程式庫檔案](#objectRef)程序。

**單元測試會呼叫不是從 DLL 匯出的非成員函式，而 DLL 可建置為靜態程式庫：** 變更 DLL 專案，讓它編譯為 *.lib* 檔。 加入會參考受測專案的個別測試專案。

這個方法有一個優點，就是可讓您的測試使用非匯出的成員，但仍然將測試保留在個別專案中。

移至[將 DLL 變更為靜態程式庫](#staticLink)程序。

**單元測試必須呼叫未匯出的非成員函式，而程式碼必須建置為動態連結程式庫 (DLL)：** 將單元測試新增至與產品程式碼相同的專案中。

請移至[在相同專案中新增單元測試](#sameProject)程序。

## <a name="create-the-tests"></a>建立測試

### <a name="to-change-the-dll-to-a-static-library"></a><a name="staticLink"></a> 將 DLL 變更為靜態程式庫

- 如果您的測試必須使用不是由 DLL 專案匯出的成員，並且受測專案是建置為動態程式庫，請考慮將它轉換成靜態程式庫。

  1. 在**方案總管**中，于受測專案的快捷方式功能表上，選擇 [**屬性**]。 專案的 [屬性]**** 視窗便會開啟。

  2. 選擇 [設定**屬性**]  >  **[一般**]。

  3. 將 [組態類型]**** 設定為 [靜態程式庫 (.lib)]****。

  繼續進行[將測試連結至物件或程式庫檔案](#objectRef)程序。

### <a name="to-reference-exported-dll-functions-from-the-test-project"></a><a name="projectRef"></a> 從測試專案參考匯出的 DLL 函式

- 如果 DLL 專案會匯出您要測試的函式，那麼您就可以從測試專案加入程式碼專案的參考。

  1. 建立原生單元測試專案。

      ::: moniker range="vs-2019"

      1. 在 [檔案]**** 功能表上，依序選擇 [新增]**** 和 [專案] > ****。 在 [新增專案]**** 對話方塊中，將 [語言]**** 設為 C++，並在搜尋方塊中鍵入 "test"。 然後選擇 [原生單元測試專案]****。

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. 在 [檔案]**** 功能表上，選擇 [新增]**[專案]** > **[Visual C++]** > **[測試]** > **[C++ 單元測試專案]** > ****。

      ::: moniker-end

  1. 在 [方案總管]**** 中，以滑鼠右鍵按一下測試專案，然後選擇 [新增]**** > [參考]****。

  1. 選取 [專案]****，然後選取要測試的專案。

       選擇 [新增] 按鈕。

  1. 在測試專案的屬性中，將受測專案的位置加入至 [Include 目錄] 中。

       選擇 [設定**屬性**] [  >  **VC + + 目錄**] [  >  **包含目錄**]。

       選擇 [編輯]****，然後新增受測專案的標頭目錄。

  移至[撰寫單元測試](#addTests)。

### <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="objectRef"></a> 將測試連結至物件或程式庫檔案

- 如果 DLL 不會匯出您要測試的函式，您可以將輸出 *.obj* 或 *.lib* 檔案新增至測試專案的相依性。

  1. 建立原生單元測試專案。

      ::: moniker range="vs-2019"

      1. 在 [檔案]**** 功能表上，依序選擇 [新增]**** 和 [專案] > ****。 在 [新增專案]**** 對話方塊中，將 [語言]**** 設為 C++，並在搜尋方塊中鍵入 "test"。 然後選擇 [原生單元測試專案]****。

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. 在 [檔案]**** 功能表上，選擇 [新增]**[專案]** > **[Visual C++]** > **[測試]** > **[C++ 單元測試專案]** > ****。

      ::: moniker-end

  2. 在**方案總管**中，于測試專案的快捷方式功能表上，選擇 [**屬性**]。

  3. 選擇 [設定**屬性**  >  **連結器**  >  ] [**輸入**  >  **其他**相依性]。

       選擇 [編輯]****，然後新增 **.obj** 或 **.lib** 檔案的名稱。 不要使用完整路徑名稱。

  4. 選擇 [設定**屬性**  >  **連結器**]  >  **[一般] [**  >  **其他程式庫目錄**]。

       選擇 [編輯]****，然後新增 **.obj** 或 **.lib** 檔案的目錄路徑。 該路徑通常是位於受測專案的組建資料夾內。

  5. 選擇 [設定**屬性**] [  >  **VC + + 目錄**] [  >  **包含目錄**]。

       選擇 [編輯]****，然後新增受測專案的標頭目錄。

  移至[撰寫單元測試](#addTests)。

### <a name="to-add-unit-tests-in-the-same-project"></a><a name="sameProject"></a> 在相同專案中新增單元測試

1. 修改產品程式碼專案屬性，以包含單元測試所需的標頭和程式庫檔案。

   1. 在 [方案總管] **** 中，於受測專案的捷徑功能表上，選擇 [屬性]****。 專案的 [屬性]**** 視窗便會開啟。

   2. 選擇 [設定] [**屬性**] [  >  **VC + + 目錄**]。

   3. 編輯 Include 目錄和程式庫目錄：

       |目錄|屬性|
       |-|-|
       |**Include 目錄** | **$(VCInstallDir)UnitTest\include;$(IncludePath)**|
       |**程式庫目錄** | **$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|

2. 加入 C++ 單元測試檔案：

   - 在 [方案總管] **** 中，於專案的捷徑功能表中，選擇 [新增]**** > [新增項目]**** > [C++ 單元測試]****。

   移至[撰寫單元測試](#addTests)。

## <a name="write-the-unit-tests"></a><a name="addTests"></a> 撰寫單元測試

1. 在每個單元測試程式碼檔案中，為受測專案的標頭加入一個 `#include` 陳述式。

2. 在單元測試程式碼檔案中加入測試類別和方法。 例如：

    ```cpp
    #include "stdafx.h"
    #include "CppUnitTest.h"
    #include "MyProjectUnderTest.h"
    using namespace Microsoft::VisualStudio::CppUnitTestFramework;
    namespace MyTest
    {
      TEST_CLASS(MyTests)
      {
      public:
          TEST_METHOD(MyTestMethod)
          {
              Assert::AreEqual(MyProject::Multiply(2,3), 6);
          }
      };
    }
    ```

## <a name="run-the-tests"></a>執行測試

1. 在 [測試]**** 功能表上，選擇 [Windows]**** > [測試總管]****。

1. 如果視窗中未顯示您所有的測試，請建置測試專案，方法是在**方案總管**中，以滑鼠右鍵按一下其節點，然後選擇 [建置]**** 或 [重建]****。

1. 在 [**測試] Explorer**中，選擇 [**全部執行**]，或選取您想要執行的特定測試。 以滑鼠右鍵按一下測試即可顯示其他選項，包括在啟用中斷點的偵錯模式中執行測試。

## <a name="see-also"></a>另請參閱

- [撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp.md)
- [VisualStudio. Microsoft.visualstudio.testtools. Microsoft.visualstudio.testtools.cppunittestframework API 參考](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)
- [對機器碼進行偵錯](../debugger/debugging-native-code.md)
- [逐步解說：建立和使用動態連結程式庫 (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [匯入及匯出](/cpp/build/importing-and-exporting)
- [快速入門：搭配測試總管進行以測試為導向的開發工作](../test/quick-start-test-driven-development-with-test-explorer.md)
