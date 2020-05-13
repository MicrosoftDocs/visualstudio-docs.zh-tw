---
title: .NET 編譯器&quot;平臺&quot;( 羅斯林 ) 可擴充性 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62ceac6e2be8a0a84d82f6b86b685c7c8b20a182
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712070"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET 編譯器&quot;平臺&quot;(羅斯林 ) 可擴充性
.NET 編譯器平臺 ("Roslyn") 的核心任務是打開 C# 和 Visual Basic 編譯器,並允許工具和開發人員共用編譯器對程式的豐富資訊。 代碼分析工具提高了代碼品質,代碼生成器有助於應用程式構建。 隨著工具變得越來越智慧,他們需要訪問越來越多的只有編譯器才具備的深層代碼知識。 Roslyn 編譯器不是不透明的轉換器(原始碼和物件代碼出),而是提供 API,可用於工具和應用程式中的代碼相關任務。

 最好的部分是,Roslyn 編譯器、它們的 API、範例和演練,以及基於這些 API 構建的實際工具都是[github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn)完全開源的。 請造訪 OSS 網站瞭解更多資訊,並開始使用羅斯林。 您將找到連結來獲取最新的 C# 和 Visual Basic 功能,這些功能可用於最終使用者,以及利用 Roslyn API 開始作為工具生成器的連結。

## <a name="see-also"></a>另請參閱
- [使用羅斯林分析儀入門](../extensibility/getting-started-with-roslyn-analyzers.md)
