---
title: 舊版語言服務中的自動格式化 |Microsoft Docs
description: 瞭解舊版語言服務中的自動格式化，這會在您開始鍵入已知的程式碼結構時，自動插入程式碼片段。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a08a56a6820917b3a954c162b1875430875c7585
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086270"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>舊版語言服務中的自動格式化
使用自動格式化時，語言服務會在使用者開始鍵入已知的程式碼結構時，自動插入程式碼片段。

## <a name="automatic-formatting-behavior"></a>自動格式化行為
 例如，當您輸入 *if* 時，語言服務會自動插入相符的大括弧，或者，如果您按下 enter 鍵，語言服務會強制新行上的插入點成為適當的縮排層級，取決於前一行是否開啟新的範圍。

 用於其他語言服務的命令篩選也可以用於自動格式化。 您也可以藉由呼叫來反白顯示成對的大括弧 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> 。

## <a name="see-also"></a>另請參閱
- [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)
