---
title: 如何： 偵錯 Visual Studio 方案可執行檔不屬於 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 241a1dbf3af5db726f344ab42d53de3fdd30db3c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49278782"
---
# <a name="how-to-debug-an-executable-not-part-of-a-visual-studio-solution"></a>如何：偵錯不屬於 Visual Studio 方案的可執行檔
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

有時，您可能想要偵錯非 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案中的可執行檔。 這種可執行檔可能是您在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 之外所建立的可執行檔，或是您從別處取得的可執行檔。  
  
 這個問題的一般解決方法是，從 Visual Studio 外啟動該可執行檔，並使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 偵錯工具附加於其上。 如需詳細資訊，請參閱 <<c0> [ 附加至執行的處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
 附加至一個應用程式需要某些手動步驟，因此需要花上幾秒鐘。 這種略微延遲表示出，附加偵錯工具對嘗試偵錯一個啟動時所發生的問題無益。 此外，如果您正在偵錯一個不會等候使用者輸入且會很快就結束的程式，您可能沒有時間在該程式附加偵錯工具。 如果您已安裝 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]，您可以建立這種程式的 EXE 專案。  
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>若要為現有的可執行檔建立 EXE 專案  
  
1.  在上**檔案**功能表上，按一下**開放**，然後選取**專案**。  
  
2.  在 **開啟專案** 對話方塊中，按一下下拉式清單下的一步**檔案名稱**方塊，然後選取**所有專案檔**。  
  
3.  找出可執行檔，然後按一下**確定**。  
  
     這樣便可以建立包含該可執行檔的暫時方案。  
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>若要將可執行檔匯入至 Visual Studio 方案中  
  
1.  在上**檔案**功能表上，指向**新增專案**，然後按一下 **現有專案**。  
  
2.  在 **加入現有專案** 對話方塊中，按一下下拉式清單下的一步**檔案名稱**方塊，然後選取**所有專案檔**。  
  
3.  找出並選取可執行檔。  
  
4.  按一下 [確定 **Deploying Office Solutions**]。  
  
5.  選擇執行命令，例如啟動可執行檔**開始**，從**偵錯**功能表。  
  
    > [!NOTE]
    >  並非所有的程式語言都支援 EXE 專案。 如果您需要使用這項功能，請安裝 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]。  
  
     當您在偵錯沒有原始程式碼的可執行檔時，不論您是附加到正在執行的可執行檔，或者是將可執行檔加入至 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 方案，可用的偵錯功能都會受到限制。 如果可執行檔在建置時沒有相容格式的偵錯資訊，將更進一步地限制可用功能。 如果您有原始程式碼，最好的方法是將原始程式碼匯入至 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，並在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中建立偵錯版的可執行檔。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [DBG 檔案](http://msdn.microsoft.com/en-us/91e449e9-8b65-4123-960f-2107cd1f1cfd)



