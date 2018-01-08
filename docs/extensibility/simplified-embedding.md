---
title: "簡化的嵌入 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 183dc4ad9d7ea1a2f6855be050ad8459a3f801ac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="simplified-embedding"></a>簡化的嵌入
簡化內嵌時，會啟用在編輯器中 （也就是對的子系） 父代其文件檢視物件[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，而<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>介面的實作來處理其視窗命令。 簡化的嵌入編輯器無法裝載作用中的控制項。 下圖中會顯示用來建立使用簡化的嵌入編輯器的物件。  
  
 ![簡化的嵌入編輯器圖形](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
使用簡化的嵌入編輯器  
  
> [!NOTE]
>  在此圖中，只有物件的`CYourEditorFactory`物件，才能建立標準以檔案為基礎的編輯器。 如果您要建立自訂編輯器，您不需要實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>，因為您的編輯器可能會有自己的私用持續性機制。 非自訂編輯器，不過，您必須這樣做。  
  
 中所包含的所有介面實作，以建立使用簡化的嵌入編輯器`CYourEditorDocument`物件。 不過，若要支援多個檢視的文件資料，分割到不同的資料，以及檢視物件的介面在下表所示。  
  
|介面|介面的位置|使用|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|檢視|提供連接至父視窗。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|檢視|處理命令。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|檢視|啟用狀態列更新。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|檢視|可讓**工具箱**項目。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|資料|當檔案變更時，會傳送通知。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|資料|啟用檔案類型 [另存新檔] 功能。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|資料|啟用文件的持續性。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|資料|可讓隱藏的檔案變更的事件，例如觸發重新載入。|