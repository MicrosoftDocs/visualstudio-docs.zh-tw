---
title: 符號提供者 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d54494a8fa23e0714769863ac0fa2e5ddc1f4c2
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276971"
---
# <a name="symbol-provider"></a>符號提供者
運算式評估工具實作必須存取以評估變數和運算式語言編譯器所產生的符號偵錯資訊。 它會藉由使用介面的符號提供者 (SP)，也稱為符號處理常式。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供 managed 程式碼，以及使用程式資料庫 (PDB) 符號的檔案格式的原生程式碼的預存程序。 除非沒有強式需要為您的程式使用自訂的格式儲存的符號，而是建議您在使用所提供的預存程序[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="implementation-notes"></a>實作注意事項  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，預存程序，使用 Common Language Runtime (CLR) 介面與預期的偵錯引擎。 如此一來，Visual Studio 偵錯引擎會使用預存程序必須支援的 CLR。 所有 CLR 偵錯介面的完整清單可在 debugref.doc，也就是組件的[!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]。  
  
 如果您的預存程序只會使用您自訂的偵錯引擎，您可以在根據您的偵錯引擎的需求適當地實作預存程序。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)