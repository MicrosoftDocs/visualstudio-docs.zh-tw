---
title: "屬性詞彙 | Microsoft IntelliTest 開發人員測試工具 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Attribute glossary
ms.assetid: 557C7869-48BE-4B82-9563-1FF356ABACDB
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.openlocfilehash: 71f8adb78c594b6558d570bf79b7535a7517ddbe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="attribute-glossary"></a>屬性字彙

## <a name="attributes-by-namespace"></a>依命名空間分類的屬性

* **Microsoft.Pex.Framework**
  * [PexAssumeNotNull](#pexassumenotnull)
  * [PexClass](#pexclass)
  * [PexGenericArguments](#pexgenericarguments)
  * [PexMethod](#pexmethod)
     - [PexExplorationAttributeBase](#pexexplorationattributebase)<p />

* **Microsoft.Pex.Framework.Settings**
  * [PexAssemblySettings](#pexassemblysettings)<p />

* **Microsoft.Pex.Framework.Instrumentation**
  * [PexAssemblyUnderTest](#pexassemblyundertest)
  * [PexInstrumentAssembly](#pexinstrumentassemblyattribute)<p />

* **Microsoft.Pex.Framework.Using**
  * [PexUseType](#pexusetype)<p />

* **Microsoft.Pex.Framework.Validation**
  * [PexAllowedException](#pexallowedexception)
  * [PexAllowedExceptionFromAssembly](#pexallowedexceptionfromassembly)
  * [PexAllowedExceptionFromType](#pexallowedexceptionfromtype)
  * [PexAllowedExceptionFromTypeUnderTest](#pexallowedexceptionfromtypeundertest)

<a name="pexassumenotnull"></a>
## <a name="pexassumenotnull"></a>PexAssumeNotNull

此屬性會判斷提示受控管的值不得為 **null**。 它可以附加至：

* 參數化測試方法的**參數**

  ```
  // assume foo is not null
  [PexMethod]
  public void SomeTest([PexAssumeNotNull]IFoo foo, ...) {}
  ```

* **欄位**

  ```
  public class Foo {
     // this field should not be null
     [PexAssumeNotNull]
     public object Bar;
  }
  ```

* **類型**

  ```
  // never consider null for Foo types
  [PexAssumeNotNull]
  public class Foo {}
  ```

它也可以附加至測試組件、測試物件或測試方法。在此情況下，第一個引數必須指出套用假設的欄位或類型。 屬性套用至類型時，會套用至具有此正式類型的所有欄位。

<a name="pexclass"></a>
## <a name="pexclass"></a>PexClass

此屬性會標示包含「探索」的類別。 它相當於 MSTest **TestClassAttribute** (或 NUnit **TestFixtureAttribute**)。 這是一個選擇性的屬性。

使用 [PexClass](#pexclass) 所標示的類別必須是「預設可建構的」：

* 公開匯出的類型
* 預設建構函式
* 非抽象

如果類別不符合這些需求，則會報告錯誤，而且探索會失敗。

也強烈建議將這些類別設為**部分**，讓 IntelliTest 可以產生為類別一部分但在不同檔案中的新測試。 這種方法因[可見度](input-generation.md#visibility)而解決許多問題，而且是 C# 中的一般技術。

**其他套件和分類**：

```
[TestClass] // MSTest test fixture attribute
[PexClass(Suite = "checkin")] // fixture attribute
public partial class MyTests { ... }
```

**指定受測類型**：

```
[PexClass(typeof(Foo))] // this is a test for Foo
public partial class FooTest { ... }
```

此類別可能會包含使用 [PexMethod](#pexmethod) 註解的方法。 IntelliTest 也了解[設定和卸除方法](test-generation.md#setup-teardown)。

<a name="pexgenericarguments"></a>
## <a name="pexgenericarguments"></a>PexGenericArguments

此屬性提供用於具現化[泛型參數化單元測試](test-generation.md#generic-parameterized)的類型 Tuple。

<a name="pexmethod"></a>
## <a name="pexmethod"></a>PexMethod

此屬性將方法標示為[參數化單元測試](test-generation.md#parameterized-unit-testing)。
此方法必須位在使用 [PexClass](#pexclass) 屬性所標示的類別內。

IntelliTest 會產生傳統的無參數測試，以使用不同的參數來呼叫[參數化單元測試](test-generation.md#parameterized-unit-testing)。

參數化單元測試：

* 必須是執行個體方法
* 對根據[設定瀑布圖](settings-waterfall.md)放入已產生測試的測試類別，必須是[可見](input-generation.md#visibility)
* 可以接受任意數目的參數
* 可以是泛型

**範例**

```
[PexClass]
public partial class MyTests {
     [PexMethod]
     public void MyTest(int i)
     { ... }
}
```

<a name="pexexplorationattributebase"></a>
## <a name="pexexplorationattributebase"></a>PexExplorationAttributeBase

[詳細資訊](https://msdn.microsoft.com/library/microsoft.pex.framework.pexexplorationattributebase.aspx)

<a name="pexassemblysettings"></a>
## <a name="pexassemblysettings"></a>PexAssemblySettings

此屬性可以設定於組件層級，以覆寫所有探索的預設設定值。

```
using Microsoft.Pex.Framework;
// overriding the test framework selection
[assembly: PexAssemblySettings(TestFramework = "Naked")]
```

<a name="pexassemblyundertest"></a>
## <a name="pexassemblyundertest"></a>PexAssemblyUnderTest

此屬性指定目前測試專案所測試的組件。 

```
[assembly: PexAssemblyUnderTest("MyAssembly")]
```

<a name="pexinstrumentassemblyattribute"></a>
## <a name="pexinstrumentassemblyattribute"></a>PexInstrumentAssemblyAttribute

此屬性用來指定要檢測的組件。

**範例**

```
using Microsoft.Pex.Framework;

// the assembly containing ATypeFromTheAssemblyToInstrument should be instrumented
[assembly: PexInstrumentAssembly(typeof(ATypeFromTheAssemblyToInstrument))]

// the assembly name can be used as well
[assembly: PexInstrumentAssembly("MyAssemblyName")]
```

<a name="pexusetype"></a>
## <a name="pexusetype"></a>PexUseType

此屬性會告知 IntelliTest 可以使用特定類型來具現化 (抽象) 基底類型或介面。

**範例**

```
[PexMethod]
[PexUseType(typeof(A))]
[PexUseType(typeof(B))]
public void MyTest(object testParameter)
{
     ... // IntelliTest will consider types A and B to instantiate 'testParameter'
}
```

<a name="pexallowedexception"></a>
## <a name="pexallowedexception"></a>PexAllowedException

如果將此屬性附加至 [PexMethod](#pexmethod) (或 [PexClass](#pexclass)，則會變更指出測試何時失敗的預設 IntelliTest 邏輯。 測試不會被視為失敗，即使擲回指定的例外狀況也是一樣。

**範例**

下列測試指定 **Stack** 的建構函式可能會擲回 **ArgumentOutOfRangeException**：

```
class Stack {
  int[] _elements;
  int _count;
  public Stack(int capacity) {
    if (capacity<0) throw new ArgumentOutOfRangeException();
    _elements = new int[capacity];
    _count = 0;
  }
  ...
}
```

篩選會附加至物件，如下所示 (它也可以定義於組件或測試層級)：

```
[PexMethod]
[PexAllowedException(typeof(ArgumentOutOfRangeException))]
class CtorTest(int capacity) {
  Stack s = new Stack(capacity); // may throw ArgumentOutOfRangeException
}
```

<a name="pexallowedexceptionfromassembly"></a>
## <a name="pexallowedexceptionfromassembly"></a>PexAllowedExceptionFromAssembly

[詳細資訊](https://msdn.microsoft.com/library/microsoft.pex.framework.validation.pexallowedexceptionfromassemblyattribute.aspx)

<a name="pexallowedexceptionfromtype"></a>
## <a name="pexallowedexceptionfromtype"></a>PexAllowedExceptionFromType

[詳細資訊](https://msdn.microsoft.com/library/microsoft.pex.framework.validation.pexallowedexceptionfromtypeattribute.aspx)

<a name="pexallowedexceptionfromtypeundertest"></a>
## <a name="pexallowedexceptionfromtypeundertest"></a>PexAllowedExceptionFromTypeUnderTest

[詳細資訊](https://msdn.microsoft.com/library/microsoft.pex.framework.validation.pexallowedexceptionfromtypeundertestattribute.aspx)

## <a name="got-feedback"></a>有任何意見反應嗎？

您可以在 **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)** 張貼想法和功能要求。
