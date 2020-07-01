---
title: 如何針對受控碼手動執行程式碼分析
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
ms.openlocfilehash: 874d95b65b99af4b5a6b00d45101236f62db3df1
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769367"
---
# <a name="how-to-run-code-analysis-manually-for-managed-code-requires-visual-studio-2019-version-165-or-later"></a>如何：針對受控碼手動執行程式碼分析（需要 Visual Studio 2019 16.5 版或更新版本）
根據預設，.NET Compiler Platform （"Roslyn"）程式碼分析器會在您進行即時分析時，以及在組建期間，分析您的 c # 或 Visual Basic 程式碼。 因此，您通常不需要手動觸發程式碼分析。 不過，在某些情況下，您可能會想要手動觸發程式碼分析：

- 根據預設，即時程式碼分析只會針對 Visual Studio 中開啟的檔案執行分析器。 不過，您可能會想要針對特定專案或方案中的所有檔案查看程式碼分析警告。 若是如此，您會想要在專案或方案上觸發一次程式碼分析。 或者，您可以啟用持續即時程式碼分析，以在整個解決方案上執行。 如需詳細資訊，請參閱[如何：設定受控碼的即時程式碼分析範圍](./configure-live-code-analysis-scope-managed-code.md)。
- 您可能想要透過持續即時分析或建立時間分析，視需要進行程式碼分析執行工作流程。 若是如此，您可以在即時分析和/或組建期間停用分析器執行。 如需停用分析的詳細資訊，請參閱[如何停用原始程式碼分析](disable-code-analysis.md)。 然後，您會想要在專案或方案上手動觸發程式碼分析一次。 

### <a name="run-code-analysis-manually"></a>手動執行程式碼分析

1. 在**方案總管**中，按一下專案。

2. 在 [**分析**] 功能表上，按一下 [針對*專案名稱***執行程式碼分析**]。

程式碼分析會開始在背景中執行。 您應該會在左下角的 Visual Studio 狀態列中，看到 [**正在執行程式碼分析 \<project> ...** ] 訊息。 程式碼分析完成之後，狀態訊息會變更為 [**已完成的 \<project> 程式碼分析**]。 [錯誤清單] 很快就會使用所有程式碼分析診斷進行重新整理。
