---
title: 偵錯不屬於 Visual Studio 方案的應用程式
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/19/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ae2ea60a4f2427cbe1509a8fa05c787d44b19d7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55019131"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>偵錯不屬於 Visual Studio 方案的應用程式 (c + +， C#，Visual Basic 中， F#)

您可能想要偵錯應用程式 (*.exe*檔案)，不是 Visual Studio 方案的一部分。 您或其他人可能已建立 Visual Studio 中，外部應用程式，或您有來自其他地方的應用程式。 

偵錯在 Visual Studio 中不存在的應用程式的一般方法是啟動 Visual Studio 中，外部應用程式，然後連結至使用**附加至處理序**Visual Studio 偵錯工具中。 如需詳細資訊，請參閱 <<c0> [ 附加至執行中處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
附加至應用程式需要花費幾秒鐘的手動步驟。 由於此延遲，附加，將不會協助偵錯的啟動問題，或應用程式，不等候使用者輸入時，會很快就結束。 

在這些情況下，您就可以建立應用程式，Visual Studio 的 EXE 專案或將它匯入到現有的C#，Visual Basic 或 c + + 方案。 並非所有的程式語言都支援 EXE 專案。 

>[!IMPORTANT]
>不在 Visual Studio 中建置的應用程式的偵錯功能，都會受到限制是否附加至應用程式，或將它新增至 Visual Studio 方案。 
>
>如果您有原始程式碼，最好的方法是將程式碼匯入 Visual Studio 專案。 然後，執行應用程式的偵錯組建。
>
>如果您沒有原始程式碼，而且應用程式不需要[偵錯資訊](../debugger/how-to-set-debug-and-release-configurations.md)相容的格式，在可用的偵錯功能都是很少。 

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>若要建立新的 EXE 專案現有應用程式  
   
1. 在 Visual Studio 中，選取**檔案** > **Open** > **專案**。  
   
1. 在 **開啟專案**對話方塊中，選取**所有專案檔**，如果尚未選取，請在下拉式清單旁**檔案名稱**。  
   
1. 瀏覽至 *.exe*檔案，加以選取，然後選取**開啟**。  
   
   檔案會出現在新的、 暫時的 Visual Studio 方案。

1. 開始偵錯應用程式中選取執行的命令，例如**開始偵錯**，從**偵錯**功能表。    
  
### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>若要將應用程式匯入現有的 Visual Studio 方案  
  
1.  使用 c + + 中， C#，或選取 Visual Basic 方案在 Visual Studio 中，開啟**檔案** > **新增** > **現有專案**。  
  
1. 在 **開啟專案**對話方塊中，選取**所有專案檔**，如果尚未選取，請在下拉式清單旁**檔案名稱**。  
   
1. 瀏覽至 *.exe*檔案，加以選取，然後選取**開啟**。  
   
   檔案會顯示為新的專案，在目前的方案。  
   
1. 選取新的檔案，啟動偵錯應用程式的方式選取執行命令，例如**開始偵錯**，從**偵錯**功能表。    
  
### <a name="see-also"></a>另請參閱  
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [DBG 檔案](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))