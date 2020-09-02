---
title: 如何：啟用和停用編輯後繼續 |Microsoft Docs
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
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 70914da9be4046589a0ca3b8e5fd4ae13210ca51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65689269"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>如何：啟用和停用編輯後繼續
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以在設計階段停用或啟用 [ **選項** ] 對話方塊中的 [編輯後繼續]。 但是在進行偵錯時，無法變更這項設定。  
  
 [編輯後繼續] 只能用於偵錯組建中。 在原生 C++ 中，[編輯後繼續] 必須使用 /INCREMENTAL 選項。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-enabledisable-edit-and-continue"></a>若要啟用/停用編輯後繼續   
  
1. [開啟調試選項] 頁面 ([ **工具]/[選項]/[調試** ]) 。  
  
2. 向下滾動至 [ **編輯後繼續** ] 類別。  
  
3. 若要啟用，請選取 [ **啟用編輯後繼續** ] 核取方塊。 若要停用，請清除該核取方塊。  
  
   > [!NOTE]
   > 如果已啟用 IntelliTrace，而且您同時收集 IntelliTrace 事件和呼叫資訊，則會停用 [編輯後繼續]。 如需詳細資訊，請參閱 [設定 IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)。  
  
4. 按一下 [確定]  。  
  
   如需這些選項的詳細資訊，請參閱 [[一般]、[偵錯工具]、[選項] 對話方塊](../debugger/general-debugging-options-dialog-box.md)。  
  
## <a name="see-also"></a>另請參閱  
 [編輯後繼續](../debugger/edit-and-continue.md)
