---
title: 專案內容 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8afa595a264f218fcc20f18de1c261a9ead6e030
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725776"
---
# <a name="project-context"></a>專案內容
當使用者加入或使用專案和專案專案時，IDE 會使用專案內容的概念來判斷應該如何執行各種作業。

 一般來說，檔案是使用者明確建立的標準專案物件，其方式是選取 [**新增專案**] 命令，或選取 [檔案 **] 功能表上**的 [**開啟專案**] 命令來提供。 在這些情況下，會在專案的內容中建立和開啟檔案，而專案類型則會定義內容來編輯檔。

 某些專案提供非常豐富的內容。 例如，專案會管理專案範圍、程式設計的命名空間或專案範圍的資料庫連接，以進行資料系結。 使用者通常可以使用特定的專案物件（例如方案總管中顯示的專案專案），直接開啟檔案或資料庫連接。

 在其他時間，則不會明確指定專案的專案內容。 例如，當使用者開啟檔案時，如果**選取 [檔案] 功能表上**的 [**開啟現有**檔案] 命令、在檔案上操作偵錯工具，或當使用者按一下 [ **檔案中的尋找檔案] 命令時，就無法使用專案的內容[尋找和取代**] 對話方塊。 為了處理這些情況，IDE 會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> 來管理尋找最佳專案以開啟檔的程式。

## <a name="see-also"></a>請參閱
- [專案優先順序](../../extensibility/internals/project-priority.md)
- [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)