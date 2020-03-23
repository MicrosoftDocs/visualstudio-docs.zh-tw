---
title: 組建記錄器 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a00bbb8ce239275ff140dbedf2157e4cdc41d44c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634522"
---
# <a name="build-loggers"></a>組建記錄器

記錄器提供一種方式，讓您能夠自訂組建的輸出，並顯示訊息、錯誤或警告來回應特定的建置事件。 每個記錄器都會實作為 .NET 類別，此類別會實作 <xref:Microsoft.Build.Framework.ILogger> 介面，此介面定義於 Microsoft.Build.Framework.dll** 組件中。

實作記錄器時有兩種方法可供使用：

- 直接實作 <xref:Microsoft.Build.Framework.ILogger> 介面。
- 從協助程式類別 <xref:Microsoft.Build.Utilities.Logger> 衍生您的類別，此協助程式類別定義於 *Microsoft.Build.Utilities.dll* 組件中。 <xref:Microsoft.Build.Utilities.Logger> 會實作 <xref:Microsoft.Build.Framework.ILogger> 並提供部分 <xref:Microsoft.Build.Framework.ILogger> 成員的預設實作。

  本主題將說明如何撰寫衍生自 <xref:Microsoft.Build.Utilities.Logger> 的簡單記錄器，並在主控台上顯示訊息來回應特定的建置事件。

## <a name="register-for-events"></a>註冊事件

記錄器的用途是當建置引擎回報時收集建置進度的相關資訊，然後以實用的方式報告該資訊。 所有記錄器都必須覆寫 <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> 方法，該方法是記錄器註冊事件的位置。 在此範例中，記錄器會註冊 <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>、<xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> 及 <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> 事件。

[!code-csharp[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]

## <a name="respond-to-events"></a>回應事件

現在已針對特定事件註冊記錄器，接著需要在這些事件發生時加以處理。 針對 <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> 和 <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> 事件，記錄器會單純寫入簡短的片語，以及涉及事件的專案檔名稱。 來自記錄器的所有訊息都會寫入主控台視窗。

[!code-csharp[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]

## <a name="respond-to-logger-verbosity-values"></a>回應記錄器詳細資訊層級值

在某些情況下，如果**MSBuild.exe-verbosity 開關**包含特定值，則可能只想記錄事件的資訊。 <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>在此示例中，如果由 **-verbosity**開關設置<xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed`<xref:Microsoft.Build.Utilities.Logger.Verbosity%2A>的屬性等於 ，則事件處理常式僅記錄一條消息。

[!code-csharp[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]

## <a name="specify-a-logger"></a>指定記錄器

將記錄器編譯到程式集後，您需要告訴 MSBuild 在生成期間使用該記錄器。 這是使用*MSBuild.exe*的 **-logger**開關完成的。 如需 *MSBuild.exe* 適用參數的詳細資訊，請參閱[命令列參考](../msbuild/msbuild-command-line-reference.md)。

下列命令列會建置 *MyProject.csproj* 專案，並使用 *SimpleLogger.dll* 中實作的記錄器類別。 **-nologo**開關隱藏橫幅和版權消息 **，-noconsolelogger**開關禁用預設的 MSBuild 主控台記錄器。

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll
```

下列命令列會建置含有相同記錄器的專案，但具備 `Verbosity` 層級的 `Detailed`。

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll -verbosity:Detailed
```

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例包含記錄器的完整程式碼。

### <a name="code"></a>程式碼

[!code-csharp[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例示範如何實作要將記錄寫入檔案的記錄器，而不是將它顯示在主控台視窗中。

### <a name="code"></a>程式碼

[!code-csharp[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]

## <a name="see-also"></a>另請參閱

- [取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)
- [MSBuild 概念](../msbuild/msbuild-concepts.md)
