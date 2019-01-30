---
title: IntelliTest 簡介
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Get started
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: fb7fc6049bd916c766651484da0c53b3aeccbe35
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929365"
---
# <a name="get-started-with-microsoft-intellitest"></a>開始使用 Microsoft IntelliTest

* 如果這是您第一次使用 IntelliTest，請：
  * 觀看 [Channel 9 影片](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest)
  * 閱讀 [MSDN Magazine 上的概觀](https://msdn.microsoft.com/magazine/dn904672.aspx) 此篇
  * 閱讀我們的[文件](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
* 在 [Stack Overflow](http://stackoverflow.com/questions/tagged/intellitest) 詢問問題
* 閱讀這份參考手冊的其餘部分
* 列印此頁面供快速參考

## <a name="important-attributes"></a>重要屬性

* [PexClass](attribute-glossary.md#pexclass) 標記包含 **PUT** 的類型
* [PexMethod](attribute-glossary.md#pexmethod) 標記 **PUT**
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) 標記非 Null 參數

```csharp
using Microsoft.Pex.Framework;

[..., PexClass(typeof(Foo))]
public partial class FooTest {
    [PexMethod]
    public void Bar([PexAssumeNotNull]Foo target, int i) {
        target.Bar(i);
    }
}
```

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest) 將測試專案繫結至專案
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) 指定要檢測的組件

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="helper-classes"></a> 重要靜態協助程式類別

* [PexAssume](static-helper-classes.md#pexassume) 評估假設 (輸入篩選)
* [PexAssert](static-helper-classes.md#pexassert) 評估判斷提示
* [PexChoose](static-helper-classes.md#pexchoose) 產生新的選擇 (其他輸入)
* [PexObserve](static-helper-classes.md#pexobserve) 將存留時間值記錄至產生的測試

```csharp
[PexMethod]
void StaticHelpers(Foo target) {
    PexAssume.IsNotNull(target);

    int i = PexChoose.Value<int>("i");
    string result = target.Bar(i);

    PexObserve.ValueForViewing<string>("result", result);
    PexAssert.IsNotNull(result);
}
```

## <a name="got-feedback"></a>有任何意見反應嗎？

在[開發人員社群](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)上張貼您的意見與功能建議。
