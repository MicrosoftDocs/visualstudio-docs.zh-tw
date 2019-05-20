---
title: Visual Studio + GitHub 搭售方案 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 04/23/2019
ms.topic: conceptual
description: 在管理 Visual Studio + GitHub 搭售方案中管理訂用帳戶
searchscope: VS Subscription
ms.openlocfilehash: a775317029db1a2be3b01411955ae197c7df6873
ms.sourcegitcommit: bd519d1da375e374016f94a44c295d3253f61a8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "64945237"
---
# <a name="managing-visual-studio-subscriptions-with-github-enterprise"></a>管理含 GitHub Enterprise 的 Visual Studio 訂用帳戶

與 Microsoft 之間簽有 Enterprise 合約 (EA) 的客戶即符合新訂用帳戶搭售方案的購買資格，這個方案結合了 Visual Studio 標準訂用帳戶與 GitHub Enterprise。 Visual Studio 訂閱者若想取得 GitHub Enterprise，這是個既簡單又經濟實惠的方法。 

當您的組織購買含 GitHub Enterprise 的 Visual Studio 訂用帳戶時，會分成兩部份佈建及管理。

## <a name="managing-visual-studio-subscriptions"></a>管理 Visual Studio 訂用帳戶

當您的組織購買含 GitHub Enterprise 的 Visual Studio 訂用帳戶時，訂用帳戶的 Visual Studio 部份會立即佈建，而訂用帳戶可在 Visual Studio [Subscriptions Administration](https://manage.visualstudio.com) 入口網站中進行指派與管理。 

如需管理訂用帳戶的詳細資訊，請查看下列主題：
- [使用管理入口網站](using-admin-portal.md)
- [指派訂用帳戶](assign-license.md)
- [編輯訂用帳戶](edit-license.md)
- [刪除訂用帳戶](delete-license.md)
- [過度分派](handle-overclaimed-license.md)

> [!Important]
> 如果含 GitHub Enterprise 的 Visual Studio 訂用帳戶由 Visual Studio 訂用帳戶系統管理員指派，而且過去未曾購買過這些訂用帳戶，就不會在組織中向 GitHub Enterprise 系統管理員顯示。 若要確保 GitHub Enterprise 訂用帳戶確實顯示，就必須在初次指派訂用帳戶時，購買**至少一個**含 GitHub Enterprise 的 Visual Studio Professional 或含 GitHub Enterprise 的 Visual Studio Enterprise。  
>
> 客戶必須負責確保指派的每個 GitHub 訂用帳戶都對應一個含 GitHub 的 Visual Studio 訂用帳戶 (在管理入口網站中指派)，以保持符合這個訂用帳戶的授權需求。

## <a name="managing-github-enterprise-subscriptions"></a>管理 GitHub Enterprise 訂用帳戶

在購買 GitHub Enterprise 訂用帳戶時，GitHub 會與客戶合作，以協助建立及設定要存取 GitHub 的組織，並指名系統管理員。  這些系統管理員接著會收到通知，告知他們已指定為系統管理員。  

由於這個過程較為複雜，在購買訂用帳戶後可能需要經過數天，組織和系統管理員才能全部設定完成。

GitHub 以雲端式 GitHub.com 或內部部署 GitHub Enterprise Server 的形式提供。  管理這兩的版本的流程並不相同。  GitHub 提供各式各樣的說明主題及系統管理員指南，協助您管理 GitHub Enterprise 訂用帳戶。  我們在下方提供了精選主題的連結。  

### <a name="githubspanspancom"></a>GitHub<span></span>.com 

如需管理 GitHub<span></span>.com 的詳細資訊，請參閱 [GitHub 說明](https://help.github.com/en)的下列主題。
- [說明主題的完整清單](https://help.github.com/en)
- [管理組織中的成員資格](https://help.github.com/en/articles/managing-membership-in-your-organization)
> - [邀請使用者加入您的組織](https://help.github.com/en/articles/inviting-users-to-join-your-organization)
> - [從小組/組織移除使用者](https://help.github.com/en/articles/removing-a-member-from-your-organization)
> - [恢復組織的前任成員](https://help.github.com/en/articles/reinstating-a-former-member-of-your-organization)
- [使用角色管理存取權](https://help.github.com/en/articles/managing-peoples-access-to-your-organization-with-roles)
- [將使用者分成小組](https://help.github.com/en/articles/organizing-members-into-teams)
- [管理組織存放庫的存取權](https://help.github.com/en/articles/managing-access-to-your-organizations-repositories)

### <a name="github-enterprise-server"></a>GitHub Enterprise Server

GitHub 說明提供包羅萬象的系統管理員指南，除了回答問題，也提供管理組織 GitHub Enterprise Server 實作的秘訣。

- [檢視所有系統管理員指南](https://help.github.com/en/enterprise/2.16/admin)
- [使用者管理](https://help.github.com/en/enterprise/2.16/admin/user-management)
> - [組織與小組](https://help.github.com/en/enterprise/2.16/admin/user-management/organizations-and-teams)
> > - [建立組織](https://help.github.com/en/enterprise/2.16/admin/user-management/creating-organizations)
> > - [建立小組](https://help.github.com/en/enterprise/2.16/admin/user-management/creating-teams)
> > - [將人員新增到小組](https://help.github.com/en/enterprise/2.16/admin/user-management/adding-people-to-teams)
> > - [從小組及組織移除人員](https://help.github.com/en/enterprise/2.16/admin/user-management/removing-users-from-teams-and-organizations)
> - [使用者安全性](https://help.github.com/en/enterprise/2.16/admin/user-management/user-security)
- [安裝及設定 GitHub Enterprise Server](https://help.github.com/en/enterprise/2.16/admin/installation)


## <a name="support-resources"></a>支援資源
-  您可以在 [GitHub 說明](https://help.github.com/en)中，找到各種 GitHub 各種相關問題的答案。
-  在 [GitHub Community Forum](https://github.community/) (GitHub 社群論壇) 可以獲得其他 GitHub 使用者的協助。
-  如需 Visual Studio 訂用帳戶有關銷售、訂閱、帳戶與計費的協助，請聯繫 Visual Studio [訂用帳戶支援](https://visualstudio.microsoft.com/subscriptions/support/)。
-  是否有關於 Visual Studio IDE、Azure DevOps Services 或其他 Visual Studio 產品或服務的問題？  前往 [Visual Studio 支援](https://visualstudio.microsoft.com/support/)
-  取得 GitHub Enterprise 的[技術支援](https://support.microsoft.com/en-us/supportforbusiness/productselection?sapId=b77fe80f-5417-80bd-4b2a-275cf0018c24)。   

## <a name="next-steps"></a>後續步驟
如需管理含 GitHub Enterprise 的 Visual Studio 訂用帳戶詳細資訊，請查看 Visual Studio [訂用帳戶系統管理員入口網站](https://visualstudio.microsoft.com/subscriptions-administration/)。