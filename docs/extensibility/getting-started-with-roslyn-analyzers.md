---
title: 使用羅斯林分析器入門 |微軟文件
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc975ff4f142b85297c20f16ac399fce588c093b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711264"
---
# <a name="get-started-with-roslyn-analyzers"></a>使用羅斯林分析儀入門

借助 Visual Studio 中基於專案的即時代碼分析器,API 作者可以將特定於網域的代碼分析作為 NuGet 包的一部分。 由於這些分析器由 .NET 編譯器平臺(代號為"Roslyn")提供支援,因此,在您鍵入之前,甚至在您完成行之前,它們就可以在代碼中生成警告(無需再等待構建代碼以發現問題)。 分析器還可以透過 Visual Studio 燈泡提示器顯示自動代碼修復,以便您立即清理代碼。

## <a name="get-started"></a>開始使用

[羅斯林分析儀概述](../code-quality/roslyn-analyzers-overview.md)

[教學課程：撰寫您的第一個分析器和程式碼修正](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[新增代碼修復演練:為使用者提供分析器問題的修復](https://msdn.microsoft.com/magazine/dn904670.aspx)

[現實世界羅斯林分析器](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md),您也可以觀看作為[談話](https://channel9.msdn.com/events/Build/2015/3-725)

[GitHub 的幾個範例,分為三種分析器](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>另請參閱

- [.NET 編譯器平臺套件版本引用](roslyn-version-support.md)
- [GitHub OSS 網站上的更多文件](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [使用羅斯林分析儀實現的FxCop規則](../code-quality/fxcop-rule-port-status.md)
