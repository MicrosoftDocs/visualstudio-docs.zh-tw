---
title: 使用適用於 C++ 的 Microsoft 單元測試架構
description: 使用 Microsoft 單元測試框架C++為C++代碼創建單元測試。
ms.date: 01/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 5c8cb794ce7891e74610f1a73164ce403d294925
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75755562"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>在 Visual Studio 中使用適用於 C++ 的 Microsoft 單元測試架構

適用於 C++ 的 Microsoft 單元測試架構預設隨附於 [使用 C++ 的桌面開發]**** 工作負載。

## <a name="to-write-unit-tests-in-a-separate-project"></a><a name="separate_project"></a> 在個別專案中撰寫單元測試

一般而言，您會在程式碼專屬的專案中測試程式碼，且該專案與您要測試的程式碼位於相同的方案中。 若要安裝及設定新的測試專案，請參閱[撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp.md)。

## <a name="to-write-unit-tests-in-the-same-project"></a><a name="same_project"></a>在同一專案中編寫單元測試

在某些情況下 (例如在 DLL 中測試非匯出函式時)，您可能需要在與要欲測試程式相同的專案中建立測試。 若要在相同專案中撰寫單元測試：

1. 修改專案屬性，以包含單元測試所需的標頭和程式庫檔案。

   1. 在"解決方案資源管理器"中，在要測試的專案的快顯功能表上，選擇 **"屬性**"。 專案的屬性視窗便會開啟。

   1. 在"屬性頁"對話方塊中，選擇 **"配置屬性** > **VC+ 目錄**"。

   1. 按一下以下行中的向下箭頭，然後選擇**\<"編輯>**"。 加入這些路徑：

      | 目錄 | 屬性 |
      |-| - |
      | **Include 目錄** | **$(VCInstallDir)Auxiliary\VS\UnitTest\include** |
      | **程式庫目錄** | **$(VCInstallDir)Auxiliary\VS\UnitTest\lib** |

1. 加入 C++ 單元測試檔案：

   - 在 [方案總管]**** 中，以滑鼠右鍵按一下專案節點，然後選擇 [新增]**** > [新增項目]**** > [C++ 檔案 (.cpp)]****。

## <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="object_files"></a> 將測試連結至物件或程式庫檔案

如果被測的代碼不匯出要測試的函數，則可以將輸出 **.obj**或 **.lib**檔添加到測試專案的依賴項。 修改測試專案的屬性，以包括單元測試所需的標頭和庫或目的檔。

1. 在方案總管中，於測試專案的捷徑功能表上，選擇 [屬性]****。 專案的屬性視窗便會開啟。

1. 選擇**配置屬性** > **連結器** > **輸入**頁，然後選擇 **"其他依賴項**"。

   選擇 [編輯]****，然後新增 **.obj** 或 **.lib** 檔案的名稱。 不要使用完整的路徑名稱。

1. 選擇 **"配置屬性** > **連結器** > **常規**"頁，然後選擇 **"其他庫目錄**"。

   選擇 [編輯]****，然後新增 **.obj** 或 **.lib** 檔案的目錄路徑。 該路徑通常是位於受測專案的組建資料夾內。

1. 選擇**配置屬性** > **VC+ 目錄**頁面，然後選擇 **"包括目錄**"。

   選擇 [編輯]****，然後新增受測專案的標頭目錄。

## <a name="write-the-tests"></a>撰寫測試

具有測試類的任何 *.cpp*檔必須包括"CppUnitTest.h"，並且具有`using namespace Microsoft::VisualStudio::CppUnitTestFramework`的 using 語句。 系統已為您設定測試專案。 它也包含命名空間定義，以及 TEST_CLASS 和 TEST_METHOD，以協助您開始進行。 您可以在類和方法宏中修改命名空間名稱和括弧中的名稱。

測試框架定義用於初始化測試模組、類和方法以及測試完成後清理資源的特殊宏。 這些宏生成代碼，用於在首次訪問類或方法之前以及運行最後一個測試之後執行。 如需詳細資訊，請參閱[初始化和清除](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup)。

使用 [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) 類別中的靜態方法來定義測試條件。 使用 [Logger](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) 類別將訊息寫入至 [輸出視窗]****。 將屬性新增至測試方法

## <a name="run-the-tests"></a>執行測試

1. 在 [測試]**** 功能表上，選擇 [Windows]**** > [測試總管]****。

1. 如果並非所有測試在視窗中可見，請通過按右鍵**解決方案資源管理器**中的節點並選擇**生成**或**重建**來生成測試專案。

1. 在**測試資源管理器中**，選擇 **"全部運行**"或選擇要運行的特定測試。 以滑鼠右鍵按一下測試即可顯示其他選項，包括在啟用中斷點的偵錯模式中執行測試。

1. 在 **"輸出視窗**"中，在下拉清單中選擇 **"測試"** 以查看`Logger`由類編寫的消息：

   ![顯示測試訊息的 C++ 輸出視窗](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>定義特徵以啟用群組

您可以在測試方法上定義特徵，從而可以在**測試資源管理器**中對測試進行分類和分組測試。 若要定義特性，請使用 `TEST_METHOD_ATTRIBUTE` 巨集。 例如，若要定義名為 `TEST_MY_TRAIT`的特性：

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

下列預先定義的特徵位於 `CppUnitTest.h` 中。 有關詳細資訊，請參閱[microsoft 單元測試框架，瞭解C++ API 參考](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)。

|巨集|描述|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|使用 TEST_METHOD_ATTRIBUTE 巨集定義特性。|
|`TEST_OWNER(ownerAlias)`|使用預先定義的擁有者特性，指定測試方法的擁有者。|
|`TEST_PRIORITY(priority)`|使用預先定義的優先權特性，將相對優先權指派給測試方法。|

## <a name="see-also"></a>另請參閱

- [快速入門：搭配測試總管進行以測試為導向的開發工作](../test/quick-start-test-driven-development-with-test-explorer.md)
