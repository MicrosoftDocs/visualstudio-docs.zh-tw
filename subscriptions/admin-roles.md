---
title: Visual Studio 訂閱的超級管理員和系統管理員角色
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 6601c395-f778-48c1-ab76-cf454b9193e4
ms.date: 03/19/2021
ms.topic: conceptual
description: 深入瞭解超級管理員和系統管理員角色，以及如何指派系統管理員。
ms.openlocfilehash: eca87026c681454925974f2e394737092c3e226d
ms.sourcegitcommit: d8d230791890cda532c263d04288dc13d2261c7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2021
ms.locfileid: "104757590"
---
# <a name="super-admins-and-admins-for-visual-studio-subscription-agreements"></a>Visual Studio 訂用帳戶協定的超級管理員和系統管理員

大量授權客戶的新 Visual Studio 訂用帳戶管理入口網站中有兩個不同角色。 這些角色像是之前存在於 VLSC 中的主要/通知連絡人角色和訂用帳戶管理員角色。

**超級管理員：** 當組織最初設定時，主要或通知連絡人預設會成為超級管理員。 主要連絡人或通知連絡人可以選擇指派額外的超級管理員或系統管理員。 超級管理員可以新增和移除其他系統管理員和訂閱者。 如果系統中有兩個以上的超級管理員，則超級管理員可以刪除所有超級管理員，但最後必須保留兩個以策安全。

系統 **管理員：** 系統管理員只能由超級管理員指派。系統管理員只能管理超級管理員指派給他們的合約中的「訂閱者」。

觀看有關如何管理系統管理員的示範。 
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6L]

## <a name="assigning-admins"></a>指派系統管理員
若要指派新的系統管理員 (系統管理員) ：
1. 使用指派為用於購買訂用帳戶的合約上超級管理員電子郵件地址登入 https://manage.visualstudio.com。
2. 按一下標示為 [管理系統管理員] 的索引標籤。
3. 按一下 **[新增]** 。
   > [!div class="mx-imgBorder"]
   > ![新增管理員](_img/admin-roles/add-admins.png "按一下 [管理系統管理員] 分頁，然後按一下 [新增] 以指派新的系統管理員。")
4. 使用新系統管理員的資訊來完成表單。  
   > [!div class="mx-imgBorder"]
   > ![新增系統管理員表單](_img/admin-roles/add-form.png "輸入新系統管理員的登入資訊，並選擇是否要讓他們成為超級系統管理員。 然後按一下 [新增]。")

   > [!NOTE]
   > 如果您想要讓此系統管理員能夠指派其他系統管理員，請記得核取 [超級管理員] 方塊。

5. 當您按一下 [新增] 指派新的系統管理員之後，他們會收到一封電子郵件，邀請他們登入入口網站。  

## <a name="resources"></a>資源
- [Visual Studio 管理與訂閱支援](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>另請參閱
- [Visual Studio 檔](/visualstudio/)
- [Azure DevOps 文件](/azure/devops/) \(英文\)
- [Azure 檔](/azure/)
- [Microsoft 365 檔](/microsoft-365/)



## <a name="next-steps"></a>下一步
- 了解如何[指派訂用帳戶](assign-license.md)
- 深入了解[訂用帳戶權益](https://visualstudio.microsoft.com/vs/benefits/)的完整範圍
- [設定合約喜好設定](admin-prefs.md)