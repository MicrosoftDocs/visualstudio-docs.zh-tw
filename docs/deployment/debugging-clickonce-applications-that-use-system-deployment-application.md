---
title: 將使用 System. Deployment 的 ClickOnce 應用程式進行偵錯工具
description: 瞭解如何藉由存取 deployment. 應用程式所提供的部署物件模型，來使用和自訂 advanced ClickOnce 部署功能。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6a014afff6c26b8cfe8f4f7fae508f78ef5905f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912247"
---
# <a name="debug-clickonce-applications-that-use-systemdeploymentapplication"></a>對使用 System.Deployment.Application 的 ClickOnce 應用程式進行偵錯
在中 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] ， [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署可讓您設定應用程式更新的方式。 但是，如果您需要使用和自訂 advanced [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] deployment 功能，您將需要存取所提供的部署物件模型 <xref:System.Deployment.Application> 。 您可以使用 <xref:System.Deployment.Application> api 進行先進的工作，例如：

- 在您的應用程式中建立 [立即更新] 選項

- 各種應用程式元件的條件式隨選下載

- 直接整合至應用程式的更新

- 保證用戶端應用程式一律保持最新狀態

  因為 <xref:System.Deployment.Application> api 只有在使用技術部署應用程式時才有效 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ，所以若要進行調試，唯一的方法就是使用部署應用程式 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 、附加至該應用程式，然後進行 debug。 因為此程式碼通常會在應用程式啟動時執行，而且您可以在附加偵錯工具之前執行，所以可能會很難儘早附加偵錯工具。 解決方法是在更新檢查程式碼或隨選程式碼之前，將中斷點放在 (或停止 Visual Basic 專案) 。

  建議的調試技術如下：

1. 開始之前，請確定已封存符號 ( .pdb) 和來源檔案。

2. 部署第1版的應用程式。

3. 建立新的空白方案。 從 [檔案] 功能表中，按一下 [新增]，然後按一下 [專案]。 在 [ **新增專案** ] 對話方塊中，開啟 [ **其他專案類型** ] 節點，然後選取 [ **Visual Studio 方案** ] 資料夾。 在 [ **範本** ] 窗格中，選取 [ **空白方案**]。

4. 將封存的來源位置新增至這個新方案的屬性。 在 **方案總管** 中，以滑鼠右鍵按一下方案節點，然後按一下 [ **屬性**]。 在 [ **屬性頁** ] 對話方塊中，選取 [ **Debug source Files**]，然後加入封存原始程式碼的目錄。 否則，偵錯工具將會尋找過期的原始程式檔，因為原始程式檔路徑會記錄在 .pdb 檔案中。 如果偵錯工具使用過期的原始程式檔，您會看到一則訊息，告訴您來源不相符。

5. 請確定偵錯工具可以找到 *.pdb* 檔案。 如果您已使用應用程式部署這些應用程式，偵錯工具會自動找到它們。 它一律會在第一個問題的元件旁邊看到。 否則，您將需要將封存路徑新增至符號檔 **( .pdb) 位置** (若要存取此選項，請從 [ **工具** ] 功能表中按一下 [ **選項**]，然後開啟 [ **調試** ] 節點，然後按一下 [ **符號** ]) 。

6. Debug `CheckForUpdate` 和 `Download` / `Update` 方法呼叫之間發生的狀況。

    例如，更新程式碼可能如下所示：

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

7. 部署第2版。

8. 嘗試將偵錯工具附加至第1版應用程式，因為它會下載第2版的更新。 或者，您也可以使用 `System.Diagnostics.Debugger.Break` 方法，或直接 `Stop` 在 Visual Basic 中使用。 當然，您不應該在實際執行程式碼中留下這些方法呼叫。

    例如，假設您正在開發 Windows Forms 的應用程式，而且您有這個方法的事件處理常式，其中有更新邏輯。 若要進行調試，只要在按下按鈕前附加，然後設定中斷點 (確定您開啟了適當的封存檔案，並將中斷點設定) 。

   只有在 <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> 部署應用程式時，才能使用屬性來叫用 <xref:System.Deployment.Application> api; 在中的偵錯工具時，不應該叫用 api [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。

## <a name="see-also"></a>另請參閱
- <xref:System.Deployment.Application>