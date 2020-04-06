---
title: 使用開啟的檔案命令顯示檔案 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc18442c55b6989c4d8668e1425fdd62a2d4b1b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708601"
---
# <a name="display-files-by-using-the-open-file-command"></a>使用「開啟檔案」指令顯示檔案
以下步驟描述 IDE 如何處理**打開檔**命令,該命令在中的 **「檔」** 選單中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可用。 這些步驟還描述了專案應如何回應源自此命令的調用。

 當使用者按下 **「檔案**」 選單上的 **「開啟檔案」** 命令,並從 **「打開檔案」** 對話框中選擇檔案時,將發生以下過程:

1. 使用正在運行的文檔表,IDE 確定檔是否已在專案中打開。

    - 如果文件處於打開狀態,IDE 將重新顯示視窗。

    - 如果檔未打開,IDE 將調<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>用 查詢每個專案以確定哪個專案可以打開該檔。

        > [!NOTE]
        > 在的項目實現中<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>,提供了一個優先順序值,指示專案打開檔的水準。 枚舉中<xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>提供了優先順序值。

2. 每個專案都回應一個優先順序,指示它是打開檔的專案的重要性。

3. IDE 使用以下條件來確定哪個項目開啟檔案:

    - 使用最高優先權(`DP_Intrinsic`) 回應的項目將打開該檔。 如果多個專案回應此優先順序,則第一個回應的專案將打開該檔。

    - 如果沒有專案以最高優先順序 ()`DP_Intrinsic`回應,但所有專案都回應相同的較低優先順序,則活動專案將打開該檔。 如果沒有專案處於活動狀態,則第一個回應的專案將打開該檔。

    - 如果沒有項目聲明檔的擁有權 (),`DP_Unsupported`則「雜項檔」 專案將打開該檔。

         如果建立了「雜項檔」 項目的實體,則是一個設定應該`DP_CanAddAsExternal`值 。 此值指示專案可以打開該檔。 此專案用於容納不在任何其他專案中的打開檔。 此專案中的專案清單不持久化;因此,該專案中的專案清單不會保留。僅當此專案用於打開檔時,該專案才在**解決方案資源管理器**中可見。

         如果「雜項檔」專案未指示可以打開該檔,則尚未創建該專案的實例。 在這種情況下,IDE 將創建「雜項檔」專案的實例,並告訴專案打開該檔。

4. 一旦IDE確定哪個項目打開該檔,它將調用該專案<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>上的方法。

5. 然後,專案可以選擇使用特定於專案的編輯器或標準編輯器打開檔。 有關詳細資訊,請參閱[如何:開啟特定於項目的編輯器](../../extensibility/how-to-open-project-specific-editors.md)和[如何:分別開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)。

## <a name="see-also"></a>另請參閱
- [使用「開啟使用」指令顯示檔案](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [開啟並儲存項目項目項目](../../extensibility/internals/opening-and-saving-project-items.md)
- [如何:開啟特定於項目的編輯器](../../extensibility/how-to-open-project-specific-editors.md)
- [如何:開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)
