---
title: 開啟並儲存專案項目 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 895306a70d386b7a895b52b22704ec42a07d17ce
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="opening-and-saving-project-items"></a>開啟並儲存專案項目
當您新增新的專案類型時，您必須管理的開啟和儲存您的專案檔案[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE)。 下列主題討論不同的方法，來開啟和儲存檔案。  
  
## <a name="in-this-section"></a>本節內容  
 [使用開啟檔案命令顯示檔案](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)  
 提供 IDE 的處理方式的逐步說明**開啟檔案**命令，而且此命令的回應中的專案的角色。  
  
 [使用開啟方式命令顯示檔案](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)  
 提供詳細的逐步說明在 IDE 如何處理**開啟**命令，提示檔案具有一些選擇的標準編輯器開啟。  
  
 [如何︰開啟專案特定的編輯器](../../extensibility/how-to-open-project-specific-editors.md)  
 提供逐步指示，來指定特定類型在專案中的檔案，應使用專案特定編輯器開啟。  
  
 [如何︰開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)  
 提供逐步指示，來指定如何啟用 IDE，才能在您的專案類型開啟檔案的標準編輯器。  
  
 [如何︰針對開啟的文件開啟編輯器](../../extensibility/how-to-open-editors-for-open-documents.md)  
 提供逐步指示，以開啟專案特定的編輯器開啟檔案。  
  
 [儲存標準文件](../../extensibility/internals/saving-a-standard-document.md)  
 提供 IDE 的處理方式的詳細的說明**儲存**，**存**，和**全部儲存**標準編輯器中開啟的文件的命令。  
  
 [儲存自訂文件](../../extensibility/internals/saving-a-custom-document.md)  
 提供圖表和 IDE 的處理方式的詳細的說明**儲存**，**存**，和**全部儲存**在自訂編輯器中開啟文件的命令。  
  
 [決定要開啟專案中檔案的編輯器](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)  
 討論 IDE 中選取適當的編輯器或設計工具的檔案時所遵循的程序。  
  
## <a name="related-sections"></a>相關章節  
 [建立自訂編輯器和設計工具](../../extensibility/creating-custom-editors-and-designers.md)  
 列出四種類型的編輯器可以裝載 IDE，並提供每個編輯器的描述。  
  
 [專案類型](../../extensibility/internals/project-types.md)  
 討論如何專案控制的程式碼進行編譯和建置的方式、 如何開啟編輯器，以及專案項目格式化的方式。