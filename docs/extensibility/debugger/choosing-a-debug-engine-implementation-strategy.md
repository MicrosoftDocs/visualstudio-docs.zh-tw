---
title: 選擇 偵錯引擎的實作策略 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 245fb14b06b5deed5ee652ef394e241bd1191022
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60048946"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>選擇 偵錯引擎的實作策略
您可以使用執行階段架構來判斷您偵錯引擎 (DE) 的實作策略。 您可以建立偵錯引擎中同處理序在偵錯的程式。 建立偵錯引擎中同處理序執行 Visual Studio 工作階段的偵錯管理員 (SDM)。 或者，您也可以建立偵錯引擎外處理到這兩者。 下列指導方針可協助您選擇下列三個策略。

## <a name="guidelines"></a>方針
 雖然您可以針對要跨處理序 DE SDM 和正在偵錯的程式，則通常沒有理由這麼做。 跨處理序界限的呼叫是相對比較慢。

 偵錯引擎已經提供 Win32 原生執行階段環境和通用語言執行階段環境。 如果您必須取代 DE 代表其中一個環境，您應該建立 SDM DE 同處理序。

 否則，您建立 DE 同處理序以 SDM 或者同處理序的程式在偵錯。 您必須考慮是否運算式評估工具的 DE 需要頻繁存取程式符號存放區。 或者，如果符號存放區可以載入記憶體中進行快速存取。 此外，請考慮下列方法：

- 如果不是運算式評估工具和符號存放區之間的許多呼叫，或是符號存放區可以讀入 SDM 記憶體空間，建立 DE 同處理序以 SDM。 它會將附加到您的程式時您必須回到 SDM 的偵錯引擎的 CLSID。 在 SDM 會使用這個 CLSID 建立 DE 同處理序執行個體。

- 如果 DE 必須呼叫程式，以存取符號存放區，建立 DE 同處理序的程式。 在此情況下，程式會建立預設的執行個體。

## <a name="see-also"></a>另請參閱
- [Visual Studio 偵錯工具擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)