---
title: 'F # 不支援編輯後繼續 |Microsoft Docs'
description: 'F # 的偵錯工具不支援 [編輯後繼續]。 在偵錯工具期間編輯程式碼不會套用至來源，因此正在進行調試的程式碼將不會符合來源。'
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 33d1e8379e71c41e42cbf761ccdfe740342ee642
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96863084"
---
# <a name="edit-and-continue-not-supported-for-f"></a>F# 不支援編輯後繼續 #
當您偵錯 F# 程式碼時，不支援 [編輯後繼續]。 在偵錯工作階段期間編輯 F# 程式碼是可行的作法，但應該避免。 偵錯工作階段期間不會套用程式碼變更。 因此，您在偵錯時對 F# 程式碼所做的任何編輯都會導致原始程式碼與正在偵錯的程式碼變成不相符。
