---
title: 副檔名、文字編輯器、選項
description: 瞭解如何使用 [副檔名] 頁面來指定 Visual Studio IDE 如何處理具有特定副檔名的所有檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.File_Extension
helpviewer_keywords:
- file extensions, associating to editor
- Editing Experience
- Options dialog box
- Editing Experience, selecting
ms.assetid: 05298fc5-fc4e-4bb2-b942-1f7d2dcdff0f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d0e782b0d141666ca7d1f79464d60afd89ef871
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039727"
---
# <a name="options-text-editor-file-extension"></a>副檔名、文字編輯器、選項

這個選項對話方塊可讓您指定 Visual Studio 整合式開發環境 (IDE) 要如何處理含特定副檔名的所有檔案。 您可以針對輸入的每個 **副檔名**，選取一種編輯體驗。 這可讓您選擇要用來開啟特定類型文件的 IDE 編輯器或設計工具。 若要顯示這些選項，請從 [工具] 功能表上選擇 [選項]，展開 [文字編輯器] 節點，然後選取 [副檔名]。

如果您選取的選項具有編碼方式，則每次開啟該類型文件時，就會顯示一個對話方塊供您選取該文件的編碼配置。 當您要準備不同平台或不同目標語言適用的專案文件版本時，此功能就非常實用。

## <a name="uielement-list"></a>UIElement 清單

**副檔名**

輸入您想要在 IDE 中為其定義編輯體驗的檔案副檔名。

**編輯器**

選取要用來開啟此檔案副檔名文件的 IDE 編輯器或設計工具。 如果您選取的選項「具有編碼方式」，則每次開啟這類文件時，就會顯示一個對話方塊供您選取編碼配置。

**加入**

可將包含指定 [副檔名] 和 [編輯體驗] 的項目新增至 [副檔名清單]。

**移除**

可從 [副檔名清單] 中刪除選取的項目。

**副檔名清單**

列出所有已指定 [編輯體驗] 的副檔名。

**將無副檔名的檔案對應到**

如果您想要指定 IDE 如何處理不含副檔名檔案的方法，請選取此選項。

**無副檔名的檔案選項**

提供的清單與 [編輯器] 相同。 選取要用來開啟不含檔案副檔名文件的 IDE 編輯器或設計工具。

## <a name="see-also"></a>另請參閱

- [如何：管理編輯器模式](../../ide/how-to-manage-editor-modes.md)
