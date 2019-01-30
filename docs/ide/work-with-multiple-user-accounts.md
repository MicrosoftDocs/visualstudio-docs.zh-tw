---
title: Work with multiple user accounts
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7470ad1a277356e663ea8756eebd36bb081cfb27
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942408"
---
# <a name="work-with-multiple-user-accounts"></a>Work with multiple user accounts

如果您有多個 Microsoft 帳戶及 (或) 工作或學校的帳戶，可以將它們全部加入 Visual Studio，這樣就可以存取所有帳戶的資源，而無須各別登入每個帳戶。 Azure、Application Insights、Azure DevOps 和 Office 365 服務都支援簡化的登入體驗。

在同一部電腦上新增多個帳戶之後，如果您於另一部電腦上登入 Visual Studio，該組帳戶會隨您漫遊。

> [!NOTE]
> 雖然帳戶名稱可以漫遊，但認證卻非如此。 當您於新電腦上第一次嘗試使用其他帳戶的資源時，系統會提示您輸入該帳戶的認證。

本文說明如何將多個帳戶新增至 Visual Studio。 也會說明如何看到可從那些帳戶存取的資源反映在 [新增已連線的服務] 對話方塊，以及 [伺服器總管] 和 [Team Explorer] 等地方。

## <a name="sign-in-to-visual-studio"></a>登入 Visual Studio

以 Microsoft 帳戶或組織帳戶登入 Visual Studio。 您應該會看到您的使用者名稱出現在視窗上方，如下所示：

![目前登入的使用者](../ide/media/vs2015_username.png)

### <a name="access-your-azure-account-in-server-explorer"></a>在伺服器總管中存取您的 Azure 帳戶

按 **Ctrl**+**Alt**+**S** 以開啟 [伺服器總管]。 展開 [Azure] 節點，會看到其包含可用於 Azure 帳戶中的資源，該帳戶與您用以登入 Visual Studio 的帳戶建立關聯。 看起來類似下圖：

![展開 Azure 節點的伺服器總管](../ide/media/work-with-multiple-user-accounts/server-explorer.png)

第一次在任何特定裝置上使用 Visual Studio 時，該對話方塊只會顯示在您登入帳戶所註冊的訂用帳戶。 您可以直接從 [伺服器總管] 存取任何其他帳戶的資源，方法是在 [Azure] 節點上按一下滑鼠右鍵，然後選擇 [管理和篩選訂用帳戶]，並從帳戶選擇器控制項新增帳戶。 您可視需要再選擇另一個帳戶，只要按一下向下箭頭，從帳戶的清單中選擇帳戶即可。 選擇帳戶之後，您可以自訂要在 [伺服器總管] 中顯示該帳戶的哪些訂用帳戶。

![[管理 Azure 訂用帳戶] 對話方塊](../ide/media/vs2015_manage_subs.png)

下次您開啟 [伺服器總管] 時，就會顯示該訂用帳戶的資源。

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>透過加入已連接服務對話方塊存取您的 Azure 帳戶

1. 開啟現有專案或建立新專案。

1. 在 [方案總管] 中選擇專案節點，然後以右鍵按一下並選擇 [新增] > [已連線的服務]。

   [新增已連線服務精靈] 隨即出現，並顯示與 Visual Studio 個人化帳戶建立關聯之 Azure 帳戶中的服務清單。 您不需要分別登入 Azure。 但當您在不同電腦上第一次嘗試存取其他帳戶的資源時，就必須登入這些帳戶。

### <a name="access-azure-active-directory-in-a-web-project"></a>在 Web 專案中存取 Azure Active Directory

Azure Active Directory (AAD) 可支援在 ASP.NET MVC Web 應用程式中進行終端使用者單一登入，或是在 Web API 服務中進行 AD 驗證。 網域驗證與個別使用者帳戶驗證不同。 對 Active Directory 網域具有存取權的使用者，可以使用其現有 AAD 帳戶連線至您的 Web 應用程式。 Office 365 應用程式也可以使用網域驗證。

