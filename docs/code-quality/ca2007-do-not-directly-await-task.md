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
ms.openlocfilehash: 0d3ab899ad660c637492a4c3d229779481184e95
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547000"
---
# <a name="ca2007-do-not-directly-await-a-task"></a>CA2007:不直接等候工作

|||
|-|-|
|TypeName|DoNotDirectlyAwaitATaskAnalyzer|
|CheckId|CA2007|
|Category|Microsoft.Reliability|
|中斷變更|不中斷|

## <a name="cause"></a>原因

非同步方法會 <xref:System.Threading.Tasks.Task>[直接等候](/dotnet/csharp/language-reference/keywords/await)。

## <a name="rule-description"></a>規則描述

當非同步方法<xref:System.Threading.Tasks.Task>直接等候時，接續會在建立工作的同一個執行緒中發生。 這種行為在效能方面可能會很昂貴，而且可能會導致 UI 執行緒上發生鎖死。 請考慮<xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType>呼叫以指示接續的意圖。

此規則是以[fxcop 分析器](install-fxcop-analyzers.md)引進，並不存在於舊版的 FxCop 分析中。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正違規， <xref:System.Threading.Tasks.Task.ConfigureAwait%2A>請在等候<xref:System.Threading.Tasks.Task>的上呼叫。 您可以為`true` `false` 參數`continueOnCapturedContext`傳遞或。

- 在`ConfigureAwait(true)`工作上呼叫的行為與未明確呼叫<xref:System.Threading.Tasks.Task.ConfigureAwait%2A>的行為相同。 藉由明確呼叫此方法，您就可以讓讀者知道您刻意想要在原始同步處理內容上執行接續。

- 在`ConfigureAwait(false)`工作上呼叫以排程接續至執行緒集區，藉此避免 UI 執行緒上發生鎖死。 傳遞`false`是適用于應用程式獨立程式庫的絕佳選項。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果您知道取用者不是圖形化使用者介面（GUI）應用程式，或取用者<xref:System.Threading.SynchronizationContext>沒有，您可以隱藏這個警告。

## <a name="example"></a>範例

下列程式碼片段會產生警告：

```csharp
public async Task Execute()
{
    Task task = null;
    await task;
}
```

若要修正違規，請<xref:System.Threading.Tasks.Task.ConfigureAwait%2A>在等待<xref:System.Threading.Tasks.Task>的上呼叫：

```csharp
public async Task Execute()
{
    Task task = null;
    await task.ConfigureAwait(false);
}
```

## <a name="configurability"></a>可設定性

您可以設定是否要排除不會從這個規則傳回值的非同步方法。 若要排除這類方法，請將下列機碼值組新增至專案中的 editorconfig 檔案：

```ini
# Package version 2.9.0 and later
dotnet_code_quality.CA2007.exclude_async_void_methods = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.skip_async_void_methods = true
```

您也可以設定要套用此規則的輸出元件類型。 例如，若只要將此規則套用至產生主控台應用程式或動態連結程式庫（也就是不是 UI 應用程式）的程式碼，請將下列機碼值組新增至專案中的 editorconfig 檔案：

```ini
dotnet_code_quality.CA2007.output_kind = ConsoleApplication, DynamicallyLinkedLibrary
```

如需詳細資訊，請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="see-also"></a>另請參閱

- [我應該使用 ConfigureAwait （false）來等待工作嗎？](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md#should-i-await-a-task-with-configureawaitfalse)
- [在 Visual Studio 中安裝 FxCop 分析器](install-fxcop-analyzers.md)