---
title: "概觀 | Microsoft IntelliTest 開發人員測試工具 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Visual Studio IntelliTest developer testing tool
ms.assetid: A7B98509-7ACA-4E25-BD1B-BBC98742F028
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: a7dac076dabaf0d44a1eda9c267e5c9b2eafe5a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="overview-of-microsoft-intellitest"></a>Microsoft IntelliTest 的概觀

IntelliTest 可讓您及早發現錯誤，並降低測試維護成本。 使用自動化和透明的測試方法，IntelliTest 可為 .NET 程式碼產生候選的測試套件。 通過您所指定的「正確性屬性」，可進一步指引測試套件產生作業。 IntelliTest 甚至會隨著受測程式碼發展自動進化測試套件。

**特徵測試**  
IntelliTest 可讓您根據一套傳統的單元測試來判斷程式碼的行為。 這類測試套件可當作迴歸套件，針對處理與重構舊版或不熟悉程式碼建立關聯的複雜性確立其基礎。

**引導式測試輸入產生**  
IntelliTest 會使用開放程式碼分析和條件約束求解方法來自動產生精確的測試輸入值；通常不需要使用者介入。 對於複雜的物件類型，它會自動產生處理站。 您可以藉由擴充及設定處理站來引導測試輸入產生作業，以符合您的需求。 還會自動使用在程式碼中指定為判斷提示的正確性屬性，進一步引導測試輸入產生作業。

**IDE 整合**  
IntelliTest 已完全整合到 Visual Studio IDE 中。 測試套件產生期間收集的所有資訊 (例如自動產生的輸入、來自程式碼的輸出、產生的測試案例，以及其通過或失敗狀態) 會出現在 Visual Studo IDE 中。 您可以輕鬆地反覆修正您的程式碼和重新執行 IntelliTest，而不需要離開 Visual Studio IDE。 測試可作為單元測試專案儲存到方案中，而且之後由 Visual Studio [測試總管] 自動偵測。

**補充現有的測試實務**  
請使用 IntelliTest 來補充您可能已遵循的任何現有測試實務。

如果您想要測試：

