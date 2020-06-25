---
title: 如何使用 C++ 的 Boost.Test
description: 使用 Boost.Test 在 Visual Studio 中建立單元測試。
ms.date: 01/29/2020
ms.topic: how-to
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 34c593469a586d1314c7ee52f3aeb3ab6faf334c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287268"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>如何在 Visual Studio 中使用 C++ 的 Boost.Test

在 Visual Studio 2017 和更新版本中，提升。測試測試介面卡已整合到 Visual Studio IDE 中。 這是**使用 c + + 進行桌面開發**工作負載的元件。

![Boost.Test 的測試配接器](media/cpp-boost-component.png)

若您尚未安裝 [使用 C++ 進行桌面開發]**** 工作負載，請開啟 **Visual Studio 安裝程式**。 選取 [使用 C++ 的桌面開發]**** 工作負載，然後選擇 [修改]**** 按鈕。

## <a name="install-boost"></a>安裝 Boost

Boost.Test 需要 [Boost](https://www.boost.org/)！ 如果您沒有安裝加速，建議您使用 Vcpkg 套件管理員。

1. 請遵循[Vcpkg：適用于 Windows 的 c + + 套件管理員](/cpp/vcpkg)中的指示來安裝 Vcpkg （如果您還沒有它的話）。

1. 安裝 Boost.Test 動態或靜態程式庫：

    - 執行 `vcpkg install boost-test` 以安裝 Boost.Test 動態程式庫。

       -或-

    - 執行 `vcpkg install boost-test:x86-windows-static` 以安裝 Boost.Test 靜態程式庫。

1. 執行 `vcpkg integrate install` 設定 Visual Studio 和程式庫，並包含 Boost 標頭和二進位檔的路徑。

您可以選擇如何在 Visual Studio 的方案中設定測試：您可以將測試程式碼包含在受測專案中，也可以為測試建立個別的測試專案。 這兩種選擇都有優點和缺點。

## <a name="add-tests-inside-your-project"></a>在專案內加入測試

在 Visual Studio 2017 15.6 版和更新版本中，您可以將測試的專案範本新增至您的專案。 測試和您的程式碼都位於相同的專案中。 您必須建立個別的組建設定，以產生測試組建。 而且，您必須將測試從您的 debug 和 release 組建中排除。

在 Visual Studio 2017 15.5 版中，沒有預先設定的測試專案或項目範本可供 Boost.Test 使用。 使用指示來建立和設定個別的測試專案。

### <a name="create-a-boosttest-item"></a>建立提升的測試專案

1. 若要為您的測試建立 *.cpp*檔案，請以滑鼠右鍵按一下**方案總管**中的專案節點，然後選擇 [**加入**  >  **新專案**]。

1. 在 [**加入新專案**] 對話方塊中，展開 [**已安裝**的  >  **Visual C++**  >  **測試**]。 選取 [**提升**]，然後選擇 [**新增**]，將*測試 .cpp*新增至您的專案。

   ![Boost.Test 項目範本](media/boost_test_item_template.png)

新的*測試 .cpp*檔案包含範例測試方法。 您可以在此檔案中包含您自己的標頭檔，並為您的應用程式撰寫測試。

測試檔案也會使用宏來定義測試設定的新 `main` 常式。 如果您現在建立專案，您會看到 LNK2005 錯誤，例如「已在 main 中定義 _main」。

### <a name="create-and-update-build-configurations"></a>建立和更新組建設定

1. 若要建立測試設定，請在功能表列上，選取 [**組建**  >  **Configuration Manager**]。 在 [ **Configuration Manager** ] 對話方塊中，開啟 [作用中**解決方案**設定] 底下的下拉式清單，然後選擇 [**新增**]。 在 [**新增方案**設定] 對話方塊中，輸入名稱，例如 "Debug run-unittests"。 在 [**複製設定**] 下選取 [ **Debug**]，然後選擇 **[確定]**。

1. 從您的 Debug 和 Release 設定中排除測試程式碼：在**方案總管**中，以滑鼠右鍵按一下 [測試 .cpp]，然後選取 [**屬性**]。 在 [**屬性頁**] 對話方塊中，選取 [設定 **] 下拉式**清單中的 [**所有**設定]。 選取 [設定**屬性**  >  ]**[一般**]，並開啟 [**從組建排除**] 屬性的下拉式清單。 選取 **[是]**，然後選擇 [套用]**以儲存**變更。

1. 若要在您的 Debug Run-unittests 設定中包含測試程式碼，請在 [**屬性頁**]**對話方塊的 [設定] 下拉式**清單中選取 [ **Debug run-unittests** ]。 在 [**從組建排除**] 屬性中選取 [**否**]，然後選擇 **[確定]** 以儲存變更。

1. 從您的 Debug Run-unittests 設定中排除主要程式碼。 在**方案總管**中，以滑鼠右鍵按一下包含您函式的檔案， `main` 然後選取 [**屬性**]。 在 [**屬性頁**] 對話方塊中，選取 [設定 **] 下拉式**清單中的 [ **Debug run-unittests** ]。 選取 [設定**屬性**  >  ]**[一般**]，並開啟 [**從組建排除**] 屬性的下拉式清單。 選取 **[是**]，然後選擇 **[確定]** 以儲存變更。

1. 將 [解決方案設定] 設為 [ **Debug run-unittests**]，然後建立您的專案，讓 [**測試瀏覽器**] 探索方法。

只要您建立的設定名稱是以 "Debug" 或 "Release" 這一字為開頭，就會自動挑選測試程式庫。

項目範本會使用 Boost.Test 的單一標頭變體，但是您可以修改 #include 路徑以使用獨立程式庫變體。 如需詳細資訊，請參閱[新增 include 指示詞](#add-include-directives)。

## <a name="create-a-separate-test-project"></a>建立個別的測試專案

在許多情況下，為您的測試使用個別的專案比較容易。 您不需要為您的專案建立特殊的測試設定。 或者，從 [Debug] 和 [Release build] 排除測試檔案。

### <a name="to-create-a-separate-test-project"></a>若要建立個別的測試專案

1. 在 [方案總管]**** 中，以滑鼠右鍵按一下方案節點，然後選擇 [新增]**** > [新增專案]****。

1. 在 [**新增專案**] 對話方塊中，選擇 [篩選] 下拉式清單中的 [ **c + +**]、[ **Windows**] 和 [**主控台**] 選取 [**主控台應用程式**] 範本，然後選擇 **[下一步]**。

1. 提供專案名稱，然後選擇 [建立]****。

1. 刪除 .cpp 檔案中的函式 `main` 。 *.cpp*

1. 如果您使用的是單一標頭或動態連結程式庫版本的 [提升]，請移至 [加入[include](#add-include-directives)指示詞]。 如果您使用的是靜態程式庫版本，則必須執行一些額外的設定：

   a. 若要編輯專案檔，請先卸載它。 在**方案總管**中，以滑鼠右鍵按一下專案節點，然後選擇 [卸載專案]****。 然後，以滑鼠右鍵按一下專案節點，選擇 [編輯 <名稱\>.vcxproj]****。

   b. 在 **Globals** 屬性群組中新增兩行，如下所示：

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```

   c. 儲存並關閉* \* .vcxproj*檔案，然後重載專案。

   d. 若要開啟 [屬性頁]****，請以滑鼠右鍵按一下專案節點，選擇 [屬性]****。

   e. 展開 [ **c/c + +** 程式  >  **代碼產生**]，然後選取 [執行時間連結**庫**]。 為偵錯靜態執行階段程式庫選取 **/MTd**，或為版本靜態執行階段程式庫選取 **/MT**。

   f. 展開 [**連結器**  >  **系統**]。 確認**子系統**已設定為**主控台**。

   g. 選擇 [確定]**** 關閉屬性頁。

## <a name="add-include-directives"></a>新增 include 指示詞

1. 在您的測試 *.cpp*檔案中，新增任何所需的指示詞， `#include` 讓測試程式碼可以看到您的程式類型和函式。 如果您使用個別的測試專案，則程式通常會在資料夾階層中的同級層級上。 如果鍵入 `#include "../"`，即會出現 IntelliSense 視窗，讓您選取標頭檔的完整路徑。

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

您現在準備好撰寫及執行 Boost Test。 如需測試宏的相關資訊，請參閱[提升測試程式庫檔](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html)。 如需使用**測試總管**探索、執行及分組測試的資訊，請參閱[使用測試總管執行單元測試](run-unit-tests-with-test-explorer.md)。

## <a name="see-also"></a>另請參閱

- [撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp.md)
