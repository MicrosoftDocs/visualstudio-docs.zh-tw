---
title: 副檔名、文字編輯器、選項 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages.text_editor.file_extension
helpviewer_keywords:
- file extensions, associating to editor
- Editing Experience
- Options dialog box
- Editing Experience, selecting
ms.assetid: 05298fc5-fc4e-4bb2-b942-1f7d2dcdff0f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 26c53633bc55efcf95ffbc579e24d2d61e4a0932
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662266"
---
# <a name="options-text-editor-file-extension"></a>副檔名、文字編輯器、選項
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

這個選項對話方塊可讓您指定 Visual Studio 整合式開發環境 (IDE) 要如何處理含特定副檔名的所有檔案。 您可以針對輸入的每個**副檔名**，選取一種編輯體驗。 這可讓您選擇要用來開啟特定類型文件的 IDE 編輯器或設計工具。 若要顯示這些選項，請從 [工具]  功能表上選擇 [選項]  ，展開 [文字編輯器]  節點，然後選取 [副檔名]  。

 如果您選取的選項具有編碼方式，則每次開啟該類型文件時，就會顯示一個對話方塊供您選取該文件的編碼配置。 當您要準備不同平台或不同目標語言適用的專案文件版本時，此功能就非常實用。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)

## <a name="uielement-list"></a>UIElement 清單
 **延伸**模組在您想要定義的 IDE 中，輸入其編輯體驗的副檔名。

 **編輯器**選取 [IDE 編輯器] 或 [設計工具]，其中會開啟具有此副檔名的檔。 如果您選取的選項具有編碼方式，則每次開啟該文件時，就會顯示一個對話方塊供您選取編碼配置。

 [新增]  可將包含指定 [副檔名]  和 [編輯體驗]  的項目新增至 [副檔名] 清單。

 **移除**從延伸模組清單中刪除選取的專案。

 [延伸模組清單] 會列出已指定編輯體驗的所有延伸模組。

 **將無副檔名檔案對應至**如果您想要指定 IDE 如何處理不含副檔名的檔案，請選取此選項。

 **無副檔名檔案選項**提供與**編輯器**相同的清單。 選取要用來開啟不含檔案副檔名文件的 IDE 編輯器或設計工具。

## <a name="see-also"></a>另請參閱
 [如何：管理編輯器模式](../../ide/how-to-manage-editor-modes.md)
