---
title: 編輯後繼續 不支援F#|Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [F#]
- Debugging [F#], Edit and Continue
ms.assetid: 40ec77bb-07e3-4b58-9254-ae015009441c
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4fef61335679e3f82d5916726981e003bf9c332
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945849"
---
# <a name="edit-and-continue-not-supported-for-f"></a>F# 不支援編輯後繼續 #
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您偵錯 F# 程式碼時，不支援 [編輯後繼續]。 在偵錯工作階段期間編輯 F# 程式碼是可行的作法，但應該避免。 偵錯工作階段期間不會套用程式碼變更。 因此，您在偵錯時對 F# 程式碼所做的任何編輯都會導致原始程式碼與正在偵錯的程式碼變成不相符。
