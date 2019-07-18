---
title: HOW TO：新增標準文字標記 |Microsoft Docs
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436012"
---
# <a name="how-to-add-standard-text-markers"></a>HOW TO：新增標準文字標記
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用下列程序建立隨附的預設文字標記類型的其中一個[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]核心編輯器。  
  
### <a name="to-create-a-text-marker"></a>若要建立文字標記  
  
1. 取決於您使用一個或兩個-維座標系統中，呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>方法或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>方法用來建立新的文字標記。  
  
     在此方法呼叫中，指定標記類型，某個範圍的文字上，建立標記和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>介面。 然後此方法會將讓指標回到新建立的文字標記中。 標記類型皆取自<xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE>列舉型別。 指定<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>介面，如果您想要收到標記事件的通知。  
  
    > [!NOTE]
    > 在主要 UI 執行緒上只能建立文字標記。 核心編輯器是要建立文字標記的文字緩衝的內容，而文字緩衝區不是安全執行緒。  
  
## <a name="adding-a-custom-command"></a>新增自訂命令  
 實作`IVsTextMarkerClient`介面，並提供給它的指標，從標記增強了數種方式的標記行為。 首先，這可讓您為您的標記提供提示，並執行命令。 這也可讓您接收事件通知，針對個別的標記，並透過標記建立自訂內容功能表。 若要將自訂命令新增至 [標記] 內容功能表使用下列程序。  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>若要將自訂命令新增至內容功能表  
  
1. 內容功能表會出現之前，環境會呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A>方法並傳遞您的文字標記的指標會受到影響的內容功能表命令項目數目。  
  
     比方說的操作功能表上的特定中斷點的命令包含**移除中斷點**透過**新中斷點**，如下列螢幕擷取畫面所示。  
  
     ![標記操作功能表](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2. 傳回一些識別的自訂命令名稱的文字。 例如，**移除中斷點**可能是自訂的命令，如果環境未已經提供它。 您也將傳遞回命令是否支援、 可用且已啟用，及/或開啟 / 關閉切換。 環境會使用這項資訊，以顯示操作功能表中的自訂命令，以正確方式。  
  
3. 若要執行的命令環境呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A>方法，您將指標傳遞到文字標記並從內容功能表中選取的命令數目。  
  
     若要執行任何動作的文字標記您自訂的命令會指定使用這個呼叫這項的資訊。  
  
## <a name="see-also"></a>另請參閱  
 [使用舊版 API 中的文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [如何：實作錯誤標記](../extensibility/how-to-implement-error-markers.md)   
 [如何：建立自訂文字標記](../extensibility/how-to-create-custom-text-markers.md)   
 [如何：使用文字標記](../extensibility/how-to-use-text-markers.md)
