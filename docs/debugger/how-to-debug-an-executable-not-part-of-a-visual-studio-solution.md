---
title: "如何： 偵錯的可執行檔不是 Visual Studio 方案的一部分 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be07be0e1374360a96b6672b095dcc039c6bb4f0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-an-executable-that-is-not-part-of-a-visual-studio-solution"></a>如何： 偵錯的可執行檔不是 Visual Studio 方案的一部分
有時候，您可能想要偵錯的可執行檔 （.exe 檔） 不屬於[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案。 這種可執行檔可能是您在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 之外所建立的可執行檔，或是您從別處取得的可執行檔。  
  
這個問題的一般解決方法是，從 Visual Studio 外啟動該可執行檔，並使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 偵錯工具附加於其上。 如需詳細資訊，請參閱[附加至執行的處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
附加至一個應用程式需要某些手動步驟，因此需要花上幾秒鐘。 這種略微延遲表示出，附加偵錯工具對嘗試偵錯一個啟動時所發生的問題無益。 此外，如果您正在偵錯一個不會等候使用者輸入且會很快就結束的程式，您可能沒有時間在該程式附加偵錯工具。 如果您有[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]和[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]安裝，您可以建立此種程式的 EXE 專案。

> [!NOTE]
>  並非所有的程式語言都支援 EXE 專案。

當您偵錯的可執行檔不是您的 Visual Studio 方案的一部分時，可用的偵錯功能，則會限制您附加到正在執行，或加入至可執行檔是否[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]方案。

- 如果您有原始程式碼，最好的方法是將原始程式碼匯入至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，並在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中建立偵錯版的可執行檔。
- 如果您沒有原始程式碼，並可執行檔建置時沒有[偵錯資訊](../debugger/how-to-set-debug-and-release-configurations.md)相容的格式，可用的偵錯功能會非常有限。 
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>若要為現有的可執行檔建立 EXE 專案  
  
1.  在**檔案**功能表上，按一下 **開啟**選取**專案**。  
  
2.  在**開啟專案** 對話方塊中，按一下旁邊的下拉式清單**檔案名稱**方塊，然後選取**所有專案檔**。  
  
3.  找出可執行檔，然後按一下**確定**。  

    這樣便可以建立包含該可執行檔的暫時方案。

5.  選擇執行命令，例如啟動可執行檔**啟動**，從**偵錯**功能表。    
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>若要將可執行檔匯入至 Visual Studio 方案中  
  
1.  在**檔案**功能表上，指向**加入專案**，然後按一下 **現有專案**。  
  
2.  在**加入現有專案** 對話方塊中，按一下旁邊的下拉式清單**檔案名稱**方塊，然後選取**所有專案檔**。  
  
3.  找出並選取可執行檔。  
  
4.  按一下 [確定]。  
  
5.  選擇執行命令，例如啟動可執行檔**啟動**，從**偵錯**功能表。    
  
## <a name="see-also"></a>另請參閱  
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [DBG 檔案](http://msdn.microsoft.com/en-us/91e449e9-8b65-4123-960f-2107cd1f1cfd)