---
title: "使用 開啟檔案命令顯示檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f2cbcb6e6239552ae32c817601634587a2fe3a41
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="displaying-files-by-using-the-open-file-command"></a>使用 開啟檔案命令顯示檔案
下列步驟描述 IDE 如何處理**開啟檔案**命令，可用於**檔案**功能表[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 步驟也會說明專案應該如何回應來自這個命令的呼叫。  
  
 當使用者按一下**開啟檔案**命令**檔案**功能表上，並選取檔案，以從**開啟檔案**對話方塊中，執行下列程序。  
  
1.  使用執行中的文件表格，IDE 會判斷檔案是否已開啟的專案中。  
  
    -   如果已開啟的檔案，IDE 會 resurfaces 視窗。  
  
    -   如果檔案未開啟，IDE 便會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>查詢來判斷哪個專案也可以開啟檔案的每個專案。  
  
        > [!NOTE]
        >  在您的專案實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>，提供優先順序值，指出您的專案會開啟檔案的層級。 中提供的優先權值<xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>列舉型別。  
  
2.  每個專案會以優先權層級，指出重要性回應，這會造成正在開啟檔案的專案。  
  
3.  IDE 會使用下列準則來判斷哪個專案開啟的檔案：  
  
    -   具有最高的優先順序 (DP_Intrinsic) 回應的專案開啟的檔案。 如果這個優先權回應多個專案，若要回應的第一個專案開啟的檔案。  
  
    -   如果沒有專案回應，具有最高的優先順序 (DP_Intrinsic)，但具有相同，較低優先權的所有專案回應，使用中的專案開啟的檔案。 如果沒有任何專案是使用中，回應的第一個專案開啟的檔案。  
  
    -   如果沒有任何專案宣告檔案 (DP_Unsupported) 的擁有權，其他檔案專案開啟的檔案。  
  
         如果建立的其他檔案專案執行個體時，專案一律會回應該值 DP_CanAddAsExternal。 這個值表示專案可以開啟檔案。 這個專案用來儲存開啟的檔案不在任何其他專案中。 不會保存此專案中的項目清單。這個專案會顯示在**方案總管 中**它在使用時才開啟檔案。  
  
         其他檔案專案並不表示它可以開啟檔案，如果尚未建立的專案執行個體。 在此情況下，IDE 會建立其他檔案專案的執行個體，並會告知專案，開啟檔案。  
  
4.  IDE 判斷哪個專案開啟的檔案，因為它會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>該專案的方法。  
  
5.  專案然後沒有使用特定專案編輯器或標準編輯器開啟檔案的選項。 如需詳細資訊，請參閱[如何： 開啟專案的特定編輯器](../../extensibility/how-to-open-project-specific-editors.md)和[如何： 開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)分別。  
  
## <a name="see-also"></a>另請參閱  
 [使用 [開啟] 命令顯示檔案](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [開啟並儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)   
 [如何： 開啟專案的特定編輯器](../../extensibility/how-to-open-project-specific-editors.md)   
 [如何︰開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)