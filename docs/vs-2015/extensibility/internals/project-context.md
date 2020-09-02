---
title: 專案內容 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4ee4da5fdea63cf1bdd33554c72f6dac30d0334
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429934"
---
# <a name="project-context"></a>專案內容
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

當使用者加入或使用專案和專案專案時，IDE 會使用專案內容的概念來決定應該如何執行各種作業。  
  
 一般而言，檔案是使用者明確建立的標準專案物件，方法是選取 [**新增專案**] 命令，或選取 [檔案 **] 功能表上**的 [**開啟專案**] 命令以提供使用。 在這些情況下，會在專案的內容中建立和開啟檔案，而專案類型會定義編輯檔的內容。  
  
 某些專案提供非常豐富的內容。 例如，專案會管理專案範圍、程式設計的命名空間或專案範圍的資料庫連接以進行資料系結。 使用者通常可以使用特定的專案物件（例如方案總管中顯示的專案專案），直接開啟檔案或資料庫連接。  
  
 在其他情況下，不會明確指定專案的專案內容。 例如，當使用者開啟檔案時，無法使用專案的內容，方法是**選取 [檔案] 功能表上**的 [**開啟現有**檔案] 命令、偵錯工具在檔案上運作，或是當使用者按一下 [**尋找和取代**] 對話方塊中的 [檔案**中尋找**] 命令。 為了處理這些情況，IDE 會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> 來管理尋找最佳專案以開啟檔的進程。  
  
## <a name="see-also"></a>另請參閱  
 [專案優先順序](../../extensibility/internals/project-priority.md)   
 [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)
