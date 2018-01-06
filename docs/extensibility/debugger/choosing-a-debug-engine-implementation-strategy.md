---
title: "選擇偵錯引擎實作策略 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fae5211ac270832f07038faafbd6f5bc463d3944
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>選擇偵錯引擎實作策略
您可以使用執行階段架構來判斷您偵錯引擎 (DE) 實作的策略。 偵錯引擎可能會建立在同處理序執行的程式偵錯，在同處理序執行的 Visual Studio 工作階段偵錯管理員 (SDM) 或超出-處理序以這兩種。 下列指導方針有助於您選擇下列三種策略。  
  
## <a name="guidelines"></a>方針  
 雖然可以是跨處理序 DE 的 SDM 和程式以進行偵錯，則通常不需要這樣做。 跨處理序界限的呼叫會相對比較慢。  
  
 偵錯引擎已經提供 Win32 原生執行階段環境，以及通用語言執行階段環境。 如果您必須取代 DE 的這兩個環境，您必須使用 SDM 建立 DE 同處理序。  
  
 否則，您可以選擇建立 DE 中同處理序執行 SDM 或同處理序的程式，以進行偵錯。 請務必考慮運算式評估工具的 DE 是否需要經常存取程式符號存放區，並將符號存放區是否載入快速存取的記憶體。 也請考慮下列各項：  
  
-   如果不是運算式評估工具和符號存放區之間的許多呼叫，或是符號存放區可以讀取到 SDM 記憶體空間，建立 DE 中同處理序執行 SDM。 當它附加到您的程式時您必須回到 SDM 的偵錯引擎的 CLSID。 SDM 會使用這個 CLSID 建立 DE 的同處理序執行個體。  
  
-   如果 DE 必須呼叫程式存取符號存放區，建立程式 DE 同處理序。 在此情況下，程式會建立 DE 的執行個體。  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 偵錯工具的擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)