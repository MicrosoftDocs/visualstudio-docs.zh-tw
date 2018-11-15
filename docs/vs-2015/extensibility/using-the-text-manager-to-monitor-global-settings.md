---
title: 使用文字管理員監控全域設定 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 25ba131512c8c57e9ddda21526ef76177d4ca4a3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839683"
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>使用文字管理員監控全域設定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您實作核心編輯器，您必須監控全域設定，所做的變更，因為這些變更可能會影響您的編輯器執行個體。 您可以藉由接聽文字管理員所引發的事件追蹤所做的變更。 例如，核心編輯器，例如其文件資料物件中指定的外觀或元件的行為全域喜好設定時文字管理員將此資訊儲存，並與所有受影響的用戶端。  
  
## <a name="text-manager-functions"></a>文字 Manager 函式  
 文字管理員會引發事件的一些設定，包括下列：  
  
- 緩衝區是否受原始程式碼控制  
  
- 如何註冊檔案變更通知  
  
- 如何檢視追蹤的是與特定緩衝區相關聯  
  
- 文字顏色標示喜好設定  
  
- 與空間喜好設定索引標籤  
  
  指定的語言特有的喜好設定不受文字管理員。 必須由每個語言服務中管理這些設定。  
  
  文字管理員的事件通知由提供<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>介面。 實作這個介面在用戶端物件來處理事件引發之文字管理員。 您藉由使用註冊這些事件<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>文字管理員上的介面。  
  
## <a name="see-also"></a>另請參閱  
 [在核心編輯器](../extensibility/inside-the-core-editor.md)   
 [編輯器功能](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)

