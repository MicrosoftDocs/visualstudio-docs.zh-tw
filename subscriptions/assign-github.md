---
title: 使用 GitHub Enterprise 指派 Visual Studio 訂用帳戶 |Microsoft 檔
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: f271d623-dcde-442a-865c-4dca5ad8a9c5
ms.date: 03/03/2021
ms.topic: conceptual
description: 使用 GitHub Enterprise 管理 Visual Studio 訂用帳戶中的訂閱
ms.openlocfilehash: 5837ec33e6f17f0970178a0f1b306960e9c42668
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249698"
---
# <a name="manage-visual-studio-subscriptions-with-github-enterprise"></a>管理含 GitHub Enterprise 的 Visual Studio 訂閱
具有 Microsoft 的 Enterprise 合約 (EA) 的客戶有資格購買新的訂用帳戶供應專案，以整合 Visual Studio 標準訂閱和 GitHub Enterprise。 Visual Studio 訂閱者若想取得 GitHub Enterprise，這是個既簡單又經濟實惠的方法。 

當您的組織購買含 GitHub Enterprise 的 Visual Studio 訂用帳戶時，會在兩個部分中布建及管理這些訂閱。

## <a name="manage-visual-studio-subscriptions"></a>管理 Visual Studio 訂閱
當您的組織購買含 GitHub Enterprise 的 Visual Studio 訂用帳戶時，訂用帳戶的 Visual Studio 部分會立即布建，而訂用帳戶可在 Visual Studio 訂用帳戶 [管理](https://manage.visualstudio.com) 入口網站中指派及管理。 當您指派具有 GitHub Enterprise 的 Visual Studio 訂用帳戶之後，訂閱者會收到一封電子郵件，讓他們知道他們可以在其上存取 Visual Studio 訂用帳戶 <https://my.visualstudio.com/subscriptions> 。

如需有關管理 Visual Studio 訂閱的詳細資訊，請參閱下列主題：
- [使用系統管理員入口網站](using-admin-portal.md)
- [指派訂閱](assign-license.md)
- [編輯訂閱](edit-license.md)
- [刪除訂閱](delete-license.md)
- [過度分派](handle-overclaimed-license.md)

> [!Important]
> 如果 visual studio 訂用帳戶（含 GitHub Enterprise）是由 Visual Studio 訂用帳戶管理員所指派，但未先購買，則 GitHub 將不會收到您想要建立 GitHub 企業帳戶的通知。  **至少購買一個** 您應在指派訂用帳戶之前，先建立具有 GitHub Enterprise 的 Visual Studio 訂用帳戶。

## <a name="moving-to-visual-studio-with-github-enterprise"></a>使用 GitHub Enterprise 移至 Visual Studio
如果您的組織在指派標準 Visual Studio Enterprise 和 Visual Studio Professional 訂用帳戶之後，使用 GitHub Enterprise 配套購買 Visual Studio 訂用帳戶，則系統管理員入口網站所包含的功能，可協助您將現有的訂閱者移至具有 GitHub Enterprise 和/或 Visual Studio Professional 含 GitHub Enterprise 訂用帳戶的對應 Visual studio Enterprise。  例如，具有 Visual Studio Professional 訂閱的訂閱者將會移至 Visual Studio Professional 含 GitHub Enterprise 訂用帳戶。 在左側的 [總覽] 面板中，您會看到下列磚：

   > [!div class="mx-imgBorder"]
   > ![立即移動按鈕](_img/assign-github/move-now.png "按一下 [立即移動]，以使用 GitHub Enterprise 訂用帳戶將訂閱升級至 Visual Studio")

> [!IMPORTANT]
> 如上所述，將會保留現有的訂閱者資料、歷程記錄和訂用帳戶識別碼，而且任何已啟用的權益都不會因為這項移動而中斷。  
>
> 這項功能是以階段部署，在您的合約 (的) 可能無法立即提供。

當您按一下 [ **立即移動** ] 按鈕時，飛出面板將會提供您移動企業和/或專業版訂閱的建議：

   > [!div class="mx-imgBorder"]
   > ![飛出面板](_img/assign-github/fly-out.png)

在此磚中，您可以查看受影響的訂閱者，並指定您是否要在移動完成後通知他們收到電子郵件通知。  這封電子郵件會通知訂閱者其權益保持不變，並鼓勵他們開始在 GitHub 中設定存在。  

按一下 [ **移動所有訂閱者** ] 按鈕之後，您將會確認選取專案，並等候幾秒鐘讓訂用帳戶移動完成。  如果適用，您將需要分別針對 Professional 和 Enterprise 執行這些步驟。  


## <a name="what-is-the-visual-studio-with-github-enterprise-setup-process"></a>什麼是含 GitHub Enterprise 設定程序的 Visual Studio？
GitHub Enterprise 是與 Visual Studio 訂用帳戶分開設定及管理的。 在使用 GitHub Enterprise 購買的 Visual Studio 訂用帳戶之後，GitHub Enterprise 帳戶設定程式會與 (平行起始，但與) 在 [manage.visualstudio.com](https://manage.visualstudio.com)中建立合約不同。 建立此 GitHub Enterprise 帳戶可能需要一些時間。 

在公司設定 GitHub Enterprise 帳戶之後，GitHub 會傳送電子郵件給相關訂閱者 (已獲指派含 GitHub Enterprise 的 Visual Studio 訂閱)，通知他們其 Visual Studio 訂閱已連結。 訂閱者收到這封電子郵件後，他們就可以與 GitHub 組織系統管理員聯繫，以接收適當組織的邀請。

如需 GitHub Enterprise 設定的詳細資訊，請參閱 [訂閱者檔](access-github.md)。   

## <a name="manage-github-enterprise-subscriptions"></a>管理 GitHub Enterprise 訂閱
購買 GitHub Enterprise 訂用帳戶時，GitHub 會與客戶合作，以協助建立及設定將存取 GitHub 並識別系統管理員的組織。  然後，系統管理員會收到通知，指出他們已設定為系統管理員。  

由於此程式更複雜，因此購買訂閱之後可能需要幾天的時間，才能完全設定組織和系統管理員。

GitHub 以雲端式 GitHub.com 或內部部署 GitHub Enterprise Server 的形式提供。  管理這兩的版本的流程並不相同。  GitHub 提供各種說明主題和系統管理指南，可協助您管理 GitHub Enterprise 訂用帳戶。  我們在下方提供了精選主題的連結。  

## <a name="support-resources"></a>支援資源

- 深入[瞭解 github 檔的 github](https://docs.github.com/en/github/setting-up-and-managing-your-enterprise-account/managing-licenses-for-the-github-enterprise-and-visual-studio-bundle)指派
- 在 [github](https://help.github.com/en)說明的廣泛 github 主題中尋找問題的答案。
- 在 [GitHub Community Forum](https://github.community/) (GitHub 社群論壇) 可以獲得其他 GitHub 使用者的協助。
- 如需有關銷售、訂用帳戶、帳戶及 Visual Studio 訂用帳戶計費的協助，請聯絡 [訂閱支援](https://visualstudio.microsoft.com/subscriptions/support/)。
- 是否有關於 Visual Studio IDE、Azure DevOps Services 或其他 Visual Studio 產品或服務的問題？  前往 [Visual Studio 支援](https://visualstudio.microsoft.com/support/)
- 取得 GitHub Enterprise 的[技術支援](https://support.microsoft.com/supportforbusiness/productselection?sapId=b77fe80f-5417-80bd-4b2a-275cf0018c24)。   

## <a name="see-also"></a>另請參閱

- [Visual Studio 檔](/visualstudio/)
- [Azure DevOps 文件](/azure/devops/) \(英文\)
- [Azure 檔](/azure/)
- [Microsoft 365 檔](/microsoft-365/)

## <a name="next-steps"></a>下一步

深入瞭解如何管理 Visual Studio 訂閱。
- [指派個別訂用帳戶](assign-license.md)
- [指派多個訂用帳戶](assign-license-bulk.md)
- [編輯訂用帳戶](edit-license.md)
- [刪除訂用帳戶](delete-license.md)
- [判斷最大使用量](maximum-usage.md)

如需使用 GitHub Enterprise 管理 Visual Studio 訂閱的詳細資訊，請參閱 Visual Studio 訂用帳戶系統 [管理員入口網站](https://visualstudio.microsoft.com/subscriptions-administration/)。