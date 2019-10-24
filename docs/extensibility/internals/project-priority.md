---
title: 專案優先順序 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee4c0f41902e74f58684d6806877d352447351bf
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725400"
---
# <a name="project-priority"></a>專案優先順序
專案專案通常是方案中唯一一個專案的成員。 因此，IDE 可以輕鬆地判斷用來開啟專案的專案。 不過，如果專案是多個專案的成員，則 IDE 會使用優先順序配置來判斷開啟專案的最佳專案。

 下列清單顯示專案優先順序配置：

- IDE 會針對方案中的每個專案呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> 方法，以判斷檔是否為該專案的成員。

- 如果檔是專案的成員，則專案會根據其處理該檔的優先順序，來回應專案。 例如，語言專案會以高優先順序回應其語言原始程式檔，但會以較低的優先順序回應無法辨識的檔案類型，而不會用來做為其組建進程的一部分。

- 為檔提供自訂、專案特定編輯器或設計工具的專案也會獲得高優先順序。

- @No__t_0 列舉會提供檔優先順序值。

- 指定最高優先順序的專案會提供開啟檔的內容。 如果兩個專案傳回相同的優先順序值，則慣用使用中的專案。 如果方案中沒有任何專案回應可以開啟檔，IDE 會將檔放在 [其他檔案] 專案中。 如需詳細資訊，請參閱[其他檔案專案](../../extensibility/internals/miscellaneous-files-project.md)。

## <a name="see-also"></a>請參閱
- [其他檔案專案](../../extensibility/internals/miscellaneous-files-project.md)
- [如何︰針對開啟的文件開啟編輯器](../../extensibility/how-to-open-editors-for-open-documents.md)
- [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)