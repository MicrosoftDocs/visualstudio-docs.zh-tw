---
title: 選擇 Debug Engine 執行策略 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6b03e69892da217d84d56b39b7df61784907d2b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183463"
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>選擇偵錯引擎的實作策略
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

您可以使用執行時間架構來決定您的 debug engine (DE) 的執行策略。 偵錯工具可能會在進程中建立，以便在進程中進行程式設計、在同進程中進行 Visual Studio 會話的 debug manager (SDM) 或跨進程處理。 下列指導方針可協助您選擇這三種策略。  
  
## <a name="guidelines"></a>指導方針  
 雖然在 SDM 和要進行偵錯工具的過程中，可能不會有任何原因，但通常沒有原因。 跨進程界限的呼叫會相當緩慢。  
  
 已經為 Win32 原生執行時間環境和 common language runtime 環境提供了偵錯工具引擎。 如果您必須取代這些環境中的任何一項，就必須使用 SDM 來建立取消處理。  
  
 否則，您可以選擇建立要進行偵錯工具之 SDM 或同進程的「取消處理」。 請務必考慮，DE 的運算式評估工具是否需要頻繁存取程式符號存放區，以及是否可以將符號存放區載入記憶體以供快速存取。 並請考慮下列項目：  
  
- 如果運算式評估工具和符號存放區之間沒有許多呼叫，或如果符號存放區可讀入 SDM 記憶體空間中，請建立對 SDM 的取消處理。 當您附加至程式時，您必須將偵錯工具的 CLSID 傳回至 SDM。 SDM 會使用這個 CLSID 來建立 DE 的同進程實例。  
  
- 如果 DE 必須呼叫程式來存取符號存放區，請建立程式的「取消處理」程式。 在此情況下，程式會建立 DE 的實例。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 偵錯工具的擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
