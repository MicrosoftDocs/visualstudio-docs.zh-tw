---
title: HOW TO：啟用和停用編輯後繼續 |Microsoft Docs
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
ms.openlocfilehash: 7d564162a92976037729c4ad638136d7c1e827c4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438294"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>HOW TO：啟用和停用編輯後繼續
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以停用或啟用編輯後繼續中的**選項**在設計階段的對話方塊。 但是在進行偵錯時，無法變更這項設定。  
  
 [編輯後繼續] 只能用於偵錯組建中。 在原生 C++ 中，[編輯後繼續] 必須使用 /INCREMENTAL 選項。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-enabledisable-edit-and-continue"></a>若要啟用/停用編輯後繼續   
  
1. 開啟偵錯的 [選項] 頁面 (**工具 / 選項 / 偵錯**)。  
  
2. 向下捲動至**編輯後繼續**類別目錄。  
  
3. 若要啟用，請選取**啟用編輯後繼續**核取方塊。 若要停用，請清除該核取方塊。  
  
   > [!NOTE]
   > 如果已啟用 IntelliTrace，而且您同時收集 IntelliTrace 事件和呼叫資訊，則會停用 [編輯後繼續]。 如需詳細資訊，請參閱 <<c0> [ 設定 IntelliTrace](http://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)。  
  
4. 按一下 [確定] 。  
  
   如需這些選項的詳細資訊，請參閱[General，Debugging，Options Dialog Box](../debugger/general-debugging-options-dialog-box.md)。  
  
## <a name="see-also"></a>另請參閱  
 [編輯後繼續](../debugger/edit-and-continue.md)
