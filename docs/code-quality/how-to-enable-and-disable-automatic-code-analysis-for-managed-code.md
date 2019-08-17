---
title: 啟用或停用程式碼分析
ms.date: 10/25/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ec0a8a3f04830115d343fcef611cfbd338163395
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551042"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>HOW TO：啟用和停用受控碼的自動程式碼分析

您可以設定 (靜態) 程式碼分析, 以便在每個 managed 程式碼專案組建之後執行。 您可以為每個組建設定設定不同的程式碼分析屬性, 例如, [debug] 和 [release]。

本文僅適用于舊版分析, 而不是使用程式碼[分析器](roslyn-analyzers-overview.md)進行即時程式碼分析。

## <a name="to-enable-or-disable-automatic-code-analysis"></a>若要啟用或停用自動程式碼分析

1. 在**方案總管**中, 以滑鼠右鍵按一下專案, 然後選擇 [**屬性**]。

1. 在專案的 [屬性] 對話方塊中, 選擇 [程式**代碼分析**] 索引標籤。

   > [!TIP]
   > 較新的專案類型 (例如 .NET Core 和 .NET Standard 應用程式) 不會有 [程式**代碼分析**] 索引標籤。舊版分析不適用於這些專案類型, 但您可以使用[.NET Compiler Platform 型程式碼分析器](roslyn-analyzers-overview.md)來取得即時程式碼分析。 若要隱藏程式碼分析器的警告, 請參閱本文結尾處的附注。

1. 在 [設定] 和 [**平臺**] 的目標平臺中指定組建類型。

1. 若要啟用或停用自動程式碼分析, 請選取或清除 [**在組建上啟用程式碼分析**] 核取方塊。

> [!NOTE]
> [**在組建上啟用程式碼分析**] 核取方塊只會影響舊版分析。 它不會影響以[.NET Compiler Platform 為基礎的程式碼分析器](roslyn-analyzers-overview.md), 如果您將其安裝為 NuGet 套件, 則一律會在組建中執行。 如果您想要從**錯誤清單**清除分析器錯誤, 可以在功能表列上選擇 [**分析** > ] [**執行程式碼分析], 並隱藏**[作用中問題], 以隱藏所有目前的違規。 如需詳細資訊, 請參閱[隱藏違規](use-roslyn-analyzers.md#suppress-violations)。
