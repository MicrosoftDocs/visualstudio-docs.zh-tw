---
title: 啟用或安裝第一方 .NET 分析器
ms.date: 08/03/2018
description: 瞭解如何從 .NET SDK 啟用第一方 .NET 分析器，或將這些分析器安裝為 NuGet 套件。
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- .NET analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f7dfa1c79af832cc54d9aee72eeafbf20bbde707
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398412"
---
# <a name="enable-or-install-first-party-net-analyzers"></a>啟用或安裝第一方 .NET 分析器

## <a name="overview"></a>概觀

.NET 編譯器平台 (Roslyn) 分析器會檢查 C# 或 Visual Basic 程式碼以找出程式碼品質與程式碼樣式問題。 第一方 .NET 分析器是 **目標平臺中立** 的。 也就是說，您的專案不需要以特定的 .NET 平臺為目標。 分析器適用于以和舊版 .NET 版本為目標的專案 `net5.0` ，例如 `netcoreapp` 、 `netstandard` 和 `net472` 。

您可以使用下列其中一種方式來啟用或安裝第一方 .NET 分析器：

- **從 .NET Sdk 啟用**：從 Visual Studio 2019 16.8 和 .Net 5.0 開始，這些分析器隨附于 [.net sdk](/dotnet/fundamentals/code-analysis/overview)。 依預設，針對以 .NET 5.0 或更新版本為目標的專案，會啟用分析。 您可以將屬性設定為，以針對以舊版 .NET 版本為目標的專案啟用程式碼分析 `EnableNETAnalyzers` `true` 。 您也可以將設定為，以停用專案的程式碼分析 `EnableNETAnalyzers` `false` 。

- **安裝為 nuget 套件**：如果您不想要移至 .net 5 + SDK，或您偏好以 nuget 套件為基礎的模型，您也可以在 `Microsoft.CodeAnalysis.NetAnalyzers` Visual Studio 2019 的 [nuget 套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) 中找到分析器。  您可能偏好以套件為基礎的模型來進行隨選版本更新。 如果您是在 Visual Studio 2017 上，請改為安裝 `2.9.x` `Microsoft.CodeAnalysis.FxCopAnalyzers` [NuGet 套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) 的最新版本。

> [!NOTE]
> 建議您在可能的情況下，從 .NET SDK 啟用分析器，而不是安裝 `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet 套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)。 從 .NET SDK 啟用分析器，可確保您在更新 SDK 之後，自動取得分析器 bug 修正和新的分析器。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的程式碼分析器總覽](roslyn-analyzers-overview.md)
- [在 Visual Studio 中使用程式碼分析器](use-roslyn-analyzers.md)
- [從舊版分析移轉至 .NET 分析器](migrate-from-legacy-analysis-to-net-analyzers.md)
- [從 FxCop 分析器移轉至 .NET 分析器](migrate-from-fxcop-analyzers-to-net-analyzers.md)
