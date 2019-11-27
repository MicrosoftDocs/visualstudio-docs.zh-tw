---
title: 使用 Roslyn 分析器的消費者入門 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2d45491fe031c01a31812f5ed4944f76d059cd60
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300022"
---
# <a name="getting-started-with-roslyn-analyzers"></a>開始使用 Roslyn 分析器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 中以專案為基礎的即時程式碼分析器，API 作者可以將特定領域的程式碼分析當做其 NuGet 套件的一部分來傳送。  因為這些分析器是由 .NET Compiler Platform （代號為 "Roslyn"）所提供，所以當您在程式程式碼完成時（不會再等待建立程式碼來探索問題），它們可能會在您的程式碼中產生警告。  分析器也可以透過 Visual Studio 燈泡提示來呈現自動程式碼修正，讓您立即清除程式碼

## <a name="getting-started"></a>使用者入門
[Roslyn 即時程式碼分析器簡介和逐步解說](https://msdn.microsoft.com/magazine/dn879356.aspx)

[新增程式碼修正逐步解說：提供使用者針對分析器問題的修正](https://msdn.microsoft.com/magazine/dn904670.aspx)

[真實世界分析器交談的簡介和逐步解說](https://channel9.msdn.com/events/Build/2015/3-725)

您也可以觀看作為[說話](https://channel9.msdn.com/events/Build/2015/3-725)的[真實世界 Roslyn 分析器](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md)

[GitHub 上的數個範例，分為三種分析器](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[一些分析器交談簡介和導覽](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>其他資源
[GitHub OSS 網站上的更多檔](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[在 GitHub 上使用 Roslyn 分析器所執行的 FxCop 規則](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
