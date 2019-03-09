---
title: CA2007:不直接等候工作
ms.date: 03/08/2019
ms.topic: reference
f1_keywords:
- CA2007
- DoNotDirectlyAwaitATaskAnalyzer
helpviewer_keywords:
- CA2007
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.openlocfilehash: 8e94b67d1924e2144f658cd6bcd5989751efdb85
ms.sourcegitcommit: 1024f336dcd8e8a4c50b9a9ad8ec85b6e70073a8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57699677"
---
# <a name="ca2007-do-not-directly-await-a-task"></a>CA2007:不直接等候工作

|||
|-|-|
|TypeName|DoNotDirectlyAwaitATaskAnalyzer|
|CheckId|CA2007|
|分類|Microsoft.Reliability|
|中斷變更|非重大|

## <a name="cause"></a>原因

非同步方法[等候](/dotnet/csharp/language-reference/keywords/await)<xref:System.Threading.Tasks.Task>直接。

## <a name="rule-description"></a>規則描述

當非同步方法會等候<xref:System.Threading.Tasks.Task>接續直接發生在相同的執行緒建立的工作。 此行為可能會嚴重降低效能，而且可能會導致鎖死 UI 執行緒。 請考慮呼叫<xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType>來通知您的意圖，接續。

此規則在引進[FxCop 分析器](install-fxcop-analyzers.md)不存在於 「 舊版 」 （靜態程式碼分析） 和 FxCop。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正違規，呼叫<xref:System.Threading.Tasks.Task.ConfigureAwait%2A>上等候<xref:System.Threading.Tasks.Task>。 您可以傳遞`true`或是`false`如`continueOnCapturedContext`參數。

- 呼叫`ConfigureAwait(true)`在工作上具有相同的行為未明確呼叫<xref:System.Threading.Tasks.Task.ConfigureAwait%2A>。 藉由明確地呼叫這個方法，就會讓讀者了解您刻意想要在原始的同步處理內容上執行接續。

- 呼叫`ConfigureAwait(false)`在排程執行緒集區的接續工作，藉此避免在 UI 執行緒鎖死。 傳遞`false`是獨立於應用程式的程式庫的理想選項。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果您知道，取用者不是圖形化使用者介面 (GUI) 應用程式，或如果取用者不需要您可以隱藏這個警告<xref:System.Threading.SynchronizationContext>。

## <a name="example"></a>範例

下列程式碼片段會產生警告：

```csharp
public async Task Execute()
{
    Task task = null;
    await task;
}
```

若要修正此違規情形，請呼叫<xref:System.Threading.Tasks.Task.ConfigureAwait%2A>上等候<xref:System.Threading.Tasks.Task>:

```csharp
public async Task Execute()
{
    Task task = null;
    await task.ConfigureAwait(false);
}
```

## <a name="see-also"></a>另請參閱

- [我應該等候 configureawait （false） 的工作嗎？](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md#should-i-await-a-task-with-configureawaitfalse)
- [在 Visual Studio 中安裝 FxCop 分析器](install-fxcop-analyzers.md)