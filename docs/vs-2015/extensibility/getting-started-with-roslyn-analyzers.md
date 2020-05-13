---
title: 使用羅斯林分析器入門 |微軟文件
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a712697bafefcf115ce10d110c0ef3a4270c6acd
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444961"
---
# <a name="getting-started-with-roslyn-analyzers"></a>開始使用 Roslyn 分析器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

借助 Visual Studio 中基於專案的即時代碼分析器,API 作者可以將特定於網域的代碼分析作為 NuGet 包的一部分。  由於這些分析器由 .NET 編譯器平臺(代號為"Roslyn")提供支援,因此,在您鍵入之前,甚至在您完成行之前,它們就可以在代碼中生成警告(無需再等待構建代碼以發現問題)。  分析儀還可以透過 Visual Studio 燈泡提示器顯示自動代碼修復,以便您立即清理程式碼

## <a name="getting-started"></a>開始使用
[羅斯林即時代碼分析儀簡介和演練](https://msdn.microsoft.com/magazine/dn879356.aspx)

[新增代碼修復演練:為分析器問題為使用者提供修復](https://msdn.microsoft.com/magazine/dn904670.aspx)

[真實世界分析儀講座的介紹與演練](https://channel9.msdn.com/events/Build/2015/3-725)

[現實世界羅斯林分析器](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md),您也可以觀看作為[談話](https://channel9.msdn.com/events/Build/2015/3-725)

[GitHub 的幾個範例,分為三種分析器](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[幾個分析器談話的介紹和旅遊](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>其他資源
[GitHub OSS 網站上的更多文件](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[在 GitHub 上使用 Roslyn 分析器實現的 FxCop 規則](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
