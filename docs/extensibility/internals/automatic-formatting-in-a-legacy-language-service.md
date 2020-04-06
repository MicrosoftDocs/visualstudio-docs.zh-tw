---
title: 舊語言服務中的自動格式 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a11e9c1fdef60e71f46cee9986d925e876dcac35
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709984"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>舊語言服務中的自動格式設定
使用自動格式,當用戶開始鍵入已知代碼建構時,語言服務會自動插入代碼段。

## <a name="automatic-formatting-behavior"></a>自動格式化行為
 例如,當您鍵入*if,* 語言服務會自動插入匹配的大括弧,或者如果按 ENTER 鍵時,語言服務會強制新行上的插入點到相應的縮進級別,具體取決於前面的行是否打開新作用域。

 用於其餘語言服務的命令篩選器也可用於自動格式化。 您還可以透過調用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>突出顯示匹配的大括弧。

## <a name="see-also"></a>另請參閱
- [開發傳統語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)
