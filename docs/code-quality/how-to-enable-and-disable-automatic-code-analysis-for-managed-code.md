---
title: 啟用或停用程式碼分析
ms.date: 10/25/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4878c25021d87e91f6a575d11a876d7aac2455d5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55918126"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>HOW TO：啟用和停用 managed 程式碼的自動程式碼分析

您可以設定 （靜態） 的程式碼分析，managed 程式碼專案的每次建置之後執行。 您可以設定不同的程式碼分析屬性，每個組建組態，例如，偵錯和發行。

本文適用於只為靜態程式碼分析，並使用未即時程式碼分析[Roslyn 程式碼分析器](roslyn-analyzers-overview.md)。

## <a name="to-enable-or-disable-automatic-code-analysis"></a>若要啟用或停用自動程式碼分析

1. 在 **方案總管**，以滑鼠右鍵按一下專案，然後選擇**屬性**。

1. 在專案 屬性 對話方塊中，選擇**程式碼分析** 索引標籤。

   > [!TIP]
   > 較新的專案類型，例如.NET Core 和.NET Standard 的應用程式沒有**程式碼分析** 索引標籤。靜態程式碼分析不適用於這些專案類型，但您仍能使用的即時程式碼分析[Roslyn 程式碼分析器](roslyn-analyzers-overview.md)。 若要隱藏警告的 Roslyn 程式碼分析器，請參閱這篇文章結尾處的附註。

1. 指定組建類型中的**組態**和中的目標平台**平台**。

1. 若要啟用或停用自動程式碼分析，請選取或清除**建置時啟用程式碼分析**核取方塊。

> [!NOTE]
> **建置時啟用程式碼分析**核取方塊只會影響靜態程式碼分析。 它不會影響[Roslyn 程式碼分析器](roslyn-analyzers-overview.md)，它一定會執行在 build 如果您安裝這些 NuGet 套件的形式。 如果您想要清除的分析器錯誤**錯誤清單**，您可以選擇隱藏所有目前的違規情形**分析** > **執行程式碼分析和隱藏作用中問題**功能表列上。 如需詳細資訊，請參閱 <<c0> [ 隱藏違規](use-roslyn-analyzers.md#suppress-violations)。
