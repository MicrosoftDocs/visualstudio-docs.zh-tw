---
title: 受控碼的程式碼分析
ms.date: 08/27/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d13a8afdfcbeb6ae9f91e39779af8b82b2461000
ms.sourcegitcommit: 016bcdc7cd3e3619457beb321800e98544efb6c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2020
ms.locfileid: "89091393"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Visual Studio 中的 .NET 程式碼分析總覽

Visual Studio 可以用兩種方式執行 managed 程式碼的程式碼分析：使用 [舊版分析](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)，也稱為 managed 元件的 FxCop 靜態分析，以及更新式的 [.NET Compiler Platform 型程式碼分析器](../code-quality/roslyn-analyzers-overview.md)。 以 .NET Compiler Platform 為基礎的程式碼分析器，會在您輸入時即時分析您的程式碼，取代舊版的 FxCop 靜態程式碼分析，而這只會分析編譯的程式碼。
