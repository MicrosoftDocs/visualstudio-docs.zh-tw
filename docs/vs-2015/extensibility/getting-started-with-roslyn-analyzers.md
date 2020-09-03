---
title: 使用 Roslyn 分析器消費者入門 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a712697bafefcf115ce10d110c0ef3a4270c6acd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444961"
---
# <a name="getting-started-with-roslyn-analyzers"></a>開始使用 Roslyn 分析器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用 Visual Studio 中的即時專案型程式碼分析器，API 作者可以將網域專屬的程式碼分析作為其 NuGet 套件的一部分來傳送。  因為這些分析器是由 .NET Compiler Platform (代號為 "Roslyn" ) 所提供，所以在您輸入的程式碼中，即使您已完成這一行，也可以在程式碼中產生警告， (不再等待建立程式碼以找出問題) 。  分析器也可以透過 Visual Studio 燈泡提示來呈現自動程式碼修正，讓您立即清除程式碼

## <a name="getting-started"></a>開始使用
[Roslyn 即時程式碼分析器簡介和逐步解說](https://msdn.microsoft.com/magazine/dn879356.aspx)

[新增程式碼修正逐步解說：為分析器問題提供使用者修正](https://msdn.microsoft.com/magazine/dn904670.aspx)

[真實世界分析器的簡介和逐步解說](https://channel9.msdn.com/events/Build/2015/3-725)

您也可以[觀賞的](https://channel9.msdn.com/events/Build/2015/3-725)[真實世界 Roslyn Analyzer](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md)

[GitHub 上的數個範例，分為三種分析器](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[一些分析器討論的簡介和導覽](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>其他資源
[GitHub OSS 網站上的其他檔](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[在 GitHub 上以 Roslyn 分析器執行的 FxCop 規則](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
