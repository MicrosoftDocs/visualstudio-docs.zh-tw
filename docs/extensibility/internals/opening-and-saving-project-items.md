---
title: 開啟與儲存項目項目 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbb89d99e401be6bae7d8ee9be8ee33fa7574723
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706960"
---
# <a name="opening-and-saving-project-items"></a>開啟和儲存專案項目
新增新項目類型時,必須在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式開發環境(IDE) 中管理專案檔的打開和儲存。 以下主題討論打開和保存檔的不同方法。

## <a name="in-this-section"></a>本節內容
- [使用開啟檔案命令顯示檔案](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 提供 IDE 如何處理**Open File**命令以及專案在回應此命令中的作用的分步說明。

- [使用開啟方式命令顯示檔案](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 提供 IDE 如何處理 **「打開隨用」** 命令的詳細分步說明,從而提示打開具有一些標準編輯器選擇的檔。

- [如何︰開啟專案特定的編輯器](../../extensibility/how-to-open-project-specific-editors.md)

 提供分步說明,用於指定應使用特定於專案的編輯器打開專案中特定類型的檔。

- [如何︰開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)

 提供分步說明,說明如何指定如何使IDE為專案類型中的文件打開標準編輯器。

- [如何︰針對開啟的文件開啟編輯器](../../extensibility/how-to-open-editors-for-open-documents.md)

 提供分步說明,用於打開打開的檔案的專案特定編輯器。

- [儲存標準文件](../../extensibility/internals/saving-a-standard-document.md)

 詳細說明 IDE 如何處理標準編輯器中開啟的文件的 **「儲存**、**儲存為**」和 **「儲存所有」** 命令。

- [儲存自訂文件](../../extensibility/internals/saving-a-custom-document.md)

 提供一個圖表,並詳細說明 IDE 如何處理在自定義編輯器中打開的文檔**的保存**、**儲存為**和**保存所有**命令。

- [決定要開啟專案中檔案的編輯器](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 討論 IDE 為檔案選擇適當的編輯器或設計器的過程。

## <a name="related-sections"></a>相關章節
- [建立自訂編輯器和設計工具](../../extensibility/creating-custom-editors-and-designers.md)

 列出 IDE 可以承載的四種編輯器類型,並給出每個編輯器的說明。

- [專案類型](../../extensibility/internals/project-types.md)

 討論專案如何控制代碼的編譯和生成方式、編輯器的打開方式以及如何設置專案專案的格式。
