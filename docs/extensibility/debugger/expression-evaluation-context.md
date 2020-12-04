---
title: 運算式評估內容 |Microsoft Docs
description: 瞭解運算式評估內容，此內容代表運算式評估的內容，並在程式于中斷點停止時存在。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26705b32628a9bd9ecc79489e2552f2d7e537273
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96559676"
---
# <a name="expression-evaluation-context"></a>運算式評估內容
在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 偵錯工具中， **運算式評估** 內容：

- 表示運算式評估的內容。 一般而言，評估內容會對應到要在其中評估變數、參數、函式和方法的詞彙範圍。 例如，與堆疊框架相關聯的運算式評估內容將提供用於評估區域變數、方法參數和類別成員的內容， (如果適用) 的話。

- 當程式在中斷點停止時存在。 運算式本身是一種資料結構，代表已剖析的運算式，可供在指定的內容中進行系結和評估。

     更詳細地說明如何使用 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 方法來建立運算式。 評估運算式時，它會產生一個可列印的字串，其中包含變數或引數的名稱和類型，以及其值。 這個字串會顯示在 IDE 的 [監看式視窗] 或 [區域變數] 視窗中。

     假設有一個 `BSTR` 和一個 [IDebugExpressionCoNtext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 介面，DEBUG engine (DE) 可以剖析運算式來建立 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 介面。 在指定 `IDebugExpression2` 介面之後，DE 可以透過同步或非同步運算式評估來取得值。 此值以及變數或引數的名稱和類型，會傳送至 IDE 以供顯示。

## <a name="see-also"></a>另請參閱
- [運算式評估介面](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)
