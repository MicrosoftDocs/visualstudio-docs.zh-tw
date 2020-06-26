---
title: Debug 使用 System.web 應用程式的 ClickOnce 應用程式
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 203f1edc2e29bbbc34fb39e6aa01c1b56bf20e91
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382649"
---
# <a name="debug-clickonce-applications-that-use-systemdeploymentapplication"></a>對使用 System.Deployment.Application 的 ClickOnce 應用程式進行偵錯
在中 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] ， [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署可讓您設定應用程式的更新方式。 不過，如果您需要使用和自訂高階 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署功能，就必須存取所提供的部署物件模型 <xref:System.Deployment.Application> 。 您可以使用 <xref:System.Deployment.Application> api 來進行 advanced 工作，例如：

- 在您的應用程式中建立「立即更新」選項

- 各種應用程式元件的條件式隨選下載

- 直接整合到應用程式中的更新

- 保證用戶端應用程式一律為最新狀態

  由於 <xref:System.Deployment.Application> api 只有在以技術部署應用程式時才會執行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ，因此若要進行 debug，唯一的方法就是使用部署應用程式 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ，並將其附加至它，然後進行 debug。 因為此程式碼通常會在應用程式啟動並執行，然後才可以附加偵錯工具，所以很難以足夠的速度附加偵錯工具。 解決方案是在您的更新檢查程式碼或隨選程式碼之前，放置中斷（或停止 Visual Basic 專案）。

  建議的調試技術如下所示：

1. 開始之前，請確定已封存符號（.pdb）和來源檔案。

2. 部署第1版的應用程式。

3. 建立新的空白方案。 從 [檔案]**** 功能表中，按一下 [新增]****，然後按一下 [專案]****。 在 [**新增專案**] 對話方塊中，開啟 [**其他專案類型**] 節點，然後選取 [ **Visual Studio 方案**] 資料夾。 在 [**範本**] 窗格中，選取 [**空白方案**]。

4. 將封存的來源位置新增至這個新方案的屬性。 在**方案總管**中，以滑鼠右鍵按一下方案節點，然後按一下 [**屬性**]。 在 [**屬性頁**] 對話方塊中，選取 [**偵錯工具原始**程式檔]，然後加入封存原始程式碼的目錄。 否則，偵錯工具會尋找過期的來源檔案，因為來源檔案路徑會記錄在 .pdb 檔案中。 如果偵錯工具使用過時的來源檔案，您會看到一則訊息，告訴您來源不相符。

5. 請確定偵錯工具可以找到 *.pdb*檔案。 如果您已使用您的應用程式部署它們，偵錯工具會自動尋找它們。 它一律會在問題的前面尋找元件的旁邊。 否則，您必須將封存路徑新增至**符號檔（.pdb）位置**（若要存取此選項，請從 [**工具**] 功能表按一下 [**選項**]，然後開啟 [**調試**] 節點，再按一下 [**符號**]）。

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

8. 嘗試在下載第2版的更新時，將偵錯工具附加至第1版的應用程式。 或者，您也可以使用 `System.Diagnostics.Debugger.Break` 方法，或直接 `Stop` 在 Visual Basic 中使用。 當然，您不應該將這些方法呼叫留在實際執行的程式碼中。

    例如，假設您正在開發 Windows Forms 應用程式，而且您有這個方法的事件處理常式，其中包含更新邏輯。 若要進行這種的偵錯工具，只需在按下按鈕之前附加，然後設定中斷點（請確定您開啟適當的封存檔案，並在該處設定中斷點）。

   只有在 <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> 部署應用程式時，才使用屬性來叫用 <xref:System.Deployment.Application> api; 在中的調試過程中，不應叫用 api [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。

## <a name="see-also"></a>另請參閱
- <xref:System.Deployment.Application>