---
title: 撰寫能夠辨識多處理器的記錄器 | Microsoft Docs
description: 瞭解 MSBuild 如何提供多處理器感知的記錄器和記錄模型，並讓您建立自訂「轉送記錄器」。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, multi-proc aware loggers
- multi-proc loggers
- loggers, multi-proc
ms.assetid: ff987d1b-1798-4803-9ef6-cc8fcc263516
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1e7cf5998645230f038c6de12c79b53b44c09dfc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847982"
---
# <a name="write-multi-processor-aware-loggers"></a>撰寫能夠辨識多處理器的記錄器

MSBuild 利用多個處理器的能力可能會減少專案建立時間，但也會增加建立事件記錄的複雜性。 在單一處理器環境中，事件、訊息、警告和錯誤是以可預測的循序方式傳入記錄器。 不過，在多處理器環境中，不同來源的事件可能會同時或不依順序傳入。 為了提供這一點，MSBuild 提供了多處理器感知的記錄器和新的記錄模型，可讓您建立自訂的「轉送記錄器」。

## <a name="multi-processor-logging-challenges"></a>多處理器記錄挑戰

 當您在多處理器或多核心系統上建立一個或多個專案時，會同時產生所有專案的 MSBuild 組建事件。 記錄器可能會同時或不依順序收到大量的事件訊息。 由於 MSBuild 2.0 記錄器並非設計用來處理這種情況，因此可能會讓記錄器負荷超過，並導致組建時間增加、記錄器輸出不正確，或甚至是中斷的組建。 為了解決這些問題，記錄器 (開始于 MSBuild 3.5) 可以處理序列外的事件，並將事件和其來源相互關聯。

 建立自訂轉送記錄器，甚至可以改善更多的記錄效率。 自訂轉送記錄器可讓您在組建之前只選擇您要監視的事件，以作為篩選。 當您使用自訂轉送記錄器時，不想要的事件不會讓記錄器不勝負荷、導致記錄雜亂，或讓組建時間變慢。

## <a name="multi-processor-logging-models"></a>多處理器記錄模型

 為了提供與多處理器相關的組建問題，MSBuild 支援兩種記錄模型（中央和分散式）。

### <a name="central-logging-model"></a>集中式記錄模型

 在集中式記錄模型中，*MSBuild.exe* 的單一執行個體做為「中央節點」，中央節點的子執行個體 (「次要節點」) 則附加至中央節點，協助它執行組建工作。

 ![中央記錄器模型](../msbuild/media/centralnode.png "CentralNode")

 附加至中央節點的各類記錄器稱為「中央記錄器」。 每個記錄器類型同時只能有一個執行個體附加到中央節點。

 組建時，次要節點會將其組建事件路由至中央節點。 中央節點則將其所有事件，以及次要節點的事件，路由至一或多個附加的中央記錄器。 然後，記錄器根據傳入的資料建立記錄檔。

 雖然中央記錄器只需要實作 <xref:Microsoft.Build.Framework.ILogger>，但建議您一併實作 <xref:Microsoft.Build.Framework.INodeLogger>，以便中央記錄器使用參與組建的節點數目初始化。 引擎初始化記錄器時，<xref:Microsoft.Build.Framework.ILogger.Initialize%2A> 方法的下列多載會叫用。

```csharp
public interface INodeLogger: ILogger
{
    public void Initialize(IEventSource eventSource, int nodeCount);
}
```

 任何預先存在的 <xref:Microsoft.Build.Framework.ILogger> 型記錄器都可當做中央記錄器，附加至組建。 不過，寫入中央記錄器但未明確支援多處理器記錄情況及失序事件，可能會中斷組建或產生無意義的輸出。

### <a name="distributed-logging-model"></a>分散式記錄模型

 在集中式記錄模型中，傳入訊息流量過多可能會造成中央節點不勝負荷，例如，同時組建許多專案時。 這會造成系統資源壓力並降低組建效能。 為了減輕這個問題，MSBuild 支援分散式記錄模型。

 ![分散式記錄模型](../msbuild/media/distnode.png "DistNode")

 分散式記錄模型可讓您建立轉送記錄器，擴展集中式記錄模型。

