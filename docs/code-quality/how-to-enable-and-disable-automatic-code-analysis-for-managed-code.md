---
title: 停用舊版程式碼分析
ms.date: 10/04/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c00a66a856dccb0ccb488937b935d9150ffc0266
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975085"
---
# <a name="how-to-enable-and-disable-binary-code-analysis-for-managed-code"></a>HOW TO：啟用和停用受控碼的二進位程式碼分析

您可以設定在每個 managed 程式碼專案組建之後執行舊版程式碼分析（二進位分析）。 您也可以針對每個組建設定（例如，[debug] 和 [發行]）提供不同的設定。

> [!NOTE]
> 舊版分析不適用於 .NET Core 和 .NET Standard 應用程式等較新的專案類型。 這些專案使用以[.NET Compiler Platform 為基礎的程式碼分析器](roslyn-analyzers-overview.md)，在即時和組建期間分析程式碼。 如需在這些專案中停用原始程式碼分析的詳細資訊，請參閱[如何停用原始程式碼分析](disable-code-analysis.md)。

若要啟用或停用舊版程式碼分析：

1. 在**方案總管**中，以滑鼠右鍵按一下專案，然後選擇 [**屬性**]。

2. 在專案的 [屬性] 對話方塊中，選擇 [程式**代碼分析**] 索引標籤。

3. 在 [設定] 和 [**平臺**] 的目標**平臺中指定**組建類型。 （僅限 Non-.NET Core/.NET Standard 專案）。

::: moniker range="vs-2017"

4. 若要啟用或停用自動程式碼分析，請選取或清除 [**在組建上啟用程式碼分析**] 核取方塊。

::: moniker-end

::: moniker range=">=vs-2019"

4. 若要啟用或停用自動程式碼分析，請選取或清除 [**二進位分析器**] 區段中的 [**在組建上執行**] 核取方塊。

   ![在 Visual Studio 中針對組建選項執行二進位程式碼分析](media/run-on-build-binary-analyzers.png)

::: moniker-end

> [!NOTE]
> 停用組建的二進位程式碼分析並不會影響以[.NET Compiler Platform 為基礎的程式碼分析器](roslyn-analyzers-overview.md)，如果您將其安裝為 NuGet 套件，則一律會在組建中執行。 如需停用這些分析器之分析的詳細資訊，請參閱[如何停用原始程式碼分析](disable-code-analysis.md)。