若要查看此作業如何進行，請建立 Web 應用程式 ([檔案] > [新增專案] > [C#] > [雲端] > [ASP.NET Web 應用程式])。 然後在 [ASP.NET 新專案] 對話方塊中，選擇 [變更驗證]。 隨即會出現驗證精靈，供您選擇要在應用程式中使用何種驗證。

![ASP.NET 的 [變更驗證] 對話方塊](../ide/media/vs2015_change_authentication.png)

如需 ASP.NET 中不同種類驗證的詳細資訊，請參閱[在 Visual Studio 中建立 ASP.NET Web 專案](/aspnet/visual-studio/overview/2013/creating-web-projects-in-visual-studio#authentication-methods)。

### <a name="access-your-azure-devops-organization"></a>存取您的 Azure DevOps 組織

從主功能表中選擇 [Team] > [管理連線]，開啟 [Team Explorer - 連線] 視窗。 選擇 [管理連線] > [連線至專案]。 在 [連線至專案] 對話方塊中選取清單中的專案 (或選取 [新增 TFS 伺服器] 並輸入您的伺服器 URL)。 如果您選取了 URL，則不必重新輸入認證即可登入。

如需詳細資訊，請參閱[連線至 Team Explorer 中的專案](connect-team-project.md)。

## <a name="add-an-additional-account-to-visual-studio"></a>在 Visual studio 中新增額外帳戶

若要在 Visual studio 中新增額外帳戶：

1. 選擇 [檔案] > [帳戶設定]。

1. 在 [所有帳戶] 下方，選擇 [新增帳戶]。

1. 在 [登入您的帳戶] 頁面上選取帳戶，或選擇 [使用其他帳戶]。 遵循提示輸入新帳戶認證。

(選擇性) 現在您可以前往 [伺服器總管] 並查看與您剛才新增之帳戶建立關聯的 Azure 服務。 在 [伺服器總管] 中，以滑鼠右鍵按一下 [Azure] 節點，然後選擇 [管理和篩選訂用帳戶]。 按一下目前帳戶旁的下拉式箭號，選擇新的帳戶，然後選擇您想要在 [伺服器總管] 中顯示的訂用帳戶。 您應該會看到與指定之訂閱建立關聯的所有服務。 即使您目前並未使用第二個帳戶登入 Visual Studio，但仍登入了該帳戶的服務與資源。 [專案] > [新增已連線的服務] 以及 [小組] > [連線到 Team Foundation Server] 也是這樣。

### <a name="add-an-account-using-device-code-flow"></a>使用裝置程式碼流程新增帳戶

在某些情況下，您無法以一般方式登入或新增帳戶。 如果 Internet Explorer 因某些原因而遭到封鎖，或您的網路有防火牆，便可能發生此情況。 若要解決這個問題，您可以啟用「裝置程式碼流程」來新增帳戶，或重新驗證您的帳戶。 裝置程式碼流程可讓您使用不同的瀏覽器登入，或在不同的電腦 (實體或虛擬 (VM)) 上登入。

使用裝置程式碼流程登入：

1. 在 [工具] > [選項] > [環境] 下方開啟 [[帳戶]](reference/accounts-environment-options-dialog-box.md) 頁面，然後選取 [新增或重新驗證帳戶時啟用裝置程式碼流程]。 選擇 [確定] 關閉選項頁面。

1. 選擇 [檔案] > [帳戶設定] 開啟帳戶管理頁面。

1. 在 [所有帳戶] 下方，選擇 [新增帳戶]。

   對話方塊會顯示您的 URL，以及用來貼到網頁瀏覽器的程式碼。

   ![裝置程式碼流程 URL 和程式碼](media/work-with-multiple-user-accounts/device-login-code.png)

1. 按 **Ctrl**+**C** 來複製對話方塊中的文字，然後選擇 [確定] 關閉對話方塊。 將您複製的文字貼到文字編輯器 (例如 [記事本])。 這可讓您在下一個步驟中輕鬆複製程式碼。

1. 巡覽至您希望用於登入 Visual Studio 之電腦或網頁瀏覽器上的裝置登入 URL，然後將複製的程式碼貼上或輸入於顯示為**程式碼**的方塊。

   **Visual Studio** 應用程式名稱應該會顯示於頁面的下方。

1. 在 **Visual Studio** 下方，選擇 [繼續]。

   ![device-login-page.png](media/work-with-multiple-user-accounts/device-login-page.png)

1. 遵循提示輸入帳戶認證。

   隨即出現一個頁面，告知您已在您的裝置上登入 Visual Studio，您現在可以關閉瀏覽器視窗。

   ![完成透過瀏覽器登入 Visual Studio](media/work-with-multiple-user-accounts/sign-in-browser-complete.png)

1. 返回 Visual Studio 中的帳戶管理頁面，您會看到新增的帳戶列於 [所有帳戶] 下方。 選擇 [關閉]。

## <a name="see-also"></a>另請參閱

- [登入 Visual Studio](signing-in-to-visual-studio.md)
- [登入 Visual Studio for Mac](/visualstudio/mac/signing-in)
