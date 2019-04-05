---
title: 開始使用 Roslyn 分析器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 104e3a30589f5892c1440266afd7917486d704ec
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941406"
---
# <a name="getting-started-with-roslyn-analyzers"></a>開始使用 Roslyn 分析器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用 Visual Studio 中的即時、 以專案為基礎的程式碼分析器，API 作者可以送出定義域專屬的程式碼分析，其 NuGet 套件的一部分。  因為這些分析器由.NET 編譯器平台 (代號為"Roslyn")，它們就會產生程式碼中的警告，當您輸入時即使您已完成的一行 （不需等待建置您的程式碼，找出問題）。  分析器可能也會出現有透過立即清除您的程式碼讓您的 Visual Studio 燈泡提示的自動程式碼修正

## <a name="getting-started"></a>快速入門
[Roslyn 即時程式碼分析器簡介和逐步解說](https://msdn.microsoft.com/magazine/dn879356.aspx)

[加入程式碼修正的逐步解說：提供使用者修正分析器問題](https://msdn.microsoft.com/magazine/dn904670.aspx)

[簡介和逐步解說的真實世界分析器演講](http://channel9.msdn.com/events/Build/2015/3-725)

[真實世界的 Roslyn 分析器](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md)，您也可以觀看為[討論](http://channel9.msdn.com/events/Build/2015/3-725)

[在 GitHub 上的數個範例分組為三種類型的分析器](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[簡介與教學課程的幾個分析器的討論](http://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>其他資源
[GitHub OSS 網站上的多個 docs](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[實作與 GitHub 上的 Roslyn 分析器的 FxCop 規則](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
