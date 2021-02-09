---
title: 選擇 Debug Engine 執行策略 |Microsoft Docs
description: 瞭解執行時間架構如何協助您選擇多個策略來進行 debug engine。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e544e4cebaa4e2e1691f6c175dfa750a1f951abc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930690"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>選擇 debug engine 執行策略
您可以使用執行時間架構來決定您的 debug engine (DE) 的執行策略。 您可以針對正在進行偵錯工具的程式建立同進程的 debug engine。 在 Visual Studio 會話 debug manager (SDM) 的同進程中建立 debug engine。 或者，為這兩個元件建立跨進程的偵錯工具引擎。 下列指導方針可協助您在這三種策略中做選擇。

## <a name="guidelines"></a>指導方針
 雖然您可以對 SDM 和您正在進行偵錯工具的程式進行非程式處理，但通常沒有理由這麼做。 跨進程界限的呼叫會相當緩慢。

 已經為 Win32 原生執行時間環境和 common language 執行時間環境提供了偵錯工具引擎。 如果您必須取代任一環境的取消，您應該使用 SDM 來建立取消處理。

 否則，您可以針對正在進行偵錯工具的程式，建立對 SDM 或同進程的取消進程。 您必須考慮是否需要經常存取程式符號存放區，才能進行 DE 的運算式評估工具。 或者，如果符號存放區可以載入記憶體以供快速存取。 此外，請考慮下列方法：

- 如果運算式評估工具和符號存放區之間沒有許多呼叫，或如果符號存放區可讀入 SDM 記憶體空間中，請建立對 SDM 的取消處理。 當您附加至程式時，您必須將偵錯工具的 CLSID 傳回至 SDM。 SDM 會使用這個 CLSID 來建立 DE 的同進程實例。

- 如果 DE 必須呼叫程式來存取符號存放區，請建立程式的「取消處理」程式。 在此情況下，程式會建立 DE 的實例。

## <a name="see-also"></a>另請參閱
- [Visual Studio 偵錯工具擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
