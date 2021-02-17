---
title: 使用適用於 C++ 的 Microsoft 單元測試架構
description: 使用適用于 c + + 的 Microsoft 單元測試架構來建立 c + + 程式碼的單元測試。
ms.date: 02/16/2021
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: a76c6ac83956cd1e6514ff958278d0b4cbcf0d2f
ms.sourcegitcommit: cc8547eb211c43b67b8123d1211b80b5642e3b18
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/17/2021
ms.locfileid: "100563430"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>在 Visual Studio 中使用適用於 C++ 的 Microsoft 單元測試架構

適用於 C++ 的 Microsoft 單元測試架構預設隨附於 [使用 C++ 的桌面開發] 工作負載。

## <a name="to-write-unit-tests-in-a-separate-project"></a><a name="separate_project"></a> 在個別專案中撰寫單元測試

一般而言，您會在程式碼專屬的專案中測試程式碼，且該專案與您要測試的程式碼位於相同的方案中。 若要安裝及設定新的測試專案，請參閱[撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp.md)。

## <a name="to-write-unit-tests-in-the-same-project"></a><a name="same_project"></a> 若要在相同專案中撰寫單元測試

在某些情況下 (例如在 DLL 中測試非匯出函式時)，您可能需要在與要欲測試程式相同的專案中建立測試。 若要在相同專案中撰寫單元測試：

1. 修改專案屬性，以包含單元測試所需的標頭和程式庫檔案。

   1. 在方案總管中，在您要測試之專案的快捷方式功能表上，選擇 [ **屬性**]。 專案的屬性視窗便會開啟。

   1. 在 [屬性頁] 對話方塊中，選取 [設定 **屬性**  >  **VC + + 目錄**]。

   1. 選取下列資料列中的向下箭號，然後選擇 **\<Edit>** 。 加入這些路徑：

      | 目錄 | 屬性 |
      |-| - |
      | **包含目錄** | **$(VCInstallDir)Auxiliary\VS\UnitTest\include** |
      | **程式庫目錄** | **$(VCInstallDir)Auxiliary\VS\UnitTest\lib** |

1. 加入 C++ 單元測試檔案：

   1. 在 **方案總管** 中，以滑鼠右鍵按一下專案節點，然後選擇 [**加入**  >  **新專案**]。

   1. 在 [ **加入新專案** ] 對話方塊中，選取 [  **c + + 檔案 ( .cpp)**，為它指定適當的名稱，然後選擇 [ **加入**]。

## <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="object_files"></a> 將測試連結至物件或程式庫檔案

如果受測程式碼不會匯出您要測試的函式，您可以將輸出 *.obj* 或 *.lib* 檔加入至測試專案的相依性。 修改測試專案的屬性，以包含單元測試所需的標頭和程式庫或物件檔案。

1. 在方案總管中，於測試專案的捷徑功能表上，選擇 [屬性]。 專案的屬性視窗便會開啟。

1. 選取 [設定 **屬性**  >  **連結器**  >  **輸入**] 頁面，然後選取 [其他相依性 **]**。

   選擇 [編輯]，然後新增 *.obj* 或 *.lib* 檔案的名稱。 請勿使用完整路徑名稱。

1. 選取 [設定 **屬性**  >  **連結器**  >  **一般**] 頁面，然後選取 [**其他程式庫目錄**]。

   選擇 [編輯]，然後新增 *.obj* 或 *.lib* 檔案的目錄路徑。 該路徑通常是位於受測專案的組建資料夾內。

1. 選取 [設定 **屬性**  >  **VC + + 目錄**] 頁面，然後選取 [**包含目錄**]。

   選擇 [編輯]，然後新增受測專案的標頭目錄。

## <a name="write-the-tests"></a>撰寫測試

具有測試類別的任何 *.cpp* 檔案都必須包含 "cppunittest.h"，而且具有的 using 語句 `using namespace Microsoft::VisualStudio::CppUnitTestFramework` 。 系統已為您設定測試專案。 它也包含命名空間定義，以及 TEST_CLASS 和 TEST_METHOD，以協助您開始進行。 您可以在類別和方法宏的括弧中修改命名空間名稱和名稱。

測試架構會定義特殊宏來初始化測試模組、類別和方法，以及在測試完成後清除資源。 這些宏會產生程式碼，以在第一次存取類別或方法之前，以及在最後一個測試執行之後執行。 如需詳細資訊，請參閱[初始化和清除](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup)。

使用 [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) 類別中的靜態方法來定義測試條件。 使用 [Logger](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) 類別將訊息寫入至 [輸出視窗]。 將屬性新增至測試方法

## <a name="run-the-tests"></a>執行測試

1. 在 [測試] 功能表上，選擇 [Windows] > [測試總管]。

1. 如果未在視窗中顯示所有測試，請在 **方案總管** 中以滑鼠右鍵按一下其節點，然後選擇 [ **建立** ] 或 [ **重建**]，以建立測試專案。

1. 在 [ **測試瀏覽器**] 中，選擇 [ **全部執行**]，或選取您想要執行的特定測試。 以滑鼠右鍵按一下測試即可顯示其他選項，包括在啟用中斷點的偵錯模式中執行測試。

1. 在 [ **輸出視窗** 選擇下拉式清單中的 [ **測試** ]，以查看由類別寫出的訊息 `Logger` ：

   ![顯示測試訊息的 C++ 輸出視窗](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>定義特徵以啟用群組

您可以在測試方法上定義特性，讓您可以在 **Test Explorer** 中分類和分組測試。 若要定義特性，請使用 `TEST_METHOD_ATTRIBUTE` 巨集。 例如，若要定義名為 `TEST_MY_TRAIT`的特性：

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

若要在單元測試中使用定義的特性：

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
    TEST_OWNER(L"OwnerName")
    TEST_PRIORITY(1)
    TEST_MY_TRAIT(L"thisTraitValue")
END_TEST_METHOD_ATTRIBUTE()

TEST_METHOD(Method1)
{
    Logger::WriteMessage("In Method1");
    Assert::AreEqual(0, 0);
}
```

### <a name="c-trait-attribute-macros"></a>C++ 特性屬性巨集

中找到下列預先定義的特性 *`CppUnitTest.h`* 。 如需詳細資訊，請參閱 [適用于 c + + 的 Microsoft 單元測試架構 API 參考](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)。

|巨集|描述|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|使用 TEST_METHOD_ATTRIBUTE 巨集定義特性。|
|`TEST_OWNER(ownerAlias)`|使用預先定義的擁有者特性，指定測試方法的擁有者。|
|`TEST_PRIORITY(priority)`|使用預先定義的優先權特性，將相對優先權指派給測試方法。|

## <a name="see-also"></a>另請參閱

- [快速入門：搭配測試總管進行以測試為導向的開發工作](../test/quick-start-test-driven-development-with-test-explorer.md)
