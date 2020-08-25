---
title: 受控碼的程式碼分析
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e6515c0df7a9c3389e754d5238788d716be49e2e
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800082"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Visual Studio 中 managed 程式碼的程式碼分析總覽

Visual Studio 可以用兩種方式執行 managed 程式碼的程式碼分析：
- 使用 [舊版分析](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)，也稱為 managed 元件的 FxCop 靜態分析。
- 使用更新式的 [.NET Compiler Platform 型程式碼分析器](../code-quality/roslyn-analyzers-overview.md)。 以 .NET Compiler Platform 為基礎的程式碼分析器，會在您輸入時即時分析您的程式碼，取代舊版的 FxCop 靜態程式碼分析，而這只會分析編譯的程式碼。