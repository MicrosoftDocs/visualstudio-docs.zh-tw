---
title: 在舊版語言服務的自動格式設定 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e052c62afcf9551cc54373da15071fb3903fe950
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126696"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>自動格式化在舊版語言服務
使用自動格式設定中，語言服務會自動插入程式碼的程式碼片段時使用者開始輸入已知的程式碼建構。  
  
## <a name="automatic-formatting-behavior"></a>自動格式化行為  
 例如，當您輸入`if`、 語言服務會自動插入對稱的括號，或如果您按下 ENTER 鍵，語言服務會強制在插入點置於新行的適當縮排層級，取決於是否前面線條會開啟新的範圍。  
  
 語言服務的其餘部分所用的命令篩選條件可以用於自動格式化。 您可以也反白顯示對稱的括號藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)