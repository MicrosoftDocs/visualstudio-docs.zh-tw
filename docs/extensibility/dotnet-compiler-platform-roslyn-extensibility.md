---
title: .NET 編譯器平台 (&quot;Roslyn&quot;) 擴充性 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 119ccbc7a14f2879d27c9c8c8e20cf978593366a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710041"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET 編譯器平台 (&quot;Roslyn&quot;) 擴充性
.NET 編譯器平台 ("Roslyn") 的核心任務是開啟的 C# 和 Visual Basic 編譯器，並讓工具和開發人員共用的豐富資訊的編譯器中有關於程式。 程式碼分析工具改善程式碼品質，以及程式碼產生器協助建構應用程式。 因為工具變得越來越聰明，他們需要存取越來越多只有編譯器所擁有的深層的程式碼知識。 而不是不透明的轉譯器 （原始程式碼和出的物件程式碼），Roslyn 編譯器會提供 Api，您可以使用工具和應用程式中的程式碼相關工作。

 最大好處是 Roslyn 編譯器、 其 Api、 範例和逐步解說和這些 Api 為基礎的實際工具會在的所有完整的開放原始碼[github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn)。 請移至 進一步了解並開始使用 roslyn 建立與 OSS 站台。 您會發現連結，以取得最新版的C#和 Visual Basic 功能，您可以用作為終端使用者，以及連結來開始運用 Roslyn Api 是工具產生器。

## <a name="see-also"></a>另請參閱
- [開始使用 Roslyn 分析器](../extensibility/getting-started-with-roslyn-analyzers.md)