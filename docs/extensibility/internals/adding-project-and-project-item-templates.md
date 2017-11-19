---
title: "加入專案和專案項目範本 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0201d2f282365a028b6251324b07276c995621ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="adding-project-and-project-item-templates"></a>加入專案和專案項目範本
當您建立您自己的專案類型時，您必須提供支援加入新的專案和專案項目使用標準[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式開發環境 (IDE) 對話方塊。 下列主題討論不同技術可加入的專案和專案項目。  
  
## <a name="in-this-section"></a>本章節內容  
 [專案內容](../../extensibility/internals/project-context.md)  
 說明此專案提供大部分的什麼瓿環境中的內容資訊。  
  
 [專案優先順序](../../extensibility/internals/project-priority.md)  
 說明專案項目通常是一個專案的成員，才能避免模稜兩可的專案用來開啟項目。  
  
 [其他檔案專案](../../extensibility/internals/miscellaneous-files-project.md)  
 提供專案扮演判斷的編輯器開啟專案項目時所要使用兩種可用來開啟檔案的專案和角色中的編輯器類型資訊。  
  
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)  
 說明發生的狀況時[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]建立專案。  
  
 [將項目新增至加入新項目對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 說明的程序加入項目至**加入新項目** 對話方塊。  
  
 [將目錄新增至新增專案對話方塊](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 提供註冊新的目錄，其中包含 VSPackage 所提供的自訂範本的範例。  
  
 [將目錄新增至加入新項目對話方塊](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 提供的註冊一組新的目錄範例**加入新項目** 對話方塊。  
  
 [用來擴充專案系統的 IDE 定義的命令](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 列出不同擴充專案系統使用的命令項目類型。  
  
 [通常用來擴充專案的物件 CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 列出的物件，可用來擴充項 Catid [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]， [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]，和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案系統。  
  
## <a name="related-sections"></a>相關章節  
 [如何︰開啟專案特定的編輯器](../../extensibility/how-to-open-project-specific-editors.md)  
 提供逐步指示，開啟內容本質上並繫結至特定的編輯器，專案項目。  
  
 [如何︰開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)  
 提供逐步指示，開啟標準編輯器。  
  
 [專案子類型](../../extensibility/internals/project-subtypes.md)  
 提供專案子類型概念性主題的連結。 專案子類型延伸現有[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案。  
  
 [專案類型](../../extensibility/internals/project-types.md)  
 提供額外的主題提供有關如何設計新的專案類型的資訊連結。