---
title: 使用 Microsoft.VisualStudio.TestTools.CppUnitTestFramework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: d1ac9188-d79f-407e-9f3a-80dbefa66317
caps.latest.revision: 10
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c561555df40bc02c3c9f3090ee1de4c0f329bcdc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657177"
---
# <a name="using-microsoftvisualstudiotesttoolscppunittestframework"></a>使用 Microsoft.VisualStudio.TestTools.CppUnitTestFramework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題列出 `Microsoft::VisualStudio::CppUnitTestFramework` 命名空間的公用成員。

 標頭檔位於  _>visualstudio2012 [x86] InstallFolder_**\VC\UnitTest\include** 資料夾中。

 Lib 檔案位於  _>visualstudio2012 [x86] InstallFolder_**\VC\UnitTest\lib** 資料夾中。

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> 本主題中
 [Cppunittest.h。h](#BKMK_CppUnitTest_h)

- [建立測試類別和方法](#BKMK_Create_test_classes_and_methods)

- [初始化和清除](#BKMK_Initialize_and_cleanup)

  - [測試方法](#BKMK_Test_methods)

  - [測試類別](#BKMK_Test_classes)

  - [測試模組](#BKMK_Test_modules)

- [建立測試屬性](#BKMK_Create_test_attributes)

  - [測試方法屬性](#BKMK_Test_method_attributes)

  - [測試類別屬性](#BKMK_Test_class_attributes)

  - [測試模組屬性](#BKMK_Test_module_attributes)

  - [預先定義的屬性](#BKMK_Pre_defined_attributes)

    [CppUnitTestAssert.h](#BKMK_CppUnitTestAssert_h)

  - [一般判斷提示](#BKMK_General_Asserts)

    - [相等](#BKMK_General_Are_Equal)

    - [不等於](#BKMK_General_Are_Not_Equal)

    - [相同](#BKMK_General_Are_Same)

    - [不相同](#BKMK_General_Are_Not_Same)

    - [為 Null](#BKMK_General_Is_Null)

    - [不是 Null](#BKMK_General_Is_Not_Null)

    - [為 True](#BKMK_General_Is_True)

    - [為 False](#BKMK_General_Is_False)

    - [失敗](#BKMK_General_Fail)

  - [Windows 執行階段判斷提示](#BKMK_WinRT_Asserts)

    - [相等](#BKMK_WinRT_Are_Equal)

    - [相同](#BKMK_WinRT_Are_Same)

    - [不等於](#BKMK_WinRT_Are_Not_Equal)

    - [不相同](#BKMK_WinRT_Are_Not_Same)

    - [為 Null](#BKMK_WinRT_Is_Null)

    - [不是 Null](#BKMK_WinRT_Is_Not_Null)

  - [例外狀況判斷提示](#BKMK_Exception_Asserts)

    - [預期例外狀況](#BKMK_Expect_Exception)

      [CppUnitTestLogger.h](#BKMK_CppUnitTestLogger_h)

    - [記錄器](#BKMK_Logger)

    - [寫入訊息](#BKMK_Write_Message)

## <a name="cppunittesth"></a><a name="BKMK_CppUnitTest_h"></a> CppUnitTest.h

### <a name="create-test-classes-and-methods"></a><a name="BKMK_Create_test_classes_and_methods"></a> 建立測試類別和方法

```cpp
TEST_CLASS(className)
```

 針對每個包含測試方法的類別為必要。 識別 *className* 為測試類別。 `TEST_CLASS` 必須在名稱空間範圍內宣告。

```cpp
TEST_METHOD(methodName)
{
    // test method body
}

```

 定義 *methodName* 為測試方法。 `TEST_METHOD` 必須在方法的類別範圍中宣告。

### <a name="initialize-and-cleanup"></a><a name="BKMK_Initialize_and_cleanup"></a> 初始化和清除

#### <a name="test-methods"></a><a name="BKMK_Test_methods"></a> 測試方法

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}

```

 定義 *methodName* 為每個測試方法執行之前要執行的方法。 `TEST_METHOD_INITIALIZE` 只能在測試類別中定義一次，且必須在測試類別中定義。

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}

```

 定義 *methodName* 為每個測試方法執行之後要執行的方法。 `TEST_METHOD_CLEANUP` 只能在測試類別中定義一次，且必須在測試類別的範圍中定義。

#### <a name="test-classes"></a><a name="BKMK_Test_classes"></a> 測試類別

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}

```

 定義 *methodName* 為每個測試類別建立之後要執行的方法。 `TEST_CLASS_INITIALIZE` 只能在測試類別中定義一次，且必須在測試類別的範圍中定義。

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}

```

 定義 *methodName* 為每個測試類別建立之後要執行的方法。 `TEST_CLASS_CLEANUP` 只能在測試類別中定義一次，且必須在測試類別的範圍中定義。

#### <a name="test-modules"></a><a name="BKMK_Test_modules"></a> 測試模組

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

### <a name="create-test-attributes"></a><a name="BKMK_Create_test_attributes"></a> 建立測試屬性

#### <a name="test-method-attributes"></a><a name="BKMK_Test_method_attributes"></a> 測試方法屬性

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

 新增以一或多個 `TEST_METHOD_ATTRIBUTE` 巨集定義的屬性至測試方法 *testClassName*。

 `TEST_METHOD_ATTRIBUTE` 巨集會以名稱 *attributeName* 和值 *attributeValue* 來定義屬性。

#### <a name="test-class-attributes"></a><a name="BKMK_Test_class_attributes"></a> 測試類別屬性

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

 新增以一或多個 `TEST_CLASS_ATTRIBUTE` 巨集定義的屬性至測試類別 *testClassName*。

 `TEST_CLASS_ATTRIBUTE` 巨集會以名稱 *attributeName* 和值 *attributeValue* 來定義屬性。

#### <a name="test-module-attributes"></a><a name="BKMK_Test_module_attributes"></a> 測試模組屬性

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

 新增以一或多個 `TEST_MODULE_ATTRIBUTE` 巨集定義的屬性至測試模組 *testModuleName*。

 `TEST_MODULE_ATTRIBUTE` 巨集會以名稱 *attributeName* 和值 *attributeValue* 來定義屬性。

#### <a name="pre-defined-attributes"></a><a name="BKMK_Pre_defined_attributes"></a> 預先定義的屬性
 這些預先定義的屬性巨集可以由巨集 `TEST_METHOD_ATTRIBUTE`、`TEST_CLASS_ATTRIBUTE` 或 `TEST_MODULE_ATTRIBUTE` 所取代，如上文所述。

```cpp
TEST_OWNER(ownerAlias)
```

 以名稱 `Owner` 和 *ownerAlias* 的屬性值定義屬性。

```cpp
TEST_DESCRIPTION(description)
```

 以名稱 `Description` 和 *description* 的屬性值來定義屬性。

```cpp
TEST_PRIORITY(priority)
```

 以名稱 `Priority` 和 *priority* 的屬性值來定義屬性。

```cpp
TEST_WORKITEM(workitem)
```

 以名稱`WorkItem` 和 *workItem* 的屬性值來定義屬性。

```cpp
TEST_IGNORE()
```

 以名稱 `Ignore` 和 `true` 的屬性值來定義屬性。

## <a name="cppunittestasserth"></a><a name="BKMK_CppUnitTestAssert_h"></a> CppUnitTestAssert。h

### <a name="general-asserts"></a><a name="BKMK_General_Asserts"></a> 一般判斷提示

#### <a name="are-equal"></a><a name="BKMK_General_Are_Equal"></a> 相等
 確認兩個物件相等

```cpp
template<typename T>
static void AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 確認兩個雙精確度浮點數相等

```cpp
static void AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 確認兩個浮點數相等

```cpp
static void AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 確認兩個 char * 字串相等

```cpp
static void AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 確認兩個 w_char * 字串相等

```cpp
static void AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-equal"></a><a name="BKMK_General_Are_Not_Equal"></a> 不相等
 確認兩個雙精確度浮點數不相等

```cpp
static void AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 確認兩個浮點數不相等

```cpp
static void AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 確認兩個 char * 字串不相等

```cpp
static void AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 確認兩個 w_char * 字串不相等

```cpp
static void AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 根據運算子 ==，確認兩個參考不相等。

```cpp
template<typename T>
static void AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-same"></a><a name="BKMK_General_Are_Same"></a> 相同
 確認兩個參考會參考相同的物件執行個體 (識別)。

```cpp
template<typename T>
static void AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-same"></a><a name="BKMK_General_Are_Not_Same"></a> 不相同
 確認兩個參考未參考相同的物件執行個體 (識別)。

```cpp
template<typename T>
static void AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-null"></a><a name="BKMK_General_Is_Null"></a> 為 Null
 確認指標為 NULL。

```cpp
template<typename T>
static void IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-not-null"></a><a name="BKMK_General_Is_Not_Null"></a> 不是 Null
 確認指標不是 NULL

```cpp
template<typename T>
static void IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-true"></a><a name="BKMK_General_Is_True"></a> 為 True
 確認條件為 True

```cpp
static void IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-false"></a><a name="BKMK_General_Is_False"></a> 為 False
 確認條件為 False

```cpp
static void IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="fail"></a><a name="BKMK_General_Fail"></a> 失敗
 強制測試案例結果為失敗

```cpp
static void Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

### <a name="windows-runtime-asserts"></a><a name="BKMK_WinRT_Asserts"></a> Windows 執行階段判斷提示

#### <a name="are-equal"></a><a name="BKMK_WinRT_Are_Equal"></a> 相等
 確認兩個 Windows 執行階段的指標相等。

```
template<typename T>
static void AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 確認兩個 Platform::String^ 字串相等。

```
template<typename T>
static void AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-same"></a><a name="BKMK_WinRT_Are_Same"></a> 相同
 確認兩個 Windows 執行階段的參考參考相同的物件。

```
template<typename T>
static void AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-equal"></a><a name="BKMK_WinRT_Are_Not_Equal"></a> 不相等
 確認兩個 Windows 執行階段的指標不相等。

```
template<typename T>
static void AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 確認兩個 Platform::String^ 字串不相等。

```
static void AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-same"></a><a name="BKMK_WinRT_Are_Not_Same"></a> 不相同
 確認兩個 Windows 執行階段參考未參考相同的物件。

```
template<typename T>
static void AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-null"></a><a name="BKMK_WinRT_Is_Null"></a> 為 Null
 確認 Windows 執行階段指標為 nullptr。

```
template<typename T>
static void IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-not-null"></a><a name="BKMK_WinRT_Is_Not_Null"></a> 不是 Null
 確認 Windows 執行階段指標不是 nullptr。

```
template<typename T>
static void IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

### <a name="exception-asserts"></a><a name="BKMK_Exception_Asserts"></a> 判斷提示例外狀況

#### <a name="expect-exception"></a><a name="BKMK_Expect_Exception"></a> 預期例外狀況
 確認函式引發例外狀況︰

```
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

 確認函式引發例外狀況︰

```
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

## <a name="cppunittestloggerh"></a><a name="BKMK_CppUnitTestLogger_h"></a> CppUnitTestLogger。h

### <a name="logger"></a><a name="BKMK_Logger"></a> 記錄
 記錄器類別包含要寫入的靜態方法

```
class Logger
```

### <a name="write-message"></a><a name="BKMK_Write_Message"></a> 寫入訊息

```
static void
Logger::WriteMessage(const wchar_t* message)
```

```
static void
Logger::WriteMessage(const char* message)
```

## <a name="example"></a>範例
 此程式碼是範例

```
////////////////////////////////////////////////////////////
/* USAGE EXAMPLE
// The following is an example of VSCppUnit usage.
// It includes examples of attribute metadata, fixtures,
// unit tests with assertions, and custom logging.

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
 對程式碼單元測試[程式碼](../test/unit-test-your-code.md)[單元測試使用 Test Explorer](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c) [將單元測試新增至現有的 c + + 應用程式](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)
