---
title: 項目優先順序 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a75c1c333d88e1bf5524281bee8b2a683ca6c98e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706426"
---
# <a name="project-priority"></a>專案優先順序
專案項通常只是解決方案中一個項目的成員。 因此,IDE 可以輕鬆地確定用於打開專案的專案。 但是,如果專案是多個項目的成員,IDE 將使用優先順序方案來確定打開專案的最佳專案。

 以下清單顯示了項目優先權方案:

- IDE 調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A>解決方案 中每個專案的方法,以確定文檔是否是該專案的成員。

- 如果文檔是專案的成員,則專案會回應專案根據對該檔的處理所分配的優先順序。 例如,語言專案對其語言源檔具有高優先順序的回應,但對於未識別的文件類型,回應優先順序較低,而這些檔類型不用作其生成過程的一部分。

- 為文檔提供自訂、特定於專案的編輯器或設計器的專案也會獲得高度優先順序。

- 枚<xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>舉提供文檔優先順序值。

- 指定最高優先順序的項目將指定打開文件的上下文。 如果兩個專案返回相等的優先順序值,則首選活動專案。 如果解決方案中沒有專案回應可以打開文檔,IDE 會將文檔放入「雜項檔」專案中。 有關詳細資訊,請參閱[雜項檔案專案](../../extensibility/internals/miscellaneous-files-project.md)。

## <a name="see-also"></a>另請參閱
- [其他檔案專案](../../extensibility/internals/miscellaneous-files-project.md)
- [如何︰針對開啟的文件開啟編輯器](../../extensibility/how-to-open-editors-for-open-documents.md)
- [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)