* 基本資料或基本資料陣列的演算法：
  * 撰寫[參數化單元測試](test-generation.md#parameterized-unit-testing)
* 複雜資料的演算法，例如編譯器：
  * 讓 IntelliTest 先產生資料的抽象表示，然後將它饋送給演算法
  * 讓 IntelliTest 建置執行個體使用[自訂物件建立](input-generation.md#objects)和資料的非變異值，然後叫用此演算法
* 資料容器：
  * 撰寫[參數化單元測試](test-generation.md#parameterized-unit-testing)
  * 讓 IntelliTest 建置執行個體使用[自訂物件建立](input-generation.md#objects)和資料的非變異值，然後叫用容器的方法並重新檢查之後的非變異值
  * 撰寫[參數化單元測試](test-generation.md#parameterized-unit-testing)，以根據參數值呼叫不同的實作方法
* 現有的程式碼基底：
  * 使用 Visual Studio 的 [IntelliTest 精靈] 來開始進行，方法是產生一組[參數化單元測試 (PUT)](test-generation.md#parameterized-unit-testing)

<a name="hello-world"></a>
## <a name="the-hello-world-of-intellitest"></a>IntelliTest 的 Hello World

IntelliTest 會尋找與所測試程式相關的輸入，這表示您可以使用它來產生知名的 **Hello World!** 字串。 這會假設您已建立 C# MSTest 架構的測試專案，並已新增 **Microsoft.Pex.Framework** 的參考。 如果您要使用不同的測試架構，請建立 C# 類別庫，並參閱有關如何設定專案的測試架構文件。

以下範例會在名為 **value** 的參數上建立兩個條件約束，以便 IntelliTest 產生必要的字串。

```
using System;
using Microsoft.Pex.Framework; 
using Microsoft.VisualStudio.TestTools.UnitTesting; 

[TestClass]
public partial class HelloWorldTest {
    [PexMethod]
    public void HelloWorld([PexAssumeNotNull]string value) {
        if (value.StartsWith("Hello")
            && value.EndsWith("World!")
            && value.Contains(" "))
            throw new Exception("found it!");
    }
}
```

編譯並執行之後，IntelliTest 會產生一組測試，如下所示：

1. ""
2. "\0\0\0\0\0"
3. "Hello"
4. "\0\0\0\0\0\0"
5. "Hello\0"
6. "Hello\0\0"
7. "Hello\0World!"
8. "Hello World!"

移到[這裡](https://docs.microsoft.com/en-gb/visualstudio/test/generate-unit-tests-for-your-code-with-intellitest#Anchor_0)來了解所產生測試的儲存位置。
產生的測試程式碼應該包含如下測試：

```
[TestMethod]
[PexGeneratedBy(typeof(global::HelloWorldTest))]
[PexRaisedException(typeof(Exception))]
public void HelloWorldThrowsException167()
{
    this.HelloWorld("Hello World!");
}
```

就是這麼簡單！

<a name="limitations"></a>
## <a name="limitations"></a>限制

本節描述 IntelliTest 的限制：

* [不具決定性](#nondeterminism)
* [並行](#concurrency)
* [原生 .NET 程式碼](#native-code)
* [平台](#platform)
* [Language](#language)
* [符號推理](#symbolic-reasoning)
* [堆疊追蹤](#incorrect-stack)

<a name="nondeterminism"></a>
### <a name="nondeterminism"></a>不具決定性

IntelliTest 會假設分析的程式具決定性。 如果不具決定性，IntelliTest 將循環執行，直到觸達探索界限。

如果程式依賴 IntelliTest 無法控制的輸入，則 IntelliTest 就會將該程式視為不具決定性 。

IntelliTest 可控制提供給[參數化單元測試](test-generation.md#parameterized-unit-testing)並從 [PexChoose](static-helper-classes.md#pexchoose) 取得的輸入。 就這個方面，Unmanaged 或未經檢測之程式碼呼叫的結果也可視為已檢測程式的「輸入」，但 IntelliTest 無法加以控制。 如果程式的控制流程相依於來自這些外部來源的特定值，則 IntelliTest 無法「操縱」程式轉向先前未涵蓋的區域。 

此外，如果在重新執行程式時來自外部來源的值變更，則程式也會被視為不具決定性。 在這種情況下，IntelliTest 會失去對程式執行的控制權，因此其搜尋變得非常沒有效率。

有時候此發生狀況並不明顯。 請參考下列範例：

* **GetHashCode()** 方法的結果是由 Unmanaged 程式碼提供，而且無法預測。
* **System.Random** 類別會使用目前的系統時間提供真正的隨機值。
* **System.DateTime** 類別會提供目前的時間，這顯然不在 IntelliTest 的控制之下。

<a name="concurrency"></a>
### <a name="concurrency"></a>並行

IntelliTest 不會處理多執行緒程式。

<a name="native-code"></a>
### <a name="native-code-net-code-that-is-not-instrumented"></a>未檢測的原生程式碼、.NET 程式碼

IntelliTest 不了解原生程式碼，例如透過 **P/Invoke** 呼叫的 x86 指令。 它不知道如何將這類呼叫轉譯成可傳遞至[條件約束規劃求解](input-generation.md#constraint-solver)的條件約束。 即使針對 .NET 程式碼，它也只能分析其檢測的程式碼。 IntelliTest 無法檢測 **mscorlib** 的特定部分，包括反映庫。 **DynamicMethod** 無法進行檢測。 

建議的因應措施是具備這類方法位於動態組件之類型中的測試模式。 不過，即使某些方法未經檢測，IntelliTest 還是會盡可能嘗試涵蓋已檢測的程式碼。

<a name="platform"></a>
### <a name="platform"></a>平台

只有 X86 32 位元 .NETframework 才支援 IntelliTest。

<a name="language"></a>
### <a name="language"></a>語言

基本上，IntelliTest 可分析以任何 .NET 語言撰寫的任意 .NET 程式。 不過，它在 Visual Studio 中只支援 C#。

<a name="symbolic-reasoning"></a>
### <a name="symbolic-reasoning"></a>符號推理

IntelliTest 會使用自動[條件約束規劃求解](input-generation.md#constraint-solver)來判定哪些值與測試和受測程式相關。 不過，條件約束規劃求解的功能一律受限。

<a name="incorrect-stack"></a>
### <a name="slightly-incorrect-stack-traces"></a>(稍微) 不正確的堆疊追蹤

因為 IntelliTest 會捕捉並「重新擲回」每個已檢測方法中的例外狀況，所以堆疊追蹤的行號不正確。 這是「重新擲回」指示設計的限制。

<a name="further-reading"></a>
## <a name="further-reading"></a>進一步閱讀

* MSDN 上的[簡介部落格文章](https://blogs.msdn.microsoft.com/visualstudioalm/2014/11/19/introducing-smart-unit-tests/)。
* [使用 IntelliTest 為程式碼產生單元測試](https://docs.microsoft.com/en-gb/visualstudio/test/generate-unit-tests-for-your-code-with-intellitest)

## <a name="got-feedback"></a>有任何意見反應嗎？

您可以在 **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)** 張貼想法和功能要求。
