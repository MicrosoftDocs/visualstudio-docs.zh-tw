---
title: "使用建立單元測試命令來建立單元測試方法虛設常式 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliTest, Get started
ms.assetid: 21FE4D68-9E7F-4BB1-BD69-B0D09A941F09
caps.latest.revision: 56
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 45d36934cf1c46902cac566203cddf4a118b7fe4
ms.openlocfilehash: 0194688e9eec258e415a30a8915379affc5f89de
ms.contentlocale: zh-tw
ms.lasthandoff: 06/02/2017

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

您可以在 **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)** 張貼想法和功能提議。

