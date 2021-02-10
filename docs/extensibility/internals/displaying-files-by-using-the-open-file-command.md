---
title: 使用開啟檔案命令顯示檔案 |Microsoft Docs
description: 瞭解 Visual Studio 整合式開發環境 (IDE) 如何處理 [檔案] 功能表上的 [開啟檔案] 命令以顯示檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 96f92aa921c7bb78511ed685d846e288518258fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946822"
---
# <a name="display-files-by-using-the-open-file-command"></a>使用開啟檔案命令顯示檔案
下列步驟說明 IDE 如何處理 [ **開啟** 檔案] 命令 **，該命令** 可在的 [檔案] 功能表上取得 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 這些步驟也會說明專案如何回應源自此命令的呼叫。

 當使用者按一下 [檔案 **] 功能表上的 [** **開啟** 檔案] 命令，並從 [**開啟** 檔案] 對話方塊中選取檔案時，會發生下列進程：

1. IDE 會使用執行中的檔資料表，判斷檔案是否已在專案中開啟。

    - 如果檔案已開啟，IDE 就會 resurfaces 視窗。

    - 如果檔案未開啟，IDE 會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 以查詢每個專案，以判斷哪個專案可以開啟檔案。

        > [!NOTE]
        > 在的專案執行中 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> ，提供優先順序值，指出專案開啟檔案的層級。 列舉中會提供優先權值 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 。

2. 每個專案都會以優先權層級回應，指出它在專案上開啟檔案的重要性。

3. IDE 會使用下列準則來判斷哪個專案會開啟檔案：

    - 以最高優先順序回應的專案 (`DP_Intrinsic`) 會開啟檔案。 如果有一個以上的專案以這個優先權回應，則第一個回應專案會開啟檔案。

    - 如果沒有任何專案以最高優先權 (`DP_Intrinsic`) ，但是所有專案都以相同、較低的優先順序回應，則使用中的專案會開啟該檔案。 如果沒有作用中的專案，則第一個回應專案會開啟檔案。

    - 如果沒有任何專案宣告檔案的擁有權 (`DP_Unsupported`) ，[其他檔案] 專案就會開啟該檔案。

         如果建立了其他檔案專案的實例，專案一律會以值回應 `DP_CanAddAsExternal` 。 這個值表示專案可以開啟檔案。 此專案用來存放不在任何其他專案中的開啟檔案。 不會保存此專案中的專案清單;只有當這個專案用來開啟檔案時，才會顯示在 **方案總管** 中。

         如果 [其他檔案] 專案沒有指出它可以開啟檔案，表示尚未建立專案的實例。 在此情況下，IDE 會建立其他檔案專案的實例，並告知專案開啟該檔案。

4. 一旦 IDE 判斷開啟檔案的專案，就會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 在該專案上呼叫方法。

5. 專案接著可以選擇使用專案特定的編輯器或標準編輯器來開啟檔案。 如需詳細資訊，請參閱 [如何：分別開啟專案特定的編輯器](../../extensibility/how-to-open-project-specific-editors.md) 和 [如何：開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)。

## <a name="see-also"></a>另請參閱
- [使用開啟檔案命令顯示檔案](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [開啟和儲存專案專案](../../extensibility/internals/opening-and-saving-project-items.md)
- [如何：開啟專案特定的編輯器](../../extensibility/how-to-open-project-specific-editors.md)
- [如何：開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)
