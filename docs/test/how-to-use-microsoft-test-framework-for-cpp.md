---
title: 使用適用於 C++ 的 Microsoft 單元測試架構
ms.date: 11/15/2017
ms.topic: conceptual
ms.author: mblome
manager: jillfra
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: f5ab27f8f10cb7221ce85bd29df13e446253b8a8
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2019
ms.locfileid: "58324905"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>在 Visual Studio 中使用適用於 C++ 的 Microsoft 單元測試架構

適用於 C++ 的 Microsoft 單元測試架構預設隨附於 [使用 C++ 的桌面開發] 工作負載。

##  <a name="separate_project"></a> 在個別專案中撰寫單元測試

一般而言，您會在程式碼專屬的專案中測試程式碼，且該專案與您要測試的程式碼位於相同的方案中。 若要安裝及設定新的測試專案，請參閱[撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp.md)。

##  <a name="same_project"></a> 在相同專案中撰寫單元測試

在某些情況下 (例如在 DLL 中測試非匯出函式時)，您可能需要在與要測試之程式相同的專案中建立測試。 若要在相同專案中撰寫單元測試：

1. 修改專案屬性，以包含單元測試所需的標頭和程式庫檔案。

   1. 在 [方案總管] 中，以滑鼠右鍵按一下您要測試之程式的專案節點，然後選擇 [屬性] > [組態屬性] > [VC++ 目錄]。

   2. 按一下下列資料列中的向下箭號，然後選擇 [\<編輯>]：


      | Directory | 屬性 |
      |-| - |
      | **Include 目錄** | **$(VCInstallDir)UnitTest\include;$(IncludePath)** |
      | **程式庫目錄** | **$(VCInstallDir)UnitTest\lib;$(LibraryPath)** |


2. 加入 C++ 單元測試檔案：

   -   在 [方案總管] 中，以滑鼠右鍵按一下專案節點，然後選擇 [新增] > [新增項目] > [C++ 單元測試]。

## <a name="write-the-tests"></a>撰寫測試

使用測試類別的任何 *.cpp* 檔都必須包含 "CppUnitTest.h"，並具有 `using namespace Microsoft::VisualStudio::CppUnitTestFramework` 的 using 陳述式。 系統已為您設定測試專案。 它也包含命名空間定義，以及 TEST_CLASS 和 TEST_METHOD，以協助您開始進行。 您可以修改命名空間名稱，以及類別和方法巨集中以括弧括住的名稱。

已定義特殊巨集來初始化測試模組、類別和方法，以及在完成測試之後清除資源。 這些巨集會產生程式碼，在第一次存取類別或方法之前執行，以及在最後一個測試執行之後執行。 如需詳細資訊，請參閱[初始化和清除](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup)。

使用 [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) 類別中的靜態方法來定義測試條件。 使用 [Logger](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) 類別將訊息寫入至 [輸出視窗]。 將屬性新增至測試方法

## <a name="run-the-tests"></a>執行測試

1. 在 [測試] 功能表上，選擇 [Windows] > [測試總管]。
2. 如果視窗中未顯示您所有的測試，請建置測試專案，方法是在**方案總管**中，以滑鼠右鍵按一下其節點，然後選擇 [建置] 或 [重建]。

3. 在 [測試總管] 中，選擇 [全部執行]，或選取您要執行的特定測試。 以滑鼠右鍵按一下測試即可顯示其他選項，包括在啟用中斷點的偵錯模式中執行測試。
4. 在 [輸出視窗] 的下拉式清單中，選擇 [測試]，以檢視由 `Logger` 類別寫出的訊息：

   ![顯示測試訊息的 C++ 輸出視窗](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>定義特徵以啟用群組

您可以在測試方法上定義特徵，以便您分類及分組**測試總管**中的測試。 若要定義特性，請使用 `TEST_METHOD_ATTRIBUTE` 巨集。 例如，若要定義名為 `TEST_MY_TRAIT`的特性：

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

下列預先定義的特徵位於 `CppUnitTest.h` 中。 如需詳細資訊，請參閱[適用於 C++ 的 Microsoft 單元測試架構 API 參考](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)。

|巨集|說明|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|使用 TEST_METHOD_ATTRIBUTE 巨集定義特性。|
|`TEST_OWNER(ownerAlias)`|使用預先定義的擁有者特性，指定測試方法的擁有者。|
|`TEST_PRIORITY(priority)`|使用預先定義的優先權特性，將相對優先權指派給測試方法。|

## <a name="see-also"></a>另請參閱

- [快速入門：搭配 [測試總管] 進行以測試為導向的開發工作](../test/quick-start-test-driven-development-with-test-explorer.md)
