---
title: 偵錯使用 System.Deployment.Application 的 ClickOnce 應用程式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6254ce933ccfc54f28e8e0e893932a5fbda27a0a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54981242"
---
# <a name="debug-clickonce-applications-that-use-systemdeploymentapplication"></a>對使用 System.Deployment.Application 的 ClickOnce 應用程式進行偵錯
在  [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署可讓您設定應用程式的更新方式。 不過，如果您要使用和自訂進階[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署功能，您將需要存取所提供的部署物件模型<xref:System.Deployment.Application>。 您可以使用<xref:System.Deployment.Application>Api 適用於這類進階工作：  
  
- 建立應用程式中的 [立即更新] 選項  
  
- 條件式，視需要下載的各種應用程式元件  
  
- 直接整合到應用程式的更新  
  
- 保證用戶端應用程式永遠最新  
  
  因為<xref:System.Deployment.Application>只有當應用程式的部署使用的 Api 運作[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]技術，加以偵錯的唯一方式是將應用程式使用[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]，附加至這個項目，然後進行偵錯。 它可能難以附加偵錯工具及早，因為應用程式啟動並執行之前，您可以附加偵錯工具時，通常會執行此程式碼。 解決方案是將符號 （或停止時，Visual Basic 專案） 放在您更新檢查程式碼或隨程式碼之前。  
  
  建議的偵錯技巧如下所示：  
  
1. 在開始之前，請確定符號 (.pdb) 和原始程式檔會封存。  
  
2. 部署應用程式的第 1 版。  
  
3. 建立新的空白方案。 從**檔案**功能表上，按一下**新增**，然後**專案**。 在 **新的專案**對話方塊中，開啟**其他專案類型**節點，然後選取**Visual Studio 方案**資料夾。 在 **範本**窗格中，選取**空白方案**。  
  
4. 加入此新方案的屬性已封存的來源位置。 在 **方案總管**，以滑鼠右鍵按一下方案節點，然後按一下**屬性**。 在 **屬性頁**對話方塊中，選取**偵錯原始程式檔**，然後新增 已封存的原始程式碼的目錄。 否則偵錯工具會尋找過期原始程式檔，因為來源檔案路徑會記錄在.pdb 檔案。 如果偵錯工具使用過期的原始程式檔，您會看到訊息，告知您與不相符的來源。  
  
5. 請確定偵錯工具可以尋找 *.pdb*檔案。 如果您已部署它們與您的應用程式，偵錯工具會自動找到它們。 它一律會尋找組件旁邊有問題第一次。 否則，您必須新增的封存路徑**符號檔 (.pdb) 位置**(若要存取此選項時，從**工具**功能表上，按一下 **選項**，然後開啟  **偵錯**節點，然後按一下**符號**)。  
  
6. 偵錯項目之間會發生`CheckForUpdate`並`Download` / `Update`方法呼叫。  
  
    例如，更新程式碼可能如下：  
  
   ```vb
       Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
           If My.Application.Deployment.IsNetworkDeployed Then  
  
               If (My.Application.Deployment.CheckForUpdate()) Then  
  
                   My.Application.Deployment.Update()  
                   Application.Restart()  
  
               End If  
  
           End If  
       End Sub  
   ```  
  
7. 部署第 2 版。  
  
8. 嘗試將偵錯工具附加至第 1 版的應用程式，因為它會下載第 2 版的更新。 或者您可以使用`System.Diagnostics.Debugger.Break`方法或只是`Stop`Visual Basic 中。 當然，您不應該在實際程式碼中留下這些方法呼叫。  
  
    例如，假設您正在開發 Windows Forms 應用程式，並可在其中更新邏輯使用這個方法的事件處理常式。 若要進行偵錯，只要附加之前為按下按鈕，則將其設定中斷點 （請確定您開啟適當的封存的檔案，並設定中斷點）。  
  
   使用<xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A>屬性，以叫用<xref:System.Deployment.Application>Api 應用程式部署時，才; Api 應該不會叫用在偵錯期間[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Deployment.Application>