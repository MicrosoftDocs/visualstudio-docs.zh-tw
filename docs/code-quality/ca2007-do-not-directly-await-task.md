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
ms.openlocfilehash: 3f35e450f17a671b800d003b94ceb5ebc2321c90
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841411"
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

## <a name="configurability"></a>設定功能

您可以設定是否要排除不傳回值的這項規則的非同步方法。 若要排除這類方法，加入專案中的.editorconfig 檔案中的下列索引鍵 / 值組：

```ini
# Package version 2.9.0 and later
dotnet_code_quality.CA2007.exclude_async_void_methods = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.skip_async_void_methods = true
```

您也可以設定哪一種輸出組件類型，要套用此規則。 比方說，為只套用此規則會產生一個主控台應用程式或動態連結程式庫 （亦即，沒有 UI 應用程式） 的程式碼，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```ini
dotnet_code_quality.CA2007.output_kind = ConsoleApplication, DynamicallyLinkedLibrary
```

如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="see-also"></a>另請參閱

- [我應該等候 configureawait （false） 的工作嗎？](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md#should-i-await-a-task-with-configureawaitfalse)
- [在 Visual Studio 中安裝 FxCop 分析器](install-fxcop-analyzers.md)