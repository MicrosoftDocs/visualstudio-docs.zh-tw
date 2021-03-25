---
title: 專案優先順序 |Microsoft Docs
description: 瞭解 Visual Studio IDE 所使用的優先順序配置，以決定如果專案是多個專案的成員，則開啟專案的最佳專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6aefb6b1670da812a36efcc1baa3cb23f23e2561
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064484"
---
# <a name="project-priority"></a>專案優先順序
專案專案通常是方案中唯一一個專案的成員。 因此，IDE 可以輕鬆地判斷要使用哪個專案來開啟專案。 但是，如果專案是多個專案的成員，則 IDE 會使用優先順序配置來判斷開啟專案的最佳專案。

 下列清單顯示專案優先順序配置：

- IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> 會針對方案中的每個專案呼叫方法，以判斷檔是否為該專案的成員。

- 如果檔是專案的成員，則專案會根據其處理該檔的優先順序，來回應專案所指派的優先順序。 例如，語言專案會以高優先順序回應其語言來源檔案，但會以較低的優先順序回應無法辨識的檔案類型，而不會用來作為其組建程式的一部分。

- 針對檔提供自訂、專案特定編輯器或設計工具的專案也會收到高優先順序。

- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>列舉會提供檔優先權值。

- 指定最高優先順序的專案會提供開啟檔的內容。 如果兩個專案傳回相等的優先順序值，則偏好使用中的專案。 如果方案中沒有任何專案回應可以開啟檔，則 IDE 會將檔放在其他檔案專案中。 如需詳細資訊，請參閱 [其他檔案專案](../../extensibility/internals/miscellaneous-files-project.md)。

## <a name="see-also"></a>另請參閱
- [其他檔案專案](../../extensibility/internals/miscellaneous-files-project.md)
- [如何︰針對開啟的文件開啟編輯器](../../extensibility/how-to-open-editors-for-open-documents.md)
- [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)
