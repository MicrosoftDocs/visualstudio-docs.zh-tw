---
title: 專案內容 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4ee4da5fdea63cf1bdd33554c72f6dac30d0334
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943224"
---
# <a name="project-context"></a>專案內容
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

當使用者加入，或適用於專案和專案項目時，則 IDE 會使用專案內容的概念來判斷應該執行各種作業。  
  
 一般而言，檔案是藉由選取的使用者明確建立標準專案物件**新的專案**命令或可選取**開啟專案**命令**檔案**功能表。 在這些情況下，建立和開啟專案的內容中的檔案和專案類型可定義進行編輯文件的內容。  
  
 有些專案提供非常豐富的內容。 例如，專案管理專案範圍，以程式設計方式命名空間或進行資料繫結的專案範圍的資料庫連接。 使用者經常可以開啟檔案或資料庫連接是直接使用特定的專案物件，例如顯示在 [方案總管] 中的專案項目。  
  
 在其他時候，專案項目的內容未明確指定。 比方說，項目無法使用內容的使用者選取 [開啟檔案時**開啟現有的檔案**命令**檔案**時偵錯工具操作檔案，或當使用者按一下的功能表**檔案中尋找**命令**尋找和取代**] 對話方塊。 若要處理這些情況下，IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>管理尋找最佳的專案，以開啟文件的程序。  
  
## <a name="see-also"></a>另請參閱  
 [專案優先順序](../../extensibility/internals/project-priority.md)   
 [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)
