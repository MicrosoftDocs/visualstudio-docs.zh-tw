---
title: "使用建立單元測試命令來建立單元測試方法虛設常式 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Get started
ms.assetid: 21FE4D68-9E7F-4BB1-BD69-B0D09A941F09
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.openlocfilehash: e89b6d8860e0964eacb9d58f6d92c64cc661afa0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="get-started-with-microsoft-intellitest"></a>開始使用 Microsoft IntelliTest

* 如果這是您第一次使用 IntelliTest，請：
  * 觀看 [Channel 9 影片](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest)
  * 閱讀 [MSDN Magazine 上的概觀](https://msdn.microsoft.com/magazine/dn904672.aspx) 此篇
  * 閱讀我們的[文件](https://docs.microsoft.com/en-gb/visualstudio/test/generate-unit-tests-for-your-code-with-intellitest)
* 在 [stackoverflow](http://stackoverflow.com/questions/tagged/intellitest) 上詢問您的問題
* 閱讀這份參考手冊的其餘部分
* 列印此頁面供快速參考

<a name="important-attributes"></a>
## <a name="important-attributes"></a>重要屬性

* [PexClass](attribute-glossary.md#pexclass) 標記包含 **PUT** 的類型
* [PexMethod](attribute-glossary.md#pexmethod) 標記 **PUT**
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) 標記非 Null 參數 

```
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

```
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

<a name="helper-classes"></a>
## <a name="important-static-helper-classes"></a>重要靜態協助程式類別

* [PexAssume](static-helper-classes.md#pexassume) 評估假設 (輸入篩選)
* [PexAssert](static-helper-classes.md#pexassert) 評估判斷提示
* [PexChoose](static-helper-classes.md#pexchoose) 產生新的選擇 (其他輸入)
* [PexObserve](static-helper-classes.md#pexobserve) 將存留時間值記錄至產生的測試

```
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

您可以在 **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)** 張貼想法和功能要求。
