---
title: 副檔名、文字編輯器、選項 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.toolsoptionspages.text_editor.file_extension
helpviewer_keywords:
- file extensions, associating to editor
- Editing Experience
- Options dialog box
- Editing Experience, selecting
ms.assetid: 05298fc5-fc4e-4bb2-b942-1f7d2dcdff0f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 99f6d7b90b86b4a5ffefadd98f30ef2f3326fa61
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47500138"
---
# <a name="options-text-editor-file-extension"></a>副檔名、文字編輯器、選項
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[選項、 文字編輯器、 副檔名](https://docs.microsoft.com/visualstudio/ide/reference/options-text-editor-file-extension)。  
  
  
這個選項對話方塊可讓您指定 Visual Studio 整合式開發環境 (IDE) 要如何處理含特定副檔名的所有檔案。 您可以針對輸入的每個**副檔名**，選取一種編輯體驗。 這可讓您選擇要用來開啟特定類型文件的 IDE 編輯器或設計工具。 若要顯示這些選項，請從 [工具] 功能表上選擇 [選項]，展開 [文字編輯器] 節點，然後選取 [副檔名]。  
  
 如果您選取的選項具有編碼方式，則每次開啟該類型文件時，就會顯示一個對話方塊供您選取該文件的編碼配置。 當您要準備不同平台或不同目標語言適用的專案文件版本時，此功能就非常實用。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
## <a name="uielement-list"></a>UIElement 清單  
 **擴充功能**  
 輸入您想要在 IDE 中為其定義編輯體驗的檔案副檔名。  
  
 **編輯器**  
 選取要用來開啟此檔案副檔名文件的 IDE 編輯器或設計工具。 如果您選取的選項具有編碼方式，則每次開啟該文件時，就會顯示一個對話方塊供您選取編碼配置。  
  
 **[新增]**  
 可將包含指定 [副檔名] 和 [編輯體驗] 的項目新增至 [副檔名清單]。  
  
 **移除**  
 可從 [副檔名清單] 中刪除選取的項目。  
  
 副檔名清單  
 列出所有已指定 [編輯體驗] 的副檔名。  
  
 **將無副檔名的檔案對應到**  
 如果您想要指定 IDE 如何處理不含副檔名檔案的方法，請選取此選項。  
  
 **無副檔名的檔案選項**  
 提供的清單與 [編輯器] 相同。 選取要用來開啟不含檔案副檔名文件的 IDE 編輯器或設計工具。  
  
## <a name="see-also"></a>另請參閱  
 [如何：管理編輯器模式](../../ide/how-to-manage-editor-modes.md)



