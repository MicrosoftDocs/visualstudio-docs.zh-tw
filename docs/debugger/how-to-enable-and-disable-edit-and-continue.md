---
title: HOW TO：啟用和停用編輯後繼續 |Microsoft Docs
ms.custom: seodec18
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: a201dab58084476f0993304d961fc5afa5693782
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55002225"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>HOW TO：啟用和停用編輯後繼續 (C#、 VB、 c + +)

您可以停用或啟用**編輯後繼續**在 Visual Studio**選項**在設計階段的對話方塊。 [編輯後繼續] 只能用於偵錯組建中。 如需詳細資訊，請參閱[編輯後繼續](../debugger/edit-and-continue.md)。 
  
原生 c + + 中，**編輯後繼續**需要使用`/INCREMENTAL`選項。 如需有關 c + + 中的功能需求的詳細資訊，請參閱此[部落格文章](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)並[編輯後繼續 （Visual c + +）](../debugger/edit-and-continue-visual-cpp.md)。
  
**若要啟用或停用編輯後繼續：**  
  
1.  如果您是在偵錯工作階段中，停止偵錯 (**偵錯** > **停止偵錯**或是**Shift**+**F5**).

1.  在 **工具** > **選項**> (或**偵錯** > **選項**) >**偵錯** > **一般**，選取**編輯後繼續**右窗格中。  
  
    > [!NOTE]
    >  如果已啟用 IntelliTrace，而且您同時收集 IntelliTrace 事件和呼叫資訊，則會停用 [編輯後繼續]。 如需詳細資訊，請參閱 < [IntelliTrace](../debugger/intellitrace.md)。
    
1.  針對 c + + 程式碼，請確定**啟用原生編輯後繼續**已選取此項目，並設定其他選項：
    - **繼續時套用變更 (僅限原生)**  
      
      如果選取，Visual Studio 會自動編譯，並繼續偵錯從中斷狀態時，會套用程式碼變更。 否則，您可以選擇要套用變更**偵錯** > **套用程式碼變更**。  
      
    - **警告出現過時的程式碼 (僅限原生)**  
      
      如果選取，會提供過時的程式碼的警告。 
  
1.  按一下 [確定 **Deploying Office Solutions**]。    
