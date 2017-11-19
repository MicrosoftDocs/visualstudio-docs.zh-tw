---
title: "在舊版語言服務的自動格式設定 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f09ab8a948011cdc53516ec21f0d213852166956
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>自動格式化在舊版語言服務
使用自動格式設定中，語言服務會自動插入程式碼的程式碼片段時使用者開始輸入已知的程式碼建構。  
  
## <a name="automatic-formatting-behavior"></a>自動格式化行為  
 例如，當您輸入`if`、 語言服務會自動插入對稱的括號，或如果您按下 ENTER 鍵，語言服務會強制在插入點置於新行的適當縮排層級，取決於是否前面線條會開啟新的範圍。  
  
 語言服務的其餘部分所用的命令篩選條件可以用於自動格式化。 您可以也反白顯示對稱的括號藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)