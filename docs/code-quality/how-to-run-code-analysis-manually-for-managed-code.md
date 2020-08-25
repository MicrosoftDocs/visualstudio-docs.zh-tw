---
title: 如何針對 managed 程式碼手動執行程式碼分析
ms.date: 11/04/2019
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mavasani
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1077e2cdae790fe8a7b7309b1e6427cd3ef81b48
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800160"
---
# <a name="how-to-run-code-analysis-manually-for-managed-code-requires-visual-studio-2019-version-165-or-later"></a>如何：針對 managed 程式碼手動執行程式碼分析 (需要 Visual Studio 2019 16.5 版或更新版本) 
根據預設，.NET Compiler Platform ( "Roslyn" ) 程式碼分析器會在您透過進行即時分析以及在組建期間進行輸入時，分析您的 c # 或 Visual Basic 程式碼。 因此，您通常不需要手動觸發程式碼分析。 不過，在某些情況下，您可能會想要手動觸發程式碼分析：

- 根據預設，即時程式碼分析只會針對 Visual Studio 中開啟的檔案執行分析器。 不過，您可能會想要針對特定專案或方案中的所有檔案，查看程式碼分析警告。 如果是，您會想要在專案或方案上觸發一次程式碼分析。 或者，您可以啟用持續即時程式碼分析，以在整個解決方案上執行。 如需詳細資訊，請參閱 [如何：設定 managed 程式碼的即時程式碼分析範圍](./configure-live-code-analysis-scope-managed-code.md)。
- 您可能會想要使用隨選程式碼分析執行工作流程，而不需要持續即時分析或建立時間分析。 若是如此，您可以在即時分析和/或組建期間停用分析器執行。 如需停用分析的相關資訊，請參閱 [如何停用原始程式碼分析](disable-code-analysis.md)。 然後您會想要在專案或方案上手動觸發程式碼分析一次。 

### <a name="run-code-analysis-manually"></a>手動執行程式碼分析

1. 在 **方案總管**中，選擇專案。

2. 在 [**分析**] 功能表上，選取 [針對*專案名稱***執行程式碼分析**]。

程式碼分析將開始在背景中執行。 您應該會在左下角的 Visual Studio 狀態列中看到 [ **正在執行程式碼分析 \<project> ** ] 的訊息。 程式碼分析完成後，狀態訊息會變更為 [**已完成的 \<project> 程式碼分析**]。 錯誤清單很快就會以所有程式碼分析診斷進行重新整理。
