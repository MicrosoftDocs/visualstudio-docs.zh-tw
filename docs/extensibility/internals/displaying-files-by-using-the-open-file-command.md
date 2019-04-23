---
title: 使用 開啟檔案命令顯示檔案 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9cc24e259ac5aaa8526d5855a1662c146e1438ff
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60112152"
---
# <a name="display-files-by-using-the-open-file-command"></a>使用 開啟檔案命令顯示檔案
下列步驟描述 IDE 如何處理**開啟的檔案**命令，其位於**檔案**功能表中的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 步驟也會說明專案應該如何回應來自這個命令的呼叫。

 當使用者按一下**開啟的檔案**命令**檔案**功能表上，並選取 [從檔案**開啟檔案**] 對話方塊中，下列程序就會發生：

1. 使用執行中的文件表格，IDE 就會判斷檔案是否已在專案中開啟。

    - 如果檔案開啟時，IDE 會 resurfaces 視窗。

    - 如果檔案未開啟，IDE 就會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>來查詢每個專案，以判斷哪個專案可以開啟檔案。

        > [!NOTE]
        >  在您專案實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>，提供優先順序值，指出您的專案會開啟檔案的層級。 中提供優先順序值<xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>列舉型別。

2. 每個專案以表示重要性的優先順序層級這會造成正在開啟檔案的專案。

3. IDE 會使用下列準則來判斷哪一個專案開啟的檔案：

    - 以最高優先權的專案 (`DP_Intrinsic`) 開啟檔案。 如果多個專案會回應此優先順序，以回應的第一個專案開啟的檔案。

    - 如果沒有任何專案回應具有最高優先順序 (`DP_Intrinsic`)，但所有專案的都回應是相同且較低的優先順序，而作用中的專案開啟的檔案。 如果沒有任何專案是使用中，回應的第一個專案開啟的檔案。

    - 如果沒有任何專案宣告檔案的擁有權 (`DP_Unsupported`)，其他檔案專案中開啟檔案。

         如果建立的其他檔案專案執行個體，則專案一律會回應該值`DP_CanAddAsExternal`。 這個值表示專案可以開啟檔案。 此專案用來儲存開啟的檔案不在任何其他專案中。 在此專案中的項目清單不會保存;此專案會顯示在**方案總管 中**它在使用時才開啟檔案。

         其他檔案專案並不表示它可以開啟檔案，方法是，如果尚未建立的專案執行個體。 在此情況下，IDE 會建立其他檔案專案的執行個體，並告知專案，以開啟該檔案。

4. IDE 判斷哪一個專案開啟的檔案，因為它會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>該專案的方法。

5. 專案則會有使用專案特定編輯器] 或 [標準編輯器開啟檔案的選項。 如需詳細資訊，請參閱[如何：開啟專案特定的編輯器](../../extensibility/how-to-open-project-specific-editors.md)和[How to:開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)分別。

## <a name="see-also"></a>另請參閱
- [使用 [開啟] 命令來顯示檔案](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)
- [如何：開啟專案特定的編輯器](../../extensibility/how-to-open-project-specific-editors.md)
- [如何：開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)