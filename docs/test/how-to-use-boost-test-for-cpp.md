---
title: 如何在 Visual Studio 中使用 C++ 的 Boost.Test
ms.date: 01/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: eebefa7b4033de5acec313e241d13cddab7120fa
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2018
ms.locfileid: "39380446"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>如何在 Visual Studio 中使用 C++ 的 Boost.Test

在 **Visual Studio 2017 15.5 版**和更新版本中，Boost.Test 測試配接器已整合至 Visual Studio IDE 作為**使用 C++ 的桌面開發**工作負載的元件。

![Boost.Test 的測試配接器](media/cpp-boost-component.png)

如未安裝**使用 C++ 的桌面開發**工作負載，請開啟 **Visual Studio 安裝程式**並選取 [修改]。 選取 [使用 C++ 的桌面開發] 工作負載，然後選擇 [修改] 按鈕。

## <a name="install-boost"></a>安裝 Boost

Boost.Test 需要 [Boost](http://www.boost.org/)！ 如果您未安裝 Boost，建議您使用 vcpkg 套件管理員。

1. 請遵循 [Vcpkg：適用於 Windows 的 C++ 套件管理員](/cpp/vcpkg)中的指示安裝 vcpkg (如果目前沒有)。

1. 安裝 Boost.Test 動態或靜態程式庫：

    - 執行 **vcpkg install boost-test** 以安裝 Boost.Test 動態程式庫。

       -或-

    - 執行 **vcpkg install boost-test:x86-windows-static** 以安裝 Boost.Test 靜態程式庫。

1. 執行 **vcpkg integrate install** 以設定 Visual Studio 和程式庫，並包含 Boost 標頭和二進位檔的路徑。

## <a name="add-the-item-template-visual-studio-2017-version-156-and-later"></a>加入項目範本 (Visual Studio 2017 15.6 版和更新版本)

1. 若要針對您的測試建立 *.cpp* 檔案，請在 [方案總管] 中，以滑鼠右鍵按一下專案節點，然後選擇 [新增項目]。

   ![Boost.Test 項目範本](media/boost_test_item_template.png)

1. 新的檔案包含範例測試方法。 建置您的專案，以便讓 [測試總管] 來探索方法。

項目範本會使用 Boost.Test 的單一標頭變體，但是您可以修改 #include 路徑以使用獨立程式庫變體。 如需詳細資訊，請參閱[新增 include 指示詞](#add-include-directives)。

## <a name="create-a-test-project-visual-studio-2017-version-155"></a>建立測試專案 (Visual Studio 2017 15.5 版)

在 Visual Studio 2017 15.5 版中，沒有預先設定的測試專案或項目範本可供 Boost.Test 使用。 因此，您必須建立並設定主控台應用程式專案來保存您的測試。

1. 在 [方案總管] 中，以滑鼠右鍵按一下方案節點，然後選擇 [新增] > [新增專案]。

1. 在左窗格中選擇 [Visual C++] > [Windows 桌面]，然後選擇 [Windows 主控台應用程式] 範本。

1. 提供專案名稱，然後選擇 [確定]。

1. 刪除 *.cpp* 檔案中的 `main` 函式。

1. 如果您是使用 Boost.Test 的單一標頭或動態程式庫版本，請移至[新增 include 指示詞](#add-include-directives)。 如果您是使用靜態程式庫版本，則必須執行一些額外的設定：

   a. 若要編輯專案檔，請先卸載它。 在**方案總管**中，以滑鼠右鍵按一下專案節點，然後選擇 [卸載專案]。 然後，以滑鼠右鍵按一下專案節點，選擇 [編輯 <名稱\>.vcxproj]。

   b. 在 **Globals** 屬性群組中新增兩行，如下所示：

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```
   c.  儲存並關閉 *\*.vcxproj* 檔案，然後重新載入專案。

   d. 若要開啟 [屬性頁]，請以滑鼠右鍵按一下專案節點，選擇 [屬性]。

   d. 展開 [C/C++] > [程式碼產生]，然後選取 [執行階段程式庫]。 為偵錯靜態執行階段程式庫選取 **/MTd**，或為版本靜態執行階段程式庫選取 **/MT**。

   f. 展開 [連結器] > [系統]。 確認 [子系統] 設為 [主控台]。

   g. 選擇 [確定] 關閉屬性頁。

## <a name="add-include-directives"></a>新增 include 指示詞

1. 在測試的 *.cpp* 檔中，新增任何需要的 `#include` 指示詞，以便測試程式碼可以看到程式的類型和函式。 一般而言，此程式會在資料夾階層中上移一層。 如果鍵入 `#include "../"`，即會出現 IntelliSense 視窗，讓您選取標頭檔的完整路徑。

   ![新增 #include 指示詞](media/cpp-gtest-includes.png)

   您可以使用獨立程式庫搭配：

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   或者，使用單一標頭版本搭配：

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   然後定義 `BOOST_TEST_MODULE`。

要讓測試可在**測試總管**中被探索到，下列範例便已足夠：

```cpp
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp\> //single-header
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my_boost_test)
{
    std::string expected_value = "Bill";

    // assume MyClass is defined in MyClass.h
    // and get_value() has public accessibility
    MyClass mc;
    BOOST_CHECK(expected_value == mc.get_value());
}
```

## <a name="write-and-run-tests"></a>撰寫及執行測試

您現在準備好撰寫及執行 Boost Test。 如需測試巨集的資訊，請參閱 [Boost Test Library 文件](http://www.boost.org/doc/libs/release/libs/test/doc/html/index.html)。 如需使用**測試總管**探索、執行及分組測試的資訊，請參閱[使用測試總管執行單元測試](run-unit-tests-with-test-explorer.md)。

## <a name="see-also"></a>另請參閱

- [撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp.md)
