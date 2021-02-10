---
title: 支援的 Roslyn 套件版本對應
description: 本文說明 Visual Studio 的不同版本支援哪些 .NET 編譯器平臺 (Roslyn) 封裝版本。
ms.custom: SEO-VS-2020
ms.date: 04/29/2019
ms.topic: reference
helpviewer_keywords:
- roslyn package versions
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f76a8dcdbb644fe456c62fca7de6fb7afe96d556
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935883"
---
# <a name="net-compiler-platform-package-version-reference"></a>.NET 編譯器平臺套件版本參考

下表顯示支援不同版本 Visual Studio 的 [.net 編譯器平臺 (Roslyn) 封裝](https://www.nuget.org/packages/Microsoft.Net.Compilers/) 版本。

例如，為了確保您的自訂分析器適用于所有版本的 Visual Studio 2017，它應該以 Microsoft.Net 2.0 版為目標。

| Roslyn 套件版本 | 支援的最低 Visual Studio 版本 |
| - | - |
| 3.x | Visual Studio 2019 |
| 2.10.0 | Visual Studio 2017 15.9 版 |
| 2.9.0 | Visual Studio 2017 15.8 版 |
| 2.8.2 | Visual Studio 2017 15.7 版 |
| 2.7.0 | Visual Studio 2017 15.6 版 |
| 2.6.1 | Visual Studio 2017 15.5 版 |
| 2.4.0 | Visual Studio 2017 15.4 版 |
| 2.3.2 | Visual Studio 2017 15.3 版 |
| 2.2.0 | Visual Studio 2017 15.2 版 |
| 2.1.0 | Visual Studio 2017 15.1 版 |
| 2.0.0 | Visual Studio 2017 RTM |
| 1.3.2 | Visual Studio 2015 update 3 |
| 1.2.2 | Visual Studio 2015 update 2 |
| 1.1.1 | Visual Studio 2015 update 1 |
| 1.0.1 | Visual Studio 2015 RTM |

> [!TIP]
> 針對支援的最低 Visual Studio 版本為 Visual Studio 2017 版本的 Roslyn 套件，也支援 Visual Studio 2019 的所有版本，因為稍後會提供這些版本。

## <a name="see-also"></a>另請參閱

- [.NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)
- [開始使用 Roslyn 分析器](getting-started-with-roslyn-analyzers.md)
