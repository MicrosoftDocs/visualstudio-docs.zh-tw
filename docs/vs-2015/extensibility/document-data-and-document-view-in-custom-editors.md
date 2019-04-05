---
title: 在自訂編輯器中檢視的文件資料和文件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2f73ffde43f2ef3608ae492a9643f7920243d818
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58939428"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>自訂編輯器中的文件資料和文件檢視
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

自訂編輯器是由兩個部分所組成： 文件資料物件和文件檢視物件。 如名稱所示，文件資料物件代表要顯示的文字資料，而文件檢視物件 （或 「 檢視 」） 表示要在其中顯示文件資料物件的一或多個視窗。  
  
## <a name="document-data-object"></a>文件資料物件  
 文件資料物件是文字的文字緩衝區中的資料表示法。 它是 COM 物件，儲存文件文字和其他資訊、 處理文件的持續性，並讓其資料的多個檢視。 如需詳細資訊，請參閱  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> 並[文件 Windows](../extensibility/internals/document-windows.md)。  
  
 自訂編輯器和設計工具，可以選擇使用<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>物件或他們自己自訂的緩衝區。 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 遵循簡化的內嵌模型的標準編輯器、 支援多個檢視，並提供用來管理多個檢視的事件介面。  
  
## <a name="document-view-object"></a>文件檢視物件  
 顯示程式碼和其他文字視窗就所謂的文件 檢視。 當您建立的編輯器時，您可以選擇單一檢視，其中的文字會顯示在單一視窗中或多個檢視，其中的文字會顯示在一個以上的視窗。 您的選擇取決於您的應用程式。 例如，如果您需要編輯並排顯示，您會選擇多個檢視。 每個檢視是整合式的開發環境 (IDE) 執行文件資料表 (RDT) 中的項目相關聯。 檢視 windows 屬於任何專案或<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>物件。  
  
 如果您的編輯器支援多個檢視的文件資料物件，則您的文件資料和文件檢視物件必須不同。 否則，可以將它們分組在一起。 如需詳細資訊，請參閱 <<c0> [ 支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)。  
  
 IDE 會通知所執行的文件資料表中的每個項目相符的項目識別項 (ItemID) 檢視關於事件 （例如，包含文件方案已關閉時）。 如需詳細資訊，請參閱[執行文件表格](../extensibility/internals/running-document-table.md)。  
  
 有兩個選項用於建立自訂編輯器的檢視。 其中一個是就地啟用模型中，檢視裝載在視窗中使用 ActiveX 控制項或文件資料物件的位置。 第二個是簡化的內嵌模型，檢視所裝載[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]和<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>實作來處理視窗命令。 如需就地啟用模型的資訊，請參閱 <<c0> [ 就地啟用](../misc/in-place-activation.md)。 簡化的內嵌模型的相關資訊，請參閱[簡化內嵌](../extensibility/simplified-embedding.md)。  
  
## <a name="see-also"></a>另請參閱  
 [支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)   
 [簡化嵌入](../extensibility/simplified-embedding.md)   
 [如何：將檢視附加至文件資料](../extensibility/how-to-attach-views-to-document-data.md)   
 [文件鎖定持有者管理](../extensibility/document-lock-holder-management.md)   
 [單一和多重索引標籤的檢視](../extensibility/single-and-multi-tab-views.md)   
 [正在儲存標準文件](../extensibility/internals/saving-a-standard-document.md)   
 [持續性和執行文件資料表](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [決定編輯器開啟專案中的檔案](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [編輯器處理站](../extensibility/editor-factories.md)
