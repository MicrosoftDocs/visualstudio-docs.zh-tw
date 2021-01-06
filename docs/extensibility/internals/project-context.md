---
title: 專案內容 |Microsoft Docs
description: 瞭解 Visual Studio IDE 如何使用專案內容來決定當使用者加入或處理專案和專案專案時，如何執行作業。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc4234481023592595de2df482d5ff6c2227a95e
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877659"
---
# <a name="project-context"></a>專案內容
當使用者加入或使用專案和專案專案時，IDE 會使用專案內容的概念來決定應該如何執行各種作業。

 一般而言，檔案是使用者明確建立的標準專案物件，方法是選取 [**新增專案**] 命令，或選取 [檔案 **] 功能表上** 的 [**開啟專案**] 命令以提供使用。 在這些情況下，會在專案的內容中建立和開啟檔案，而專案類型會定義編輯檔的內容。

 某些專案提供非常豐富的內容。 例如，專案會管理專案範圍、程式設計的命名空間或專案範圍的資料庫連接以進行資料系結。 使用者通常可以使用特定的專案物件（例如方案總管中顯示的專案專案），直接開啟檔案或資料庫連接。

 在其他情況下，不會明確指定專案的專案內容。 例如，當使用者開啟檔案時，無法使用專案的內容，方法是 **選取 [檔案] 功能表上** 的 [**開啟現有** 檔案] 命令、偵錯工具在檔案上運作，或是當使用者按一下 [**尋找和取代**] 對話方塊中的 [檔案 **中尋找**] 命令。 為了處理這些情況，IDE 會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> 來管理尋找最佳專案以開啟檔的進程。

## <a name="see-also"></a>請參閱
- [專案優先順序](../../extensibility/internals/project-priority.md)
- [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)
