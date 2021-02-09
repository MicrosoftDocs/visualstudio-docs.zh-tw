---
title: 工作流程設計工具的錯誤訊息
description: 瞭解使用工作流程設計工具時，您可能會遇到的錯誤訊息類型。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3e9e0cc71018d85d91e88d2969e76b49fcf9066a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876572"
---
# <a name="error-messages-in-workflow-designer"></a>工作流程設計工具的錯誤訊息

本主題說明使用工作流程設計工具時可能遇到的錯誤訊息類型。

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>在工作流程設計工具中發生錯誤的情況

在下列情況中，工作流程設計工具發生錯誤：

1. 此為運算式中的錯誤。

2. 未滿足活動的驗證條件約束。

3. XAML 檔中發生導致活動無法載入的錯誤。

4. XAML 檔中發生導致工作流程無法載入的錯誤。

無效的運算式與不滿足驗證條件限制並不會造成工作流程建置失敗。 建立您的工作流程會成功，但是 <xref:System.Activities.InvalidWorkflowException> 會在執行時間擲回。 如果 XAML 中有錯誤，建置就會失敗。

在 Visual Studio 中，載入工作流程時，其錯誤會顯示在 [ **錯誤清單**] 中。 若要流覽至錯誤來源的活動，請按兩下 [ **錯誤清單**] 中的錯誤。

### <a name="expression-errors"></a>運算式錯誤
 如果有無效的運算式，則會在運算式旁出現內含白色驚嘆號的紅色圓圈來標註。 將游標移至這個圖示上方，隨即出現描述錯誤來源的工具提示。 在 Visual Studio 中，按一下運算式以查看將錯誤來源加上底線的行。 將游標移至這行文字上方，隨即出現描述錯誤來源的工具提示。

### <a name="activity-validation-errors"></a>活動驗證錯誤
 當未滿足活動的驗證條件限制時，活動的右上角會出現內含白色驚嘆號的紅色圓圈。 將游標移至這個圖示上方，隨即出現描述錯誤來源的工具提示。

### <a name="xaml-load-errors"></a>XAML 載入錯誤
 當活動無法載入時，會出現包含「因為 XAML 中的錯誤而無法載入活動」文字的紅色方塊。 這通常發生在無法解析活動的型別時。 選取紅色方塊並加以刪除，以刪除設計工具中無效的活動。

### <a name="workflow-load-errors"></a>工作流程載入錯誤
 當工作流程無法載入時，設計工具介面上會出現「工作流程設計工具遇到檔問題」文字，以及造成工作流程載入失敗的例外狀況資訊。 通常當無法剖析 XAML 檔時，就會發生這個錯誤。
