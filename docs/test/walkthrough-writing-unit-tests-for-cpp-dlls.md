---
title: 如何：撰寫 C++ DLL 的單元測試
description: 瞭解如何使用測試優先方法開發原生 c + + DLL。 從建立原生測試專案開始。
ms.custom: SEO-VS-2020
ms.date: 06/13/2019
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 2d145e1383e8f6c0d7c25ae72232fdbe2a8d703d
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727537"
---
# <a name="how-to-write-unit-tests-for-c-dlls"></a>如何：撰寫 C++ DLL 的單元測試

本逐步解說描述如何使用測試先行方法來開發原生 C++ DLL。 基本步驟如下：

1. [建立原生測試專案](#create_test_project)。 測試專案位於與 DLL 專案相同的方案中。

2. [建立 DLL 專案](#create_dll_project)。 此逐步解說會建立新的 DLL，但是測試現有 DLL 的程序很相似。

3. [讓測試能夠看到 DLL 函式](#make_functions_visible)。

4. [反覆擴大測試範圍](#iterate)。 建議您使用由測試所引導之程式碼開發的「紅-綠-重構」循環。

5. [偵錯導致失敗的測試](#debug)。 您可以在偵錯模式下執行測試。

6. [在測試保持不變的情況下重構](#refactor)。 重構代表改善程式碼的結構，而不會變更其外部行為。 這麼做可以改善程式碼的效能、擴充性或可讀性。 由於目的並不是要變更行為，所以當您對程式碼進行重構變更時，不會變更測試。 測試有助於確保進行重構時不會產生 Bug。

7. [檢查涵蓋範圍](using-code-coverage-to-determine-how-much-code-is-being-tested.md)。 單元測試運用愈多程式碼，就愈有用。 您可以探索測試曾經使用過程式碼的哪些部分。

8. [將單元與外部資源隔離](using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)。 一般而言，DLL 相依於您開發之系統的其他元件，例如其他 DLL、資料庫或遠端子系統。 將每個單元與其相依性隔離，進行獨立測試會很有用。 外部元件可能會使測試執行速度變慢。 在開發期間，其他元件可能並不完整。

## <a name="create-a-native-unit-test-project"></a><a name="create_test_project"></a> 建立原生單元測試專案

1. 在 [檔案] 功能表上，依序選擇 [新增] 和 [專案] > 。

     **Visual Studio 2017 及更早版本**：展開 [**已安裝**  >  的 **範本**]  >  **Visual C++**  >  **測試**]。
     **Visual Studio 2019**：將 **Language** 設定為 c + +，並在搜尋方塊中輸入 "test"。

     選擇 [原生單元測試專案] 範本，或您偏好的任何已安裝架構。 如果您選擇其他範本 (例如 Google Test 或 Boost.Test)，基本原則相同，但有些細節則不同。

     在此逐步解說中，測試專案名為 `NativeRooterTest`。

2. 在新的專案中，檢查 **unittest1.cpp**

     ![包含 TEST&#95;CLASS 和 TEST&#95;METHOD 的測試專案](../test/media/utecpp2.png)

     請注意：

    - 每項測試都會使用 `TEST_METHOD(YourTestName){...}` 來定義。

         您不必撰寫傳統的函式簽章。 簽章會由巨集 TEST_METHOD 建立。 該巨集會產生傳回 void 的執行個體函式。 它也會產生靜態函式，以傳回測試方法的相關資訊。 此資訊可讓測試總管找到該方法。

    - 測試方法會使用 `TEST_CLASS(YourClassName){...}`來分類。

         在測試執行時，會建立每個測試類別的執行個體。 將會以非指定的順序來呼叫測試方法。 您可以定義在每個模組、類別或方法之前和之後叫用的特殊方法。

3. 確認測試在測試總管中執行：

    1. 插入一些測試程式碼：

        ```cpp
        TEST_METHOD(TestMethod1)
        {
            Assert::AreEqual(1,1);
        }
        ```

         請注意， `Assert` 類別提供數個靜態方法，可讓您在測試方法中用來驗證結果。

    2. 在 [測試] 功能表上，選擇 [執行] > [所有測試]。

         測試會開始建置及執行。

         [測試總管] 隨即出現。

         此測試會出現在 [通過的測試] 底下。

         ![[單元測試總管] 中有一個測試成功](../test/media/utecpp04.png)

## <a name="create-a-dll-project"></a><a name="create_dll_project"></a> 建立 DLL 專案

::: moniker range="vs-2019"

下列步驟會示範如何在 Visual Studio 2019 中建立 DLL 專案。

1. 使用 **Windows Desktop Wizard** 建立 c + + 專案：以滑鼠右鍵按一下 **方案總管** 中的方案名稱，然後選擇 [**加入**  >  **新專案**]。 將 [語言] 設為 C++，然後在搜尋方塊中鍵入 "windows"。 從結果清單中選擇 [Windows 傳統式精靈]。

     在此逐步解說中，專案名為 `RootFinder`。

2. 按下 [建立] 。 在下一個對話方塊中，於 [應用程式類型] 下方，選擇 [動態連結程式庫 (dll)]，然後選取 [匯出符號]。

     [匯出符號]  選項會產生方便的巨集，可讓您用來宣告匯出的方法。

     ![已選取 [DLL] 和 [匯出符號] 的 C++ 專案精靈設定](../test/media/vs-2019/windows-desktop-project-dll.png)

3. 在主體 *.h* 檔案中宣告匯出的函式：

     ![新的 DLL 程式碼專案以及包含 API 巨集的 .h 檔案](../test/media/utecpp07.png)

     宣告子 `__declspec(dllexport)` 會使類別的 public 和 protected 成員顯示在 DLL 外部。 如需詳細資訊，請參閱 [Using dllimport and dllexport in C++ Classes](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes)。

4. 在主體 *.cpp* 檔案中，新增函式的最小主體：

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

::: moniker-end

::: moniker range="vs-2017"

下列步驟會示範如何在 Visual Studio 2017 中建立 DLL 專案。

1. 使用 [Win32 專案] 範本建立 C++ 專案。

     在此逐步解說中，專案名為 `RootFinder`。

2. 在 [Win32 應用程式精靈] 中選取 [DLL]  和 [匯出符號]  。

     [匯出符號]  選項會產生方便的巨集，可讓您用來宣告匯出的方法。

     ![已選取 [DLL] 和 [匯出符號] 的 C++ 專案精靈設定](../test/media/utecpp06.png)

3. 在主體 *.h* 檔案中宣告匯出的函式：

     ![新的 DLL 程式碼專案以及包含 API 巨集的 .h 檔案](../test/media/utecpp07.png)

     宣告子 `__declspec(dllexport)` 會使類別的 public 和 protected 成員顯示在 DLL 外部。 如需詳細資訊，請參閱 [Using dllimport and dllexport in C++ Classes](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes)。

4. 在主體 *.cpp* 檔案中，新增函式的最小主體：

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

::: moniker-end

## <a name="couple-the-test-project-to-the-dll-project"></a><a name="make_functions_visible"></a> 將測試專案結合至 DLL 專案

1. 將 DLL 專案加入測試專案的專案參考中：

   1. 在 [方案總管] 中，以滑鼠右鍵按一下測試專案節點，然後選擇 [加入] > [參考]。

   2. 在 [加入參考]  對話方塊中，選取 DLL 專案，並選擇 [加入] 。

        ![C++ 專案屬性 | 新增參考](../test/media/utecpp09.png)

2. 在主體單元測試 *.cpp* 檔案中，新增 DLL 程式碼的 *.h* 檔案：

   ```cpp
   #include "..\RootFinder\RootFinder.h"
   ```

3. 加入使用匯出函式的基本測試：

   ```cpp
   TEST_METHOD(BasicTest)
   {
      CRootFinder rooter;
      Assert::AreEqual(
         // Expected value:
         0.0,
         // Actual value:
         rooter.SquareRoot(0.0),
         // Tolerance:
         0.01,
        // Message:
        L"Basic test failed",
        // Line number - used if there is no PDB file:
        LINE_INFO());
   }
   ```

4. 建置方案。

    新測試會出現在 [測試總管] 中。

5. 在 [測試總管] 中，選擇 [全部執行]。

    ![[單元測試總管] &#45;「基本測試」成功](../test/media/utecpp10.png)

   您已經設定測試和程式碼專案，並確認您可以執行在程式碼專案中執行函式的測試。 現在您可以開始撰寫真正的測試和程式碼。

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="iterate"></a> 反復增強測試並使其通過

1. 加入新的測試：

    ```cpp
    TEST_METHOD(RangeTest)
    {
      CRootFinder rooter;
      for (double v = 1e-6; v < 1e6; v = v * 3.2)
      {
        double actual = rooter.SquareRoot(v*v);
        Assert::AreEqual(v, actual, v/1000);
      }
    }
    ```

    > [!TIP]
    > 建議您不要變更已通過的測試。 相反地，請加入新的測試，更新程式碼，使測試通過，然後再加入另一個測試，依此類推。
    >
    > 當您的使用者變更他們的需求時，請停用已不再正確的測試。 以相同的累加方式，撰寫新的測試，一次使一個測試生效。

2. 建置解決方案，然後在 [測試總管] 中選擇 [全部執行]。

     新的測試失敗。

     ![RangeTest 失敗](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > 確認每個測試在您撰寫之後立即失敗。 這樣有助於避免撰寫永遠不會失敗的測試這種易犯的錯誤。

3. 增強您的 DLL 程式碼，讓新測試能夠成功：

    ```cpp
    #include <math.h>
    ...
    double CRootFinder::SquareRoot(double v)
    {
      double result = v;
      double diff = v;
      while (diff > result/1000)
      {
        double oldResult = result;
        result = result - (result*result - v)/(2*result);
        diff = abs (oldResult - result);
      }
      return result;
    }
    ```

4. 建立方案，然後在 [ **Test Explorer**] 中選擇 [ **全部執行**]。

     這兩個測試都通過。

     ![[單元測試總管] &#45;「範圍測試」成功](../test/media/utecpp12.png)

    > [!TIP]
    > 開發程式碼時，一次加入一個測試。 確定所有測試在每次反覆之後都通過。

## <a name="debug-a-failing-test"></a><a name="debug"></a> 將失敗的測試進行調試

1. 加入另一個測試：

    ```cpp
    #include <stdexcept>
    ...
    // Verify that negative inputs throw an exception.
    TEST_METHOD(NegativeRangeTest)
    {
      wchar_t message[200];
      CRootFinder rooter;
      for (double v = -0.1; v > -3.0; v = v - 0.5)
      {
        try
        {
          // Should raise an exception:
          double result = rooter.SquareRoot(v);

          _swprintf(message, L"No exception for input %g", v);
          Assert::Fail(message, LINE_INFO());
        }
        catch (std::out_of_range ex)
        {
          continue; // Correct exception.
        }
        catch (...)
        {
          _swprintf(message, L"Incorrect exception for %g", v);
          Assert::Fail(message, LINE_INFO());
        }
      }
    }
    ```

2. 建置方案，然後選擇 [全部執行] 。

3. 開啟 (或按兩下) 失敗的測試。

     失敗的判斷提示會反白顯示。 [測試總管] 的詳細資料窗格中會顯示失敗的訊息。

     ![NegativeRangeTests 失敗](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

4. 若要查看測試失敗的原因，請逐步執行函式：

    1. 在 SquareRoot 函式開頭設定中斷點。

    2. 在失敗測試的捷徑功能表上，選擇 [偵錯選取的測試] 。

         當在中斷點停止執行時，逐步執行程式碼。

5. 將程式碼插入您開發的函式中：

    ```cpp

    #include <stdexcept>
    ...
    double CRootFinder::SquareRoot(double v)
    {
        // Validate parameter:
        if (v < 0.0)
        {
          throw std::out_of_range("Can't do square roots of negatives");
        }

    ```

6. 現在所有測試都通過了。

   ![所有測試都成功](../test/media/ute_ult_alltestspass.png)

::: moniker range="vs-2017"

> [!TIP]
> 如果個別測試沒有任何相依性可防止它們依任何循序執行，請使用 ![ [測試瀏覽器] 工具列上 [平行測試執行] 切換按鈕的螢幕擷取畫面，開啟平行測試執行。 選取此按鈕時，將會以平行方式執行測試。](../test/media/ute_parallelicon-small.png) 切換按鈕開啟平行測試執行。 這可大幅縮短執行所有測試所需的時間。

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> 如果個別測試沒有任何會防止它們依任意順序執行的相依性，請使用工具列的設定功能表開啟平行測試執行。 這可大幅縮短執行所有測試所需的時間。

::: moniker-end

## <a name="refactor-the-code-without-changing-tests"></a><a name="refactor"></a> 重構程式碼而不變更測試

1. 簡化 SquareRoot 函式中的主要計算：

    ```cpp
    // old code:
    //   result = result - (result*result - v)/(2*result);
    // new code:
         result = (result + v/result)/2.0;

    ```

2. 建置方案，然後選擇 [全部執行] ，確定您沒有引入錯誤。

    > [!TIP]
    > 一組良好的單元測試可讓您有信心，當您變更程式碼時，不會引入 Bug。
    >
    > 將重構作業與其他變更分開。

## <a name="next-steps"></a>後續步驟

- **分離。** 大部分 DLL 相依於其他子系統，例如資料庫和其他 DLL。 這些其他元件通常會以平行方式開發。 若要在還無法使用其他元件時，允許單元測試，您必須替換模擬或

- **組建驗證測試。** 您可以依設定的間隔，在小組的組建伺服器上執行測試。 這樣可以確保，當整合數個小組成員的工作時，不會引入 Bug。

- **簽入測試。** 您可以強制在每位小組成員將程式碼簽入原始檔控制之前，執行某些測試。 一般而言，這是一組完整組建驗證測試的子集。

   您也可以強制規定程式碼涵蓋範圍的最低層級。

## <a name="see-also"></a>請參閱

- [將單元測試新增至現有的 C++ 應用程式](../test/how-to-use-microsoft-test-framework-for-cpp.md)
- [使用 Microsoft.VisualStudio.TestTools.CppUnitTestFramework](how-to-use-microsoft-test-framework-for-cpp.md)
- [對機器碼進行偵錯](../debugger/debugging-native-code.md)
- [逐步解說：建立和使用動態連結程式庫 (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [匯入及匯出](/cpp/build/importing-and-exporting)
