---
title: "專案內容 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 368f6ecb67bc8b01df975da6e68e95b553a0e31d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="project-context"></a>專案內容
當使用者加入或適用於專案和專案項目時，IDE 會使用專案內容的概念來決定應該執行的各種方式作業。  
  
 一般而言，檔案是藉由選取的使用者明確建立標準專案物件**新專案**命令或使用選取**開啟專案**命令**檔案**功能表。 在這些情況下，檔案會建立專案的內容中開啟及專案類型會定義編輯文件的內容。  
  
 有些專案提供非常豐富的內容。 例如，專案管理專案範圍，以程式設計方式命名空間或資料繫結的專案範圍的資料庫連接。 使用者經常可以開啟檔案或資料庫連接是直接使用特定的專案物件，例如 [方案總管] 中顯示的專案項目。  
  
 在其他時候，專案項目的內容未明確指定。 比方說，內容項目的不是使用使用者選取 [開啟檔案時**開啟現有檔案**命令**檔案**功能表上，偵錯工具操作檔案，或當使用者按一下時**檔案中尋找**命令**尋找和取代**] 對話方塊。 若要處理這些情況下，IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>管理尋找最佳的專案開啟的文件的程序。  
  
## <a name="see-also"></a>另請參閱  
 [專案優先順序](../../extensibility/internals/project-priority.md)   
 [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)