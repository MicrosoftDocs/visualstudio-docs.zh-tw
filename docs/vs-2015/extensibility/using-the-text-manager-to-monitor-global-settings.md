---
title: 使用文字管理員監視全域設定 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ece51450b8344ae4715a912399ec538171a26a5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695461"
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>使用文字管理員監視全域設定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您執行的是核心編輯器，則必須監視對全域設定所做的變更，因為這些變更可能會影響您的編輯器實例。 您可以藉由接聽文字管理員所引發的事件來追蹤變更。 例如，當您在核心編輯器中指定元件外觀或行為的全域喜好設定（例如其檔資料物件）時，文字管理員會儲存此資訊，並將其傳達給所有受影響的用戶端。  
  
## <a name="text-manager-functions"></a>文字管理員函數  
 文字管理員會引發一些設定的事件，包括下列各項：  
  
- 緩衝區是否在原始程式碼控制之下  
  
- 如何註冊檔案變更通知  
  
- 如何追蹤與特定緩衝區相關聯的視圖  
  
- 文字顏色標示喜好設定  
  
- 定位鍵與空間喜好設定  
  
  特定語言的唯一喜好設定不受文本管理員的管理。 這些設定必須由每個語言服務管理。  
  
  文字管理員的事件通知是由 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> 介面提供。 在您的用戶端物件上執行此介面，以處理引發文字管理員的事件。 您可以使用文字管理員上的介面來註冊這些事件 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> 。  
  
## <a name="see-also"></a>另請參閱  
 [在核心編輯器中](../extensibility/inside-the-core-editor.md)   
 [編輯器功能](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)
