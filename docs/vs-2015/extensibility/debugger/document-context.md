---
title: 文件內容 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c5753e2353b351f6aa4bd73c5aced3d4959b3cde
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741197"
---
# <a name="document-context"></a>文件內容
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]偵錯**文件內容**:  
  
-   表示原始程式檔中的位置。 其中的原始程式檔可能不存在的語言，文件內容會識別通常是由執行階段環境產生的文件中的位置。 例如，指令碼引擎可能會產生從指令碼的文件。 如需詳細資訊，請參閱 <<c0> [ 文件位置](../../extensibility/debugger/document-position.md)。  
  
-   描述對應至程式碼內容的來源文件中的位置。 符號處理常式會將程式碼內容對應至文件內容中，使用由編譯器或解譯器所產生的資訊。  
  
-   由實作[IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md)介面。  
  
## <a name="see-also"></a>另請參閱  
 [程式碼內容](../../extensibility/debugger/code-context.md)   
 [符號提供者](../../extensibility/debugger/symbol-provider.md)   
 [符號提供者介面](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)

