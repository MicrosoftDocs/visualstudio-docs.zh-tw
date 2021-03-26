---
title: .NET Compiler Platform (&quot; Roslyn &quot;) 擴充性 |Microsoft Docs
description: 瞭解 .NET Compiler Platform，讓工具和開發人員能夠在豐富的資訊編譯器中分享有關程式的資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: af9be2c4a57763b4521f3564e95c760e5bdd566d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091158"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET Compiler Platform (&quot; Roslyn &quot;) 擴充性
.NET Compiler Platform ( "Roslyn" ) 的核心任務是開啟 c # 和 Visual Basic 編譯器，並讓工具和開發人員在豐富的資訊編譯器中共用程式的相關資訊。 程式碼分析工具會改善程式碼品質，而程式碼產生器會協助應用程式結構。 當工具變得更聰明時，他們需要存取更多的深入程式碼知識，而且只有編譯器才擁有。 Roslyn 編譯器會提供 Api，讓您可以在工具和應用程式中用於程式碼相關工作，而不是不透明的轉譯程式 (中的原始程式碼和物件程式碼) 。

 最棒的是，Roslyn 編譯器、其 Api、範例和逐步解說，以及建置於這些 Api 之上的實際工具，都是 [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn)的完全開放原始碼。 若要深入瞭解並開始使用 Roslyn，請前往 OSS 網站。 您可以找到連結來取得可作為使用者使用的最新 c # 和 Visual Basic 功能，以及使用 Roslyn Api 作為工具產生器的入門連結。

## <a name="see-also"></a>另請參閱
- [開始使用 Roslyn 分析器](../extensibility/getting-started-with-roslyn-analyzers.md)
