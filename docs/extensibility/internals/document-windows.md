---
title: 文件視窗 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f2fd5b77bfc853da1c6098c00110e75b9d9acb75
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="document-windows"></a>文件視窗
在 Visual Studio*文件視窗*是相關聯的多重文件介面 (MDI) 視窗框架的子視窗。 文件視窗通常用於顯示和修改原始程式碼或文字，但它們也可以裝載其他功能的類型。 文件視窗：  
  
-   可以組織 MDI 父系中的另一個水平或垂直索引標籤群組中，因此可以同時檢視多個檔案。  
  
-   可停駐在 MDI 父代中的任何順序。  
  
-   可以是自由浮動。  
  
-   連結到其他 MDI 視窗索引標籤順序。  
  
 群組的命令，停駐和浮動可以找到文件視窗索引標籤的捷徑功能表上。  
  
 如需 Visual Studio 中的視窗行為的詳細資訊，請參閱[自訂視窗版面配置](../../ide/customizing-window-layouts-in-visual-studio.md)。  
  
## <a name="document-window-implementation"></a>文件視窗實作  
 文件視窗是由實作編輯器建立的。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>介面建立的具現化編輯器一部分的文件視窗。 如需詳細資訊，請參閱[在編輯器中的傳統介面](../../extensibility/legacy-interfaces-in-the-editor.md)。  
  
> [!NOTE]
>  若要提供向後和向前巡覽點視窗中的，實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation>介面。 文字編輯器會使用文字標記來識別瀏覽文件中的點。  
  
## <a name="the-running-document-table"></a>執行 Document 資料表  
 IDE 使用執行中文件資料表 (RDT) 來追蹤每個文件視窗的狀態。 RDT 是透過哪份文件視窗會收到通知的事件，例如關閉方案時，或已對檔案進行編輯的機制。 如需詳細資訊，請參閱[執行中的文件表格](../../extensibility/internals/running-document-table.md)。  
  
## <a name="see-also"></a>另請參閱  
 [已延遲載入文件](../../extensibility/internals/delayed-document-loading.md)