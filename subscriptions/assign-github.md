---
title: Visual Studio + GitHub Enterprise 供應專案 |Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: f271d623-dcde-442a-865c-4dca5ad8a9c5
ms.date: 03/17/2020
ms.topic: conceptual
description: 管理 Visual Studio + GitHub Enterprise 供應專案中的訂用帳戶
ms.openlocfilehash: 01b043698aaeb23151357595d5c39cd117fd47c7
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2020
ms.locfileid: "88249838"
---
# <a name="manage-visual-studio-subscriptions-with-github-enterprise"></a>管理含 GitHub Enterprise 的 Visual Studio 訂閱
 (EA) 與 Microsoft 簽訂 Enterprise 合約的客戶，有資格購買新的訂用帳戶供應專案，以結合 Visual Studio 標準訂閱和 GitHub Enterprise。 Visual Studio 訂閱者若想取得 GitHub Enterprise，這是個既簡單又經濟實惠的方法。 

當您的組織購買含 GitHub Enterprise 的 Visual Studio 訂用帳戶時，會分成兩部份佈建及管理。

## <a name="manage-visual-studio-subscriptions"></a>管理 Visual Studio 訂閱
當您的組織使用 GitHub Enterprise 購買 Visual Studio 訂用帳戶時，訂用帳戶的 Visual Studio 部分會立即布建，而訂用帳戶可在 Visual Studio 訂用帳戶系統 [管理](https://manage.visualstudio.com) 入口網站中指派和管理。 

如需管理訂用帳戶的詳細資訊，請查看下列主題：
- [使用系統管理員入口網站](using-admin-portal.md)
- [指派訂閱](assign-license.md)
- [編輯訂閱](edit-license.md)
- [刪除訂閱](delete-license.md)
- [過度分派](handle-overclaimed-license.md)

> [!Important]
> 如果含 GitHub Enterprise 的 Visual Studio 訂用帳戶由 Visual Studio 訂用帳戶系統管理員指派，而且過去未曾購買過這些訂用帳戶，就不會在組織中向 GitHub Enterprise 系統管理員顯示。 若要確保 GitHub Enterprise 訂用帳戶確實顯示，就必須在初次指派訂用帳戶時，購買**至少一個**含 GitHub Enterprise 的 Visual Studio Professional 或含 GitHub Enterprise 的 Visual Studio Enterprise。  
>
> 客戶必須負責確保每個指派的 GitHub 訂用帳戶都有對應的 Visual Studio，並在 Visual Studio 訂用帳戶管理入口網站中指派 GitHub 訂用帳戶，以維持符合此訂閱的授權需求。

## <a name="manage-github-enterprise-subscriptions"></a>管理 GitHub Enterprise 訂閱
在購買 GitHub Enterprise 訂用帳戶時，GitHub 會與客戶合作，以協助建立及設定要存取 GitHub 的組織，並指名系統管理員。  這些系統管理員接著會收到通知，告知他們已指定為系統管理員。  

由於此程式較為複雜，因此可能需要幾天的時間，才能購買訂閱，讓組織和系統管理員完全設定。

GitHub 以雲端式 GitHub.com 或內部部署 GitHub Enterprise Server 的形式提供。  管理這兩的版本的流程並不相同。  GitHub 提供各式各樣的說明主題及系統管理員指南，協助您管理 GitHub Enterprise 訂用帳戶。  我們在下方提供了精選主題的連結。  

### <a name="githubcom"></a>GitHub.com 
如需有關管理 GitHub.com 的詳細資訊，請參閱 [GitHub 說明](https://help.github.com/en)的下列主題。
+ [說明主題的完整清單](https://help.github.com/en)
+ [管理組織中的成員資格](https://help.github.com/en/articles/managing-membership-in-your-organization)
+ [邀請使用者加入您的組織](https://help.github.com/en/articles/inviting-users-to-join-your-organization)
  - [從小組/組織移除使用者](https://help.github.com/en/articles/removing-a-member-from-your-organization)
  - [恢復組織的前任成員](https://help.github.com/en/articles/reinstating-a-former-member-of-your-organization)
+ [使用角色管理存取權](https://help.github.com/en/articles/managing-peoples-access-to-your-organization-with-roles)
+ [將使用者分成小組](https://help.github.com/en/articles/organizing-members-into-teams)
+ [管理組織存放庫的存取權](https://help.github.com/en/articles/managing-access-to-your-organizations-repositories) \(英文\)

### <a name="github-enterprise-server"></a>GitHub Enterprise Server
GitHub 說明提供包羅萬象的系統管理員指南，除了回答問題，也提供管理組織 GitHub Enterprise Server 實作的秘訣。

+ [檢視所有系統管理員指南](https://help.github.com/en/enterprise/2.16/admin)
+ [使用者管理](https://help.github.com/en/enterprise/2.16/admin/user-management)
  - [組織與小組](https://help.github.com/en/enterprise/2.16/admin/user-management/organizations-and-teams)
    - [建立組織](https://help.github.com/en/enterprise/2.16/admin/user-management/creating-organizations)
    - [建立小組](https://help.github.com/en/enterprise/2.16/admin/user-management/creating-teams)
    - [將人員新增到小組](https://help.github.com/en/enterprise/2.16/admin/user-management/adding-people-to-teams)
    - [從小組及組織移除人員](https://help.github.com/en/enterprise/2.16/admin/user-management/removing-users-from-teams-and-organizations)
  - [使用者安全性](https://help.github.com/en/enterprise/2.16/admin/user-management/user-security)
+ [安裝及設定 GitHub Enterprise Server](https://help.github.com/en/enterprise/2.16/admin/installation)

## <a name="support-resources"></a>支援資源

- 您可以在 [GitHub 說明](https://help.github.com/en)中，找到各種 GitHub 各種相關問題的答案。
- 在 [GitHub Community Forum](https://github.community/) (GitHub 社群論壇) 可以獲得其他 GitHub 使用者的協助。
- 如需 Visual Studio 訂閱的銷售、訂閱、帳戶和計費的協助，請聯絡 Visual Studio [訂閱支援](https://visualstudio.microsoft.com/subscriptions/support/)。
- 是否有關於 Visual Studio IDE、Azure DevOps Services 或其他 Visual Studio 產品或服務的問題？  前往 [Visual Studio 支援](https://visualstudio.microsoft.com/support/)
- 取得 GitHub Enterprise 的[技術支援](https://support.microsoft.com/en-us/supportforbusiness/productselection?sapId=b77fe80f-5417-80bd-4b2a-275cf0018c24)。   

## <a name="see-also"></a>另請參閱

- [Visual Studio 檔](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 檔](https://docs.microsoft.com/azure/devops/)
- [Azure 檔](https://docs.microsoft.com/azure/)
- [Microsoft 365 檔](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>後續步驟

深入瞭解如何管理 Visual Studio 訂閱。
- [指派個別訂閱](assign-license.md)
- [指派多個訂用帳戶](assign-license-bulk.md)
- [編輯訂用帳戶](edit-license.md)
- [刪除訂用帳戶](delete-license.md)
- [判斷最大使用量](maximum-usage.md)

如需管理含 GitHub Enterprise 的 Visual Studio 訂用帳戶詳細資訊，請查看 Visual Studio [訂用帳戶系統管理員入口網站](https://visualstudio.microsoft.com/subscriptions-administration/)。
