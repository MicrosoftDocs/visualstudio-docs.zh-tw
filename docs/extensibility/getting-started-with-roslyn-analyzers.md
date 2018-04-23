---
title: 開始使用 Roslyn 分析器 |Microsoft 文件
ms.date: 04/02/2018
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7b887703343dab10f9cc1f0cbf8e2e2b37b0065b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="getting-started-with-roslyn-analyzers"></a>開始使用 Roslyn 分析器

使用 Visual Studio 中的即時、 以專案為基礎的程式碼分析器，應用程式開發介面作者可以送出網域專屬的程式碼分析，做為其 NuGet 封裝的一部分。 這些分析器由.NET 編譯器平台 (code-named"Roslyn")，因為它們會產生您的程式碼中的警告，當您輸入您已完成 （沒有其他等待建置您的程式碼，找出問題） 的行之前。 分析器可以也介面透過立即讓您清理您的程式碼的 Visual Studio 燈泡提示的自動程式碼修正。

## <a name="getting-started"></a>使用者入門

[Roslyn 即時程式碼分析器的簡介與逐步解說](https://msdn.microsoft.com/magazine/dn879356.aspx)

[加入程式碼修正的逐步解說： 針對分析的問題提供使用者修正](https://msdn.microsoft.com/magazine/dn904670.aspx)

[簡介與真實世界分析器 Talk 的逐步解說](http://channel9.msdn.com/events/Build/2015/3-725)

[真實世界 Roslyn 分析器](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md)，您也可以觀看為[交談](http://channel9.msdn.com/events/Build/2015/3-725)

[在 github 上的數個範例會分組為三種類型的分析器](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[簡介與教學課程的幾個分析器交談](http://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="see-also"></a>另請參閱

- [Roslyn 分析器概觀](../code-quality/roslyn-analyzers-overview.md)
- [OS github 網站上的多個文件](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [實作與 Roslyn 分析器 github 上的 FxCop 規則](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)