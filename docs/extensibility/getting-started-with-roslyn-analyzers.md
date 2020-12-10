---
title: 使用 Roslyn 分析器消費者入門 |Microsoft Docs
description: 使用這些資源來開始使用 Visual Studio 中的 Roslyn 分析器;包含教學課程和數個範例。
ms.custom: SEO-VS-2020
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c63510083f227f617b2a11ddec07510ffd792433
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994351"
---
# <a name="get-started-with-roslyn-analyzers"></a>開始使用 Roslyn 分析器

使用 Visual Studio 中的即時專案型程式碼分析器，API 作者可以將網域專屬的程式碼分析作為其 NuGet 套件的一部分來傳送。 因為這些分析器是由 .NET Compiler Platform (代號為 "Roslyn" ) 所提供，所以在您輸入的程式碼中，即使您已完成這一行，也可以在程式碼中產生警告， (不再等待建立程式碼以找出問題) 。 分析器也可以透過 Visual Studio 燈泡提示來呈現自動程式碼修正，讓您立即清除程式碼。

## <a name="get-started"></a>開始使用

[Roslyn 分析器總覽](../code-quality/roslyn-analyzers-overview.md)

[教學課程：撰寫您的第一個分析器和程式碼修正](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[新增程式碼修正逐步解說：提供使用者針對分析器問題的修正](/archive/msdn-magazine/2015/february/csharp-adding-a-code-fix-to-your-roslyn-analyzer)

您也可以[觀賞的](https://channel9.msdn.com/events/Build/2015/3-725)[真實世界 Roslyn analyzer](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md)

[GitHub 上的數個範例，分為三種分析器](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>另請參閱

- [.NET 編譯器平臺套件版本參考](roslyn-version-support.md)
- [GitHub OSS 網站上的其他檔](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [使用 Roslyn 分析器執行的 FxCop 規則](../code-quality/fxcop-rule-port-status.md)
