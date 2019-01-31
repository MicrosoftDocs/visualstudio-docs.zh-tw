---
title: 編輯後繼續 不支援F#|Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [F#]
- Debugging [F#], Edit and Continue
ms.assetid: 40ec77bb-07e3-4b58-9254-ae015009441c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5b0809b1d6a19a2bb46fefbf90338589de614a8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976364"
---
# <a name="edit-and-continue-not-supported-for-f"></a>F# 不支援編輯後繼續 #
當您偵錯 F# 程式碼時，不支援 [編輯後繼續]。 在偵錯工作階段期間編輯 F# 程式碼是可行的作法，但應該避免。 偵錯工作階段期間不會套用程式碼變更。 因此，您在偵錯時對 F# 程式碼所做的任何編輯都會導致原始程式碼與正在偵錯的程式碼變成不相符。
