---
title: 管理入口網站中的超級管理員和系統管理員角色
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/02/2020
ms.topic: conceptual
description: 了解超級管理員和系統管理員角色，以及如何指派系統管理員。
ms.openlocfilehash: ef0ba479c099bf1e34fe871386984297b130ffd6
ms.sourcegitcommit: 9eff8371b7a79a637ebb6850f775dd3eed343d8b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2020
ms.locfileid: "78234815"
---
# <a name="super-admins-and-administrators-for-visual-studio-subscription-agreements"></a>Visual Studio 訂用帳戶合約的超級管理員和系統管理員

大量授權客戶的新 Visual Studio 訂用帳戶管理入口網站中有兩個不同角色。 這些角色像是之前存在於 VLSC 中的主要/通知連絡人角色和訂用帳戶管理員角色。

**超級管理員：** 一開始設定組織時，主要或通知連絡人預設會成為超級管理員。 主要或通知連絡人可以選擇指派其他的超級管理員或系統管理員。 超級管理員可以新增和移除其他系統管理員以及訂閱者。 如果系統中有兩個以上的超級管理員，則超級管理員可以刪除所有超級管理員，但最後必須保留兩個以策安全。

系統**管理員：** 系統管理員只能由超級管理員指派。系統管理員只能管理超級管理員指派給他們的合約中的「訂閱者」。

## <a name="assigning-administrators"></a>指派系統管理員
指派新的系統管理員：
1. 使用指派為用於購買訂用帳戶的合約上超級管理員電子郵件地址登入 https://manage.visualstudio.com。
2. 按一下標示為 [管理系統管理員] 的索引標籤。
3. 按一下 [新增]。
   > [!div class="mx-imgBorder"]
   > ![新增系統管理員](_img/admin-roles/add-admins.png)
4. 使用新系統管理員的資訊來完成表單。  
   > [!div class="mx-imgBorder"]
   > ![新增系統管理員表單](_img/admin-roles/add-form.png)

   > [!NOTE]
   > 如果您想要讓此系統管理員能夠指派其他系統管理員，請記得核取 [超級管理員] 方塊。

5. 當您按一下 [新增] 指派新的系統管理員之後，他們會收到一封電子郵件，邀請他們登入入口網站。  

## <a name="resources"></a>資源
- [Visual Studio 管理與訂閱支援](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="see-also"></a>另請參閱
- [Visual Studio 檔](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 檔](https://docs.microsoft.com/azure/devops/)
- [Azure 文件](https://docs.microsoft.com/azure/)
- [Microsoft 365 檔](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>後續步驟
- 了解如何[指派訂用帳戶](assign-license.md)
- 深入了解[訂用帳戶權益](https://visualstudio.microsoft.com/vs/benefits/)的完整範圍
- [設定合約喜好設定](admin-prefs.md) 


