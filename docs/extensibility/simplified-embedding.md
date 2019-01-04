---
title: 簡化嵌入 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 010f610a6dc39afab87c67ab3c11ffd05f614ebe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941647"
---
# <a name="simplified-embedding"></a>簡化嵌入
當其文件檢視物件的父系 （也就是與之前的子系） 簡化內嵌在編輯器中啟用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，而<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>介面的實作來處理其視窗命令。 簡化的內嵌編輯器無法裝載作用中的控制項。 用來建立編輯器來簡化內嵌的物件會在下圖中顯示。  
  
 ![簡化的嵌入編輯器圖形](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
使用簡化的嵌入編輯器  
  
> [!NOTE]
>  在此圖中，只有物件的`CYourEditorFactory`物件才能建立標準檔案為基礎的編輯器。 如果您要建立自訂編輯器，您不需要實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>，因為您的編輯器可能會有自己的私用持續性機制。 非自訂編輯器，不過，您必須執行這項作業。  
  
 中包含所有的介面實作，以建立編輯器來簡化內嵌`CYourEditorDocument`物件。 不過，若要支援多個檢視的文件資料，分割到不同的資料和檢視物件的介面下表所示。  
  
|介面|介面的位置|使用|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|檢視|提供給父視窗的連線。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|檢視|處理命令。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|檢視|啟用狀態列更新。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|檢視|可讓**工具箱**項目。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|資料|當檔案變更時，會傳送通知。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|資料|啟用檔案類型的 [另存新檔] 功能。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|資料|啟用文件的持續性。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|資料|可讓隱藏項目檔案變更的事件，例如觸發重新載入。|