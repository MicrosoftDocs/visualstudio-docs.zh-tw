---
title: 選擇 偵錯引擎的實作策略 |Microsoft Docs
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117690"
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>選擇偵錯引擎的實作策略
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

您可以使用執行階段架構來判斷您偵錯引擎 (DE) 的實作策略。 偵錯引擎可能會建立同處理序程式偵錯，內含於 Visual Studio 工作階段偵錯管理員 (SDM) 或外處理到這兩者。 下列指導方針應可協助您選擇下列三個策略。  
  
## <a name="guidelines"></a>方針  
 雖然您可以針對要跨處理序 DE SDM 和程式進行偵錯，則通常沒有理由這麼做。 跨處理序界限的呼叫是相對比較慢。  
  
 偵錯引擎已經提供 Win32 原生執行階段環境和 common language runtime 環境。 如果您必須取代 DE 針對這兩個環境，您必須建立 SDM DE 同處理序。  
  
 否則，您可以選擇建立 DE，內含於 SDM 或同處理序進行偵錯的程式。 請務必考慮運算式評估工具的裝置是否需要頻繁存取程式符號存放區，並將符號存放區是否載入記憶體進行快速存取。 也請考慮下列各項：  
  
- 如果不是運算式評估工具和符號存放區之間的許多呼叫，或是符號存放區可以讀入 SDM 記憶體空間，建立 DE 同處理序以 SDM。 它會將附加到您的程式時您必須回到 SDM 的偵錯引擎的 CLSID。 在 SDM 會使用這個 CLSID 建立 DE 同處理序執行個體。  
  
- 如果 DE 必須呼叫程式，以存取符號存放區，建立 DE 同處理序的程式。 在此情況下，程式會建立預設的執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 偵錯工具的擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
