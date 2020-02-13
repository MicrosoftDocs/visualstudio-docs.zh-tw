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
ms.openlocfilehash: f4e5aad0ffcd6febce411d952b1b36a0669b109a
ms.sourcegitcommit: bb72ce6ec173f3ae06c7ae57322c43690f27553c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2020
ms.locfileid: "76967301"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Visual Studio 中受控碼的程式碼分析總覽

Visual Studio 可以透過兩種方式來執行 managed 程式碼的程式碼分析：使用[舊版分析](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)（也稱為 managed 元件的 FxCop 靜態分析），以及更現代化的[.NET Compiler Platform 程式碼分析器](../code-quality/roslyn-analyzers-overview.md)。 以 .NET Compiler Platform 為基礎的程式碼分析器（可在您輸入時即時分析您的程式碼），取代舊版 FxCop 靜態程式碼分析，這只會分析已編譯的程式碼。

