---
title: "如何在 Visual Studio 中使用 C++ 的 Boost.Test | Microsoft Docs"
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0710a8-8e8a-4f6e-8415-5ab3eb830079
caps.latest.revision: "14"
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6bfce4aa4153d8f01fa9ef6cd6dc0d4b08eedbc4
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>如何在 Visual Studio 中使用 C++ 的 Boost.Test
在 **Visual Studio 2017 15.5 版**和更新版本中，Boost.Test 已整合到 Visual Studio IDE 作為 [使用 C++ 的桌面開發] 工作負載的元件。 若要將它安裝在您的電腦上，請開啟 Visual Studio 安裝程式，並在工作負載元件清單下尋找 **Boost.Test 配接器**：

![安裝 Boost Test](media/cpp-boost-component.png "安裝 C++ 的 Boost.Test")

## <a name="install-boost"></a>安裝 Boost

 Boost.Test 需要 [Boost](http://www.boost.org/)！ 如果您未安裝 Boost，建議您使用 vcpkg 套件管理員。 

1. 請遵循 [vcpkg：適用於 Windows 的 C++ 套件管理員](/cpp/vcpkg)中的指示安裝 vcpkg (如果目前沒有)。
2. 執行 `vcpkg install boost` 安裝 Boost 程式庫。
3. 執行 `vcpkg integrate install` 命令設定 Visual Studio 和程式庫，並包含 Boost 標頭和二進位檔的路徑。 

## <a name="create-a-project-for-your-tests"></a>建立要測試的專案
在 Visual Studio 2017 15.5 版中，沒有預先設定的測試專案或項目範本可供 Boost.Test 使用。 因此，您必須建立主控台應用程式專案來保存您的測試。 Visual Studio 的未來版本將加入 Boost.Test 的測試範本。 

1. 在**方案總管**中，以滑鼠右鍵按一下方案節點，然後選擇 [新增] | [新增專案]。 
2. 在左窗格中選擇 [Windows 桌面]，然後在中間窗格中選擇 [Windows 主控台應用程式]。 
3. 提供專案名稱，然後按一下 [確定]。 

## <a name="add-include-directives"></a>新增 include 指示詞
在測試的 .cpp 檔中，新增任何需要的 `#include` 指示詞，以便測試程式碼可以看到程式的類型和函式。 一般而言，此程式會在資料夾階層中上移一層。 如果您鍵入 `#include "../"`，IntelliSense 視窗會隨即出現並讓您選取標頭檔的完整路徑。

![新增 #include 指示詞](media/cpp-gtest-includes.png "將 include 指示詞新增至測試的 .cpp 檔")

您必須至少包含具有 `#include <path>/unit_test.hpp` 之 [Boost.Test 的單一標頭變體](http://www.boost.org/doc/libs/1_48_0/libs/test/doc/html/utf/user-guide/usage-variants/single-header-variant.html)，並定義 `BOOST_TEST_MODULE`。 要讓測試可在**測試總管**中被探索到，下列範例便已足夠：

```cpp
#include "stdafx.h"
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp>
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my_boost_test)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual();
    BOOST_CHECK(name == mc.GetName());
}
```

## <a name="write-and-run-tests"></a>撰寫及執行測試
您現在準備好撰寫及執行 Boost Test。 如需測試巨集的資訊，請參閱 [Boost Test Library 文件](http://www.boost.org/doc/libs/1_38_0/libs/test/doc/html/index.html)。 如需使用**測試總管**探索、執行及分組測試的資訊，請參閱[使用測試總管執行單元測試](run-unit-tests-with-test-explorer.md)。

## <a name="see-also"></a>另請參閱
[撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp.md)


  