#### <a name="forwarding-loggers"></a>轉送記錄器

 轉送記錄器是次要的輕量型記錄器，有附加至次要節點的事件篩選器，並可從該節點接收傳入的組建事件。 它會篩選傳入的事件，並只將您指定的事件轉送到中央節點。 這會減少傳送到中央節點的訊息流量，改善整體的組建效能。

 使用分散式記錄的方式有兩種，如下所示：

- 自訂預先製作的 <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> 轉送記錄器。

- 撰寫您自己的自訂轉送記錄器。

您可以修改 ConfigurableForwardingLogger 使符合您的需求。 若要這樣做，請使用 *MSBuild.exe* 在命令列上呼叫記錄器，並列出您想要記錄器轉送到中央節點的組建事件。

或者，您也可以建立自訂的轉送記錄器。 建立自訂轉送記錄器，可以微調記錄器的行為。 不過，建立自訂轉送記錄器會比只自訂 ConfigurableForwardingLogger 更為複雜。 如需詳細資訊，請參閱[建立轉送記錄器](../msbuild/creating-forwarding-loggers.md)。

## <a name="using-the-configurableforwardinglogger-for-simple-distributed-logging"></a>使用 ConfigurableForwardingLogger 進行簡單的分散式記錄

 若要附加 ConfigurableForwardingLogger 或自訂的轉送記錄器，請在 *MSBuild.exe* 命令列組建中使用 `-distributedlogger` 參數 (簡寫為 `-dl`)。 用於指定記錄器類型和類別名稱的格式與 `-logger` 參數相同，差異在於分散式記錄器一律有兩個記錄類別，而不是一個：轉送記錄器和集中式記錄器。 以下是如何附加 XMLForwardingLogger 自訂轉送記錄器的範例。

```cmd
msbuild.exe myproj.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral
```

> [!NOTE]
> `-dl` 參數中必須使用星號 (*) 分隔兩個記錄器名稱。

 除非您附加 ConfigurableForwardingLogger 記錄器，而不是您想要 ConfigurableForwardingLogger 傳遞至中央節點的事件，否則使用 ConfigurableForwardingLogger 就像使用任何其他記錄器 (如 [取得組建記錄](../msbuild/obtaining-build-logs-with-msbuild.md) 檔) 中所述。

 例如，如果只想收到組建開始和結束以及發生錯誤的通知，您可以傳遞 `BUILDSTARTEDEVENT`、`BUILDFINISHEDEVENT` 和 `ERROREVENT` 做為參數。 傳遞多個參數時可以分號分隔。 下例示範如何使用 ConfigurableForwardingLogger 只轉送 `BUILDSTARTEDEVENT`、`BUILDFINISHEDEVENT` 和 `ERROREVENT` 事件。

```cmd
msbuild.exe myproj.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*ConfigureableForwardingLogger,C:\My.dll;BUILDSTARTEDEVENT; BUILDFINISHEDEVENT;ERROREVENT
```

 以下是可用的 ConfigurableForwardingLogger 參數清單。

|ConfigurableForwardingLogger 參數|
| - |
|BUILDSTARTEDEVENT|
|BUILDFINISHEDEVENT|
|PROJECTSTARTEDEVENT|
|PROJECTFINISHEDEVENT|
|TARGETSTARTEDEVENT|
|TARGETFINISHEDEVENT|
|TASKSTARTEDEVENT|
|TASKFINISHEDEVENT|
|ERROREVENT|
|WARNINGEVENT|
|HIGHMESSAGEEVENT|
|NORMALMESSAGEEVENT|
|LOWMESSAGEEVENT|
|CUSTOMEVENT|
|COMMANDLINE|
|PERFORMANCESUMMARY|
|NOSUMMARY|
|SHOWCOMMANDLINE|

## <a name="see-also"></a>另請參閱

- [建立轉送記錄器](../msbuild/creating-forwarding-loggers.md)