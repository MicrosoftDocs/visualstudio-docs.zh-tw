---
title: 受控碼的程式碼分析
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c3231efbac4f4c101632e281fd54718e688bb885
ms.sourcegitcommit: fd5a5b057df3d733f5224c305096907989811f85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2019
ms.locfileid: "67195136"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>在 Visual Studio 中的 managed 程式碼的程式碼分析的概觀

Visual Studio 可以執行的 managed 程式碼的程式碼分析，有兩種： 使用[二進位分析器](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)，也稱為 FxCop 靜態分析 managed 組件，並以更多新式[Roslyn 分析器](../code-quality/roslyn-analyzers-overview.md)。 Roslyn 分析器，當您輸入時，請分析即時程式碼，取代 FxCop 靜態分析，只會在建置之後的分析您的程式碼。  

## <a name="see-also"></a>另請參閱

- [Roslyn 分析器的概觀](../code-quality/roslyn-analyzers-overview.md)
