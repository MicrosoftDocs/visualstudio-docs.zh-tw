---
title: 開啟和儲存專案專案 |Microsoft Docs
description: 瞭解在 Visual Studio IDE 中為您的新專案類型開啟和儲存檔案的不同方法。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 971fef7939c91bdcdea9098da530c7ecb2daf9ec
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877620"
---
# <a name="opening-and-saving-project-items"></a>開啟和儲存專案項目
當您加入新的專案類型時，您必須在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 整合式開發環境 (IDE) 中，管理專案檔案的開啟和儲存。 下列主題討論開啟和儲存檔案的不同方法。

## <a name="in-this-section"></a>本節內容
- [使用開啟檔案命令顯示檔案](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 提供逐步解說，說明 IDE 如何處理 **開啟** 檔案命令，以及專案在回應此命令時的角色。

- [使用開啟方式命令顯示檔案](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 提供詳細的逐步解說，說明 IDE 如何處理 **開啟的 With** 命令，並提示開啟具有一些標準編輯器的檔案。

- [如何︰開啟專案特定的編輯器](../../extensibility/how-to-open-project-specific-editors.md)

 提供逐步指示，說明如何使用專案特定的編輯器來開啟專案中特定類型的檔案。

- [如何︰開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)

 提供逐步指示，說明如何為您的專案類型中的檔案，指定如何讓 IDE 開啟標準編輯器。

- [如何︰針對開啟的文件開啟編輯器](../../extensibility/how-to-open-editors-for-open-documents.md)

 提供逐步指示，說明如何針對開啟的檔案開啟專案特定編輯器。

- [儲存標準文件](../../extensibility/internals/saving-a-standard-document.md)

 提供 IDE 如何處理在標準編輯器中開啟之檔的 [ **儲存**]、[ **另存** 新檔] 和 [ **儲存所有** ] 命令的詳細說明。

- [儲存自訂文件](../../extensibility/internals/saving-a-custom-document.md)

 提供圖表和詳細說明，說明 IDE 如何處理在自訂編輯器中開啟之檔的 **儲存**、 **另存** 新檔和 **儲存所有** 命令。

- [決定要開啟專案中檔案的編輯器](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 討論 IDE 在為檔案選取適當的編輯器或設計工具時，所遵循的流程。

## <a name="related-sections"></a>相關章節
- [建立自訂編輯器和設計工具](../../extensibility/creating-custom-editors-and-designers.md)

 列出 IDE 可以裝載的四種編輯器類型，並提供每個編輯器的說明。

- [專案類型](../../extensibility/internals/project-types.md)

 討論專案如何控制編譯和建立程式碼的方式、編輯器的開啟方式，以及專案專案的格式化方式。
