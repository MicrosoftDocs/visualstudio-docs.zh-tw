---
title: 如何使用 C++ 的 Boost.Test
description: 使用 Boost.Test 在 Visual Studio 中建立單元測試。
ms.date: 01/29/2020
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 0a1a621c7ee7175d86b2cbcf9a6e2c02c0aecbb3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "76922914"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>如何在 Visual Studio 中使用 C++ 的 Boost.Test

在 Visual Studio 2017 及更高版本中，Boost.Test 測試配接器集成到視覺化工作室 IDE 中。 它是**桌面開發的組成部分，具有C++** 工作負載。

![Boost.Test 的測試配接器](media/cpp-boost-component.png)

若您尚未安裝 [使用 C++ 進行桌面開發]**** 工作負載，請開啟 **Visual Studio 安裝程式**。 選取 [使用 C++ 的桌面開發]**** 工作負載，然後選擇 [修改]**** 按鈕。

## <a name="install-boost"></a>安裝 Boost

Boost.Test 需要 [Boost](https://www.boost.org/)！ 如果您沒有安裝 Boost，我們建議您使用 Vcpkg 包管理器。

1. 按照[Vcpkg 的說明操作：Windows 安裝](/cpp/vcpkg)vcpkg 的C++包管理器（如果您還沒有安裝）。

1. 安裝 Boost.Test 動態或靜態程式庫：

    - 執行 `vcpkg install boost-test` 以安裝 Boost.Test 動態程式庫。

       -或-

    - 執行 `vcpkg install boost-test:x86-windows-static` 以安裝 Boost.Test 靜態程式庫。

1. 執行 `vcpkg integrate install` 設定 Visual Studio 和程式庫，並包含 Boost 標頭和二進位檔的路徑。

您可以選擇如何在 Visual Studio 中配置解決方案中的測試：您可以在被測試專案中包括測試代碼，也可以為測試創建單獨的測試專案。 兩種選擇都有優缺點。

## <a name="add-tests-inside-your-project"></a>在專案內添加測試

在 Visual Studio 2017 版本 15.6 及更高版本中，您可以將用於測試的專案範本添加到專案中。 測試和代碼都位於同一專案中。 您必須創建單獨的組建組態才能生成測試生成。 而且，您需要將測試保留在調試和發佈版本中。

在 Visual Studio 2017 15.5 版中，沒有預先設定的測試專案或項目範本可供 Boost.Test 使用。 使用說明創建和配置單獨的測試專案。

### <a name="create-a-boosttest-item"></a>創建提升.測試項

1. 要為測試創建 *.cpp*檔，請按右鍵**解決方案資源管理器**中的專案節點，然後選擇**Add** > "**添加新專案**"。

1. 在 **"添加新專案"** 對話方塊中，展開**已安裝** > **的可視C++** > **測試**。 選擇 **"提升.測試**"，然後選擇 **"添加"** 以將*Test.cpp*添加到專案中。

   ![Boost.Test 項目範本](media/boost_test_item_template.png)

新的*Test.cpp*檔包含一個示例測試方法。 此檔是您可以包括自己的標頭檔和為應用編寫測試的位置。

測試檔案還使用宏為測試組態定義新的`main`常式。 如果現在生成專案，您將看到 LNK2005 錯誤，例如"_main已在 main.obj 中定義。

### <a name="create-and-update-build-configurations"></a>創建和更新組建組態

1. 要創建測試組態，請在功能表列上選擇 **"生成** > **組態管理員**"。 在 **"組態管理員"** 對話方塊中，打開 **"活動解決方案配置**"下的下拉清單，然後選擇 **"新建**"。 在新**解決方案配置**對話方塊中，輸入名稱，如"調試單元測試"。 在 **"從"調試"中複製設置**，然後選擇 **"確定**"。 **Debug**

1. 從調試和發佈配置中排除測試代碼：在**解決方案資源管理器**中，按右鍵 Test.cpp 並選擇**屬性**。 在 **"屬性頁"** 對話方塊中，在 **"配置"** 下拉清單中選擇 **"所有配置**"。 選擇 **"配置屬性** > **常規"** 並打開 **"從生成中排除**"屬性的下拉清單。 選擇 **"是**"，然後選擇 **"應用"** 以保存更改。

1. 要在調試單元測試配置中包括測試代碼，請在 **"屬性頁"** 對話方塊中，在 **"配置"** 下拉下下拉清單中選擇**調試單元測試**。 在 **"從生成中排除**"屬性中選擇 **"否**"，然後選擇 **"確定"** 以保存更改。

1. 從調試單元測試配置中排除主代碼。 在**解決方案資源管理器**中，按右鍵包含函數`main`的檔並選擇**屬性**。 在 **"屬性頁"** 對話方塊中，在 **"配置**"下拉清單中選擇**調試單元測試**。 選擇 **"配置屬性** > **常規"** 並打開 **"從生成中排除**"屬性的下拉清單。 選擇 **"是**"，然後選擇 **"確定"** 以保存更改。

1. 將解決方案配置設置為**調試單元測試**，然後生成專案以使**測試資源管理器**能夠發現該方法。

只要您創建的配置名稱以"調試"或"釋放"等字開頭，相應的 Boost.Test 庫將自動選取。

項目範本會使用 Boost.Test 的單一標頭變體，但是您可以修改 #include 路徑以使用獨立程式庫變體。 如需詳細資訊，請參閱[新增 include 指示詞](#add-include-directives)。

## <a name="create-a-separate-test-project"></a>創建單獨的測試專案

在許多情況下，使用單獨的專案進行測試會更容易。 您不必為專案創建特殊的測試組態。 或者，從調試和發佈生成中排除測試檔案。

### <a name="to-create-a-separate-test-project"></a>創建單獨的測試專案

1. 在 [方案總管]**** 中，以滑鼠右鍵按一下方案節點，然後選擇 [新增]**** > [新增專案]****。

1. 在"**添加新專案**"對話方塊中，在篩選器下拉清單中選擇**C++** **、Windows**和**主控台**。 選擇**主控台應用**範本，然後選擇 **"下一步**"。

1. 提供專案名稱，然後選擇 [建立]****。

1. 刪除`main` *.cpp*檔中的函數。

1. 如果您使用的是 Boost.Test 的單標題或動態庫版本，請轉到[添加包含指令](#add-include-directives)。 如果使用靜態程式庫版本，則必須執行一些其他配置：

   a. 若要編輯專案檔，請先卸載它。 在**方案總管**中，以滑鼠右鍵按一下專案節點，然後選擇 [卸載專案]****。 然後，以滑鼠右鍵按一下專案節點，選擇 [編輯 <名稱\>.vcxproj]****。

   b. 在 **Globals** 屬性群組中新增兩行，如下所示：

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```

   c. 保存並關閉*\*.vcxproj*檔，然後重新載入專案。

   d. 若要開啟 [屬性頁]****，請以滑鼠右鍵按一下專案節點，選擇 [屬性]****。

   e. 展開**C/C++** > **代碼生成**，然後選擇**運行時庫**。 為偵錯靜態執行階段程式庫選取 **/MTd**，或為版本靜態執行階段程式庫選取 **/MT**。

   f. 展開**連結器** > **系統**。 驗證**子系統**已設置為**主控台**。

   g. 選擇 [確定]**** 關閉屬性頁。

## <a name="add-include-directives"></a>新增 include 指示詞

1. 在 test *.cpp*檔中，添加`#include`任何所需的指令，以使程式的類型和函數對測試代碼可見。 如果您使用的是單獨的測試專案（通常，該程式位於資料夾層次結構中的同級級別）。 如果鍵入 `#include "../"`，即會出現 IntelliSense 視窗，讓您選取標頭檔的完整路徑。

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

您現在準備好撰寫及執行 Boost Test。 有關測試宏的資訊，請參閱[Boost 測試庫文檔](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html)。 如需使用**測試總管**探索、執行及分組測試的資訊，請參閱[使用測試總管執行單元測試](run-unit-tests-with-test-explorer.md)。

## <a name="see-also"></a>另請參閱

- [撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp.md)
