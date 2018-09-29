---
title: 如何：啟用和停用 Managed 程式碼的自動程式碼分析
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3113143b07ccb6f765cd0cf1735b34be6e952c72
ms.sourcegitcommit: 6672a1e9d135d7e5cca3cceea07c6fe5a0871475
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2018
ms.locfileid: "47443541"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>如何： 啟用和停用 managed 程式碼的自動程式碼分析

您可以設定程式碼分析，managed 程式碼專案的每次建置之後執行。 您可以設定不同的程式碼分析屬性，每個組建組態，例如，偵錯和發行。

## <a name="to-enable-or-disable-automatic-code-analysis"></a>若要啟用或停用自動程式碼分析

1. 在 **方案總管**，以滑鼠右鍵按一下專案，然後選擇**屬性**。

1. 在專案 屬性 對話方塊中，選擇**程式碼分析** 索引標籤。

1. 指定組建類型中的**組態**和中的目標平台**平台**。

1. 若要啟用或停用自動程式碼分析，請選取或清除**建置時啟用程式碼分析**核取方塊。

> [!NOTE]
> **建置時啟用程式碼分析**核取方塊只會影響靜態程式碼分析。 它不會影響[Roslyn 程式碼分析器](roslyn-analyzers-overview.md)，它一定會執行在 build 如果您安裝這些 NuGet 套件的形式。 如果您想要清除的分析器錯誤**錯誤清單**，您可以選擇隱藏所有目前的違規情形**分析** > **執行程式碼分析和隱藏作用中問題**功能表列上。 如需詳細資訊，請參閱 <<c0> [ 隱藏違規](use-roslyn-analyzers.md#suppress-violations)。
