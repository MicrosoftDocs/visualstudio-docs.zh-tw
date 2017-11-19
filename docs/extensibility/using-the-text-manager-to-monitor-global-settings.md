---
title: "使用文字管理員監控全域設定 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9687e4f0be16fb42f13c6f9dd20a2cb39be50cd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>使用文字管理員監控全域設定
如果您實作的核心編輯器，您必須監視通用的設定值所做的變更，因為這些變更可能會影響您在編輯器的執行個體。 您可以透過文字管理員所引發的事件接聽追蹤所做的變更。 比方說，當您指定的外觀或行為元件的全域喜好設定，在核心編輯器中，其文件資料物件，例如文字管理員儲存這項資訊和通訊受影響的所有用戶端。  
  
## <a name="text-manager-functions"></a>文字管理員函式  
 文字管理員會引發事件的設定，包括下列：  
  
-   緩衝區是否原始程式碼控制之下  
  
-   如何登錄的檔案變更通知  
  
-   如何檢視追蹤的是與特定緩衝區相關聯  
  
-   文字的顏色標示喜好設定  
  
-   與空間喜好設定索引標籤  
  
 文字管理員無法管理對指定的語言都是唯一的喜好設定。 必須由每個語言服務管理這些設定。  
  
 文字管理員的事件通知由提供<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>介面。 實作這個介面上您的用戶端物件來處理事件引發文字管理員。 使用註冊這些事件<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>文字管理員上的介面。  
  
## <a name="see-also"></a>另請參閱  
 [核心編輯器內](../extensibility/inside-the-core-editor.md)   
 [編輯器功能](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)