---
title: 了解取樣資料值 | Microsoft Docs
description: 瞭解 Visual Studio 的取樣程式碼剖析方法分析工具如何在設定的間隔內中斷電腦處理器，並收集函式呼叫堆疊。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 40902746e1dd1a4c68c9e1aa54ed4e72030a8fff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886024"
---
# <a name="understand-sampling-data-values"></a>了解取樣資料值

Visual Studio 分析工具的「取樣」分析方法會依設定的間隔來中斷電腦處理器，並收集函式呼叫堆疊。 「呼叫堆疊」是一個動態結構，其中儲存在處理器上執行的函式相關資訊。

分析工具分析會判斷處理器是否正在執行目標處理序中的程式碼。 如果處理器未在執行目標處理序中的程式碼，則會捨棄此樣本。

如果處理器在執行目標程式碼，分析工具會讓呼叫堆疊上每個函式的樣本計數遞增。 取樣時，呼叫堆疊上只能有一個函式正在執行程式碼。 堆疊上的其他函式則是函式呼叫階層中的父代，會等候其子系傳回。

對於樣本事件，該分析工具會讓目前正在執行其指示的函式「專有」樣本計數遞增。 因為專有樣本也是函式總 (內含) 樣本數的一部分，所以目前作用中函式的內含樣本計數也會遞增。

 分析工具會讓呼叫堆疊上所有其他函式的內含樣本計數遞增。

## <a name="inclusive-samples"></a>內含樣本

目標函式執行期間所收集的樣本總數。

這包括在直接執行函式程式碼期間收集的樣本，以及在執行目標函式所呼叫子函式期間收集的樣本。

## <a name="exclusive-samples"></a>專有樣本

目標函式直接執行指示期間所收集的樣本數。

專有樣本不包含目標函式所呼叫的函式執行期間所收集的樣本。

## <a name="inclusive-percent"></a>內含百分比

就程式碼剖析執行時的內含樣本總數，函式或資料範圍的內含樣本所佔的百分比。

## <a name="exclusive-percent"></a>專有百分比

就程式碼剖析執行時的專有樣本總數，函式或資料範圍的專有樣本所佔的百分比。

## <a name="see-also"></a>另請參閱

[如何：選擇收集方法](../profiling/how-to-choose-collection-methods.md) 
[分析效能工具資料](../profiling/analyzing-performance-tools-data.md)
