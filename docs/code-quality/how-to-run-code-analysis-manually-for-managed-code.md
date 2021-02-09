---
title: 如何針對 .NET 手動執行程式碼分析
ms.date: 09/02/2020
description: '瞭解如何在 Visual Studio 2019 16.5 版或更新版本中手動執行程式碼分析。 瞭解如何在 c # 或 Visual Basic 程式碼上執行 Roslyn 分析器。'
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 997fc6f6ecb8ffbd8c48e2352dcc9ae2f6092211
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860018"
---
# <a name="run-code-analysis-manually-for-net"></a>針對 .NET 手動執行程式碼分析
根據預設，.NET Compiler Platform ( "Roslyn" ) 分析器會在您透過進行即時分析以及在組建期間進行輸入，來分析您的 c # 或 Visual Basic 程式碼。 因此，您通常不需要手動觸發程式碼分析。 不過，在某些情況下，您可能會想要手動觸發程式碼分析：

> [!NOTE]
> 手動執行程式碼分析需要 Visual Studio 2019 16.5 版或更新版本

- 根據預設，即時程式碼分析只會針對 Visual Studio 中開啟的檔案執行分析器。 不過，您可能會想要針對特定專案或方案中的所有檔案，查看程式碼分析警告。 如果是，您會想要在專案或方案上觸發一次程式碼分析。 或者，您可以啟用持續即時程式碼分析，以在整個解決方案上執行。 如需詳細資訊，請參閱 [如何：設定 managed 程式碼的即時程式碼分析範圍](./configure-live-code-analysis-scope-managed-code.md)。
- 您可能會想要使用隨選程式碼分析執行工作流程，而不需要持續即時分析或建立時間分析。 若是如此，您可以在即時分析和/或組建期間停用分析器執行。 如需停用分析的相關資訊，請參閱 [如何停用原始程式碼分析](disable-code-analysis.md)。 然後您會想要在專案或方案上手動觸發程式碼分析一次。

### <a name="run-code-analysis-manually"></a>手動執行程式碼分析

1. 在 **方案總管** 中，選取專案。

2. 在 [**分析**] 功能表上，選取 [針對 *專案名稱***執行程式碼分析**]。

程式碼分析將開始在背景中執行。 您應該會在左下角的 Visual Studio 狀態列中看到 [ **正在執行程式碼分析 \<project>** ] 的訊息。 程式碼分析完成後，狀態訊息會變更為 [**已完成的 \<project> 程式碼分析**]。 錯誤清單很快就會以所有程式碼分析診斷進行重新整理。
