---
title: 如何：新增標準文字標記 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 912d5d7a225520fc825d832bf73f5cfc733a9486
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838778"
---
# <a name="how-to-add-standard-text-markers"></a>如何：新增標準文字標記
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用下列程式，建立核心編輯器提供的其中一個預設文字標記類型 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。  
  
### <a name="to-create-a-text-marker"></a>若要建立文字標記  
  
1. 根據您使用的是一或兩個維度座標系統，呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> 方法或 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> 方法來建立新的文字標記。  
  
     在這個方法呼叫中，指定標記類型、要建立標記的文字範圍，以及 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 介面。 然後，這個方法會傳回新建立之文字標記的指標。 標記類型取自 <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> 列舉。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>如果您想要收到標記事件的通知，請指定介面。  
  
    > [!NOTE]
    > 僅在主要 UI 執行緒上建立文字標記。 核心編輯器依賴文字緩衝區的內容來建立文字標記，而文字緩衝區不是安全線程。  
  
## <a name="adding-a-custom-command"></a>新增自訂命令  
 `IVsTextMarkerClient`從標記中執行介面並提供指向它的指標可增強標記行為的方式有好幾種。 首先，這可讓您為標記提供提示，以及執行命令。 這也可讓您接收個別標記的事件通知，以及在標記上建立自訂的內容功能表。 使用下列程式，將自訂命令新增至標記操作功能表。  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>將自訂命令新增至內容功能表  
  
1. 在顯示操作功能表之前，環境會呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> 方法，並將指標指向受影響的文字標記，以及內容功能表中命令專案的數目。  
  
     例如，操作功能表上的中斷點特定命令包含透過**新中斷點****移除中斷點**，如下列螢幕擷取畫面所示。  
  
     ![標記內容功能表](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercoNtextmenu")  
  
2. 傳回一些可識別自訂命令名稱的文字。 例如，如果環境尚未提供自訂命令，則 **移除中斷點** 可能是自訂命令。 您也可以傳回命令是否受到支援、可用和啟用，以及/或關閉切換。 環境會使用這項資訊，以正確的方式顯示內容功能表中的自訂命令。  
  
3. 為了執行此命令，環境 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> 會呼叫方法，並傳遞文字標記的指標，以及從內容功能表選取的命令數目。  
  
     從此呼叫使用這項資訊，以執行您的自訂命令所規定之文字標記的任何動作。  
  
## <a name="see-also"></a>另請參閱  
 [搭配舊版 API 使用文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [如何：執行錯誤標記](../extensibility/how-to-implement-error-markers.md)   
 [如何：建立自訂文字標記](../extensibility/how-to-create-custom-text-markers.md)   
 [如何：使用文字標記](../extensibility/how-to-use-text-markers.md)
