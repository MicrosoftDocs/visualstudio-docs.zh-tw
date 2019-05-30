---
title: 舊版語言服務中的自動格式設定 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b69419e917a5ab5293af15b21822ca6473a9e292
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344926"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>舊版語言服務中的自動格式化
使用自動格式設定中，語言服務會自動插入程式碼的片段，當使用者開始輸入已知的程式碼建構。

## <a name="automatic-formatting-behavior"></a>自動格式化行為
 例如，當您鍵入*如果*、 語言服務會自動插入對稱的括號，或如果您按 ENTER 鍵時，語言服務會強制將插入點在新的一行適當縮排層級，取決於不論上述列會開啟新的範圍。

 使用語言服務的 rest 命令篩選條件可以用於自動格式化。 您也可以藉由呼叫白對稱的括號<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>。

## <a name="see-also"></a>另請參閱
- [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)