---
title: "在自訂編輯器中檢視的文件資料和文件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7c7e24ed2db4538ab0fd38dbb85930452611f0ee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="document-data-and-document-view-in-custom-editors"></a>文件資料和文件 檢視中自訂編輯器
自訂編輯器包含兩個部分： 文件資料物件和文件檢視物件。 如名稱所示，文件資料物件代表要顯示的文字資料，而文件檢視物件 （或 「 檢視 」） 則代表要在其中顯示文件資料物件的一或多個 windows。  
  
## <a name="document-data-object"></a>文件資料物件  
 文件資料物件是文字的資料表示法中的文字緩衝。 它是 COM 物件，儲存文件文字和其他資訊、 處理文件的持續性，並讓其資料的多個檢視。 如需詳細資訊，請參閱  
  
 <xref:EnvDTE80.Window2.DocumentData%2A>和[文件視窗](../extensibility/internals/document-windows.md)。  
  
 自訂編輯器和設計工具可以選擇使用<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>物件或他們自己自訂的緩衝區。 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>簡化的內嵌模型會遵循標準編輯器、 支援多個檢視，並提供用來管理多個檢視的事件介面。  
  
## <a name="document-view-object"></a>文件檢視物件  
 顯示程式碼和其他文字的視窗稱為文件 檢視。 當您建立編輯器時，您可以選擇在單一視窗中，會顯示文字的單一檢視或多個檢視中，在多個視窗中顯示文字。 您的選擇取決於您的應用程式。 比方說，如果您需要為並存編輯，您會選擇多個檢視。 每個檢視是整合式的開發環境 (IDE) 執行文件資料表 (RDT) 中的項目相關聯。 檢視 windows 屬於任何專案或<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>物件。  
  
 如果您的編輯器支援多個檢視的文件資料物件，則您的文件資料和文件檢視物件必須是不同。 否則，它們可以群組在一起。 如需詳細資訊，請參閱[支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)。  
  
 IDE 會通知所執行的文件資料表中每個項目相符的項目識別項 (ItemID) 檢視關於事件 （例如，關閉方案，包含文件時）。 如需詳細資訊，請參閱[執行中的文件表格](../extensibility/internals/running-document-table.md)。  
  
 有兩個選項用於建立自訂編輯器的檢視。 其中一個是就地啟用模型中，檢視裝載在視窗中使用 ActiveX 控制項或文件資料物件的位置。 第二個是簡化的內嵌模型，由裝載檢視[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>實作來處理視窗命令。 就地啟用模型的相關資訊，請參閱[就地啟用](../extensibility/in-place-activation.md)。 簡化的內嵌模型的相關資訊，請參閱[簡化內嵌](../extensibility/simplified-embedding.md)。  
  
## <a name="see-also"></a>請參閱  
 [支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)   
 [簡化的嵌入](../extensibility/simplified-embedding.md)   
 [如何： 將附加至文件資料的檢視](../extensibility/how-to-attach-views-to-document-data.md)   
 [文件鎖定持有者管理](../extensibility/document-lock-holder-management.md)   
 [單一和多重索引標籤檢視](../extensibility/single-and-multi-tab-views.md)   
 [正在儲存標準文件](../extensibility/internals/saving-a-standard-document.md)   
 [持續性和執行 Document 資料表](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [決定編輯器開啟的專案中的檔案](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [編輯器 Factory](../extensibility/editor-factories.md)