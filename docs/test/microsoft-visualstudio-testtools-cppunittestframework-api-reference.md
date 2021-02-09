---
title: Microsoft.VisualStudio.TestTools.CppUnitTestFramework API
description: 本文描述 >microsoft.visualstudio.testtools.cppunittestframework 成員，您可以使用這些成員撰寫以 Microsoft 原生單元測試架構為基礎的 c + + 單元測試。
ms.custom: SEO-VS-2020
ms.date: 09/27/2019
ms.topic: reference
ms.author: corob
manager: jmartens
ms.workload:
- multiple
author: corob-msft
ms.openlocfilehash: 355259f784d496fae574a331382d03d3fbe5bfd6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844524"
---
# <a name="microsoftvisualstudiotesttoolscppunittestframework-api-reference"></a>Microsoft.VisualStudio.TestTools.CppUnitTestFramework API 參考

本主題列出 `Microsoft::VisualStudio::CppUnitTestFramework` 命名空間的公用成員。 您可以使用這些 API 來撰寫以 Microsoft 原生單元測試架構為基礎的 C++ 單元測試。 本主題結尾有[使用範例](#example)。

標頭和程式庫檔案位於 *\<Visual Studio installation folder> \VC\Auxiliary\VS\UnitTest* 下。

標頭和 lib 路徑會自動在原生測試專案中設定。

## <a name="in-this-topic"></a><a name="In_this_topic"></a> 本主題中

[Cppunittest.h。h](#cppUnitTest_h)

- [建立測試類別和方法](#create_test_classes_and_methods)

- [初始化和清除](#Initialize_and_cleanup)

  - [測試方法](#test_methods)

  - [測試類別](#test_classes)

  - [測試模組](#test_modules)

- [建立測試屬性](#create_test_attributes)

  - [測試方法屬性](#test_method_attributes)

  - [測試類別屬性](#test_class_attributes)

  - [測試模組屬性](#test_module_attributes)

  - [預先定義的屬性](#pre_defined_attributes)

    [CppUnitTestAssert.h](#cppUnitTestAssert_h)

  - [一般判斷提示](#general_asserts)

    - [相等](#general_are_equal)

    - [不等於](#general_are_not_equal)

    - [相同](#general_are_same)

    - [不相同](#general_are_not_same)

    - [為 Null](#general_is_null)

    - [不是 Null](#general_is_not_null)

    - [為 True](#general_is_True)

    - [為 False](#general_is_false)

    - [失敗](#general_Fail)

  - [Windows 執行階段判斷提示](#winrt_asserts)

    - [相等](#winrt_are_equal)

    - [相同](#winrt_are_same)

    - [不等於](#winrt_are_not_equal)

    - [不相同](#winrt_are_not_same)

    - [為 Null](#winrt_is_null)

    - [不是 Null](#winrt_is_not_null)

  - [例外狀況判斷提示](#exception_asserts)

    - [預期例外狀況](#expect_exception)

      [CppUnitTestLogger.h](#cppunittestlogger_h)

    - [記錄器](#logger)

    - [ 寫入訊息](#write_message)

  - [使用範例](#example)

## <a name="cppunittesth"></a><a name="cppUnitTest_h"></a> CppUnitTest.h

### <a name="create-test-classes-and-methods"></a><a name="create_test_classes_and_methods"></a> 建立測試類別和方法

```cpp
TEST_CLASS(className)
```

針對每個包含測試方法的類別為必要。 識別 *className* 為測試類別。 `TEST_CLASS` 必須在命名空間範圍中宣告。

```cpp
TEST_METHOD(methodName)
{
    // test method body
}
```

定義 *methodName* 為測試方法。 `TEST_METHOD` 必須在方法的類別範圍中宣告。

### <a name="initialize-and-cleanup"></a><a name="Initialize_and_cleanup"></a> 初始化和清除

#### <a name="test-methods"></a><a name="test_methods"></a> 測試方法

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}
```

定義 *methodName* 為每個測試方法執行之前要執行的方法。 `TEST_METHOD_INITIALIZE` 只能在測試類別中定義一次，且必須在測試類別的範圍中定義。

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}
```

定義 *methodName* 為每個測試方法執行之後要執行的方法。 `TEST_METHOD_CLEANUP` 只能在測試類別中定義一次，且必須在測試類別的範圍中定義。

#### <a name="test-classes"></a><a name="test_classes"></a> 測試類別

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}
```

定義 *methodName* 為每個測試類別建立之前要執行的方法。 `TEST_CLASS_INITIALIZE` 只能在測試類別中定義一次，且必須在測試類別的範圍中定義。

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}
```

定義 *methodName* 為每個測試類別建立之後要執行的方法。 `TEST_CLASS_CLEANUP` 只能在測試類別中定義一次，且必須在測試類別的範圍中定義。

#### <a name="test-modules"></a><a name="test_modules"></a> 測試模組

```cpp
TEST_MODULE_INITIALIZE(methodName)
{
    // module initialization code
}
```

定義載入模組時要執行的方法 *methodName*。 `TEST_MODULE_INITIALIZE` 只能在測試模組中定義一次，且必須在命名空間範圍中宣告。

```cpp
TEST_MODULE_CLEANUP(methodName)
```

定義卸載模組時要執行的方法 *methodName*。 `TEST_MODULE_CLEANUP` 只能在測試模組中定義一次，且必須在命名空間範圍中宣告。

### <a name="create-test-attributes"></a><a name="create_test_attributes"></a> 建立測試屬性

#### <a name="test-method-attributes"></a><a name="test_method_attributes"></a> 測試方法屬性

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

將以一或多個 `TEST_METHOD_ATTRIBUTE` 巨集定義的屬性加入至測試方法 *testMethodName*。

`TEST_METHOD_ATTRIBUTE` 巨集會以名稱 *attributeName* 和值 *attributeValue* 來定義屬性。

#### <a name="test-class-attributes"></a><a name="test_class_attributes"></a> 測試類別屬性

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

新增以一或多個 `TEST_CLASS_ATTRIBUTE` 巨集定義的屬性至測試類別 *testClassName*。

`TEST_CLASS_ATTRIBUTE` 巨集會以名稱 *attributeName* 和值 *attributeValue* 來定義屬性。

#### <a name="test-module-attributes"></a><a name="test_module_attributes"></a> 測試模組屬性

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

新增以一或多個 `TEST_MODULE_ATTRIBUTE` 巨集定義的屬性至測試模組 *testModuleName*。

`TEST_MODULE_ATTRIBUTE` 巨集會以名稱 *attributeName* 和值 *attributeValue* 來定義屬性。

#### <a name="pre-defined-attributes"></a><a name="pre_defined_attributes"></a> 預先定義的屬性

這些預先定義的屬性巨集是提供來為常見案例提供方便性。 它們可以被上述巨集 `TEST_METHOD_ATTRIBUTE` 取代。

```cpp
TEST_OWNER(ownerAlias)
```

以名稱 `Owner` 和 *ownerAlias* 的屬性值定義 `TEST_METHOD_ATTRIBUTE`。

```cpp
TEST_DESCRIPTION(description)
```

以名稱 `Description` 和 *description* 的屬性值定義 `TEST_METHOD_ATTRIBUTE`。

```cpp
TEST_PRIORITY(priority)
```

以名稱 `Priority` 和 *priority* 的屬性值定義 `TEST_METHOD_ATTRIBUTE`。

```cpp
TEST_WORKITEM(workitem)
```

以名稱 `WorkItem` 和 *workItem* 的屬性值定義 `TEST_METHOD_ATTRIBUTE`。

```cpp
TEST_IGNORE()
```

以名稱 `Ignore` 和 `true` 的屬性值定義 `TEST_METHOD_ATTRIBUTE`。

## <a name="cppunittestasserth"></a><a name="cppUnitTestAssert_h"></a> CppUnitTestAssert。h

### <a name="general-asserts"></a><a name="general_asserts"></a> 一般判斷提示

#### <a name="are-equal"></a><a name="general_are_equal"></a> 相等
確認兩個物件相等

```cpp
template<typename T>
static void Assert::AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

確認兩個雙精確度浮點數相等

```cpp
static void Assert::AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

確認兩個浮點數相等

```cpp
static void Assert::AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

確認兩個 char * 字串相等

```cpp
static void Assert::AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

確認兩個 w_char * 字串相等

```cpp
static void Assert::AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-equal"></a><a name="general_are_not_equal"></a> 不相等
確認兩個雙精確度浮點數不相等

```cpp
static void Assert::AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

確認兩個浮點數不相等

```cpp
static void Assert::AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

確認兩個 char * 字串不相等

```cpp
static void Assert::AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

確認兩個 w_char * 字串不相等

```cpp
static void Assert::AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

根據運算子 ==，確認兩個參考不相等。

```cpp
template<typename T>
static void Assert::AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-same"></a><a name="general_are_same"></a> 相同
確認兩個參考會參考相同的物件執行個體 (識別)。

```cpp
template<typename T>
static void Assert::AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-same"></a><a name="general_are_not_same"></a> 不相同
確認兩個參考未參考相同的物件執行個體 (識別)。

```cpp
template<typename T>
static void Assert::AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-null"></a><a name="general_is_null"></a> 為 Null
確認指標為 NULL。

```cpp
template<typename T>
static void Assert::IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-not-null"></a><a name="general_is_not_null"></a> 不是 Null
確認指標不是 NULL

```cpp
template<typename T>
static void Assert::IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-true"></a><a name="general_is_True"></a> 為 True
確認條件為 True

```cpp
static void Assert::IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-false"></a><a name="general_is_false"></a> 為 False
確認條件為 False

```cpp
static void Assert::IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="fail"></a><a name="general_Fail"></a> 失敗
強制測試案例結果為失敗

```cpp
static void Assert::Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

### <a name="windows-runtime-asserts"></a><a name="winrt_asserts"></a> Windows 執行階段判斷提示

#### <a name="are-equal"></a><a name="winrt_are_equal"></a> 相等
確認兩個 Windows 執行階段的指標相等。

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

確認兩個 Platform::String^ 字串相等。

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-same"></a><a name="winrt_are_same"></a> 相同
確認兩個 Windows 執行階段的參考參考相同的物件。

```cpp
template<typename T>
static void Assert::AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-equal"></a><a name="winrt_are_not_equal"></a> 不相等
確認兩個 Windows 執行階段的指標不相等。

```cpp
template<typename T>
static void Assert::AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

確認兩個 Platform::String^ 字串不相等。

```cpp
static void Assert::AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-same"></a><a name="winrt_are_not_same"></a> 不相同
確認兩個 Windows 執行階段參考未參考相同的物件。

```cpp
template<typename T>
static void Assert::AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-null"></a><a name="winrt_is_null"></a> 為 Null
確認 Windows 執行階段指標為 nullptr。

```cpp
template<typename T>
static void Assert::IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-not-null"></a><a name="winrt_is_not_null"></a> 不是 Null
確認 Windows 執行階段指標不是 nullptr。

```cpp
template<typename T>
static void Assert::IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

### <a name="exception-asserts"></a><a name="exception_asserts"></a> 判斷提示例外狀況

#### <a name="expect-exception"></a><a name="expect_exception"></a> 預期例外狀況
確認函式引發例外狀況︰

```cpp
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void Assert::ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

確認函式引發例外狀況︰

```cpp
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void Assert::ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

## <a name="cppunittestloggerh"></a><a name="cppunittestlogger_h"></a> CppUnitTestLogger。h

### <a name="logger"></a><a name="logger"></a> 記錄
記錄器類別包含要寫入至 [輸出視窗] 的靜態方法。

### <a name="write-message"></a><a name="write_message"></a> 寫入訊息
將字串寫入至 [輸出視窗]

```cpp
static void Logger::WriteMessage(const wchar_t* message)
```

```cpp
static void Logger::WriteMessage(const char* message)
```

## <a name="example"></a><a name="example"></a> 範例
此程式碼是 VSCppUnit 的使用範例。 其中包含屬性中繼資料、裝置、使用判斷提示的單元測試及自訂記錄等範例。

```cpp
// USAGE EXAMPLE

#include <CppUnitTest.h>

using namespace Microsoft::VisualStudio::CppUnitTestFramework;

BEGIN_TEST_MODULE_ATTRIBUTE()
    TEST_MODULE_ATTRIBUTE(L"Date", L"2010/6/12")
END_TEST_MODULE_ATTRIBUTE()

TEST_MODULE_INITIALIZE(ModuleInitialize)
{
    Logger::WriteMessage("In Module Initialize");
}

TEST_MODULE_CLEANUP(ModuleCleanup)
{
    Logger::WriteMessage("In Module Cleanup");
}

TEST_CLASS(Class1)
{

public:

    Class1()
    {
        Logger::WriteMessage("In Class1");
    }

    ~Class1()
    {
        Logger::WriteMessage("In ~Class1");
    }

    TEST_CLASS_INITIALIZE(ClassInitialize)
    {
        Logger::WriteMessage("In Class Initialize");
    }

    TEST_CLASS_CLEANUP(ClassCleanup)
    {
        Logger::WriteMessage("In Class Cleanup");
    }

    BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
        TEST_OWNER(L"OwnerName")
        TEST_PRIORITY(1)
    END_TEST_METHOD_ATTRIBUTE()

    TEST_METHOD(Method1)
    {
        Logger::WriteMessage("In Method1");
        Assert::AreEqual(0, 0);
    }

    TEST_METHOD(Method2)
    {
        Assert::Fail(L"Fail");
    }
};
```

## <a name="see-also"></a>另請參閱

- [對程式碼進行單元測試](../test/unit-test-your-code.md)
- [撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp.md)
