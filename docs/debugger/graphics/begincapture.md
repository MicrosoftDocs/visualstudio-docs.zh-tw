---
title: BeginCapture | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e714245ff2585f9de0b998160ce08f04c88b097
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62896432"
---
# <a name="begincapture"></a>BeginCapture
開始會結束，在擷取間隔`EndCapture`。

## <a name="syntax"></a>語法

```C++
void BeginCapture();
```

## <a name="remarks"></a>備註
 在擷取間隔通常會跨越一個框架，例如當您想要擷取的相關特定種類的繪製呼叫的圖形資訊的子集。 如果擷取間隔跨越呼叫呈現，則會擷取圖形資訊的兩個框架。 第一個畫面格跨越的呼叫之間的間隔`BeginCapture`呈現; 的呼叫與第二個畫面格跨越呈現呼叫之後的第一個 Direct3D 事件和呼叫之間的間隔`EndCapture`。

 若要擷取的間隔，您必須準備您的應用程式，來擷取和記錄的圖形資訊 — 也就是您必須先呼叫[Init](init.md)的執行個體透過`VsgDbg`類別在呼叫之前`BeginCapture`或`EndCapture`。

## <a name="see-also"></a>另請參閱
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)