---
title: 使用 Roslyn 分析器的消費者入門 |Microsoft Docs
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21b2d77d8c038988fa77293280c9ff7ad38cc82e
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2019
ms.locfileid: "68822337"
---
# <a name="get-started-with-roslyn-analyzers"></a>開始使用 Roslyn 分析器

在 Visual Studio 中以專案為基礎的即時程式碼分析器, API 作者可以將特定領域的程式碼分析當做其 NuGet 套件的一部分來傳送。 因為這些分析器是由 .NET Compiler Platform (代號為 "Roslyn") 所提供, 所以當您在程式程式碼完成時 (不會再等待建立程式碼來探索問題), 它們可能會在您的程式碼中產生警告。 分析器也可以透過 Visual Studio 燈泡提示來呈現自動程式碼修正, 讓您立即清除程式碼。

## <a name="get-started"></a>開始使用

[Roslyn 分析器總覽](../code-quality/roslyn-analyzers-overview.md)

[教學課程：撰寫您的第一個分析器和程式碼修正](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[新增程式碼修正逐步解說:提供使用者針對分析器問題的修正](https://msdn.microsoft.com/magazine/dn904670.aspx)

您也可以觀看作為[說話](https://channel9.msdn.com/events/Build/2015/3-725)的[真實世界 Roslyn 分析器](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md)

[GitHub 上的數個範例, 分為三種分析器](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>另請參閱

- [.NET 編譯器平臺套件版本參考](roslyn-version-support.md)
- [GitHub OSS 網站上的更多檔](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [使用 Roslyn 分析器執行的 FxCop 規則](../code-quality/fxcop-rule-port-status.md)
