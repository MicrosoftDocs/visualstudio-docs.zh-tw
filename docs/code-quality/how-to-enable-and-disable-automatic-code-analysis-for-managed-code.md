---
title: 停用舊版程式碼分析
ms.date: 10/04/2019
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eb4422a12620d7650b4fe150313b10fe59835064
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801018"
---
# <a name="how-to-enable-and-disable-binary-code-analysis-for-managed-code"></a>如何：啟用和停用 managed 程式碼的二進位程式碼分析

您可以設定舊版程式碼分析， (二進位分析) 在 managed 程式碼專案的每個組建之後執行。 您也可以針對每個組建設定使用不同的設定，例如，debug 和 release。

> [!NOTE]
> 舊版分析不適用於較新的專案類型，例如 .NET Core 和 .NET Standard 應用程式。 這些專案使用以 [.NET Compiler Platform 為基礎的程式碼分析器](roslyn-analyzers-overview.md) 來分析程式碼（即時和在組建階段）。 如需有關在這些專案中停用原始程式碼分析的詳細資訊，請參閱 [如何停用原始程式碼分析](disable-code-analysis.md)。

若要啟用或停用舊版程式碼分析：

1. 在 **方案總管**中，選取並按住 (或以滑鼠右鍵按一下專案) ，然後選取 [ **屬性**]。

2. 在專案的 [屬性] 對話方塊中，移至 [程式 **代碼分析** ] 索引標籤。

3. 在 [**平臺**] 的 [設定] 和 [目標平臺 **] 中指定**組建類型。  (僅限 Non-.NET Core/.NET Standard 專案。 ) 

::: moniker range="vs-2017"

4. 若要啟用或停用自動程式碼分析，請選取或清除 [ **啟用組建的程式碼分析** ] 核取方塊。

::: moniker-end

::: moniker range=">=vs-2019"

4. 若要啟用或停用自動程式碼分析，請選取或清除 [**二進位分析器**] 區段中的 [**在組建上執行**] 核取方塊。

   ![針對 Visual Studio 中的組建選項執行二進位程式碼分析](media/run-on-build-binary-analyzers.png)

::: moniker-end

> [!NOTE]
> 停用組建上的二進位程式碼分析並不會影響以 [.NET Compiler Platform 為基礎的程式碼分析器](roslyn-analyzers-overview.md)，如果您將其安裝為 NuGet 套件，它一律會在組建中執行。 如需有關停用這些分析器分析的詳細資訊，請參閱 [如何停用原始程式碼分析](disable-code-analysis.md)。
